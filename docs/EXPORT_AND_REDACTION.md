# Export + redaction (V1)

## Goal
Share the workflow publicly without leaking personal data.

## Public-safe rules
Never include in public exports:
- absolute paths (`/Users/...`, `C:\\Users\\...`)
- emails / phone numbers
- addresses or unit numbers
- family member names
- chat IDs / user IDs
- tokens / API keys

## Placeholder strategy
Replace sensitive strings with:
- `<JOURNAL_ROOT>` / `<OBSIDIAN_VAULT_ROOT>`
- `<PROJECT_ROOT>`
- `<PERSON>`
- `<ID>`
- `<LINK>`

## Recommended export shapes
- Publish only templates + synthetic examples.
- If you must export real notes, do a manual review pass + search:
  - `/Users/` and `C:\\Users\\`
  - `@` (emails)
  - long digit strings (IDs)

V2: provide an automated redaction script.
