## Cursor Cloud specific instructions

This is GitHub's `.github` organization-level meta-repository. It contains **no application code** — only Markdown community health files (`README.md`, `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`, `profile/README.md`) and a `config/repolinter-ruleset.json` configuration.

### Linting

The only tool that actually runs in this repo is [repolinter](https://github.com/todogroup/repolinter), which validates repos against policy rules defined in `config/repolinter-ruleset.json`. (`CONTRIBUTING.md` also references `script/bootstrap` and `script/cibuild`, but those are placeholder instructions and do not exist.)

Run it with:
```
repolinter lint --rulesetFile config/repolinter-ruleset.json --dryRun .
```

Use `--dryRun` to avoid auto-creating fix files (e.g. a `CODEOWNERS` file). Without `--dryRun`, repolinter will apply fixes and create files in the working directory.

This checks 3 rules: `license-file-is-MIT`, `readme-file-exists`, and `codeowners-file-exists`.

### No build, no tests, no dev server

There are no dependencies, no test suite, no build step, and no dev server to run. Changes are Markdown-only and can be validated visually or with repolinter.
