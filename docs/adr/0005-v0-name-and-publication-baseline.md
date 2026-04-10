# ADR 0005: v0 Name and Publication Baseline

- Status: Accepted
- Date: 2026-04-10

## Context

The repository has reached a coherent v0 shape and needs a stable publication baseline for naming, maintenance, and future sharing.

## Decision

For v0, keep the repository name as **`agent-context-tenets`**.

Also adopt the following publication baseline:

1. add contribution guidance
2. add CI that runs the lightweight repository checks
3. keep agent-specific export generation deferred until reuse patterns justify it
4. add new exemplar domains only when they teach a substantially new lesson

## Rationale

The current name keeps continuity with the upstream inspiration while making the repository's purpose explicit: agent-readable context and tenets.

The publication baseline emphasizes maintainability over premature packaging automation.

## Consequences

### Positive

- the repo now has a stable v0 identity
- contribution and review expectations are clearer
- CI protects the structure from silent drift
- the project avoids overcommitting to export automation too early

### Negative

- the name remains somewhat long
- future branding may still revisit the name
- agent-specific export convenience remains deferred for now

## Rules implied by this ADR

- treat `agent-context-tenets` as the v0 public name unless a later ADR changes it
- keep CI lightweight and aligned with local checks
- new exemplar domains must justify themselves by teaching something meaningfully different
