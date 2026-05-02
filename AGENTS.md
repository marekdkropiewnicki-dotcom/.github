# AGENTS.md

## Cursor Cloud specific instructions

This is a GitHub organization `.github` repository containing community health files (Markdown docs and a repolinter config). There is no application code, no build step, and no services to run.

### Repository contents

- `README.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md` — community health files
- `profile/README.md` — GitHub organization profile page
- `config/repolinter-ruleset.json` — repolinter rules for enforcing repo standards (MIT license, README, CODEOWNERS)

### Available dev tools

- **repolinter**: `repolinter lint --rulesetFile config/repolinter-ruleset.json` — runs repo policy checks using the custom ruleset
- **markdownlint**: `markdownlint '*.md' 'profile/*.md'` — lints Markdown files (many pre-existing warnings are expected)

### Known issues

- `config/repolinter-ruleset.json` has a trailing comma on the last rule entry (line 65-66), which makes it invalid strict JSON. Repolinter's parser handles it, but `JSON.parse()` and `python3 json.load()` will fail. Do not attempt to "fix" this unless explicitly asked.
- `CONTRIBUTING.md` references `script/bootstrap` and `script/cibuild` commands that do not exist in this repository — they are generic placeholder instructions.
- Repolinter's `license-file-is-MIT` rule will flag a warning because this repo has no LICENSE file (expected for an org-level `.github` repo).
- Running `repolinter lint` with the custom ruleset may auto-create a `CODEOWNERS` file via its fix rule. Clean up with `rm -f CODEOWNERS` if this happens unintentionally.
