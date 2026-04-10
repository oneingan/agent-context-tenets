# Boundary and Decomposition Patterns

## Summary

- Good boundaries protect meaning, ownership, and change cadence.
- These patterns help choose where to split, where to translate, and where to keep a shared vocabulary.
- Use them to compare options, not as mandatory templates.
- A pattern is useful only if it reduces ambiguity or future change cost.

## Load this when

- comparing decomposition options
- deciding whether a new bounded context is justified
- reviewing context leakage or ownership confusion

## Pattern 1: Single Decision Owner

### Use when
A concept or workflow has one clear place where business meaning should be decided.

### Shape
- one bounded context owns the decision
- adjacent contexts consume the result, not the internal reasoning
- the owner emits or returns stable outcomes

### Benefits
- clearer ownership
- less accidental coupling
- easier review of invariants

### Risks
- over-centralization if unrelated decisions are forced together

## Pattern 2: Translation Seam

### Use when
Two contexts use related concepts with different meanings or levels of detail.

### Shape
- define a seam between contexts
- translate incoming and outgoing terms explicitly
- do not share internal structures across the seam

### Benefits
- protects local language
- limits leakage of foreign concepts

### Risks
- extra ceremony if the two sides are not actually meaningfully different

## Pattern 3: Shared Vocabulary by Agreement

### Use when
Two contexts genuinely share a small stable set of terms.

### Shape
- agree on a narrow shared vocabulary
- keep the shared surface small and stable
- let deeper internal models remain private

### Benefits
- avoids unnecessary translation
- keeps shared contracts simple

### Risks
- the shared set can grow until it becomes accidental coupling

## Pattern 4: Split by Change Pressure

### Use when
Different parts of the model change for different business reasons or at different speeds.

### Shape
- separate the areas whose policies or language evolve independently
- connect them through explicit contracts

### Benefits
- lower change blast radius
- clearer ownership boundaries

### Risks
- splitting too early can create ceremony without value

## Pattern 5: Shielding Edge Context

### Use when
A vendor, gateway, or protocol changes frequently and should not contaminate the core domain model.

### Shape
- place translation and protocol detail at the edge-facing boundary
- expose stable domain-relevant outputs inward

### Benefits
- protects the core model from edge churn
- makes replacement easier

### Risks
- if the shield is too thin, leakage still occurs; if too thick, it may become opaque and hard to review

## Related example

The `examples/subscription-renewal/03-bounded-contexts.md` example combines:
- Single Decision Owner in Subscription Lifecycle
- Translation Seam between Lifecycle and Billing
- Shielding Edge Context around billing details

## Related docs

- `context/principles/03-bounded-contexts-and-boundaries.md`
- `context/playbooks/02-bounded-context-definition-playbook.md`
- `examples/subscription-renewal/03-bounded-contexts.md`
