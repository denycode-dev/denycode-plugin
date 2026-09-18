---
name: financial-engineering-principles
description: Apply professional-grade accounting and money-management engineering principles whenever writing, reviewing, or designing code that touches money — ledgers, wallets, balances, transactions, budgets, invoices, payments, expense tracking, currency conversion, or financial reports. Use this skill any time a task involves storing or calculating a monetary amount, designing a database schema for financial data, building a shared/couple balance or settlement feature, implementing a budgeting or reconciliation feature, or reviewing existing financial code for correctness — even if the user never says "accounting," "GAAP," or "ledger" explicitly. Covers exact-precision money representation, double-entry bookkeeping, immutable audit trails, idempotency, transactional/concurrency safety, chart-of-accounts design, multi-currency rounding, reconciliation, and financial data security. Trigger this before generating a single line of code that computes, stores, or moves money.
---

# Financial Engineering & Accounting Principles

## Why this exists

A bug in a to-do app loses a checkbox. A bug in money code loses trust — and
sometimes money, an audit finding, or a legal problem. Financial code doesn't
fail loudly in code review; it fails quietly, months later, when a retry
double-charges someone, a rounding rule drifts by half a cent per transaction,
or two concurrent requests both read the same stale balance. None of these are
exotic edge cases. They are the normal operating conditions of any system that
touches money: retries happen, clocks disagree, users double-tap, currencies
mix, and two people in a shared account edit at the same instant.

The principles below exist to make the *normal* case safe by construction,
not to bolt on correctness after something breaks. Apply them proportionally —
a personal expense tracker doesn't need a bank's core ledger — but never skip
the ones marked **non-negotiable**. Those hold regardless of project size,
because the failure mode they prevent (silent numeric drift, unauditable
history, duplicated transactions) is exactly as damaging in a small app as in
a large one; it just takes longer to notice.

---

## 1. Choose the right ledger model for the problem

Before writing a single table, decide how much accounting rigor the feature
actually needs. Two ends of a spectrum, both legitimate:

- **Full double-entry ledger** — needed whenever money moves *between*
  identifiable parties or accounts, where users need to answer "where did
  this come from / go to," where balances must reconcile against an external
  source (a bank, a payment processor), or where more than one person shares
  visibility into the same funds (a couple's shared account, a family budget,
  a business). This is the "source of truth" pattern used by real payment
  systems.
- **Lightweight append-only ledger** — sufficient for a single user tracking
  their own spending against categories, with no transfers between parties
  and no external reconciliation requirement. It skips formal debit/credit
  bookkeeping but **keeps every other invariant below**: immutable history,
  derived balances, an audit trail, atomic writes.

The costly mistakes run in both directions: bolting a full chart of accounts
onto a single-user habit tracker wastes effort and confuses contributors;
giving a shared/couple balance a single mutable `balance` column guarantees a
"why is my balance wrong and who changed it" support ticket eventually,
because there is no history to answer the question. If a feature involves two
or more people's money in the same place (contribution tracking, expense
splitting, settlement), treat it as needing at least a lightweight ledger with
per-party attribution from day one — retrofitting attribution onto a single
number later means the historical data is unrecoverable.

---

## 2. Never represent money as binary floating point (non-negotiable)

Floating-point numbers (`float`, `double`, JavaScript's `number`) store values
in base 2, which cannot exactly represent most decimal fractions:

```
0.1 + 0.2 === 0.30000000000000004   // JS, Python, Java, C — same root cause
165 * 1.40 === 230.99999999999997   // "sell 165 apples at $1.40" is already wrong
```

These aren't rare glitches; they're guaranteed behavior of IEEE 754, and the
errors compound with every operation. A model asked to "calculate the total"
will reach for `number`/`float` by default because that's the common pattern
in general-purpose code — override that default explicitly for anything
monetary.

**Rules to apply:**

- Represent amounts as either an **integer count of the currency's smallest
  unit** (e.g. cents: `1999` for $19.99) or an **arbitrary-precision decimal**
  type (`NUMERIC`/`DECIMAL` in Postgres, `BigDecimal` in Java, `decimal.Decimal`
  in Python, a decimal library in JS such as `decimal.js` or `dinero.js`, a
  scaled `int64` or `decimal` package in Go).
- Never store or transmit money as a bare number without its currency — a
  `Money` value pairs `{ amount, currency }` always. `100` is meaningless;
  `$100` and `¥100` are different amounts of value.
- Decide and document **where rounding happens** (see §8) — don't let it
  happen implicitly wherever a division occurs.

```ts
// TypeScript — minor units + explicit currency
type Money = { readonly minorUnits: bigint; readonly currency: string }; // "USD", "IDR"

function add(a: Money, b: Money): Money {
  if (a.currency !== b.currency) throw new Error("currency mismatch");
  return { minorUnits: a.minorUnits + b.minorUnits, currency: a.currency };
}
```

```sql
-- Postgres — NUMERIC, never FLOAT/REAL, for anything monetary
amount        NUMERIC(19, 4) NOT NULL,
currency_code CHAR(3)        NOT NULL, -- ISO 4217
```

```go
// Go — integer minor units keeps arithmetic exact and fast
type Money struct {
    MinorUnits int64  // 1999 = $19.99
    Currency   string // ISO 4217
}
```

---

## 3. The transaction history is the source of truth, not a balance column (non-negotiable)

The tempting design is one mutable `balance` field per account, incremented
and decremented in place. It is wrong for the same reason a codebase with no
version control is wrong: there's a number, but no way to explain how it got
there, and no protection against a crash that updates one side of a transfer
without the other.

**Rules to apply:**

- Model every movement of money as an **entry appended to an immutable log**,
  never an in-place update to a running total. The balance of an account is
  the sum (or last verified snapshot + subsequent sum) of its entries —
  computed, not independently maintained as the only record.
- **Never `UPDATE` or `DELETE` a financial record that has already been
  committed.** A correction is a new entry that reverses the original
  (a "credit memo," a compensating transaction), so the full history —
  including the mistake and its fix — stays visible. This is what makes the
  system auditable and what lets you answer "why is this number what it is"
  months later.
- Every entry carries **who, what, when, and why**: an actor (user or system
  process), a timestamp, a reference to the source event (an API call, an
  imported bank line, a recurring job run), and enough context to reconstruct
  intent without guessing.

```sql
-- Minimal double-entry shape (works for a couple/shared app too:
-- each "account" can represent a person, a category, or a shared pool)
CREATE TABLE accounts (
  id            UUID PRIMARY KEY,
  owner_id      UUID NOT NULL,          -- which user/entity this belongs to
  type          TEXT NOT NULL,          -- asset | liability | income | expense | equity
  currency_code CHAR(3) NOT NULL,
  created_at    TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE transactions (
  id           UUID PRIMARY KEY,
  occurred_at  TIMESTAMPTZ NOT NULL,     -- when the economic event happened
  recorded_at  TIMESTAMPTZ NOT NULL DEFAULT now(), -- when it entered the system
  description  TEXT,
  source_ref   TEXT,                     -- idempotency / external reference (see §5)
  reversed_by  UUID REFERENCES transactions(id) -- set if this txn was corrected
);

CREATE TABLE entries (
  id             UUID PRIMARY KEY,
  transaction_id UUID NOT NULL REFERENCES transactions(id),
  account_id     UUID NOT NULL REFERENCES accounts(id),
  amount         NUMERIC(19,4) NOT NULL, -- positive = debit, negative = credit (pick one convention, document it)
  created_by     UUID NOT NULL,          -- actor for the audit trail
  created_at     TIMESTAMPTZ NOT NULL DEFAULT now()
);

-- Every transaction must balance to zero across its entries.
-- Enforce with a trigger or an application-level check inside the same DB transaction.
```

If the feature is genuinely single-user with no transfers (a personal expense
log), a single `entries`-style append-only table without a full debit/credit
model is fine — but it still must be append-only with a derived balance and a
full audit trail. The formality of double-entry is optional; immutability and
traceability are not.

---

## 4. Wrap every financial write in an atomic, correctly isolated transaction (non-negotiable)

Multi-row financial writes (debit one account, credit another; deduct a
budget, log an expense) must succeed or fail together. A partial write — one
side committed, the other lost to a crash or a timeout — is exactly how books
stop balancing.

**Rules to apply:**

- Wrap every operation that touches more than one financial row in a single
  database transaction (`BEGIN…COMMIT`), so a failure midway rolls back
  cleanly instead of leaving the ledger inconsistent.
- Watch for the classic **read-then-write race**: request A reads a balance,
  request B reads the same balance, both compute a new value from the stale
  read, and one write clobbers the other. Under PostgreSQL's default `READ
  COMMITTED` isolation this can happen even though the database is "ACID."
  Guard against it with one of:
  - a single atomic SQL statement (`UPDATE accounts SET balance = balance - $1
    WHERE id = $2 AND balance >= $1`) instead of separate read/compute/write
    steps in application code,
  - explicit row locking (`SELECT … FOR UPDATE`) before modifying a balance,
  - or `SERIALIZABLE` isolation with retry-on-conflict logic for the
    highest-stakes paths (transfers, settlement).
- Add database-level invariants as a second line of defense, not just
  application logic: a `CHECK` constraint that a balance never goes negative
  where that's a real rule, a constraint or trigger that a transaction's
  entries sum to zero. Application bugs will happen; let the database refuse
  to persist an impossible state.

---

## 5. Make every money-moving operation idempotent (non-negotiable)

Networks retry. Users double-click a "Pay" button on a slow connection. Queue
messages get redelivered. Any of these turning into a duplicate charge or a
duplicate ledger entry is a direct financial bug, not a cosmetic one.

**Rules to apply:**

- Every API endpoint or background job that **creates** a financial record
  must accept (or generate) an idempotency key — a client-supplied UUID, or a
  natural key from the source system (a payment provider's transaction ID, a
  bank statement line's unique reference).
- Persist the idempotency key alongside the record it produced. On a repeat
  request with the same key, return the original result instead of creating a
  new one — don't just silently ignore the retry, actually hand back what was
  already done so the caller can confirm success.
- If a retry arrives with the *same key but a different payload*, treat that
  as an error, not a silent overwrite — it signals a client bug or a replay
  attack, not a legitimate retry.

```sql
CREATE TABLE idempotency_keys (
  key             TEXT PRIMARY KEY,
  request_hash    TEXT NOT NULL,       -- fingerprint of the request payload
  transaction_id  UUID REFERENCES transactions(id),
  created_at      TIMESTAMPTZ NOT NULL DEFAULT now()
);
-- On each write request: look up the key inside the same DB transaction
-- that would create the financial record, so the check-then-insert is atomic.
```

---

## 6. Let accounting principles — not just code correctness — shape the design

These come from GAAP but they're really just accumulated hard-won judgment
about what makes financial numbers *meaningful*, translated into engineering
rules:

- **Accrual over cash timing, when timing matters.** Record an economic event
  when it happens, not only when money settles. A budget feature that only
  logs an expense once a bank clears it will always feel a day behind reality
  to the user; distinguish *pending* vs *cleared* rather than hiding pending
  activity entirely.
- **Matching.** Tie an expense or income to the period and category it
  actually belongs to, not just the moment it was typed in — a subscription
  charged annually shouldn't distort one month's "spending" chart if the
  feature's purpose is to show ongoing burn rate.
- **Consistency.** Don't silently change a rounding rule, a categorization
  algorithm, or a currency-conversion source mid-stream — version such rules
  so historical reports remain reproducible and explainable.
- **Conservatism.** Don't present uncertain or unconfirmed money as if it
  were settled fact. A pending transfer, an estimated exchange rate, or a
  provisional balance should be visibly distinguished from confirmed figures.
- **Materiality.** Not every number needs six decimal places or a push
  notification. Decide deliberately what precision and what threshold of
  change actually matters to the person using the feature, and don't drown
  signal in noise.
- **Full disclosure / traceability.** Any total or chart shown to a user
  should be traceable back to the specific entries that produced it. If a
  user can't ask "why is this number X" and get a real answer from the data,
  the report is a black box, and black boxes erode trust exactly where trust
  matters most.
- **Economic entity separation.** Never co-mingle two people's or two
  entities' money in one record without an explicit ownership or split field.
  This is the single most common design flaw in shared/couple money apps:
  a "family balance" that doesn't actually track who contributed or who owes
  whom cannot answer basic questions the moment two people disagree about it.

---

## 7. Design a categorization system (chart of accounts) that scales

- Structure categories hierarchically — a small set of top-level types
  (e.g. income / expense / transfer / savings for a personal app; asset /
  liability / equity / income / expense for anything closer to formal
  bookkeeping) with groups and leaf categories underneath.
- Give every category a **stable identifier**, separate from its display
  label. Labels get renamed, re-translated, or reworded; reports and
  historical entries must keep pointing at the same underlying category
  regardless.
- Let users add custom leaf categories under the fixed top-level types, but
  don't let the *type* taxonomy itself sprawl freely — that's what keeps
  aggregate reporting (totals by type) meaningful across the whole system.
- Keep it as simple as the use case allows. An over-engineered chart of
  accounts with dozens of categories nobody uses is as much a design failure
  as one with too few to be useful.

---

## 8. Handle currency and rounding deliberately

- Use ISO 4217 currency codes, and don't hardcode "2 decimal places" —
  minor-unit precision varies by currency (JPY and KRW have 0 minor units;
  most currencies have 2; a few have 3).
- Never convert currency implicitly or silently. Store the original amount
  and currency as recorded; if a converted value is shown, store the
  exchange rate used and the timestamp it was fetched, so the conversion is
  reproducible and auditable rather than a black box.
- Pick **one explicit rounding rule** (round-half-to-even / "banker's
  rounding" is the common professional default because it doesn't bias sums
  upward over many transactions) and apply it **only at defined aggregation
  or display boundaries** — not repeatedly mid-calculation, where rounding
  errors compound invisibly across many small operations.

---

## 9. Reconcile and verify continuously, not just when something looks wrong

- Turn accounting invariants into automated checks rather than manual
  review: every transaction's entries must sum to zero; every account's
  computed balance must match any cached/denormalized balance; scheduled
  jobs should compare the internal ledger against an external source of
  truth (a bank feed, a payment gateway's records) where one exists.
- Treat a reconciliation mismatch as a first-class alert someone has to look
  at, not a line buried in a log file. Silent drift is how small bugs become
  large, hard-to-unwind discrepancies.
- Write these invariants as tests, not just runtime checks: property-based or
  scenario tests that assert "the sum of all entries for any transaction is
  zero," "an account balance never goes negative when the business rule says
  it shouldn't," and "replaying the same idempotency key never creates a
  second record."

---

## 10. Protect financial data like it's sensitive by default

- Encrypt financial data at rest and in transit; don't treat this as optional
  because "it's just a budgeting app."
- **Minimize what's stored.** Don't store full card or bank account numbers
  if a tokenized reference from a payment/banking provider will do; if PCI
  DSS-scoped data (full card numbers) is ever involved, that scope should be
  pushed to a certified processor rather than handled directly.
- Apply least-privilege access control, and **log access to financial
  records, not just changes to them** — who viewed what matters for
  sensitive financial data, not only who edited it.
- In shared/couple or multi-party contexts, make sure both parties see the
  same underlying source of truth. A design where one person's edits are
  invisible or reversible only by them, with no shared audit trail, recreates
  the "why is the balance wrong" problem at a relationship level, not just a
  technical one.

---

## 11. Money-management product specifics (budgeting, expense tracking, shared accounts)

- Make the **budgeting methodology pluggable**, not hardcoded — zero-based,
  50/30/20, and envelope budgeting are different allocation strategies over
  the *same* underlying transaction and category data. Model the allocation
  rule as configuration, so the choice belongs to the user, not the schema.
- For shared or couple money: every shared transaction needs an explicit
  **who paid** and **how it should be split** (equal, percentage, fixed
  amount), and settlement between two parties is itself a real ledger entry —
  not a number subtracted somewhere and forgotten. This is what lets either
  person later ask "who owes whom, and why" and get a real answer.
- Recurring transactions should generate real, dated ledger entries (or an
  explicit, visible "upcoming/projected" entry pending confirmation) rather
  than being silently assumed to have happened. A projected transaction and a
  confirmed one are not the same fact and must not be presented as if they
  were (see conservatism, §6).

---

## 12. Pre-ship checklist

Before merging code that stores, computes, or moves money, confirm:

- [ ] No `float`/`double`/JS `number` is used for a monetary amount anywhere
      in the change — minor-unit integers or a decimal type only.
- [ ] Every amount is paired with its currency; no bare numeric amount is
      passed or stored without one.
- [ ] Financial records are inserted, never updated/deleted, after commit;
      corrections are modeled as reversing entries.
- [ ] Every write that touches more than one financial row happens inside one
      database transaction.
- [ ] Balance-affecting reads-then-writes are protected against race
      conditions (atomic SQL, row locks, or serializable isolation) — verified
      with a concurrent test, not just reasoning about it.
- [ ] Every endpoint/job that creates a financial record accepts or derives
      an idempotency key, and repeat requests are provably safe.
- [ ] Rounding happens at one well-defined, documented boundary, using one
      consistent rule.
- [ ] Every total or report shown to a user is traceable back to the entries
      that produced it.
- [ ] Access to financial data is least-privilege and logged.
- [ ] There is at least one automated test asserting the core invariant
      (entries sum to zero / balance matches ledger / idempotent replay is
      safe) — not just a happy-path unit test.

---

## 13. Anti-patterns — treat any of these as a stop-and-reconsider signal

- A `balance` column updated in place with no backing transaction history.
- Money stored as `float`/`double`/plain JS `number`.
- An amount stored or passed without its currency.
- A financial record that gets `UPDATE`d or `DELETE`d after it was committed.
- A multi-account money movement implemented as two separate, unwrapped
  writes instead of one atomic transaction.
- A "Pay" or "Transfer" endpoint with no idempotency key, relying on the
  client to "just not click twice."
- Currency conversion applied silently, with no stored rate or timestamp.
- Rounding applied repeatedly inside a loop or a chain of calculations
  instead of once at a defined boundary.
- A shared/couple balance with no per-person attribution — just one number
  two people both edit.
- A dashboard total that can't be traced back to the underlying transactions
  that produced it.

---

## 14. Quick reference — money type per stack

| Stack | Use this for monetary amounts | Avoid |
|---|---|---|
| PostgreSQL | `NUMERIC(19,4)` (or integer minor units) | `FLOAT`, `REAL`, `MONEY` type (locale-dependent, avoid) |
| TypeScript / JavaScript | `bigint` minor units, or a decimal library (`decimal.js`, `dinero.js`) | plain `number` |
| Go | `int64` minor units, or `shopspring/decimal` | `float32`/`float64` |
| Python | `decimal.Decimal` | plain `float` |
| Java / Kotlin | `BigDecimal`, or an integer minor-unit `long` | `float`/`double` |