# Context Map

This file is the main navigation entrypoint for the framework.

## Load order

1. `README.md`
2. `context/00-map.md`
3. `context/manifests/project-manifest.yaml`
4. the smallest relevant leaf docs
5. ADRs if trade-offs are needed
6. examples only when necessary

## Areas

### `principles/`
Canonical rules and stable design tenets.

Load when you need:
- definitions
- non-negotiables
- review baselines

### `patterns/`
Reusable structures such as boundaries, workflows, errors, state transitions, integration seams, and decomposition approaches.

Load when you need:
- a reusable shape
- trade-off framing
- comparisons between alternatives

### `playbooks/`
Task-oriented guidance.

Load when you need to:
- model a domain
- define a bounded context
- review an architecture
- add an integration
- write an ADR

### `glossary/`
Vocabulary and term definitions.

Load when names or meanings are unclear.

### `review/`
Checklists and quality gates.

Load when evaluating proposed changes.

### `manifests/`
Machine-readable retrieval metadata.

Load when automating or deciding what to read next.

## Authoring rules for this directory

- one file, one abstraction level
- summary first
- link instead of duplicating
- prefer tables/checklists/state descriptions over long prose
- update manifests when adding new topics

## Planned next canonical docs

- principles for ubiquitous language and naming
- principles for boundaries and deep modules
- principles for workflows, invariants, and errors
- playbook for domain modeling
- review checklist for architecture and context quality
