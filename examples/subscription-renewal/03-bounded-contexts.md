# Subscription Renewal Bounded Contexts

## Summary

- The example uses three bounded contexts: Subscription Lifecycle, Billing, and Notifications.
- The main semantic boundary is between lifecycle decisions and edge execution details.
- Billing and Notifications are kept separate so their technical churn does not rewrite the lifecycle model.
- The example favors explicit translation at the seam over shared internal structures.

## Context table

| Context | Purpose | Responsibilities | Non-responsibilities |
|---|---|---|---|
| Subscription Lifecycle | Protect the meaning of subscription state and renewal decisions. | eligibility, renewal state, grace period, lapse decisions, emitted lifecycle outcomes | payment gateway details, message delivery mechanics |
| Billing | Execute charge attempts and classify payment outcomes. | billing attempts, gateway integration, payment result classification | deciding subscription lifecycle meaning |
| Notifications | Communicate already decided business outcomes. | message selection, delivery attempts, channel-specific behavior | deciding whether renewal succeeded or failed |

## Relationships

### Subscription Lifecycle ↔ Billing

- Lifecycle requests a billing attempt when renewal is initiated.
- Billing returns or emits a billing outcome.
- Lifecycle translates that outcome into subscription meaning.

Shared or translated terms:
- shared enough: subscription identity, billing outcome type
- translated: gateway-specific failure detail becomes stable lifecycle-relevant categories

### Subscription Lifecycle ↔ Notifications

- Lifecycle emits business outcomes such as renewal succeeded, retry scheduled, or subscription lapsed.
- Notifications consumes those outcomes and decides how to communicate them.

### Billing ↔ Notifications

No direct dependency is required for the core example. Communication is mediated through lifecycle outcomes.

## Why these boundaries earn their cost

- Billing changes for gateway or settlement reasons.
- Notifications changes for channel or content reasons.
- Subscription Lifecycle changes for business policy reasons.

Keeping these separate protects the core model from edge churn.

## Minimal context cards

### Subscription Lifecycle

- Purpose: decide whether a subscription may renew and what state it should occupy
- Core vocabulary: subscription, renewal window, grace period, lapse
- Main workflows: renew subscription, process billing outcome, lapse subscription
- Main invariants: only eligible subscriptions may begin renewal; lapsed subscriptions are not treated as active

### Billing

- Purpose: attempt charging and classify outcomes
- Core vocabulary: billing attempt, payment success, payment failure
- Main workflows: attempt charge, return billing outcome

### Notifications

- Purpose: communicate already determined outcomes
- Core vocabulary: notification request, delivery channel, message template
- Main workflows: send renewal success notice, send retry notice, send lapse notice

## Related docs

- `examples/subscription-renewal/02-glossary.md`
- `examples/subscription-renewal/04-workflows-and-state.md`
- `context/principles/03-bounded-contexts-and-boundaries.md`
