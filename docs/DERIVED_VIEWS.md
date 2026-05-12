# Derived views (V1 spec)

V1 stores daily notes as:
- `<JOURNAL_ROOT>/YYYY-MM-DD.md`

Derived views are additional markdown files that summarize and *link back* to the specific source blocks in the daily notes.

## Why block IDs matter

To make summaries auditable and “well-connected,” every promoted triage bullet (and optionally key minutes bullets) should end with a stable block anchor:
- decisions: `^d-YYYYMMDD-01`
- actions: `^a-YYYYMMDD-01`
- minutes: `^m-YYYYMMDD-01`

Obsidian treats `^anchor` as a block ID and supports deep links like:
- `[[2026-05-13]]#^d-20260513-01`

Even without Obsidian, these anchors remain stable textual references.

## Weekly review

Recommended file path:
- `<JOURNAL_ROOT>/weekly/YYYY-WW.md`

Template provided at:
- `templates/weekly-review.md`

Rules:
- Include a Sources section listing all 7 daily notes.
- Every decision/action bullet in the weekly review should include a `(source: [[YYYY-MM-DD]]#^...)` link.

## Monthly review

Recommended file path:
- `<JOURNAL_ROOT>/monthly/YYYY-MM.md`

Template provided at:
- `templates/monthly-review.md`

Rules:
- Link back to source decisions/actions using block anchors.

## Carry-forward behavior (optional)

A weekly/monthly review may carry-forward:
- still-pending decisions
- still-open actions

If carried forward, keep the original source link and optionally add a new “review note” bullet with its own anchor.
