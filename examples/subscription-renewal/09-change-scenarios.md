# Subscription Renewal Change Scenarios

## Summary

- This example is useful not only for the initial model, but also for thinking through changes.
- The point is to trace changes through language, invariants, workflows, and mappings before patching pseudocode.
- Each scenario shows how DMMF-style model evolution can stay explicit.

## Scenario 1: Tier-based retry limits

New requirement:
- premium subscriptions may retry more times than standard subscriptions

Model-first ripple:
1. glossary adds or sharpens `subscription tier`
2. trusted model adds retry policy distinctions
3. lifecycle workflow changes retry eligibility logic
4. persistence may need to store policy or derived retry state

## Scenario 2: Manual renewal approval for enterprise accounts

New requirement:
- some renewals must be approved before billing begins

Model-first ripple:
1. glossary adds `approval pending`
2. lifecycle state model adds a new waiting state
3. workflow pipeline inserts an approval decision step
4. notification outcomes may now include approval-needed events

## Scenario 3: Billing provider split by geography

New requirement:
- different providers are used in different regions

Model-first ripple:
1. Billing context changes provider routing logic
2. lifecycle meaning should remain mostly unchanged
3. mapping boundaries and provider translation grow in Billing, not in Lifecycle

## Decision lesson

If a change mostly affects provider detail, the Billing boundary should absorb it.
If a change affects lifecycle meaning or states, the Lifecycle model should change explicitly.

## Related docs

- `context/principles/11-evolving-models-through-change.md`
- `context/playbooks/04-adr-writing-playbook.md`
- `examples/subscription-renewal/04-workflows-and-state.md`
