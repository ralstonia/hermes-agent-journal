# Hermes /journal — GitHub-ready package (privacy-safe)

This folder is a *public-shareable* packaging of the “agentic journaling / session minutes” workflow.

Design goals:
- Local-first: you own the artifacts (Obsidian is an optional preset, not a dependency)
- Triage-first: keep a small, current top section (Decisions + Next actions)
- Append-only minutes: add new “session minutes” blocks, do not rewrite your prose
- Backend-optional: flat files, Obsidian, JSONL now; SQLite/Postgres/canvas planned
- Privacy-safe by default: templates avoid absolute paths, names, emails, and other PII

## What’s included

- `skill/` — publishable skill template (`journal`), backend-optional (flat files default; Obsidian preset)
- `examples/` — synthetic/redacted daily-note examples
- `docs/` — options tree, feature matrix, proposal, UX spec, privacy, export/redaction
- `templates/` — daily note templates
- `schemas/` — JSON schema for JSONL/event backends
- `marketing/` — banner/social card assets (SVG)

## Install (local)

This is meant as a *shareable template*. For your own machine, you’ll likely want to set your vault root.

Recommended approach:
1) Copy the skill to your Hermes skills folder.
2) Set the vault root in your own local configuration/memory (not in the public template).

See: `docs/INSTALL.md`

## Safety boundaries (summary)

- Do not export raw daily notes.
- Do not embed absolute paths, emails, phone numbers, addresses, or private identifiers in any public doc.
- In examples, use placeholders like:
  - `<VAULT_ROOT>`
  - `<PROJECT_ROOT>`
  - `<LINK>`
  - `<PERSON>`

## License

MIT (suggested) — see `LICENSE` at repo root (or add one if/when this gets split into its own repo).
