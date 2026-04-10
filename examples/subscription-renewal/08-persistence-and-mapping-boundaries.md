# Subscription Renewal Persistence and Mapping Boundaries

## Summary

- Each bounded context owns the meaning of its persisted data.
- Domain shapes are not assumed to be identical to storage records or provider payloads.
- Mapping boundaries are explicit so the database or provider does not become the hidden domain model.
- Read convenience should not collapse the write-side consistency boundaries.

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

## Read/write caution

A reporting view might want a flattened renewal history across Lifecycle and Billing. That can be useful, but it should be treated as a read-side convenience, not as permission for a shared mutable model.

## Related docs

- `examples/subscription-renewal/06-trusted-and-untrusted-representations.md`
- `context/playbooks/07-persistence-and-mapping-boundaries-playbook.md`
- `context/principles/10-serialization-persistence-and-data-ownership.md`
