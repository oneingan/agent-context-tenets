# Subscription Renewal Change Scenarios

## Summary

- This example is useful not only for the initial model, but also for thinking through changes.
- The point is to trace changes through language, events, workflows, contracts, and mappings before patching pseudocode.
- Each scenario shows how DMMF-style model evolution can stay explicit.

## Scenario 1: Tier-based retry limits

New requirement:
- premium subscriptions may retry more times than standard subscriptions

Model-first ripple:
1. glossary adds or sharpens `subscription tier`
2. trusted model adds retry policy distinctions
3. lifecycle workflow changes retry eligibility logic
4. `renewal retry scheduled` may need richer policy context for projections
5. persistence may need to store policy or derived retry state

## Scenario 2: Manual renewal approval for enterprise accounts

New requirement:
- some renewals must be approved before billing begins

Model-first ripple:
1. glossary adds `approval pending`
2. lifecycle state model adds a new waiting state
3. workflow pipeline inserts an approval decision step
4. event catalog adds approval-related events
5. a new Approval context or contract may be needed before Billing is involved
6. notification outcomes may now include approval-needed events

## Scenario 3: Billing provider split by geography

New requirement:
- different providers are used in different regions

Model-first ripple:
1. Billing context changes provider routing logic
2. Lifecycle meaning should remain mostly unchanged
3. Billing request contracts may need region or provider-routing inputs
4. provider translation grows inside Billing, not in Lifecycle
5. read-side reporting may want provider-by-region projections, but those stay secondary

## Decision lesson

If a change mostly affects provider detail, the Billing boundary should absorb it.
If a change affects lifecycle meaning, events, or states, the Lifecycle model should change explicitly.
If a change creates a new recurring decision seam, add or sharpen the contract artifact.

## Related docs

- `context/principles/11-evolving-models-through-change.md`
- `context/playbooks/04-adr-writing-playbook.md`
- `templates/change-impact-analysis-template.md`
- `examples/subscription-renewal/04-workflows-and-state.md`
- `examples/subscription-renewal/10-event-catalog.md`
- `examples/subscription-renewal/11-context-contracts.md`
