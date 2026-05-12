# Install (local) — Hermes /journal skill

This guide installs the `journal` skill on a local machine.

## 1) Copy the skill template

Copy `journaling/skill/SKILL.md` into your Hermes skills directory.

Example:
- Destination: `~/.hermes/skills/note-taking/journal/SKILL.md`

## 2) Set your Obsidian vault root (private)

The public template intentionally uses `<OBSIDIAN_VAULT_ROOT>`.

Choose ONE private way to provide it:

A) Put it in your own local skill file (private fork)
- Replace `<OBSIDIAN_VAULT_ROOT>` with your actual vault path
- Do NOT publish that file.

B) Keep skill public-safe, but teach the agent the vault path via memory
- Tell Hermes once: “My Obsidian vault root is: /abs/path/to/vault”
- Hermes should then read that from memory for all future `/journal` calls.

## 3) Try it

In a Hermes chat session:
- `/journal` then paste 5–15 lines of what happened

Expected:
- A daily note `YYYY-MM-DD.md` is created/updated
- Top-of-file triage updated (max 3 decisions + max 3 actions)
- A new append-only “Session minutes (Hermes)” block is appended
