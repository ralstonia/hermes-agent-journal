# Releasing hermes-agent-journal

This repo is docs/templates/skill-first, so releases are lightweight. The goal is to make it easy for people to know:
- what changed
- how to install
- what version they’re on

## Release checklist (copy/paste)

### 0) Decide the version

We use SemVer-ish:
- Patch (0.2.x): typo fixes, doc clarifications, new examples
- Minor (0.x): new templates, new derived views, skill behavior tweaks (non-breaking)
- Major (1.0.0): stable contract for the template + anchors + derived views

### 1) Preflight sanity

Run locally:
- `git status --porcelain`  (must be clean)
- `rg -n "/Users/|C:\\Users\\|@" .` (PII scan; expected hits only in privacy docs)
- Open `README.md` and confirm images render:
  - `marketing/banner.svg`
  - `docs/flow-diagram.svg`
  - `docs/daily-note-anatomy.svg`
  - `docs/weekly-review-linking.svg`

### 2) Update CHANGELOG

Create or update `CHANGELOG.md` with:
- Added / Changed / Fixed
- Link to key docs if needed

### 3) Bump version(s)

Update:
- `skill/SKILL.md` frontmatter `version:`

(Optional) If we later add a package manifest (pyproject/package.json), bump that too.

### 4) Commit

- `git add CHANGELOG.md skill/SKILL.md`
- `git commit -m "release: vX.Y.Z"`

### 5) Tag

- `git tag -a vX.Y.Z -m "vX.Y.Z"`
- `git push --follow-tags`

### 6) Create GitHub Release notes

Using GitHub CLI:
- `gh release create vX.Y.Z --title "vX.Y.Z" --notes-file RELEASE_NOTES.md`

Or quick inline notes:
- `gh release create vX.Y.Z --title "vX.Y.Z" --notes "…"`

## Release notes template

Create `RELEASE_NOTES.md`:

- Summary (1–2 lines)
- Highlights (3 bullets)
- Install/Upgrade notes
- Links: README, DERIVED_VIEWS, skill

## Definition of Done

- Tag exists on GitHub
- GitHub Release exists with notes
- README still renders images
- No accidental personal data in public text
