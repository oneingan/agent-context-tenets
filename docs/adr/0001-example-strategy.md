# ADR 0001: Example Strategy

- Status: Accepted
- Date: 2026-04-10

## Context

This repository should remain language agnostic, but examples can still be valuable. The open question is whether the repo should contain:

1. no code at all
2. pseudocode only
3. polyglot examples

## Decision

Adopt a **three-tier example strategy**:

1. **Canonical core:** prose, checklists, manifests, schemas, state tables, ADRs
2. **Default illustration layer:** pseudocode and structured text examples
3. **Optional extension layer:** tiny polyglot examples kept separate from canonical docs

## Rationale

This approach:

- preserves language neutrality in the core
- avoids early repo bloat
- keeps context requirements low
- still allows demonstrating language-specific strengths when it truly matters
- makes it easier to grow examples incrementally

## Consequences

### Positive

- better fit for limited context windows
- easier reuse across projects and languages
- lower maintenance burden than full code examples everywhere
- clearer separation between principle and implementation

### Negative

- some readers may want more executable examples sooner
- pseudocode can become vague if not written carefully
- polyglot examples will still need curation when added

## Rules implied by this ADR

- do not add large code examples to canonical principle docs
- keep pseudocode short and focused on behavior or boundaries
- if polyglot examples are added, isolate them under `examples/`
- when a code example is added, explain **why this language is being shown**
