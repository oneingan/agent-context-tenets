# Playbooks Map

This directory contains task-oriented guidance for applying the framework.

## How to use this directory

### If you need to shape a domain model
Read:
1. `context/playbooks/01-domain-modeling-playbook.md`
2. `context/principles/02-ubiquitous-language-and-naming.md`
3. `context/principles/03-bounded-contexts-and-boundaries.md`

### If you need to define a bounded context
Read:
1. `context/playbooks/02-bounded-context-definition-playbook.md`
2. `context/principles/03-bounded-contexts-and-boundaries.md`

### If you need to model workflow behavior or states
Read:
1. `context/playbooks/03-workflow-and-state-modeling-playbook.md`
2. `context/principles/04-workflows-invariants-and-state.md`
3. `context/principles/05-errors-and-edge-responsibilities.md`

### If you need to record a structural decision
Read:
1. `context/playbooks/04-adr-writing-playbook.md`
2. `context/review/01-quality-gates.md`

## Documents

- `01-domain-modeling-playbook.md`
  - step-by-step domain discovery and artifact creation
- `02-bounded-context-definition-playbook.md`
  - how to define a bounded context and its seam contracts
- `03-workflow-and-state-modeling-playbook.md`
  - how to model behavior, states, invariants, and failure modes
- `04-adr-writing-playbook.md`
  - how to capture a meaningful architectural decision

## Directory rules

- explain what to do, not all theory behind why
- assume principles are authoritative and link to them
- prefer compact checklists, tables, and examples over long essays
- update the playbooks manifest when adding or renaming playbooks

## Related docs

- `context/manifests/playbooks-manifest.yaml`
- `context/principles/00-map.md`
- `context/review/00-map.md`
