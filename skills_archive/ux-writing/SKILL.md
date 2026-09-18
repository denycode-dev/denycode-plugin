---
name: ux-writing
description: Write, review, or rewrite any UX copy — UI text, buttons/labels, microcopy, error messages, empty states, notifications, onboarding text, form fields, tooltips, link text, headings, or confirmation dialogs — according to the Clear/Concise/Useful UX writing principles (based on Nielsen Norman Group research). Use this whenever the user asks to write copy for an app/website interface, review or audit existing UI text, fix a vague or wordy button/label/error/toast message, or asks for "UX writing", "microcopy", "UI copy", or feedback on interface wording — in any language. Always apply this skill instead of writing generic copy from intuition.
---

# UX Writing

A skill for producing and reviewing interface copy (UI text, buttons, labels, errors, empty states, notifications, links, onboarding, tooltips) using the three core UX writing principles — **Clear, Concise, Useful** — grounded in Nielsen Norman Group (NN/g) research.

This skill works in **any situation**: writing new copy from scratch, rewriting/auditing existing copy, or reviewing a whole screen/flow. It also works in any language the user is writing in — the principles are language-agnostic; apply them to the user's language rather than translating to English.

## Core framework: Clear, Concise, Useful

Every piece of UX copy should be evaluated (and written) against all three principles. They often trade off against each other — resolve conflicts in this order: **Useful > Clear > Concise**. Never cut a word if doing so makes the copy less clear or less actionable; never keep a clever/vague word if a plain, concrete one is available and just as short.

### 1. Clear
- **Be direct.** Use everyday words. No technical jargon or internal system/business terms unless the audience is that specific technical group (see `references/principles.md#jargon`).
- **Avoid cleverness.** Puns, brand voice flourishes, and cute wording are only acceptable *after* the user understands what's happening — never instead of clarity. If a reviewer/user would have to pause to decode a joke, cut it.
- **Be concrete.** Replace vague words with exact details: "3 business days" not "soon"; "Under 5 MB" not "too large"; "You need $12,000 more" not "insufficient funds."
- Describe the state the system will move **into**, not the current state (e.g., a Play button becomes "Pause" while playing).
- Use verbs for action commands ("Delete file", "Save changes") and adjectives for state/appearance changes ("Bold", "Dark mode").

### 2. Concise
- **Cut every word that doesn't help the user complete the task.** No filler, no throat-clearing ("Please note that...", "In order to...").
- **Frontload the important word.** The first 1–2 words of a heading, link, or button carry the most scanning weight — put the key noun/verb first.
- **Save space, but never below the floor set by Clear/Useful.** There's no fixed word-count minimum or maximum for links/labels — a label can be long if every word earns its place (e.g., "Lasting power of attorney" is fine at 4 words; "Learn more" fails at 2).
- Remove articles ("a", "an", "the") from short command labels where scannability matters more than grammatical formality (e.g., app menu items).

### 3. Useful
- **Guide the action.** Every piece of copy should make it obvious what the user does next.
- **Turn errors into solutions.** State what happened, why (in plain terms), and exactly how to fix it. Never just say "An error occurred."
- **Never blame the user.** Avoid "invalid", "illegal", "incorrect", "you failed to..." — the system should sound like it's on the user's side.
- **Preserve effort.** Copy should never imply the user has to redo work they've already done; if relevant, say what's preserved ("Your draft is saved").
- **Stay consistent** in voice: human, polite, and matched to the user's likely emotional state at that moment (calm/reassuring during errors, upbeat during success, neutral during routine tasks).

For the full research basis (eyetracking/scanning behavior, tone of voice, formatting/chunking, link-label 4 Ss, command-label rules, error-message guidelines) see `references/principles.md`.

## Workflow

### A. Writing new copy
1. Identify the **copy type** (button/command, error message, link, heading, empty state, notification, form field/helper text, tooltip, onboarding). Different types have different rules — check `references/copy-types.md` for the relevant checklist before writing.
2. Identify what the user needs to know or do **right now** at this exact moment in the flow, and what they're likely feeling (confused, anxious, accomplished, blocked). Let that drive tone.
3. Draft 1–3 words/sentences over-length first if needed, then cut ruthlessly against the Concise checklist.
4. Run the draft through the **Quick Self-Check** below before presenting it.
5. When relevant, present 1–2 short alternates (e.g., a slightly longer "substantial" version vs. a tighter one) rather than a single take, especially for ambiguous cases — but never pad the response with more than that.

### B. Reviewing / auditing existing copy
1. Go string by string (or screen by screen for a flow).
2. For each string, flag violations by principle (Clear / Concise / Useful) — don't just say "this is bad," name which principle it breaks and why.
3. Give a rewritten version for every flagged string.
4. If auditing many strings, output as a table: `Original | Issue | Principle broken | Rewrite`.
5. Call out any inconsistency in voice/terminology across strings (e.g., "Delete" used in one place and "Remove" for the same action elsewhere).

### C. Error messages specifically
Use this 3-part structure, sourced from NN/g's error-message guidelines (`references/copy-types.md#errors`):
1. **What happened** — plain-language, specific (not "An error occurred").
2. **Why / context** — only if it helps the user understand or fix it; skip internal error codes unless they're needed for support.
3. **What to do next** — a concrete recovery action, ideally as a button/link, not just prose.
Never use humor in errors users will see repeatedly. Reserve any "delight"/novelty tone for rare, catastrophic, non-recoverable failures only (e.g., full outage pages).

### D. Link text and buttons
Apply the **4 Ss**: Specific, Sincere, Substantial, Succinct (in that priority order — succinctness is last and should never override the other three). Never use "Learn more", "Click here", or "Read more" alone — always name what the link leads to. See `references/copy-types.md#links`.

## Quick Self-Check (run on every deliverable before presenting)

- [ ] Would a first-time user understand this without re-reading it?
- [ ] Is there a vague word ("soon", "some", "an error", "invalid") that could be replaced with a specific detail?
- [ ] Can any word be deleted without losing meaning or action-guidance?
- [ ] Does the most important word appear in the first 1–2 words?
- [ ] Does it tell the user what to do next (if action is needed)?
- [ ] Does it avoid blaming or lecturing the user?
- [ ] Is the tone consistent with the rest of the product's voice and the user's likely emotional state?

If the user provides existing product voice/tone guidelines or example strings, follow those over generic defaults — brand-specific jargon is not jargon to that audience if it's part of the established product vocabulary.

## Output format

- For a single string: give the rewritten copy directly, plus a one-line rationale citing which principle(s) it fixes. Don't over-explain unless asked.
- For multiple strings/a flow: use a table (Original / Rewrite / Why) so it's scannable — mirroring the same "concise, scannable" standard the copy itself must meet.
- Match the user's language (Indonesian, English, etc.) — write the copy itself in that language; keep any rationale in the same language too.