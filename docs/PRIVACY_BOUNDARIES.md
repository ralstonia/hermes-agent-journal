# Privacy boundaries for /journal (public + local)

## Redaction policy for public materials

Public docs and examples must not include:
- absolute file paths (e.g., `/Users/...`, `C:\Users\...`)
- emails, phone numbers
- addresses, unit numbers
- names of family members / non-public individuals
- chat IDs / user IDs
- API keys / tokens

Use placeholders:
- `<OBSIDIAN_VAULT_ROOT>`
- `<PROJECT_ROOT>`
- `<LINK>`
- `<PERSON>`
- `<ID>`

## Behavior constraints (agent)

- Never guess the vault root.
- Do not rewrite user prose.
- Only append minutes blocks.
- Only update triage section with minimal, reviewable edits.
- Do not upload/export notes.

## Review checklist before publishing

- Search for `/Users/` and `C:\Users\`
- Search for `@` (emails)
- Search for long digit strings (IDs)
- Search for family names / locations
- Ensure examples are synthetic
