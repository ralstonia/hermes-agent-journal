# Install (local) — Hermes Agent /journal skill

This guide installs the `journal` skill on a local machine.

## 1) Copy the skill template

Copy `journaling/skill/SKILL.md` into your Hermes skills directory.

Example:
- Destination: `~/.hermes/skills/note-taking/journal/SKILL.md`

## 2) Set your journal root (private)

V1 default backend is flat files: `<JOURNAL_ROOT>/YYYY-MM-DD.md`.

The public template intentionally uses `<JOURNAL_ROOT>`.

Choose ONE private way to provide it:

A) Put it in your own local skill file (private fork)
- Replace `<JOURNAL_ROOT>` with an absolute folder path on your machine
- Do NOT publish that file.

B) Keep skill public-safe, but teach the agent the path via memory
- Tell Hermes once: “My journal root is: /abs/path/to/journal”
- Hermes should then read that from memory for all future `/journal` calls.

### Obsidian preset (optional)

If you use Obsidian daily notes, set `<JOURNAL_ROOT>` to your vault root. (Same file format; Obsidian is just the viewer.)

## 3) Try it

In a Hermes chat session:
- `/journal` then paste 5–15 lines of what happened

Expected:
- A daily note `YYYY-MM-DD.md` is created/updated
- Top-of-file triage updated (max 3 decisions + max 3 actions)
- A new append-only “Session minutes (Hermes)” block is appended
