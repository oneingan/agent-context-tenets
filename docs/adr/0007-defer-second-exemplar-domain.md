# ADR 0007: Defer a Second Exemplar Domain

- Status: Accepted
- Date: 2026-04-10

## Context

The repository now has:
- a stronger DMMF-focused principle set
- new playbooks for trusted/untrusted representations, aggregate decisions, and persistence boundaries
- a deeper subscription-renewal example

The open question is whether a second exemplar domain should be added immediately.

## Decision

Do **not** add a second exemplar domain yet.

Defer it until the current playbooks and example expose a clearly missing lesson that cannot be taught well by the subscription-renewal domain.

## Rationale

Adding another example too early would:
- increase maintenance cost
- expand retrieval surface area
- risk duplicating lessons already covered by the current exemplar

A second exemplar is justified only if it teaches something meaningfully different, such as:
- a distinct aggregate structure
- a different style of long-running workflow
- a very different persistence or context-mapping problem

## Consequences

### Positive

- keeps the corpus focused
- protects context-window efficiency
- forces the current example to carry its intended lessons well

### Negative

- some readers may still want a second domain sooner
- a few concepts may remain under-illustrated until a new lesson clearly emerges

## Rules implied by this ADR

- do not add a second exemplar just for variety
- add a new exemplar only when it teaches a substantially new modeling lesson
- prefer deepening the current example before multiplying example areas
