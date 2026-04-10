# Subscription Renewal Workflows and State

## Summary

- The example uses explicit workflow descriptions instead of implicit controller or database behavior.
- Subscription Lifecycle owns the meaning of state transitions.
- Billing outcomes are translated into lifecycle outcomes rather than treated as the same thing.
- Long-running behavior is visible through waiting and grace states.

## Primary workflow: Renew Subscription

### Trigger

- the subscription enters its renewal window, or
- a valid renewal request is made during that window

### Input

- subscription identity
- current lifecycle state
- renewal policy information

### Output

- renewal initiated, or
- explicit rejection such as renewal window closed or subscription not eligible

### Core steps

1. load the subscription state
2. verify renewal eligibility
3. calculate the next renewal term
4. transition to `renewal_pending_payment`
5. request a billing attempt at the edge
6. await billing outcome

## Secondary workflow: Process Billing Outcome

### Trigger

- Billing emits a success or failure outcome for a pending renewal

### Input

- subscription identity
- pending renewal attempt reference
- billing outcome classification

### Output

- renewed subscription
- retry scheduled
- explicit lapse
- or a classified unexpected/out-of-sequence outcome

### Core steps

1. verify that a renewal is pending
2. translate the billing outcome into lifecycle meaning
3. decide whether to renew, retry, or lapse
4. transition state accordingly
5. emit lifecycle outcome for Notifications or other listeners

## State model

| State | Meaning |
|---|---|
| active | subscription is currently valid |
| renewal_pending_payment | renewal has started and awaits billing outcome |
| grace_period | billing failed but recovery is still allowed |
| lapsed | renewal did not complete in time |
| cancelled | explicit stop state outside the main renewal flow |

## Transition table

| From | Trigger | Guard | To | Notes |
|---|---|---|---|---|
| active | renewal requested | within renewal window and not cancelled | renewal_pending_payment | initiate billing at the edge |
| renewal_pending_payment | billing succeeded | pending attempt exists | active | extend term and emit renewal succeeded |
| renewal_pending_payment | billing failed | retry still allowed | grace_period | emit retry scheduled |
| grace_period | retry requested | retry eligibility remains | renewal_pending_payment | start another billing attempt |
| grace_period | grace period expired | no successful renewal | lapsed | emit subscription lapsed |
| cancelled | renewal requested | none | cancelled | explicit rejection path |

## Long-running behavior notes

- `renewal_pending_payment` is a waiting state.
- `grace_period` is also time-sensitive and may require retries or scheduled checks.
- Notifications are not part of the core transition decision; they react after a business outcome exists.

## Related docs

- `examples/subscription-renewal/05-invariants-and-failure-model.md`
- `examples/subscription-renewal/pseudocode/renew-subscription.md`
- `examples/subscription-renewal/pseudocode/process-billing-outcome.md`
- `context/patterns/02-workflow-and-state-transition-patterns.md`
- `context/principles/04-workflows-invariants-and-state.md`
