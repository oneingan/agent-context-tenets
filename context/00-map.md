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

### Model a domain or capability
Read:
1. `context/principles/02-ubiquitous-language-and-naming.md`
2. `context/principles/03-bounded-contexts-and-boundaries.md`
3. `context/principles/04-workflows-invariants-and-state.md`
4. `context/principles/05-errors-and-edge-responsibilities.md`

### Decide how examples should behave
Read:
1. `docs/adr/0001-example-strategy.md`
2. `examples/README.md`

## Areas

### `principles/`
Canonical rules and stable design tenets.

Entry docs:
- `context/principles/00-map.md`
- `context/manifests/principles-manifest.yaml`

### `patterns/`
Reusable structures such as boundaries, workflows, errors, state transitions, integration seams, and decomposition approaches.

Current state: planned.

### `playbooks/`
Task-oriented guidance.

Current state: planned.

### `glossary/`
Vocabulary and term definitions.

Current state: planned.

### `review/`
Checklists and quality gates.

Current state: planned.

### `manifests/`
Machine-readable retrieval metadata.

Current entry docs:
- `context/manifests/README.md`
- `context/manifests/project-manifest.yaml`
- `context/manifests/principles-manifest.yaml`

## Authoring rules for this directory

- one file, one abstraction level
- summary first
- link instead of duplicating
- prefer tables, checklists, state descriptions, and short examples over long prose
- update maps and manifests when adding new canonical docs

## Current canonical principle set

- information architecture and manifests
- ubiquitous language and naming
- bounded contexts and boundaries
- workflows, invariants, and state
- errors and edge responsibilities
- deep modules and information hiding
