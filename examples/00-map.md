# Examples Map

This directory contains secondary, pseudocode-first illustrations of the framework.

## How to use this directory

Examples are not the main specification. Read the relevant canonical docs first.

### If you want to see the framework applied to one domain
Read:
1. `examples/subscription-renewal/00-map.md`
2. the smallest relevant note or pseudocode file under `examples/subscription-renewal/`

## Available examples

- `examples/subscription-renewal/`
  - subscription renewal as a compact exemplar domain with multiple bounded contexts, explicit state transitions, event catalogs, and contract tables

## Rules for this directory

- examples stay smaller than the concepts they illustrate
- examples link back to canonical docs
- examples do not redefine framework principles
- prefer pseudocode over real language implementations unless a language choice teaches something unique

## Related docs

- `context/review/04-example-acceptance-criteria.md`
- `context/review/06-event-and-contract-artifact-checklist.md`
- `docs/adr/0001-example-strategy.md`
- `docs/adr/0003-first-exemplar-domain-subscription-renewal.md`
