# Principles Map

This directory holds the canonical rules for the framework.

## How to use this directory

Read the smallest subset that matches the task.

### If you are shaping the repository itself
Read:
1. `01-information-architecture-and-manifests.md`
2. `06-deep-modules-and-information-hiding.md`

### If you are modeling a domain
Read:
1. `02-ubiquitous-language-and-naming.md`
2. `03-bounded-contexts-and-boundaries.md`
3. `04-workflows-invariants-and-state.md`
4. `05-errors-and-edge-responsibilities.md`

### If you are reviewing proposed changes
Read:
1. `01-information-architecture-and-manifests.md`
2. `05-errors-and-edge-responsibilities.md`
3. `06-deep-modules-and-information-hiding.md`

## Documents

- `01-information-architecture-and-manifests.md`
  - file and directory responsibilities, load order, size budgets, manifest conventions
- `02-ubiquitous-language-and-naming.md`
  - vocabulary-first design and naming rules
- `03-bounded-contexts-and-boundaries.md`
  - how to partition models and define seams between them
- `04-workflows-invariants-and-state.md`
  - how to model behavior, state transitions, and constraints
- `05-errors-and-edge-responsibilities.md`
  - how to make failure modes explicit and keep edge concerns at the edges
- `06-deep-modules-and-information-hiding.md`
  - how to keep the knowledge base deep, compact, and low-friction to retrieve

## Directory rules

- keep one abstraction level per file
- summarize first, elaborate second
- treat these files as canonical over examples
- prefer links to duplication
- update `context/manifests/principles-manifest.yaml` when adding or renaming docs

## Related docs

- `context/00-map.md`
- `context/manifests/project-manifest.yaml`
- `context/manifests/principles-manifest.yaml`
- `docs/adr/0001-example-strategy.md`
- `docs/adr/0002-information-architecture-and-manifests.md`
