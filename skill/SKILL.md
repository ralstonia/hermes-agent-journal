---
name: journal
description: "Append session minutes + auto-promote triage into daily journal artifacts (triage-first). Flat files by default; Obsidian is an optional preset. Includes both factual (A) and reflective (B) journaling."
version: 0.2.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [obsidian, journaling, daily-notes, minutes, triage, local-first]
---

# /journal — Agentic journaling (backend-optional)

V1 default backend: flat files (daily markdown).
Obsidian is an optional preset (same file format, different root).

Use when the user types `/journal` (or asks to journal / log session minutes).

## Prime directive

- You own the artifacts (local-first). Obsidian is optional.
- Preserve the user’s original prose. Do NOT rewrite their existing note content.
- Make changes in two forms only:
  1) append a new “Session minutes (Hermes)” block
  2) small, reviewable edits to the top “Triage” section

## Backend (V1): flat files (daily markdown)

Assume the daily note lives at:
- Journal root: `<JOURNAL_ROOT>`
- Daily note filename: `YYYY-MM-DD.md` in that directory

Rules:
- Journal root is user-specific and must not be guessed.
- If unknown, ask the user.
- In public examples, always use placeholders.

### Obsidian preset (optional)

If the user uses Obsidian daily notes, `<JOURNAL_ROOT>` can be their vault root. (Same files, same format.)

## Triage-first header (create if missing)

Triage

Decisions pending
- …

Next actions (owner + DoD)
- …

----

## What to write (two layers)

A) Pointed minutes (factual)
- Lane / context (1 line)
- Decisions made (bullets)
- Decisions pending (bullets)
- Next actions (owner + DoD)
- Artifacts (paths/URLs/session IDs) — only if the user already provided them

B) Reflection (grounded, non-cheesy)
- 3–7 lines max
- Must reference what actually happened in this session
- No generic platitudes
- Optional: 1 evidence-based concept (only state as fact if verified)

## Promotion heuristics (deterministic)

Promote from minutes → triage (top of file):

1) Decisions pending
- Promote bullets that contain:
  - “decide”, “choose”, “pick”, “scope”, “confirm”, “boundary”, “whether”, “should we”
- Rewrite promoted item into a single question starting with a verb:
  - “Decide …”, “Confirm …”, “Choose …”

2) Next actions
- Promote items that have:
  - an owner (explicit or inferable as User/Hermes/Both)
  - a concrete deliverable
- Enforce DoD (definition of done): must be objectively checkable.

3) Triage cap
- Keep max 3 decisions + max 3 actions.
- Selection rule if overflowing:
  - prefer items that unblock multiple others
  - prefer “today/next” over “someday”

## Minutes block format (append-only)

Append to the end of the file:

Session minutes (Hermes)

<TIMESTAMP>

A) Pointed minutes
<content>

B) Reflection
<content>

----

^AI <YYYY-MM-DD HH:MM:SS TZ> — Hermes (<model>)

## Implementation steps (must use tools)

1) Read current time: `date '+%Y-%m-%d %H:%M:%S %Z'`
2) Get filename: `date '+%Y-%m-%d'` → `<YYYY-MM-DD>.md`
3) Read file if exists; otherwise create it.
4) Ensure triage header exists at top.
5) Append minutes block.
6) Update triage section:
   - merge promoted items with existing triage
   - enforce 3+3 cap
7) Verify:
   - re-read the first ~80 lines
   - confirm the new appended block exists

## Example (redacted)

Triage

Decisions pending
- Decide whether “/journal” should be skill-only or also a native slash-command.

Next actions (owner + DoD)
- Hermes: Draft proposal doc (1 page) with UX + safety boundaries. DoD: saved under `journaling/docs/`.
- User: Pick preferred naming (“journal” vs “minutes”). DoD: decision written in triage.

----

Session minutes (Hermes)

2026-05-13 21:40 IST

A) Pointed minutes
Lane: <PROJECT/LANE>
- Decision: Keep daily note triage capped (3 decisions + 3 actions).
- Open loop: confirm what counts as PII for public templates.

B) Reflection
The win today is not volume; it’s clarity. A short triage is a promise to your future self that you’ll return with focus, not guilt.

----

^AI 2026-05-13 21:40:12 IST — Hermes (model unknown)
