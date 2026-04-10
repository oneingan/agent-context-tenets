# Subscription Renewal Invariants and Failure Model

## Summary

- The example makes correctness rules explicit rather than leaving them implicit in code.
- Invariants protect the meaning of subscription state and renewal outcomes.
- Failures are grouped into domain-significant, contract, operational, and unexpected categories.
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

## Failure taxonomy

| Failure | Category | Detected in | Stable surface | Recovery owner |
|---|---|---|---|---|
| renewal window closed | domain-significant | Lifecycle intake | renewal rejected | Lifecycle |
| subscription cancelled | domain-significant | Lifecycle intake | renewal rejected | Lifecycle |
| renewal already pending | domain-significant | Lifecycle intake | renewal rejected | Lifecycle |
| missing subscription identity | contract / input | request boundary | invalid renewal request | edge adapter |
| unknown billing outcome category | contract / input | Lifecycle seam | invalid billing outcome | Billing seam owner |
| payment gateway timeout | operational | Billing edge | billing outcome unavailable | Billing / operations |
| billing success with no pending renewal | unexpected outcome | Lifecycle outcome handler | unexpected billing outcome | Lifecycle |
| notification provider outage | operational | Notifications edge | notification delivery delayed | Notifications / operations |

## Translation rule

A gateway-specific error such as `provider_timeout_504` should not become a core lifecycle concept.
The lifecycle context only needs a stable category such as `billing outcome unavailable` if the distinction matters to business recovery.

## Review prompts

- Are the invariants visible near the workflow and state rules they protect?
- Are domain failures named in domain language?
- Are operational failures translated before entering the core model?
- Are unexpected or out-of-sequence outcomes quarantined instead of normalized?
- Is notification behavior clearly secondary to lifecycle decisions?

## Related docs

- `examples/subscription-renewal/04-workflows-and-state.md`
- `examples/subscription-renewal/11-context-contracts.md`
- `context/playbooks/09-domain-error-and-failure-taxonomy-playbook.md`
- `context/patterns/03-error-and-edge-translation-patterns.md`
- `context/principles/05-errors-and-edge-responsibilities.md`
- `context/principles/07-type-shaped-models-and-illegal-states.md`
- `context/review/06-event-and-contract-artifact-checklist.md`
