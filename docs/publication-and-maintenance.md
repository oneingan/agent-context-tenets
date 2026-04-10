# Publication and Maintenance Notes

## Summary

- v0 is ready for publication as `agent-context-tenets`.
- CI should run the same lightweight checks used locally.
- Export automation to other agent formats remains intentionally deferred.
- A second exemplar domain should only be added if it teaches a meaningfully new lesson.

## Publication checklist

- [x] stable v0 repository name chosen
- [x] contribution guidance added
- [x] local validation scripts added
- [x] CI workflow added
- [x] publication baseline recorded in an ADR
- [x] choose and add a license
- [ ] add a GitHub remote and push when ready

## Local validation

```bash
nix shell nixpkgs#yq -c ./tooling/run-checks.sh
```

## Suggested GitHub push flow

If you create the remote manually, the push sequence will usually be:

```bash
git remote add origin <your-github-repo-url>
git push -u origin main
```

## What is intentionally deferred

- automatic export generation for Claude, Cursor, Copilot, or AGENTS subsets
- heavy markdown linting and advanced retrieval automation
- additional exemplar domains without a clearly new teaching purpose

## Related docs

- `LICENSE`
- `CONTRIBUTING.md`
- `tooling/tooling-evaluation.md`
- `docs/adr/0004-lightweight-validation-before-agent-exports.md`
- `docs/adr/0005-v0-name-and-publication-baseline.md`
- `docs/adr/0006-license-choice.md`
