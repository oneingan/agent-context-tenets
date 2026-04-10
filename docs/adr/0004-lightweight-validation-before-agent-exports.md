# ADR 0004: Lightweight Validation Before Agent Exports

- Status: Accepted
- Date: 2026-04-10

## Context

The repository now has enough structure that drift in manifests, maps, and document size can create maintenance problems. At the same time, the corpus is still evolving, so heavy automation for agent-specific exports would likely add churn and duplicated maintenance.

## Decision

Adopt a lightweight tooling strategy:

1. implement validation for manifests now
2. implement simple doc-budget checks now
3. provide one lightweight command to run those checks
4. defer automatic export generation for Claude, Cursor, Copilot, or AGENTS formats until the corpus stabilizes further

## Rationale

This approach provides immediate value where failure risk is highest:

- invalid YAML breaks retrieval and tooling
- oversized docs work against the repo's context-window strategy
- lightweight checks are cheap to maintain

By contrast, export generators would currently:
- duplicate evolving structure
- require curation rules that are not fully stable yet
- add maintenance burden before the corpus settles

## Consequences

### Positive

- quick feedback on structural drift
- low maintenance overhead
- better alignment with the repository's limited-context goals

### Negative

- no one-command export to external agent formats yet
- validation remains intentionally shallow for now
- some manual curation is still required when reusing content elsewhere

## Rules implied by this ADR

- prefer small validation tools over heavy automation in early phases
- export automation must justify its maintenance cost before being added
- corpus stability comes before export convenience
