# Pseudocode — Renew Subscription

This is a small illustration of the `renew subscription` workflow.

It is **not** the canonical specification.
Read first:
- `examples/subscription-renewal/04-workflows-and-state.md`
- `examples/subscription-renewal/10-event-catalog.md`
- `examples/subscription-renewal/11-context-contracts.md`
- `context/principles/04-workflows-invariants-and-state.md`
- `context/principles/05-errors-and-edge-responsibilities.md`

```text
workflow renew_subscription(subscription_id, renewal_request):
  subscription = load_subscription(subscription_id)

  if subscription.state == cancelled:
    return reject("subscription cancelled")

  if not is_within_renewal_window(subscription, renewal_request.requested_at):
    return reject("renewal window closed")

  if subscription.state == renewal_pending_payment:
    return reject("renewal already pending")

  next_term = calculate_next_term(subscription, renewal_request.policy)

  transition subscription to renewal_pending_payment
  record pending renewal attempt for next_term
  emit_event("renewal initiated")

  request_billing_attempt_at_edge(
    subscription_id = subscription.id,
    next_term = next_term,
    amount = renewal_request.amount
  )

  return accepted("renewal initiated")
```

## Notes

- eligibility and state meaning stay in the lifecycle model
- the billing request is an edge action governed by a seam contract
- no gateway-specific detail leaks into the core workflow here

## Related docs

- `examples/subscription-renewal/pseudocode/process-billing-outcome.md`
- `context/playbooks/03-workflow-and-state-modeling-playbook.md`
