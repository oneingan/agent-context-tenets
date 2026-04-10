# ADR 0003: First Exemplar Domain is Subscription Renewal

- Status: Accepted
- Date: 2026-04-10

## Context

The repository needed a first worked example that could demonstrate the framework without turning the examples directory into a full application or a language-specific codebase.

## Decision

Use **subscription renewal** as the first exemplar domain.

Represent it with:
- glossary and overview docs
- bounded-context and workflow docs
- explicit invariants and failure categories
- small pseudocode illustrations instead of runnable application code

## Rationale

Subscription renewal is a strong first example because it shows:

- a clear ubiquitous language
- multiple bounded contexts with meaningful seams
- explicit state transitions and long-running behavior
- domain-significant failures distinct from operational failures
- clear separation between lifecycle meaning and edge concerns such as billing or notifications

## Consequences

### Positive

- demonstrates most core framework ideas in a compact domain
- stays language agnostic
- avoids large example codebases
- creates a practical base for future polyglot micro-examples if they become useful

### Negative

- the example does not cover every kind of domain
- some readers may prefer an order or catalog domain first
- notification and billing details remain intentionally simplified

## Rules implied by this ADR

- examples should remain pseudocode-first unless language choice teaches something unique
- the exemplar domain should link back to canonical principles and playbooks
- future examples should add new lessons, not duplicate the same ground
