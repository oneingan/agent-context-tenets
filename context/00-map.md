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

### Model a domain deeply
Read:
1. `docs/research/dmmf-deep-synthesis.md`
2. `context/playbooks/01-domain-modeling-playbook.md`
3. `context/playbooks/08-business-event-discovery-and-event-catalog-playbook.md`
4. `context/principles/07-type-shaped-models-and-illegal-states.md`
5. `context/principles/08-entities-value-objects-and-aggregates.md`
6. `context/principles/03-bounded-contexts-and-boundaries.md`

### Discover business events or build an event catalog
Read:
1. `context/playbooks/08-business-event-discovery-and-event-catalog-playbook.md`
2. `context/principles/04-workflows-invariants-and-state.md`
3. `examples/subscription-renewal/10-event-catalog.md`

### Model workflow behavior, effects, or state changes
Read:
1. `context/principles/04-workflows-invariants-and-state.md`
2. `context/principles/09-workflow-pipelines-effects-and-dependencies.md`
3. `context/playbooks/03-workflow-and-state-modeling-playbook.md`
4. `context/playbooks/09-domain-error-and-failure-taxonomy-playbook.md`

### Define cross-context contracts or translation seams
Read:
1. `context/playbooks/10-cross-context-contract-and-anti-corruption-playbook.md`
2. `context/principles/03-bounded-contexts-and-boundaries.md`
3. `context/principles/10-serialization-persistence-and-data-ownership.md`
4. `examples/subscription-renewal/11-context-contracts.md`

### Integrate persistence or revisit data ownership
Read:
1. `context/principles/10-serialization-persistence-and-data-ownership.md`
2. `context/playbooks/07-persistence-and-mapping-boundaries-playbook.md`
3. `context/patterns/03-error-and-edge-translation-patterns.md`
4. `examples/subscription-renewal/08-persistence-and-mapping-boundaries.md`

### Evolve the model after requirement changes
Read:
1. `context/principles/11-evolving-models-through-change.md`
2. `templates/change-impact-analysis-template.md`
3. `examples/subscription-renewal/09-change-scenarios.md`
4. `context/playbooks/04-adr-writing-playbook.md`

### Review docs or designs
Read:
1. `context/review/01-quality-gates.md`
2. `context/review/03-documentation-quality-checklist.md`
3. `context/review/05-vocabulary-drift-checklist.md`
4. `context/review/06-event-and-contract-artifact-checklist.md`

### See one worked example
Read:
1. `examples/00-map.md`
2. `examples/subscription-renewal/00-map.md`
3. the smallest relevant example note or pseudocode file

### Decide how examples should behave
Read:
1. `docs/adr/0001-example-strategy.md`
2. `context/patterns/04-example-linking-patterns.md`
3. `context/review/04-example-acceptance-criteria.md`
4. `docs/adr/0007-defer-second-exemplar-domain.md`
5. `examples/README.md`

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

