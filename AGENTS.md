## Cursor Cloud specific instructions

This is GitHub's `.github` organization-level meta-repository. It contains **no application code** — only Markdown community health files (`README.md`, `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`, `profile/README.md`) and a `config/repolinter-ruleset.json` configuration.

### Linting

The only tooling available is [repolinter](https://github.com/todogroup/repolinter), which validates repos against policy rules defined in `config/repolinter-ruleset.json`.

Run it with:
```
repolinter lint --rulesetFile config/repolinter-ruleset.json --dryRun .
```

Use `--dryRun` to avoid auto-creating fix files (e.g. a `CODEOWNERS` file). Without `--dryRun`, repolinter will apply fixes and create files in the working directory.

### No build, no tests, no dev server

There are no dependencies, no test suite, no build step, and no dev server to run. Changes are Markdown-only and can be validated visually or with repolinter.
