# Global Antigravity Agent Rules

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

## 1. Think Before Coding

Don't assume. Don't hide confusion. Surface tradeoffs.

Before implementing:

- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them — don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

Minimum code that solves the problem. Nothing speculative.

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

Touch only what you must. Clean up only your own mess.

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it — don't delete it.

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

Define success criteria. Loop until verified.

Transform tasks into verifiable goals:

- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:

1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

These guidelines are working if: fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

<!-- context7 -->

## 5. Context7 — Library/Framework Docs

Use Context7 MCP to fetch current documentation whenever the user asks about a library, framework, SDK, API, CLI tool, or cloud service — even well-known ones (React, Next.js, Prisma, Express, Tailwind, Django, Spring Boot). This includes API syntax, configuration, version migration, library-specific debugging, setup instructions, and CLI tool usage. Use even when you think you know the answer — your training data may not reflect recent changes. Prefer this over web search for library docs.

Do not use for: refactoring, writing scripts from scratch, debugging business logic, code review, or general programming concepts.

**Steps:**

1. Always start with `resolve-library-id` using the library name and what to look up, unless the user provides an exact `/org/project` ID.
2. Pick the best match by: exact name match, description relevance, code snippet count, source reputation (High/Medium preferred), and benchmark score. If results look wrong, try alternate names or queries. Use version-specific IDs when the user names a version.
3. `query-docs` with the selected library ID, scoped to a single concept per call. If the question spans multiple distinct concepts (routing + auth + caching), issue one `query-docs` call per concept — combined queries dilute ranking.
4. Answer using the fetched docs.
<!-- context7 -->

---

## 6. ripwire + context-mode Orchestration

### 6.0 The Two Jobs, In One Sentence Each

- **ripwire answers "how is this code connected?"** — symbols, callers, callees, blast radius, ownership. Local, deterministic, zero-dependency binary. Never calls a model, never sends code anywhere, needs no API key.
- **context-mode answers "what is inside this output?"** — file content, command output, logs, fetched web docs, JSON/CSV, browser snapshots. Runs the reading/parsing/filtering **inside a sandbox** so raw bytes never enter the conversation — only what the agent prints comes back.

**Antigravity Agent is the orchestrator.** It never reads large raw content by hand and never guesses dependencies by hand. Map first (ripwire), then read content (context-mode), then act — proportional to task size (see 6.7).

### 6.1 Respect Each Project's Own Skill System (progressive loading)

Both projects ship many skills; loading every description at once wastes context. Follow their own design intent:

- **ripwire ships ~16 usable skills** (plus one contributor-only skill, `ripwire-opt-remarks`, irrelevant unless building ripwire itself — never load it). Expose only the entry point:
  - `ripwire-router` — reads the task in one line and routes to the right deeper skill (`ripwire-orient` for cold orientation, `ripwire-repo-map` for architecture, `ripwire-find-bug` for bug hunting, `ripwire-fresh-eyes` for second-opinion review, `ripwire-security-scan` for security).
  - Treat `ripwire-router` as mandatory-first for any ripwire-shaped task; let it route to a deeper skill only when the task actually needs it.
- **context-mode ships one primary routing skill** (`context-mode`, plus `ctx-doctor` diagnostics and platform variants). Keep `context-mode` always active — it carries the MANDATORY rule in 6.4; never weaken or skip it.

### 6.2 Master Rule (say this to the agent, verbatim)

> "Before touching any code: ask 'do I need to know how this connects (ripwire), or what is inside this content (context-mode)?' Never use one tool to answer the other tool's question. Never read raw source, logs, or command output by hand when either tool can answer with less context — unless the task qualifies for the fast path in 6.7."

### 6.3 ripwire — Structural Layer

Core idea: ripwire parses the repo into symbols and call edges, ranks them with PageRank, and for a task query uses BM25 to pick anchor symbols, then walks the graph (Personalized PageRank). It only surfaces things that are both text-matched and structurally central. It is **honest about uncertainty** — if nothing scores well, it returns nothing and says so (`confidence="low"`, `reason="no_candidates"`) instead of padding the answer.

| Agent needs to know                                                  | Verb / Skill                               |
| -------------------------------------------------------------------- | ------------------------------------------ |
| Cold orientation in a repo/subdir before reading anything            | `analyze`, or skill `ripwire-orient`       |
| "What's here to reuse before I build something new?"                 | `for` (a reuse lens — not a locator)       |
| A symbol's direct neighborhood (who calls it, what it calls)         | `find_symbol` / `find_referencing_symbols` |
| Full transitive blast radius before changing/deleting a symbol       | `impact`                                   |
| Read/write/import sites, not just calls (before a rename)            | `uses`                                     |
| Does A reach B, and how?                                             | `path_between`                             |
| Interface + every implementor                                        | `lego`                                     |
| Bus-factor / who owns this file                                      | `owners`                                   |
| Files that historically change together (Shotgun Surgery)            | `cochange`                                 |
| Best existing pattern in the repo to imitate before writing new code | `exemplar`                                 |
| Map a stack trace / compiler error onto real symbols                 | `from_trace`                               |
| Did my edit change a function's contract, and who breaks?            | `edit_check`                               |
| Pre-PR quality regression check (complexity, dead code, duplication) | `quality_delta`                            |
| Bug hunting session                                                  | skill `ripwire-find-bug`                   |
| Second-opinion / fresh review of a change                            | skill `ripwire-fresh-eyes`                 |
| Security-focused pass                                                | skill `ripwire-security-scan`              |
| One-call full task orientation (ranking + bodies + callers + tests)  | `explore`                                  |
| Not sure which verb fits                                             | `--help-task="..."` (ask ripwire itself)   |

**Hard rules:**

1. **Never** use ripwire to dump or read full file contents to understand "what's inside" — that's context-mode's job. `fetch_body` exists only to pull the _specific_ body a graph query already pointed at.
2. **Always** run `impact`/`uses`/`edit_check` before and after a non-trivial edit — before to know blast radius, after to confirm no broken contract. (Trivial edits: see 6.7.)
3. **Always** treat `confidence="low"`, `graph_ambiguous`, `graph_unresolved`, and "0 candidates" as real answers meaning "look elsewhere" — never silently retry with different wording until a match appears.
4. ripwire is weak on data-heavy repos (mostly JSON/config, little call-graph depth). If the target directory is data, not code, skip straight to context-mode.
5. If ripwire is unavailable or errors out, follow the fallback in 6.6 — do not silently substitute manual keyword search without saying so.

### 6.4 context-mode — Content Layer

The official skill states one mandatory rule:

> **Default to context-mode for ALL commands. Only use plain shell for guaranteed-small-output operations.**

**"Guaranteed-small-output" is defined concretely, not left to judgment:**

- File reads: allowed directly (no context-mode) only if the file is under ~20 lines OR you already know from context (e.g. a prior `ls`) that it's small.
- Command output: allowed directly only for commands with inherently bounded, small output — `pwd`, `which`, `echo`, `git status` (short repos), single-package `npm view <pkg> version`, etc.
- Anything where output size is unknown, unbounded, or could plausibly exceed ~50 lines / a few hundred tokens (logs, test runs, `git diff`, `git log`, directory listings of unknown size, API responses, build output) **must** go through context-mode.
- When genuinely unsure, default to context-mode — the cost of a wrong guess (dumping raw output into the conversation) is much higher than one extra sandbox call.

**Shell whitelist (safe to run directly, never needs context-mode):**
File mutations (`mkdir`, `mv`, `cp`, `rm`, `touch`, `chmod`) · git writes (`add`, `commit`, `push`, `checkout`, `branch`, `merge`) · navigation (`cd`, `pwd`, `which`) · process control (`kill`, `pkill`) · package installs (`npm install`, `pip install`) · trivial output (`echo`, `printf`).

**Everything else** — anything that reads, queries, fetches, lists, logs, tests, builds, diffs, inspects, or calls an external service (any CLI: `gh`, `aws`, `kubectl`, `docker`, `terraform`, etc.) — goes through `ctx_execute` or `ctx_execute_file`.

**Which tool for which situation:**

| Situation                                                                    | Tool                                                                                                                                                                                       |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Hit an API, run a CLI, run tests, git log/diff                               | `ctx_execute`                                                                                                                                                                              |
| Read/parse a specific file (log, CSV, JSON, source) without loading it whole | `ctx_execute_file`                                                                                                                                                                         |
| Fetch external docs/URL (never `cat` a URL, never re-implement a fetch)      | `ctx_fetch_and_index` → then `ctx_search`                                                                                                                                                  |
| Multiple related commands you'd otherwise run one by one                     | `ctx_batch_execute`                                                                                                                                                                        |
| Recall something already indexed earlier in this session                     | `ctx_search`                                                                                                                                                                               |
| Browser snapshot / console / network inspection (Playwright)                 | Save with the tool's `filename` param first, then `ctx_index(path)` or `ctx_execute_file(path)` — never pass large snapshot output straight into context or into `ctx_index(content: ...)` |
| Output from another MCP tool already visible in context                      | Use it directly — do **not** re-index it                                                                                                                                                   |
| Wipe indexed content                                                         | `ctx_purge(confirm: true, ...)` — destructive, needs an explicit scope                                                                                                                     |

**Hard rules:**

1. **Always print the derived answer, not the raw data.** `console.log`/`print` only what the agent actually needs (counts, specific bad rows, IDs, line numbers) — never `console.log(JSON.stringify(everything))`.
2. **Never** use context-mode to read a file the agent is about to _edit_ — use the normal file-read tool so the subsequent edit can match exact text. context-mode is for analysis, not editing.
3. **Never** call `ctx_index(content: <big text>)` — that pushes big text through context as a parameter. Use `ctx_index(path: ...)` so the file is read server-side.
4. **Batch every related search into one `ctx_search` call** using the `queries` array — never issue multiple separate search calls for questions that could be asked together.
5. **Always scope with `source`** when more than one thing has been indexed, to avoid mixing results from unrelated documents.
6. If context-mode's sandbox is unavailable or errors out, follow the fallback in 6.6 — do not silently fall back to raw shell reads without saying so.

### 6.5 Non-Overlap (Hard Constraint)

Every information need is answered by exactly one of the two layers. Never let both answer the same question, and never let one substitute for the other:

```
❌ ripwire      → "what does this file contain"     (that's context-mode)
❌ context-mode → "who calls this function"          (that's ripwire)
```

If a need could plausibly go either way: relationship/dependency questions default to **ripwire**; content/volume questions default to **context-mode**.

### 6.6 Fallback When a Tool Fails or Is Unavailable

Neither tool is guaranteed to be installed or reachable in every project. If a required tool call errors, times out, or the MCP server isn't configured:

1. **Say so explicitly** in your response — name the tool and the failure (e.g. "ripwire isn't available in this project, falling back to manual search").
2. **Do not silently substitute** the old manual pattern (grepping, reading many files by hand) without disclosure — that defeats the point of this workflow and hides degraded confidence from the user.
3. **Retry once** if the failure looks transient (timeout, cold start). Do not retry indefinitely.
4. If the fallback path is used, treat its output with lower confidence than the tool's would have been, and say so if it affects a downstream decision (e.g. "I couldn't verify blast radius via ripwire, so please double-check callers of X manually").

### 6.7 Proportional Workflow — Full Path vs. Fast Path

**Full two-stage workflow (default, for non-trivial changes):**

```
1. ripwire      → map the relevant symbols & dependencies (ripwire-router
                  picks the right lens: orient / repo-map / find-bug / etc.)
2. ripwire      → compute the affected graph (impact / find_referencing_symbols)
3. context-mode → pull ONLY the source content the map in steps 1-2 named
                  (never a broad glob like src/**/*.tsx)
4. Read/inspect those specific files before editing (normal Read tool)
5. Make the smallest safe change
6. Run the relevant tests (via context-mode's ctx_execute if output could be large)
7. ripwire      → re-run edit_check / impact / quality_delta to confirm no
                  regression in contract or quality
8. If a design doc claims the old structure, run ripwire's doc_drift check
```

**Fast path (skip to step 4 — read, edit, test):** allowed only when ALL of these hold:

- The user named the exact file and location (e.g. "fix the typo in `utils/date.ts` line 42", "change this one config value").
- The change is confined to a single function or a single file, with no rename/signature change that could affect callers.
- The file is not a shared interface, exported type, or something `lego`/`uses` would plausibly show many dependents for.

If any of those don't clearly hold, use the full path — when in doubt, map first. Even on the fast path, still run `edit_check` (step 7) before calling the task done if the change touches a function signature or exported symbol.

Do **not** substitute the full path with the old, expensive pattern of manually searching keywords and reading many files to guess at dependencies for genuinely non-trivial changes — that is exactly the cost this two-tool setup exists to remove.

### 6.8 Call Budget

To prevent unbounded search loops on large repos:

- Cap ripwire mapping calls at **3** per task before either acting on the best available signal or explicitly telling the user the mapping was inconclusive.
- Cap context-mode content-pull calls at **5** per task unless the user's request explicitly spans more files than that.
- If a budget is hit without a clear answer, stop and report what was found plus what remains uncertain — don't keep searching hoping for a better result.

### 6.9 Guardrail: Avoid MCP Tool Explosion

- Only expose the tools this workflow actually uses. Don't add unrelated MCP servers (SonarQube, Git hosting, filesystem browsers, etc.) for needs already covered above.
- Restrict MCP permissions in Antigravity to what's needed:

```
mcp(ripwire/*)
mcp(context-mode/ctx_execute)
mcp(context-mode/ctx_execute_file)
mcp(context-mode/ctx_batch_execute)
mcp(context-mode/ctx_search)
mcp(context-mode/ctx_index)
mcp(context-mode/ctx_fetch_and_index)
```

- Only load `ripwire-router` and the main `context-mode` skill by default; let them route to deeper skills on demand (6.1).

### 6.10 Worked Example

Task: _"Fix Talent Analytics so every card follows Time Machine."_

```
Step 1 — ripwire-router → routes to ripwire-orient / analyze
  Map: TimeMachine → TimeMachineStore, useTimeMachine,
       Analytics → TalentDistribution, TalentCategory, TeamDistribution

Step 2 — ripwire.impact / find_referencing_symbols
  TalentAnalytics → TalentAnalyticsCard → useTalentAnalytics → analyticsQuery

Step 3 — context-mode.ctx_execute_file, one call per file named above
  (NOT a glob over the whole src/ tree)
  TalentAnalytics.tsx, useTimeMachine.ts, TalentAnalyticsCard.tsx,
  analytics-query.ts, types.ts

Step 4 — Agent reasoning: STRUCTURE (ripwire) + CONTENT (context-mode) + TASK
       → EDIT

Step 5 — Run tests via context-mode (ctx_execute) if output may be long

Step 6 — ripwire.edit_check + quality_delta → confirm no contract/quality
       regression before calling the task done
```

This task doesn't qualify for the fast path (6.7): it touches a shared card component and a hook, both plausible callers of other cards, so the full map-first path is correct here.

---

## 7. Testing Policy: No Automated Browser Testing

**CRITICAL RULE:** Never open or automate the browser (do NOT use `browser_subagent` or automated browser sessions) to test, verify, or capture UI changes. Always instruct the user to perform manual testing by providing the target URL and a concise step-by-step verification checklist.

## 8. Enforcement Statement (paste into agent system rules verbatim)

> "Before changing any code: (1) if the task doesn't clearly qualify for the fast path (Section 6.7), you MUST use `ripwire` (starting from `ripwire-router`) to map the relevant symbols and dependencies first; (2) you MUST use `context-mode` only to pull the specific content that map identified — broad, unmapped reads or greps are not allowed; (3) after editing, you MUST re-run `ripwire` (`edit_check`/`impact`/`quality_delta`) to confirm nothing broke, unless the fast path applied and the change didn't touch a signature or exported symbol. Skipping any of these steps outside the fast path is a workflow violation, not a style choice. If a tool fails, disclose it and follow the fallback in Section 6.6 — never silently substitute the old manual pattern. If you catch yourself using the wrong tool for a question (Section 6.5), stop, re-check the routing table, and redo the step with the correct tool before continuing. Never exceed the call budget in Section 6.8 without reporting your findings so far."
>
> **NO AUTOMATED BROWSER TESTING** — see Section 7. This applies regardless of how the task is phrased.

---
