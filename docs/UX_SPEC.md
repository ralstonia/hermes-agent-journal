# UX spec — /journal

## Primary command

/journal

Prompts the user (if needed) for the minimal “what happened” content, then writes:
- triage updates (top-of-file)
- appended minutes block

## Options (future)

/journal --lane <name>
- Adds/uses a lane label in the minutes block
- Optional: lane-specific triage sections (not default)

/journal --reflect off
- Writes only A) Pointed minutes

/journal --no-promote
- Appends minutes only, does not touch triage

/journal --dry-run
- Shows a diff preview (ideal for core command)

## Interaction rules
- If the agent cannot resolve `<JOURNAL_ROOT>`, it asks.
- The agent never guesses paths.
- The agent never “fixes writing.” It only appends and lightly edits triage bullets.

## Output guarantees
- Triage section exists and stays near the top
- A max of 3 decisions + 3 actions
- Every appended minutes block has an AI signature line
