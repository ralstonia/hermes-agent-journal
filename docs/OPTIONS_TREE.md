# Options tree — /journal (backend-optional)

## Step 1: Choose where journal artifacts live (backend)

A) Flat files (default)
- Daily markdown files: `<JOURNAL_ROOT>/YYYY-MM-DD.md`
- Human-readable, git-friendly, Obsidian-compatible (but not required)

B) Obsidian preset (same as flat files)
- Daily markdown files live in your vault root
- Same file format; just a convention + UX preference

C) JSONL events
- Append-only: `<JOURNAL_ROOT>/entries.jsonl`
- Derived views generated into markdown: `triage.md`, `daily/YYYY-MM-DD.md`

Planned (V2)
- SQLite (local DB + search)
- Postgres (shared/team)

## Step 2: Choose interaction surface

V1
- Hermes skill: `/journal`

Planned (V2)
- Browser canvas/viewer (reads JSON schema / DB)

## Step 3: Choose optional derived views

- Triage-only view (top 3 decisions + top 3 actions)
- Weekly review (themes + repeated blockers)
- Decision log (decisions only)

## Always-on safety boundaries

- Append-only minutes blocks
- Minimal triage edits only
- Never guess paths
- Never export/upload notes unless explicitly requested
