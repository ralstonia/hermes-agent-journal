# Proposal: Make “/journal” a first-class Hermes workflow (skill-first, core-ready)

## Problem
Hermes produces a lot of useful ephemeral context (decisions, actions, boundaries). Without a consistent capture loop:
- context leaks across sessions
- next steps are forgotten or duplicated
- “agent work” isn’t reviewable/auditable

Users who are local-first often already have a system-of-record (Obsidian). They need a minimal, safe mechanism to:
- append session minutes
- promote a tiny triage section (Decisions + Next actions)

## Proposed solution
Introduce `/journal` as an officially supported pattern.

**Default implementation path:** skill-first (ships today via Skills)
**Core-ready path:** optionally add a native helper later (for better UX / safer path discovery).

### User experience
- User types `/journal` at end of a session (or whenever they want)
- Hermes appends a “Session minutes (Hermes)” block to today’s daily note
- Hermes promotes up to 3 decisions + 3 next actions into a top-of-file “Triage” section

### Safety boundaries
Hard constraints that keep it safe:
- Append-only for minutes blocks
- Do not rewrite user prose
- Only small, reviewable edits at the top triage section
- Never guess vault paths
- Never export note contents to the web without explicit user request

## Why Hermes should care
This is the “closing loop” for agentic work:
- increases user trust (audit trail)
- reduces repeated prompting (“what did we decide?”)
- improves cross-session continuity
- aligns with Hermes strengths: skills + memory + local tooling

## Minimal implementation sketch (core)
If the Hermes team wants to productize beyond a skill:

1) Add a built-in slash command `/journal` in `hermes_cli/commands.py`
2) Implement handler in `cli.py` (or the shared agent command dispatcher) that:
   - resolves vault root (explicit config key OR ask user)
   - loads today’s note
   - applies triage-first structure
   - appends minutes block

Suggested config key:
- `note_taking.obsidian.vault_root: "/abs/path"`

This keeps private pathing in local config (not in skills).

## Open questions
- Should `/journal` live as skill-only for flexibility, or ship a tiny core command that calls into a built-in “journal” tool?
- Should there be lanes (`--lane`) for multi-project days?

## Acceptance criteria
- Works on macOS/Linux/WSL (file paths)
- Never overwrites existing user prose
- Triage cap enforced (3 decisions + 3 actions)
- Vault path never guessed
- Clear audit signature (timestamp + model)
