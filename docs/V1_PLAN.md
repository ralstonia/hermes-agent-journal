# V1 Build Plan — Backend-optional /journal

Goal: ship a V1 journaling package where Obsidian is an optional preset, not a dependency.

## V1 scope (must-have)

### Core invariants
- Append-only minutes blocks (immutable history)
- Triage view (max 3 decisions + 3 actions) derived from minutes + editable
- Deterministic-ish promotion heuristics
- Privacy-safe by default: no guessed paths, no uploads, public examples are synthetic

### Supported backends (V1)
- Flat files (daily markdown) — DEFAULT
- Obsidian preset (same as flat files, just a convention/preset)
- JSONL events (append-only) + derived views (spec/schema only; generation can be manual in V1)

V1 explicitly does NOT implement SQLite/Postgres yet, but documents them as V2 paths.

### Interaction surfaces (V1)
- Hermes CLI skill (/journal)
- No web UI yet; we only specify what a canvas viewer would consume.

## Deliverables (this repo)

1) Options tree + decision guide
- `docs/OPTIONS_TREE.md`
- `docs/FEATURE_MATRIX.md`

2) Backend specs + templates
- `templates/daily-note.md` (triage-first + minutes blocks)
- `schemas/journal-entry.schema.json` (for JSONL)

3) Updated skill template (GitHub-safe)
- `skill/SKILL.md` updated to support backend selection:
  - `<JOURNAL_ROOT>` for flat files
  - `<OBSIDIAN_VAULT_ROOT>` for Obsidian preset

4) Minimal export/redaction guidance
- `docs/EXPORT_AND_REDACTION.md` (no code in V1)

## V2 (roadmap, not implemented)
- SQLite backend (local search + FTS)
- Postgres backend (multi-user)
- Canvas/browser viewer (reads the same schema)

## Acceptance criteria
- A newcomer can pick a backend in <2 minutes.
- Public package contains no PII.
- Examples are synthetic and work without Obsidian installed.
