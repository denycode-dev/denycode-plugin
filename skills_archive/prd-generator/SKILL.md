---
name: prd-writing
description: Use this skill whenever the user asks to create, revise, or review a PRD (Product Requirements Document) for a software feature — including requests phrased as "help me plan feature X", "buatkan dokumen requirement", "I want to add feature Y, write the PRD", "design the database and API for this feature", or when the user attaches a SQL schema/ERD/sample API response and asks for a new feature to be designed on top of it — even if the word "PRD" is never used. Especially suited for engineering-facing technical PRDs that combine business rules, database schema changes, and API contracts in one document — not narrative product-marketing PRDs.
---

# Writing a Good Technical PRD

## Language rule (read this first)

This skill's own instructions are written in English, but **every PRD you produce, every clarifying question you ask, and every reply to the user must be written in the user's language** (Bahasa Indonesia by default for this workspace, unless the user writes in another language). Do not let the English wording of this skill leak into the deliverable — section headers, table labels, and body text in the actual PRD should read naturally in the user's language, not as a translation artifact.

## Why this matters

A technical PRD is read directly by developers for implementation — it is not a narrative memo for non-technical stakeholders. A 2025 Carnegie Mellon Software Engineering Institute analysis found that 60-80% of software development cost goes into rework, and that disciplined requirements management alone can eliminate 50-80% of project defects[^1]. In other words, the leverage of this skill is not "produce a tidy document" — it's **removing ambiguity before a developer writes a single line of code**, by studying what already exists, deciding which decisions genuinely need the user's input versus which can be assumed with a documented rationale, and writing everything in a consistent, verifiable format.

## Workflow

### 1. Study existing context before writing anything

Don't start drafting sections until this is done:
- If the user attaches a SQL schema/ERD, read all of it. Note relations, constraints, and naming conventions already in use (e.g. soft-delete via `deleted_at`, audit columns `created_by`/`updated_by`, FK naming patterns).
- If the user shares an example API response, extract the **exact** envelope shape (`success`/`message`/`data`/`meta`, error format) and preserve it for every new endpoint — don't invent a "better" shape. Industry guidance converges on wrapping payload + metadata in a consistent envelope and using a single, predictable error structure with a machine-readable code and human-readable message, precisely so clients never have to guess the format[^2][^3].
- Check whether a generic table/mechanism already covers the need (e.g. a generic audit-log table) before proposing a new one — reuse should be considered first, then rejected with an explicit reason if it genuinely doesn't fit.
- Frame the underlying problem, not the missing feature. Don't write "users don't have X" — dig into the pain point or inefficiency that X would solve; this keeps the rest of the document anchored in the actual need instead of a pre-chosen solution[^4].

### 2. Calibration: when to ask, when to assume

This is the single highest-leverage decision in the whole workflow.

**Ask the user** (using short multiple-choice questions, at most 2-3 at once, each with 2-4 concrete options) when the decision:
- Fundamentally changes the data model and is expensive to reverse later (e.g. one-to-one vs one-to-many vs many-to-many between core entities).
- Has 2+ options that are equally technically valid but differ significantly in business or UX impact (e.g. embedding a full history vs truncating it and exposing a separate paginated endpoint).
- Has an ambiguous data source across multiple plausible tables.

**Assume and proceed** (then record the assumption explicitly — never assume silently) when:
- An existing, consistent convention already answers the question.
- The decision is cheap to revise later without a major breaking change (label wording, column ordering, error message copy).

Don't ask about things the provided context already answers, and don't silently assume things with large downside — both failure modes degrade the PRD equally.

### 3. Standard structure

Use the section skeleton below consistently. A ready-to-copy empty skeleton lives in `references/prd-template.md` — read it when starting a new draft, and remember to translate every header and label into the user's language when you actually write the PRD (see the language rule above).

| Section | Why it's needed |
|---|---|
| Background | Developers need the underlying problem/gap before they can judge the proposed solution — frame it as a problem, not a missing feature[^4] |
| Goals & Scope/Non-Goals | Prevents scope creep and misunderstanding about what is explicitly *not* being built[^5] |
| Actors & User Flow | Branching flows (login, approval, etc.) are understood faster as a text/ASCII diagram than as prose. For simple flows, the classic user-story shape — "As a `<user>`, I want `<goal>` so that `<benefit>`" — keeps requirements human-centered[^6] |
| Business Rules (numbered table) | Rules must be individually citable during review/QA, not buried in paragraphs. For larger features, tag rules P0/P1/P2 so scope can be trimmed without renegotiating the whole document[^5] |
| Database Schema | Developers need to know WHAT changes and WHY, not just raw DDL |
| API Contract | A wrong contract format means frontend and backend fail to integrate even if the underlying logic is correct[^2][^3] |
| Authorization/Access | Access level for every new endpoint must be explicit, never implied |
| Assumptions & Open Questions | Where every assumed (not asked) decision from Step 2 is recorded, so it can be corrected quickly |
| Non-functional notes (when relevant) | Performance, security, and reliability constraints should not be an afterthought — call them out explicitly whenever a feature is sensitive to them[^5] |
| Schema Change Summary | A 3-4 line recap at the end so a senior reviewer can judge impact without re-reading everything |

### 4. Writing business rules — avoid generic phrasing

**Before (weak):**
> Users can CRUD talent data.

**After (good):**
| # | Rule |
|---|---|
| 5 | CRUD user + set status (`active`/`inactive`); deletion is soft-delete |

A generic rule can't be verified by a developer or QA. A good rule names the concrete operation, the valid enum values, and the deletion mechanism (hard vs soft).

Concrete, testable statements beat vague ones like "user-friendly" or "handles errors gracefully" — vague requirement language is one of the most common root causes of misaligned implementations[^5].

### 5. Writing database schema changes — always justify the reasoning

Use a `Column | Action | Reason` table, not a bare DDL dump. Example:

| Column | Action | Reason |
|---|---|---|
| `status` | Change to enum `pending`\|`active`\|`inactive` | Rules #2 & #5 need these 3 states for approval + activation |

Two additional rules that are easy to miss:
- **Any FK column that will appear in an API response or a log must be resolved to a human-readable label**, not a raw UUID — otherwise the response/log isn't actually usable by whoever reads it.
- **If a generic table already exists that could serve the same purpose**, state the reuse-vs-new-table trade-off explicitly in the PRD (not just in your own reasoning), so the user can see and correct the decision.

### 6. Writing the API contract — consistency is non-negotiable

- Always follow the project's existing response envelope (see Step 1) — never invent a new shape.
- Include **full request AND response JSON examples**, not just a field-by-field description.
- Explicitly define the authorization level (`admin`/`viewer`/etc.) for every new endpoint — never leave it implied.
- Model resources as plural nouns and keep nesting shallow (two levels deep is usually the practical maximum) — this is standard REST guidance that keeps URLs predictable for API consumers[^3][^7].
- For potentially long data (history, logs, lists), state the trade-off between embedding everything vs truncating + a separate paginated endpoint, and treat this as a candidate question (Step 2) whenever it has real performance/UX impact.

### 7. Handling revisions

- When the user gives numbered revisions plus answers to earlier questions, map every answer back to the question it answers before rewriting anything — no answer should go unreflected in the document.
- Apply revisions **exactly to the scope requested**. "Remove section X" means delete it entirely — not shorten it or relocate it.
- Don't silently reverse a decision confirmed in an earlier revision unless the user explicitly asks again in the new revision.
- Treat the PRD as a living document: when a revision touches many sections at once, rewrite the whole document rather than patching fragments, and bump the version number in the header so readers can tell it changed[^5].

### 8. Verify before calling it done

Before handing over a PRD as final, check:

- [ ] Every business rule from the user's request is reflected in the Business Rules table
- [ ] Every new/changed schema column has a stated reason, not just DDL
- [ ] Every API example follows the same envelope format already used elsewhere in the project
- [ ] FK/relation fields in responses or logs are shown as labels, not raw UUIDs
- [ ] Access level (admin/viewer/etc.) is explicit for every new endpoint
- [ ] The Assumptions/Open Questions section lists EVERY decision that was assumed rather than confirmed by the user
- [ ] No decision confirmed in a previous session was silently changed without being asked again
- [ ] The document still follows the standard section structure (Step 3)
- [ ] All headers, labels, and body text are in the user's language, per the language rule at the top

## Boundaries — don't do this

- Don't change or remove a decision the user already confirmed in a previous session without them explicitly asking again.
- Don't introduce a new pattern/schema/naming style inconsistent with the conventions already used in the files the user provided, unless you state an explicit reason in the PRD.
- Don't unilaterally decide high-stakes business policy (data retention, deletion policy, cross-role authorization policy) — this always belongs in the "ask" bucket from Step 2, never a silent assumption.
- Don't insert your own opinions or preferences into the PRD framed as settled business facts.

## Gotchas — lessons from real cases

- Core entity relationships (e.g. how many roles a single user may hold) are often assumed without asking, even though changing them later means a schema migration. Always turn this into an explicit question up front, not an assumption.
- If a display field (e.g. "name") could already be sourced from another table via an existing relation, don't rush to add a new physical column — check whether the data is already reachable via a join first.
- A generic existing log/audit table can look "reusable enough," but its granularity (full snapshot vs per-field diff) may not fit the exact display need — verify granularity before reusing it, don't assume it fits automatically.
- Conditions like "if field X is empty, it means Y" (e.g. no user name means the system completed it automatically) must be written as an explicit rule and reflected in the JSON example — don't leave it implicit in the happy path only.
- "Remove this section" is a final instruction — delete it completely, don't shorten it.

## References

These are the industry sources this skill's guidance is drawn from — worth reading directly for deeper background:

[^1]: Carnegie Mellon Software Engineering Institute (2025) — analysis on requirements engineering and rework cost, cited via Parallel's PRD guide: https://www.parallelhq.com/blog/how-to-write-product-requirements
[^2]: Google Cloud — "RESTful web API Design best practices": https://cloud.google.com/blog/products/api-management/restful-web-api-design-best-practices
[^3]: General REST API design guidance on envelope patterns, standardized error objects, and resource naming (community-aggregated, consistent with Google Cloud's guidance): https://oneuptime.com/blog/post/2026-02-20-api-design-rest-best-practices/view
[^4]: Kuse — "PRD Document Template: How to Write Effective Product Requirements": https://www.kuse.ai/blog/insight/prd-document-template-in-2025-how-to-write-effective-product-requirements
[^5]: Parallel — "How to Write Product Requirements: Guide & PRD Template" (over/under-specifying, non-functional requirements, scope creep, living documents): https://www.parallelhq.com/blog/how-to-write-product-requirements
[^6]: Agile Alliance — user story format ("As a `<user>`, I want `<goal>` so that `<benefit>`"), referenced via: https://www.uladshauchenka.com/p/how-to-write-a-good-product-requirements
[^7]: Atlassian — product requirements guide and Confluence PRD template, widely used as a baseline structure: https://www.atlassian.com/agile/product-management/requirements

For value-risk-heavy features (will anyone actually want this?), consider Amazon's "Working Backwards" PR/FAQ technique as a precursor narrative before the technical PRD — it forces clarity on customer impact before diving into mechanics. See: https://www.uladshauchenka.com/p/how-to-write-a-good-product-requirements

## Reference files

- `references/prd-template.md` — empty PRD section skeleton, ready to copy when starting a new draft. Header labels are shown bilingually (English / Indonesian) as a reminder to translate — the filled-in PRD itself must be entirely in the user's language.