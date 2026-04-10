# Subscription Renewal Persistence and Mapping Boundaries

## Summary

- Each bounded context owns the meaning of its persisted data.
- Domain shapes are not assumed to be identical to storage records or provider payloads.
- Mapping boundaries are explicit so the database or provider does not become the hidden domain model.
- Read-side projections are useful, but they do not collapse the write-side consistency boundaries.

## Ownership sketch

| Context | Owned data meaning | Examples |
|---|---|---|
| Subscription Lifecycle | subscription state, renewal status, grace/lapse meaning | subscription record, pending renewal state |
| Billing | billing attempts and provider outcome translation | attempt record, provider reference, classified outcome |
| Notifications | delivery requests and delivery status | notification request record, channel delivery status |

## Mapping boundaries

### API or request edge → Lifecycle

Map:
- raw request payload
- to parsed request
- to trusted renewal command

### Billing provider → Billing context

Map:
- raw provider response
- to classified billing outcome
- to lifecycle-facing outcome category

### Domain aggregate ↔ persistence record

Map:
- domain state and value objects
- to storage fields or documents
- back into trusted aggregate form when read

## Write-side and read-side notes

| Concern | Preferred shape |
|---|---|
| write-side renewal decisions | Lifecycle aggregate and workflow state |
| billing execution history | Billing-owned attempt records |
| support or reporting timeline | read-side projection built from lifecycle and billing events |
| notification delivery audit | Notifications-owned read or reporting view |

## Projection notes

A flattened renewal timeline across Lifecycle and Billing can be useful for support, reporting, or analytics.
Treat it as a read-side projection that consumes stable events or copied data, not as permission for a shared mutable write model.

Useful projection examples:
- customer support renewal timeline
- retry and lapse reporting dashboard
- business intelligence renewal funnel

## Read/write caution

A reporting view might want a flattened renewal history across Lifecycle and Billing.
That is useful, but it should be treated as a read-side convenience, not as authority over lifecycle or billing state.

## Related docs

- `examples/subscription-renewal/06-trusted-and-untrusted-representations.md`
- `examples/subscription-renewal/10-event-catalog.md`
- `examples/subscription-renewal/11-context-contracts.md`
- `context/playbooks/07-persistence-and-mapping-boundaries-playbook.md`
- `context/principles/10-serialization-persistence-and-data-ownership.md`
