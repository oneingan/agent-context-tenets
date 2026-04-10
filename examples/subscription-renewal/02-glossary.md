# Subscription Renewal Glossary

## Summary

- These terms are local to the exemplar domain.
- They should be used consistently across the example docs and pseudocode.
- If a term conflicts with another domain, translation should be explicit rather than assumed.

## Terms

| Term | Meaning | Notes |
|---|---|---|
| subscription | A time-bounded entitlement held by a customer. | Core concept of the example. |
| renewal | The act of extending a subscription into a new valid term. | A business action, not a payment API call. |
| renewal window | The period during which renewal is allowed or expected. | Used in eligibility decisions. |
| billing attempt | A payment attempt associated with renewal. | Owned by Billing, not by Subscription Lifecycle. |
| grace period | A limited period after a failed billing outcome during which renewal may still recover. | Distinct from full active status. |
| lapse | The loss of active status because renewal did not complete in time. | Domain-significant outcome. |
| renewal pending payment | A state in which renewal was initiated and is waiting on billing outcome. | Long-running state. |
| billing outcome | The result produced by Billing, such as success or failure. | Must be translated into lifecycle decisions. |
| retry eligibility | Whether another billing attempt may be made. | A business rule, not only a scheduler concern. |
| notification request | A request to communicate an already determined business outcome. | Owned by Notifications. |

## Easily confused terms

- **renewal** vs **billing attempt**
  - renewal is the business process; billing attempt is one edge interaction within it
- **grace period** vs **active**
  - grace period allows limited recovery and should not be treated as normal active status
- **lapse** vs **cancel**
  - lapse happens because renewal did not complete; cancellation is an explicit stop decision and is out of scope here

## Related docs

- `examples/subscription-renewal/01-domain-overview.md`
- `examples/subscription-renewal/03-bounded-contexts.md`
- `context/glossary/01-framework-glossary.md`
