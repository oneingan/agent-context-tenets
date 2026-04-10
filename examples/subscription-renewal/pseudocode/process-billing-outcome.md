# Pseudocode — Process Billing Outcome

This is a small illustration of how Billing outcomes are translated into lifecycle meaning.

It is **not** the canonical specification.
Read first:
- `examples/subscription-renewal/04-workflows-and-state.md`
- `examples/subscription-renewal/05-invariants-and-failure-model.md`
- `context/principles/05-errors-and-edge-responsibilities.md`

```text
workflow process_billing_outcome(subscription_id, billing_outcome):
  subscription = load_subscription(subscription_id)

  if subscription.state != renewal_pending_payment and subscription.state != grace_period:
    return classify_as_unexpected("no renewal in progress")

  if billing_outcome == success:
    extend_subscription_term(subscription)
    transition subscription to active
    emit_lifecycle_outcome("subscription renewed")
    return accepted("renewal completed")

  if billing_outcome == failure and retry_is_allowed(subscription):
    transition subscription to grace_period
    schedule_retry_at_edge(subscription.id)
    emit_lifecycle_outcome("renewal retry scheduled")
    return accepted("retry scheduled")

  transition subscription to lapsed
  emit_lifecycle_outcome("subscription lapsed")
  return accepted("subscription lapsed")
```

## Notes

- Billing owns the payment attempt, but Lifecycle owns the meaning of state changes
- retry scheduling is an edge concern triggered by a domain decision
- notification handling should react to lifecycle outcomes, not decide them

## Related docs

- `examples/subscription-renewal/pseudocode/renew-subscription.md`
- `context/playbooks/03-workflow-and-state-modeling-playbook.md`
