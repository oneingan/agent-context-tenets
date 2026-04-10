# Subscription Renewal Invariants and Failure Model

## Summary

- The example makes correctness rules explicit rather than leaving them implicit in code.
- Invariants protect the meaning of subscription state and renewal outcomes.
- Failures are grouped into domain-significant, contract, and operational categories.
- Billing and notification technology details are translated before they affect the lifecycle model.

## Invariants

- a cancelled subscription does not enter `renewal_pending_payment`
- a lapsed subscription is not treated as active
- only one pending renewal attempt exists for a subscription term at a time
- a successful renewal extends the term before downstream notifications are requested
- a retry path may exist only while retry eligibility or grace period rules still allow it

## Forbidden situations

- starting a new renewal while one is already pending
- renewing outside the allowed renewal window
- treating a gateway timeout as if it were a successful business renewal
- letting notification delivery success determine whether the subscription renewed

## Failure categories

### Domain-significant failures

- renewal window closed
- subscription cancelled
- renewal already pending
- grace period expired
- retry no longer allowed

These belong in the lifecycle model and should be named in business language.

### Contract or input failures

- missing subscription identity
- unknown billing outcome category
- malformed renewal request

These indicate that the boundary interaction is wrong.

### Operational failures

- payment gateway timeout
- message bus delay
- database unavailable
- notification provider outage

These should be handled at the edge and translated before they affect the lifecycle model.

## Translation rule

A gateway-specific error such as `provider_timeout_504` should not become a core lifecycle concept. The lifecycle context only needs a stable category such as `billing outcome unavailable` or `billing attempt unresolved`, if that distinction matters.

## Review prompts

- Are the invariants visible near the workflow and state rules they protect?
- Are domain failures named in domain language?
- Are operational failures translated before entering the core model?
- Is notification behavior clearly secondary to lifecycle decisions?

## Related docs

- `examples/subscription-renewal/04-workflows-and-state.md`
- `context/patterns/03-error-and-edge-translation-patterns.md`
- `context/principles/05-errors-and-edge-responsibilities.md`
- `context/review/02-architecture-review-checklist.md`
