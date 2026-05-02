# AGENTS.md

## Cursor Cloud specific instructions

This is GitHub's `.github` meta-repository containing default community health files (README, CODE_OF_CONDUCT, CONTRIBUTING, SECURITY) and a repolinter configuration. There is **no application code, no build system, no tests, and no package dependencies**.

### What this repo contains

- `README.md` / `profile/README.md` — Organization description and profile page
- `CODE_OF_CONDUCT.md` — Contributor Covenant v2.1
- `CONTRIBUTING.md` — Default contributing guidelines
- `SECURITY.md` — Security vulnerability reporting policy
- `config/repolinter-ruleset.json` — Repolinter rules enforcing LICENSE, README, and CODEOWNERS file presence

### Running repolinter (the only tool)

Repolinter is the only tooling referenced by this repo. To lint the repo against its ruleset:

```sh
repolinter lint --rulesetFile config/repolinter-ruleset.json
```

This checks 3 rules: `license-file-is-MIT`, `readme-file-exists`, and `codeowners-file-exists`.

### Gotchas

- `config/repolinter-ruleset.json` has a trailing comma on line 65 (closing `codeowners-file-exists`) which is technically invalid JSON, but repolinter parses it without error.
- `CONTRIBUTING.md` references `script/bootstrap` and `script/cibuild` — these scripts do **not** exist in this repo and are generic placeholder instructions.
- Repolinter's `fix` actions may auto-create files (e.g. CODEOWNERS) when rules fail — be aware of untracked files after a lint run.
