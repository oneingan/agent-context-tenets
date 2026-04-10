# Subscription Renewal Context Contracts

## Summary

- The example uses explicit contract notes so context seams stay reviewable.
- Billing and Notifications receive only the business meaning they need, while internal detail remains local.
- Contract ownership depends on interaction direction; one seam can be supplier-owned while the return seam is consumer-shaped.
- Anti-corruption translation is used to keep provider and channel detail from colonizing Lifecycle language.

## Contract 1: Subscription Lifecycle → Billing

### Purpose

Request a billing attempt for a renewal that Lifecycle has already decided may proceed.

### Contract summary

| Facet | Value |
|---|---|
| Direction | request into Billing |
| Relationship model | Billing-owned request surface |
| Contract owner | Billing |
| Trigger | `renewal initiated` |
| Stable outcomes | request accepted, request rejected, attempt could not start |

### Shared and translated terms

| Term | Lifecycle meaning | Billing meaning | Handling |
|---|---|---|---|
| subscription identity | the subscription being renewed | correlation reference for the attempt | shared enough |
| renewal term | the term Lifecycle wants to extend into | what the charge is buying | shared enough |
| amount to charge | renewal amount | billing amount | shared enough |
| lifecycle state | renewal_pending_payment, grace_period, active | not needed as Billing vocabulary | private to Lifecycle |

### Anti-corruption note

Billing does not need Lifecycle's full internal state model.
It only needs a stable request surface for starting a charge attempt.

## Contract 2: Billing → Subscription Lifecycle

### Purpose

Report a stable billing outcome that Lifecycle can translate into renewal meaning.

### Contract summary

| Facet | Value |
|---|---|
| Direction | event or callback into Lifecycle |
| Relationship model | Lifecycle-owned inward outcome categories |
| Contract owner | Lifecycle for the inward-facing categories |
| Trigger | Billing classifies a provider outcome |
| Stable outcomes | success, failure, outcome unavailable, invalid or unexpected outcome |

### Outcome envelope

| Outcome category | Meaning to Lifecycle | Translation note |
|---|---|---|
| success | renewal may complete | provider approval detail stays local to Billing |
| failure | renewal did not succeed and Lifecycle must decide retry or lapse | retryability or terminality may require a stable subcategory |
| outcome unavailable | Billing cannot yet provide a final business-usable result | timeouts and provider ambiguity stay collapsed here |
| invalid outcome | the seam contract itself was violated | contract issue, not a business renewal result |

### Anti-corruption note

Provider response codes, webhook quirks, and settlement-specific terms stay inside Billing.
Lifecycle receives only the distinctions that affect renewal meaning.

## Contract 3: Subscription Lifecycle → Notifications

### Purpose

Request communication after Lifecycle has already decided the business outcome.

### Contract summary

| Facet | Value |
|---|---|
| Direction | event or request into Notifications |
| Relationship model | Lifecycle-owned business outcome contract |
| Contract owner | Lifecycle for outcome meaning; Notifications for delivery behavior |
| Trigger | `subscription renewed`, `renewal retry scheduled`, or `subscription lapsed` |
| Stable outcomes | notification requested, delivery accepted, delivery delayed |

### Shared and translated terms

| Term | Lifecycle meaning | Notifications meaning | Handling |
|---|---|---|---|
| renewal outcome | business fact already decided | message-selection input | shared enough |
| customer contact preferences | reference for communication policy | delivery-routing input | translated or copied as needed |
| channel retry policy | not part of lifecycle meaning | delivery responsibility | private to Notifications |

### Anti-corruption note

Notification templates, provider response codes, and channel scheduling should not flow back and reshape Lifecycle states.

## Read-side consumer note

Reporting and support projections may consume lifecycle and billing events from these seams.
Those projections are consumers of stable contracts, not owners of write-side meaning.

## Related docs

- `examples/subscription-renewal/03-bounded-contexts.md`
- `examples/subscription-renewal/10-event-catalog.md`
- `context/playbooks/10-cross-context-contract-and-anti-corruption-playbook.md`
- `context/patterns/01-boundary-and-decomposition-patterns.md`
- `templates/cross-context-contract-template.md`
