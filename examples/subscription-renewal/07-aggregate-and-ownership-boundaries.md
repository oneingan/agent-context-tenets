# Subscription Renewal Aggregate and Ownership Boundaries

## Summary

- The example keeps aggregate boundaries smaller than the whole bounded context.
- Identity and value distinctions are explicit enough to protect core invariants.
- Cross-aggregate and cross-context coordination is handled through workflows and outcomes rather than shared internals.
- Ownership boundaries show where consistency must hold together.

## Aggregate sketch

### Subscription Lifecycle aggregate

Likely entity:
- `Subscription`

Likely value objects:
- `RenewalWindow`
- `SubscriptionTerm`
- `GracePeriodPolicy`
- `RetryEligibility`

Protected together:
- current lifecycle state
- pending renewal state
- term extension rules
- lapse decision rules

### Billing aggregate

Likely entity:
- `BillingAttempt`

Likely value objects:
- `ChargeAmount`
- `BillingOutcome`
- `GatewayReference`

Protected together:
- attempt identity
- outcome classification
- retry-related attempt history

### Notifications aggregate or request unit

This example keeps Notifications lightweight. It may track `NotificationRequest` as an entity if delivery lifecycle matters, or treat it as a thinner request object if only dispatch is relevant.

## Ownership rule

- Lifecycle owns the meaning of subscription renewal and lapse.
- Billing owns payment attempt execution and provider translation.
- Notifications owns message dispatch behavior.

No neighboring context should silently rewrite those meanings.

## Why aggregate boundaries matter here

- a `Subscription` should not renew twice for the same term by accident
- a `BillingAttempt` should not decide lifecycle meaning directly
- notification delivery should not decide whether renewal succeeded

## Related docs

- `examples/subscription-renewal/03-bounded-contexts.md`
- `context/playbooks/06-entity-value-object-and-aggregate-design-playbook.md`
- `context/principles/08-entities-value-objects-and-aggregates.md`
