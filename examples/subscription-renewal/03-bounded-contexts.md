# Subscription Renewal Bounded Contexts

## Summary

- The example uses three bounded contexts: Subscription Lifecycle, Billing, and Notifications.
- Subscription Lifecycle owns the business meaning of renewal state and outcome.
- Billing and Notifications are kept separate so their churn does not rewrite the lifecycle model.
- Each seam has an explicit contract and translation story rather than a shared internal model.

## Context table

| Context | Purpose | Responsibilities | Non-responsibilities |
|---|---|---|---|
| Subscription Lifecycle | Protect the meaning of subscription state and renewal decisions. | eligibility, renewal state, grace period, lapse decisions, emitted lifecycle outcomes | payment gateway details, message delivery mechanics |
| Billing | Execute charge attempts and classify payment outcomes. | billing attempts, gateway integration, payment result classification | deciding subscription lifecycle meaning |
| Notifications | Communicate already decided business outcomes. | message selection, delivery attempts, channel-specific behavior | deciding whether renewal succeeded or failed |

## Relationship notes

| Context seam | Purpose | Contract owner / shape | Translation note |
|---|---|---|---|
| Subscription Lifecycle → Billing | request a charge attempt for a pending renewal | Billing owns the accepted request surface | lifecycle state meaning stays private to Lifecycle |
| Billing → Subscription Lifecycle | report a stable billing outcome | Lifecycle owns the inward-facing outcome categories it relies on | provider-specific outcomes are collapsed inside Billing |
| Subscription Lifecycle → Notifications | request communication after an already-decided outcome | Lifecycle owns outcome meaning; Notifications owns delivery behavior | templates, channels, and retry mechanics stay local to Notifications |
| Billing ↔ Notifications | none in the core example | no direct seam needed | any future coordination should avoid bypassing Lifecycle-owned meaning |

## Why these boundaries earn their cost

- Billing changes for gateway or settlement reasons.
- Notifications changes for channel or content reasons.
- Subscription Lifecycle changes for business policy reasons.

Keeping these separate protects the core model from edge churn and keeps contracts small.

## Minimal context cards

### Subscription Lifecycle

- Purpose: decide whether a subscription may renew and what state it should occupy
- Core vocabulary: subscription, renewal window, grace period, lapse
- Main workflows: renew subscription, process billing outcome, lapse subscription
- Main invariants: only eligible subscriptions may begin renewal; lapsed subscriptions are not treated as active

### Billing

- Purpose: attempt charging and classify outcomes
- Core vocabulary: billing attempt, payment success, payment failure
- Main workflows: request billing attempt, classify provider outcome, report billing outcome

### Notifications

- Purpose: communicate already determined outcomes
- Core vocabulary: notification request, delivery channel, message template
- Main workflows: send renewal success notice, send retry notice, send lapse notice

## Related docs

- `examples/subscription-renewal/02-glossary.md`
- `examples/subscription-renewal/04-workflows-and-state.md`
- `examples/subscription-renewal/11-context-contracts.md`
- `context/patterns/01-boundary-and-decomposition-patterns.md`
- `context/playbooks/10-cross-context-contract-and-anti-corruption-playbook.md`
- `context/principles/03-bounded-contexts-and-boundaries.md`
- `context/principles/10-serialization-persistence-and-data-ownership.md`
