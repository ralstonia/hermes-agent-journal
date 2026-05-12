# Hermes /journal — GitHub-ready package (privacy-safe)

This folder is a *public-shareable* packaging of the “agentic journaling / session minutes” workflow.

Design goals:
- Local-first: Obsidian is the system of record
- Triage-first: keep a small, current top section (Decisions + Next actions)
- Append-only minutes: add new “session minutes” blocks, do not rewrite the user’s prose
- Privacy-safe by default: templates avoid absolute paths, names, emails, and other PII

## What’s included

- `skill/` — a publishable skill template (`journal`), with placeholders for vault path
- `examples/` — redacted daily-note example(s)
- `docs/` — proposal + UX spec + safety boundaries
- `marketing/` — banner/social card assets (SVG + optional PNG)

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
