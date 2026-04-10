# Context Map

This file is the main navigation entrypoint for the framework.

## Default load order

1. `README.md`
2. `context/00-map.md`
3. `context/manifests/project-manifest.yaml`
4. the nearest area map or manifest
5. the smallest relevant leaf docs
6. ADRs if trade-offs are needed
7. examples only when necessary

## Quick start by task

### Shape or refactor the repository
Read:
1. `context/principles/01-information-architecture-and-manifests.md`
2. `context/principles/06-deep-modules-and-information-hiding.md`
3. `docs/adr/0002-information-architecture-and-manifests.md`

### Compare reusable design shapes
Read:
1. `context/patterns/00-map.md`
2. the smallest relevant pattern doc for boundaries, workflows, errors, or examples

### Model a domain or capability
Read:
1. `context/playbooks/01-domain-modeling-playbook.md`
2. `context/principles/02-ubiquitous-language-and-naming.md`
3. `context/principles/03-bounded-contexts-and-boundaries.md`
4. `context/principles/04-workflows-invariants-and-state.md`

### Define a bounded context
Read:
1. `context/playbooks/02-bounded-context-definition-playbook.md`
2. `context/patterns/01-boundary-and-decomposition-patterns.md`
3. `context/review/02-architecture-review-checklist.md`

### Model workflow behavior or state changes
Read:
1. `context/playbooks/03-workflow-and-state-modeling-playbook.md`
2. `context/patterns/02-workflow-and-state-transition-patterns.md`
3. `context/principles/05-errors-and-edge-responsibilities.md`

### Review docs or designs
Read:
1. `context/review/01-quality-gates.md`
2. `context/review/03-documentation-quality-checklist.md`
3. `context/review/05-vocabulary-drift-checklist.md`

### See one worked example
Read:
1. `examples/00-map.md`
2. `examples/subscription-renewal/00-map.md`
3. the smallest relevant pseudocode file

### Decide how examples should behave
Read:
1. `docs/adr/0001-example-strategy.md`
2. `context/patterns/04-example-linking-patterns.md`
3. `context/review/04-example-acceptance-criteria.md`
4. `examples/README.md`

## Areas

### `principles/`
Canonical rules and stable design tenets.

Entry docs:
- `context/principles/00-map.md`
- `context/manifests/principles-manifest.yaml`

### `patterns/`
Reusable structures and comparative solution shapes.

Entry docs:
- `context/patterns/00-map.md`
- `context/manifests/patterns-manifest.yaml`

### `glossary/`
Vocabulary and naming guidance.

Entry docs:
- `context/glossary/00-map.md`
- `context/manifests/glossary-manifest.yaml`

### `playbooks/`
Task-oriented guidance.

Entry docs:
- `context/playbooks/00-map.md`
- `context/manifests/playbooks-manifest.yaml`

### `review/`
Checklists and quality gates.

Entry docs:
- `context/review/00-map.md`
- `context/manifests/review-manifest.yaml`

### `examples/`
Secondary, pseudocode-first illustrations.

Entry docs:
- `examples/00-map.md`
- `context/manifests/examples-manifest.yaml`

### `manifests/`
Machine-readable retrieval metadata.

Current entry docs:
- `context/manifests/README.md`
- `context/manifests/project-manifest.yaml`

## Authoring rules for this directory

- one file, one abstraction level
- summary first
- link instead of duplicating
- prefer tables, checklists, state descriptions, and short examples over long prose
- update maps and manifests when adding new canonical docs or new major example areas

## Current canonical layers available now

- principles
- patterns
- glossary
- playbooks
- review

## Current secondary example area

- subscription renewal
