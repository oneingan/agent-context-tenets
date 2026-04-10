# Example Acceptance Criteria

## Summary

- Examples are secondary evidence, not the canonical source of truth.
- Prefer pseudocode and tiny focused illustrations over large runnable apps.
- A new example should justify both its existence and its language choice.
- If deleting the example would break understanding, the canonical docs are insufficient.

## Use this when

- proposing a new example
- reviewing whether a code sample belongs in the repo
- deciding whether a polyglot example is justified

## Acceptance criteria

- [ ] the example points back to the relevant canonical docs
- [ ] the example teaches something prose alone could not teach clearly
- [ ] the example is as small as possible
- [ ] the example is isolated from the canonical rules
- [ ] the example does not redefine concepts already defined elsewhere
- [ ] if a real language is used, the reason for that language choice is explicit
- [ ] the example does not create maintenance burden disproportionate to its value

## Rejection signals

Reject or simplify an example if:
- it is effectively the real specification
- it exists only because the principles are still vague
- it duplicates another example with little additional value
- it requires loading a large codebase to learn a small lesson

## Related docs

- `docs/adr/0001-example-strategy.md`
- `context/review/01-quality-gates.md`
- `examples/README.md`
