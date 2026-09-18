# UX Writing — Research Basis (from Nielsen Norman Group)

Deeper background for the rules in SKILL.md. Read this when a case is ambiguous, when the user asks "why" a rule exists, or when writing/reviewing something unusual (long-form in-product content, tone-of-voice systems, jargon calls).

## How people actually read online
- People scan, they don't read word-for-word. Common scan patterns: F-shaped, layer-cake (driven by good headings), spotted/exhaustive review (rare, only when highly motivated, e.g., comparing prices).
- The first ~11 characters / first 2 words of a heading, link, or label carry disproportionate weight for whether users correctly predict what follows — always frontload the key word.
- Users on mobile read even less thoroughly than desktop; keep mobile copy at the tightest end of the concise scale.
- Because users scan rather than read surrounding text, **UI elements (links, buttons, headings) must be understandable in isolation** — don't rely on a paragraph above/below to supply meaning a label lacks.

## Jargon
- Default to plain language; avoid internal/technical/industry terms.
- Exception: if the *actual audience* uses a term routinely in their own speech (e.g., "API key" for developers, "saldo" for banking users), it is not jargon to them — using the plain-language substitute can actually reduce clarity for a specialist audience. Confirm who the audience is before deciding.
- Never make users decode or Google a term to understand a command or message.

## Tone of voice
- Tone should be human, polite, and calibrated to the user's emotional state at that moment — not a fixed, one-size-fits-all brand voice.
- Tone has a measurable effect on brand trust; inconsistent tone across a flow undermines credibility even if each string is individually fine.
- Avoid sounding robotic or overly formal in conversational/AI interfaces, but avoid excessive casualness in high-stakes moments (payments, legal, errors, deletions).

## Command / button / menu labels (UI copy)
- Keep to roughly 2–4 words; drop articles ("a/an/the") to aid scanning.
- Label the **state the system will move into**, not the current state (e.g., "Pause" while a video plays, not "Playing").
- Use verbs for actions ("Save", "Continue to Billing"); use adjectives for state/appearance toggles ("Bold", "Dark Mode").
- Avoid vague command names ("Manage", "Options") when a more specific verb is available.
- Avoid generic confirmation labels like "OK" in destructive/consequential dialogs — say exactly what will happen ("Discard changes", not "OK").
- When the same action recurs across contexts, keep the label word-for-word identical each time (don't alternate "Delete"/"Remove" for the same action).
- Add a noun after the verb when the action alone is ambiguous ("Delete Folder" vs. bare "Delete").
- Use ellipses ("...") on commands that require further input before executing (e.g., "Export...").

## Links — the 4 Ss (in priority order)
1. **Specific** — tells users exactly what they'll find; never "Learn more", "Click here", "Read more" standing alone.
2. **Sincere** — sets expectations that are met the instant the user clicks (don't promise "book now" if it opens a contact form).
3. **Substantial** — must make sense read in isolation, without surrounding text, since users often read only the link.
4. **Succinct** — no fixed word limit; a link can be long if every word is earning its place, but cut anything that doesn't add specificity, sincerity, or standalone meaning.

## Error messages (full model)
**Visibility**
- Show the error next to the element it concerns (proximity reduces cognitive load).
- Use redundant signals (not color alone) — icon + text + border, for accessibility (color-vision deficiency affects ~350M people worldwide).
- Match severity to treatment: minor/advisory issues → inline label or toast; severe, blocking issues → modal.
- Don't show errors prematurely — never flag a field as wrong just because the user is still exploring/hasn't finished. Reserve real-time inline validation for genuinely error-prone fields (e.g., password rules).

**Communication**
- Plain, human-readable language; hide technical codes (show only if needed for support/debugging).
- Be specific about what happened — never just "An error occurred."
- Always offer a constructive next step, not just a diagnosis.
- Positive, non-blaming tone — avoid "invalid," "illegal," "incorrect," or anything implying user fault. The system, not the user, owns the correct-usage contract.
- Avoid humor in errors that recur — it goes stale and can feel dismissive.

**Efficiency**
- Prevent likely mistakes proactively where possible (e.g., warn before sending an email that references a missing attachment).
- Preserve user input/work on error — never make them retype from scratch.
- Where feasible, offer one-click fixes instead of just a description of the problem (e.g., suggest the matching city for a mismatched ZIP code).
- Link out to more detail only when necessary, and keep the primary message concise regardless.

**Catastrophic/rare failures only**
- Total, unrecoverable failures (server down, no possible fix) are the *only* place where blending apology with something novel or delightful may help — this is an exception, not the default, and should never appear in routine, recurring errors.

## Formatting & structure (for longer in-product content — help articles, onboarding, empty states with body text)
- Use the inverted pyramid: put the conclusion / most important info first, supporting detail after.
- Chunk content under clear, scannable subheadings rather than long unbroken paragraphs.
- Use numerals ("3 days") instead of spelled-out numbers in digital copy — numerals are easier to scan.
- Bulleted lists should be genuinely parallel in structure and each bullet scannable on its own.