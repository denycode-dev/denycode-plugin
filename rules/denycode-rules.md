# Global Antigravity Agent Rules v3

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

<!-- context7 -->

Use Context7 MCP to fetch current documentation whenever the user asks about a library, framework, SDK, API, CLI tool, or cloud service — even well-known ones like React, Next.js, Prisma, Express, Tailwind, Django, or Spring Boot. This includes API syntax, configuration, version migration, library-specific debugging, setup instructions, and CLI tool usage. Use even when you think you know the answer — your training data may not reflect recent changes. Prefer this over web search for library docs.

Do not use for: refactoring, writing scripts from scratch, debugging business logic, code review, or general programming concepts.

Steps:

1. Always start with `resolve-library-id` using the library name and what to look up, unless the user provides an exact library ID in `/org/project` format.
2. Pick the best match by exact name match, description relevance, code snippet count, source reputation, and benchmark score. Retry with alternate names/queries if results don't look right.
3. `query-docs` with the selected library ID, scoped to a single concept per call — split multi-concept questions into separate calls.
4. Answer using the fetched docs.
<!-- /context7 -->

---

# Command Execution Orchestration: context-mode + RTK

Antigravity uses **context-mode** as the sandbox for heavy analysis (large logs, multi-file diagnostics, doc indexing/search) and **RTK (Rust Token Killer)** as a lightweight, always-on filtering proxy for individual shell commands. They are complementary, not competing: RTK compresses a single command's raw output; context-mode sandboxes multi-step reasoning over that output. Raw, unfiltered bytes must **never** land in conversation context from either path.

## A. The Core Principle (Mandatory)

> **Every shell command that isn't a guaranteed-tiny mutation goes through `rtk` first. Every multi-step analysis, aggregation, or large-file/log inspection goes through context-mode. When both apply, RTK runs _inside_ the context-mode sandbox, not instead of it.**

## B. Decision Tree (check top to bottom, stop at first match)

1. **Tiny, predictable-output mutation?** (`mkdir`, `mv`, `cp`, `rm`, `touch`, `chmod`, `git add`, `git commit`, `git checkout`, `git branch`, `git merge`, `git push`, `kill`, `pkill`, `npm install`/`pip install` quiet, `echo`, `printf`, `pwd`)
   → Run raw in plain shell. No `rtk`, no context-mode — output is already minimal.

2. **Single read/query command with RTK support, and the result will be consumed as-is (no further multi-file aggregation)?** (`git status`, `git diff`, `git log`, `ls`, `grep`, `find`, `docker ps`, `gh pr list`, `cargo test`, etc.)
   → Run directly as `rtk <cmd>` in plain shell. Skip the context-mode sandbox entirely — spinning up `ctx_execute` for a single already-filtered command is wasted overhead.

3. **Same kind of command as #2, but the output still needs programmatic parsing, cross-file aggregation, or the raw output could still be large** (e.g. `git log` across a huge repo, `grep` over a large tree, test runs with verbose failures)?
   → Route through `ctx_execute`, and _inside_ the sandbox call `rtk <cmd>` instead of the raw command before parsing. RTK does the first-pass compression; the sandbox script does the second-pass extraction (counts, failing lines, specific matches). Emit only the derived answer to context.

4. **External docs / remote URLs?**
   → `ctx_fetch_and_index` → `ctx_search`. RTK doesn't apply to network fetches.

5. **Indexing large local files/content for later search?**
   → `ctx_index` with `path:` (server-side). RTK doesn't apply here either — this is content indexing, not command filtering.

6. **About to edit a file?**
   → Never read it via context-mode or `rtk` for this purpose. Use the standard targeted file-read tool so the edit/replace matches exact character sequences.

7. **RTK meta/reporting commands?** (`rtk gain`, `rtk gain --history`, `rtk discover`, `rtk proxy <cmd>`)
   → Run directly in plain shell whenever the user asks about savings or you suspect a missed RTK opportunity. `rtk proxy <cmd>` is for debugging only — bypasses filtering, so never use it as the default path.

## C. Hard Rules for Maximizing Context Efficiency

1. **Always print derived answers, never raw dumps.** Inside `ctx_execute`/`ctx_execute_file`, output counts, specific failing tests, bug details, or exact matching lines — never the full blob, even after RTK has already compressed it once.
2. **Never read files with context-mode when about to edit.** Context-mode/RTK are for analysis and diagnostics only.
3. **Never call `ctx_index(content: <large text>)`.** Always `ctx_index(path: ...)`.
4. **Batch related searches** with `ctx_search`'s `queries: [...]` array instead of separate calls.
5. **Always scope searches with `source`** when multiple documents are indexed.
6. **Don't re-index or re-run RTK on data already in context.** If a prior step already returned the derived output, reuse it.
7. **Don't double-sandbox.** If `rtk <cmd>` alone (step B.2) already gives a small, directly usable answer, do not additionally wrap it in `ctx_execute` — that's redundant overhead RTK was meant to remove.

## D. MCP Permissions Guardrail

Keep MCP scope lean and focused:

```
mcp(context-mode/ctx_execute)
mcp(context-mode/ctx_execute_file)
mcp(context-mode/ctx_batch_execute)
mcp(context-mode/ctx_search)
mcp(context-mode/ctx_index)
mcp(context-mode/ctx_fetch_and_index)
mcp(context-mode/ctx_purge)
```

RTK is a CLI proxy, not an MCP server — it wraps shell invocations regardless of which execution path (plain shell or `ctx_execute`) is used, per the decision tree above.

## E. Enforcement Statement

> "Before executing any reading, querying, testing, or external command: first check whether RTK alone (plain shell, `rtk <cmd>`) already gives a small, directly usable answer — use that path when it does. Otherwise default to `context-mode` (`ctx_execute`/`ctx_execute_file`), calling `rtk <cmd>` for the underlying shell step where RTK supports that command. Never dump raw logs, command outputs, or bulk file contents directly into context when RTK and/or the sandbox can filter, aggregate, and return only the exact answer needed."

> **CRITICAL RULE — NO AUTOMATED BROWSER TESTING:**
> Never open or automate the browser (do NOT use `browser_subagent` or automated browser sessions) to test, verify, or capture UI changes. Always instruct the user to perform manual testing by providing the target URL and a concise step-by-step verification checklist.
