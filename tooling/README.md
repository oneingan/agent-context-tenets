# Tooling

This directory holds lightweight helpers and evaluation notes.

Current tools:
- `tooling/run-checks.sh` — run the lightweight validation checks
- `tooling/validate-manifests.sh` — validate YAML manifests with `yq`
- `tooling/check-doc-budgets.sh` — warn when docs exceed soft size budgets
- `tooling/tooling-evaluation.md` — explains what is implemented now vs deferred

Current stance:
- implement lightweight validation now
- defer heavy export automation until the corpus is more stable
- keep CI aligned with the local `tooling/run-checks.sh` command
