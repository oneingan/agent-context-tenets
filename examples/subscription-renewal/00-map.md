# Subscription Renewal Example Map

This example shows how the framework can be applied to a compact but non-trivial domain.

## Why this example exists

Subscription renewal is a good first exemplar because it demonstrates:

- bounded contexts with different responsibilities
- business event discovery and compact event catalogs
- explicit workflows and state transitions
- domain-significant failures vs operational failures
- cross-context contracts and translation seams
- long-running behavior without requiring a large codebase
- trusted/untrusted transitions, aggregate ownership, persistence boundaries, and model evolution in a compact domain

## Recommended read order

1. `examples/subscription-renewal/01-domain-overview.md`
2. `examples/subscription-renewal/02-glossary.md`
3. `examples/subscription-renewal/03-bounded-contexts.md`
4. `examples/subscription-renewal/04-workflows-and-state.md`
5. `examples/subscription-renewal/10-event-catalog.md`
6. `examples/subscription-renewal/05-invariants-and-failure-model.md`
7. `examples/subscription-renewal/11-context-contracts.md`
8. `examples/subscription-renewal/06-trusted-and-untrusted-representations.md`
9. `examples/subscription-renewal/07-aggregate-and-ownership-boundaries.md`
10. `examples/subscription-renewal/08-persistence-and-mapping-boundaries.md`
11. `examples/subscription-renewal/09-change-scenarios.md`
12. one focused pseudocode file under `examples/subscription-renewal/pseudocode/`

## Files

- `01-domain-overview.md`
  - scope, business pressure, key events, and why the domain is useful
- `02-glossary.md`
  - domain vocabulary for the example
- `03-bounded-contexts.md`
  - context responsibilities, seams, and relationship notes
- `04-workflows-and-state.md`
  - workflows, emitted events, and state transitions
- `05-invariants-and-failure-model.md`
  - invariants, forbidden situations, and failure taxonomy
- `06-trusted-and-untrusted-representations.md`
  - where the example earns trust and narrows representations
- `07-aggregate-and-ownership-boundaries.md`
  - identity, value-object, and aggregate-boundary decisions
- `08-persistence-and-mapping-boundaries.md`
  - data ownership, mapping boundaries, and read-side projection notes
- `09-change-scenarios.md`
  - requirement changes traced through language, events, contracts, and mappings
- `10-event-catalog.md`
  - compact business-event catalog for the example
- `11-context-contracts.md`
  - contract tables and anti-corruption notes between contexts
- `pseudocode/renew-subscription.md`
  - small pseudocode illustration of renewal initiation
- `pseudocode/process-billing-outcome.md`
  - small pseudocode illustration of outcome handling

## Related canonical docs

- `context/playbooks/01-domain-modeling-playbook.md`
- `context/playbooks/02-bounded-context-definition-playbook.md`
- `context/playbooks/03-workflow-and-state-modeling-playbook.md`
- `context/playbooks/05-trusted-and-untrusted-representations-playbook.md`
- `context/playbooks/06-entity-value-object-and-aggregate-design-playbook.md`
- `context/playbooks/07-persistence-and-mapping-boundaries-playbook.md`
- `context/playbooks/08-business-event-discovery-and-event-catalog-playbook.md`
- `context/playbooks/09-domain-error-and-failure-taxonomy-playbook.md`
- `context/playbooks/10-cross-context-contract-and-anti-corruption-playbook.md`
- `context/review/06-event-and-contract-artifact-checklist.md`
- `context/patterns/01-boundary-and-decomposition-patterns.md`
- `context/patterns/02-workflow-and-state-transition-patterns.md`
- `context/patterns/03-error-and-edge-translation-patterns.md`
- `context/principles/07-type-shaped-models-and-illegal-states.md`
- `context/principles/08-entities-value-objects-and-aggregates.md`
- `context/principles/09-workflow-pipelines-effects-and-dependencies.md`
- `context/principles/10-serialization-persistence-and-data-ownership.md`
- `context/principles/11-evolving-models-through-change.md`
