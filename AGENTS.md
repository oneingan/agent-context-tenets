# AGENTS.md

Use this repository with **progressive disclosure**. Do not load the whole repo unless explicitly asked.

## Default load order

1. `README.md`
2. `context/00-map.md`
3. `context/manifests/project-manifest.yaml`
4. the smallest relevant leaf documents for the current task
5. matching ADRs in `docs/adr/`
6. examples only if the canonical docs are insufficient

## Retrieval heuristics

Choose files by:

- **task type**: design, review, modeling, naming, testing, migration
- **scope**: repo-wide, bounded context, pattern, playbook
- **change surface**: principles before examples, examples before experiments

## Hard rules

- Prefer **maps, manifests, summaries, ADRs, and checklists** over long narrative documents.
- Prefer **one bounded context or one capability at a time**.
- Keep documents small enough to be read independently.
- Avoid duplicating the same rule in many places; link instead.
- Treat examples as illustrative, not canonical, unless explicitly marked.

## When authoring new content

- write the summary first
- keep names aligned with the glossary
- hide complexity behind deep, stable modules
- make invalid interpretations hard through templates, schemas, and checklists
- update manifests when adding new directories or concepts

## If context is tight

Read in this order:

1. nearest map/readme
2. glossary entry
3. principle doc
4. playbook/checklist
5. ADR

Then stop and act.
