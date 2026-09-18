# PRD Template — Empty Skeleton

Copy this structure when starting a new PRD draft. Section headers are shown bilingually (English / Indonesian) as a reminder — **when you actually write the PRD, translate everything into the user's language**; don't leave English labels in the delivered document. Remove a section only if it's truly irrelevant to the feature (e.g. skip "User Flow" for a feature with no staged flow), not just because it would be short.

```markdown
# PRD — [Feature Name / Nama Fitur]

**Project:** [project name]
**Version/Versi:** 1.0
**Date/Tanggal:** [date]
**Author:** [name]

## 1. Background / Latar Belakang
[What gap or problem underlies this feature? Frame it as a problem, not a missing feature. What already exists and what doesn't?]

## 2. Goals / Tujuan
1. [Concrete goal 1]
2. [Concrete goal 2]

## 3. Scope & Non-Goals
**In scope:** [...]
**Out of scope:** [...and why — especially for related tables/features intentionally left untouched]

## 4. Actors / Aktor
| Actor | Description |
|---|---|

## 5. User Flow
[Text/ASCII diagram for branching flows, or numbered steps for a linear flow. For simple cases: "As a <user>, I want <goal> so that <benefit>."]

## 6. Business Rules
| # | Rule |
|---|---|
[Each rule: concrete operation, valid enum values, deletion mechanism if relevant — not a generic sentence. Tag P0/P1/P2 if scope is large.]

## 7. Database Schema

### New Table: `table_name`
| Column | Type | Notes |
|---|---|---|

### Changes to Existing Table: `existing_table`
| Column | Action | Reason |
|---|---|---|

[For any FK/relation column that will appear in an API response or log: state explicitly that it's resolved to a label, not a raw UUID]

## 8. API Contract

Response format follows the existing standard:
[paste the envelope shape already used by the project — success/message/data/meta or otherwise]

### `[METHOD] /path` — [short description]
```json
// Request
{ }
```
```json
// Response
{ }
```
**Access/Akses:** [admin/viewer/etc — explicit]

## 9. Authorization (if it needs cross-endpoint explanation)
[Who can access which menu/endpoint, if not already clear per-endpoint in section 8]

## 10. Assumptions & Open Questions
[Every decision that was assumed (not asked) MUST be recorded here, with a short reason for the assumption]

## 11. Schema Change Summary
**New tables:** [...]
**Changed tables:** [...]
**Unchanged tables:** [...]
```