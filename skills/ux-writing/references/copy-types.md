# Checklists by Copy Type

Use the relevant section as a checklist before finalizing copy. Examples are illustrative — write final copy in the user's actual language, not a translation of these.

## Buttons / commands
- 2–4 words, verb-led ("Save changes", not "Save Changes Now Please")
- Describes the resulting state, not current state
- No generic "OK" on consequential/destructive dialogs — say what happens ("Discard draft", "Delete 3 files")
- Consistent label for the same action everywhere it appears
- ❌ "Submit" (for canceling a subscription) → ✅ "Cancel subscription"
- ❌ "OK" (before deleting an account) → ✅ "Delete my account"

## Links {#links}
Apply the 4 Ss (Specific > Sincere > Substantial > Succinct):
- ❌ "Learn more" → ✅ "See pricing plans"
- ❌ "Click here for details" → ✅ "View shipping policy"
- Must stand alone without needing the surrounding sentence to make sense
- No fixed max length — a precise 6–8 word link beats a vague 2-word one

## Error messages {#errors}
Structure: **What happened → Why (optional) → What to do next**
- ❌ "An error occurred. Please try again." 
- ✅ "We couldn't save your changes because you're offline. Reconnect and we'll save automatically."
- ❌ "Invalid input" 
- ✅ "Enter a phone number with 10 digits, e.g. 0812xxxxxxx"
- ❌ "Payment failed" 
- ✅ "Your card was declined by the bank. Try another card or contact your bank."
- Never blame: avoid "You entered the wrong...", prefer "This doesn't match..."
- Preserve input — never clear the field that caused the error
- Inline, near the field; not a distant banner, unless it's a page-level/system-level issue

## Empty states
- Explain what will appear here and (if applicable) how to add the first item
- Avoid pure decoration with no action — give a clear next step
- ❌ "Nothing here yet" → ✅ "No invoices yet. Create your first invoice to get started." + button

## Notifications / toasts
- Lead with the outcome, not the mechanism: ❌ "Request processed" → ✅ "Your refund was approved"
- Time-bound or reversible actions should say so: "Undo" affordance if applicable
- Keep to one line where possible; frontload the key noun

## Form fields & helper text
- Field labels: nouns, no punctuation, no "Please enter..." — the field itself implies entry
- Helper/hint text: concrete formats and examples ("MM/DD/YYYY"), not vague guidance ("enter a valid date")
- Validation messages appear inline, next to the field, immediately on blur/submit — not preemptively while typing

## Tooltips
- Only for supplementary info, never for content critical to task completion (tooltips are easy to miss/skip)
- One short sentence; no restating the label verbatim

## Onboarding / first-run copy
- Focus on the user's goal, not the feature list ("Set up your first project" not "Welcome to our powerful platform")
- Keep steps short; one action per screen
- Avoid marketing tone — this is instructional content, not a pitch

## Headings / page titles
- Frontload the keyword users are scanning for
- Passive voice is acceptable here specifically to allow leading with the key noun (e.g., "Password Changed" is fine even though passive)
- Avoid clever/punny headings that delay understanding of what the section is about

## Confirmation dialogs
- Title: state the action plainly ("Delete this project?")
- Body: state the consequence concretely, especially if irreversible ("This will permanently delete all 12 files inside. This can't be undone.")
- Primary button: names the action, not "Yes"/"OK" ("Delete project")
- Secondary button: "Cancel" or "Keep project" (be consistent app-wide)