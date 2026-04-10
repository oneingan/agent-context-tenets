# Subscription Renewal Event Catalog

## Summary

- The event catalog captures the main facts the subscription-renewal domain notices.
- Event names are written in past tense and linked to the bounded context that emits them.
- Business events stay distinct from commands and purely technical notifications.
- The catalog makes workflow handoffs and read-side projection inputs easier to review.

## Naming note

`renew subscription` is a workflow or command name.
`renewal initiated` is an event name.
Keep those distinct so the catalog stays about facts, not requests.

## Core event catalog

| Event | Meaning | Emitting context | Trigger | Typical consumers | Contract notes |
|---|---|---|---|---|---|
| renewal requested | a renewal request was accepted for evaluation | Subscription Lifecycle intake | user or scheduled trigger reached the renewal path | Lifecycle workflow, audit trail | edge fact; may remain local if not persisted |
| renewal initiated | Lifecycle decided renewal may begin and moved into pending payment | Subscription Lifecycle | eligibility checks passed | Billing, projections | emitted before or alongside billing-attempt request |
| billing attempt requested | Billing received a request to charge for the renewal | Billing entry seam | Lifecycle initiated renewal | Billing workflow, audit trail | request surface is Billing-owned |
| billing succeeded | Billing classified the provider outcome as success | Billing | provider success response | Lifecycle, projections | provider detail stays local to Billing |
| billing failed | Billing classified the provider outcome as a stable failure | Billing | provider decline or retryable failure | Lifecycle, projections | detailed decline reason may stay edge-local |
| billing outcome unavailable | Billing could not yet resolve a stable final outcome | Billing | timeout, unknown provider state, or incomplete callback | Lifecycle, operations | prevents treating operational ambiguity as business success |
| renewal retry scheduled | Lifecycle kept the renewal alive and opened a retry path | Subscription Lifecycle | retry-eligible billing failure | Notifications, retry scheduler, projections | scheduler is edge-owned, decision is Lifecycle-owned |
| subscription renewed | Lifecycle completed the renewal successfully | Subscription Lifecycle | billing success for pending renewal | Notifications, reporting, analytics | canonical success outcome |
| subscription lapsed | Lifecycle ended the renewal path without success | Subscription Lifecycle | grace period expired or failure became terminal | Notifications, reporting, analytics | canonical terminal outcome |
| notification requested | a previously decided business outcome now needs communication | Subscription Lifecycle | lifecycle outcome emitted | Notifications | message content and delivery remain private to Notifications |

## Signals kept outside the core business catalog

| Signal | Why it stays secondary |
|---|---|
| notification delivered | important operationally, but it does not decide renewal meaning |
| provider webhook received | raw edge signal that must be translated before entering the model |
| projection updated | read-side implementation detail rather than domain fact |

## Related docs

- `examples/subscription-renewal/04-workflows-and-state.md`
- `examples/subscription-renewal/11-context-contracts.md`
- `context/playbooks/08-business-event-discovery-and-event-catalog-playbook.md`
- `templates/event-catalog-template.md`
