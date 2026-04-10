# agent-context-tenets

> Reusable, language-agnostic AI agent context framework for DDD, workflows, patterns, review checklists, and pseudocode-first examples.

## Why this repository exists

This repository is meant to be a personal, reusable alternative to [bardiakhosravi/tenets](https://github.com/bardiakhosravi/tenets): a place to store opinionated context that AI agents can load when designing, reviewing, and evolving software systems.

The goal is broader than the original project:

- **language agnostic first**
- focused on **architecture, domain modeling, workflows, and quality**
- optimized for **agent consumption under limited context windows**
- reusable across **multiple languages, stacks, and project types**

## Main design inputs

This repo is being designed from three main sources:

1. **Upstream inspiration: `tenets`**
   - layered context packs
   - task-specific guidance
   - path-aware loading for agents
   - architecture review mindset

2. **Scott Wlaschin — _Domain Modeling Made Functional_**
   - ubiquitous language
   - bounded contexts
   - explicit invariants and state transitions
   - workflow/pipeline thinking
   - domain events, contracts, and edge-bound persistence

3. **John Ousterhout — _A Philosophy of Software Design_**
   - strategic programming
   - deep modules
   - information hiding
   - error prevention over error handling
   - comments, naming, and ADRs as design tools

## Repository stance

### Canonical content

The canonical layer should be mostly:

- prose principles
- reusable patterns
- glossaries and naming rules
- playbooks and checklists
- decision records
- manifests and schemas
- maps and review artifacts

### Examples policy

Current recommended default:

- **no large codebases inside the core framework**
- **small pseudocode snippets** when behavior matters more than syntax
- **optional polyglot micro-examples** only in isolated example folders

That keeps the framework language agnostic while still showing trade-offs between languages when useful.

## Repository map

### Start here

1. `README.md`
2. `context/00-map.md`
3. `context/manifests/project-manifest.yaml`

### Design and research

- `docs/repository-plan.md` — implementation roadmap
- `docs/research/source-synthesis.md` — distilled design inputs
- `docs/research/context-window-strategy.md` — large-repo operating model for agents
- `docs/research/dmmf-deep-synthesis.md` — deeper DMMF chapter-to-framework mapping, now extended with v0.2.0 targeted reread findings
- `docs/research/aposd-follow-up-notes-for-dmmf-iteration.md` — APOSD notes supporting the DMMF-heavy iterations and v0.2.0 packaging
- `docs/publication-and-maintenance.md` — publication baseline and push checklist
- `docs/adr/0001-example-strategy.md` — code vs pseudocode vs polyglot policy
- `docs/adr/0002-information-architecture-and-manifests.md` — structural decision for maps/manifests/layers
- `docs/adr/0003-first-exemplar-domain-subscription-renewal.md` — rationale for the first worked example
- `docs/adr/0004-lightweight-validation-before-agent-exports.md` — tooling strategy
- `docs/adr/0005-v0-name-and-publication-baseline.md` — v0 naming and publication baseline
- `docs/adr/0006-license-choice.md` — repository license choice
- `docs/adr/0007-defer-second-exemplar-domain.md` — why a second exemplar is deferred for now

### Canonical layers available now

- `context/principles/00-map.md` — canonical design rules, including deeper DMMF-focused docs
- `context/patterns/00-map.md` — reusable solution shapes
- `context/glossary/00-map.md` — vocabulary and naming governance
- `context/playbooks/00-map.md` — task-oriented procedures, including event discovery, failure taxonomy, and cross-context contract guidance
- `context/review/00-map.md` — quality gates and checklists, including event/contract artifact review

### Secondary example area available now

- `examples/00-map.md` — example entrypoint
- `examples/subscription-renewal/00-map.md` — first exemplar domain, now expanded with event catalogs and contract tables

### Reusable templates available now

- `templates/README.md`
- `templates/event-catalog-template.md`
- `templates/trust-boundary-template.md`
- `templates/aggregate-decision-template.md`
- `templates/cross-context-contract-template.md`
- `templates/change-impact-analysis-template.md`

### Lightweight tooling available now

- `tooling/README.md`
- `tooling/run-checks.sh`
- `tooling/validate-manifests.sh`
- `tooling/check-doc-budgets.sh`
- `tooling/tooling-evaluation.md`
- `.github/workflows/validate.yml`

### Operational files

- `context/manifests/project-manifest.yaml` — machine-readable load map
- `context/manifests/principles-manifest.yaml` — principle index
- `context/manifests/patterns-manifest.yaml` — pattern index
- `context/manifests/glossary-manifest.yaml` — glossary index
- `context/manifests/playbooks-manifest.yaml` — playbook index
- `context/manifests/review-manifest.yaml` — review index
- `context/manifests/examples-manifest.yaml` — examples index
- `LICENSE` — MIT license
- `.pi/todos/` — implementation backlog for the repo itself

## Success criteria

A good release should let an agent:

1. understand the framework without loading the whole repo
2. find the right context by topic and task
3. reason about domains, boundaries, events, contracts, workflows, and failures in a language-neutral way
4. apply the framework to a new project with minimal adaptation
5. evolve over time through ADRs, manifests, small focused documents, and explicit examples

## Current status

The repository now includes:

- planning and research documents
- ADRs for example strategy, information architecture, exemplar-domain choice, tooling strategy, publication baseline, and license choice
- canonical principles derived from the source books
- reusable patterns for boundaries, workflows, errors, and example linking
- glossary and naming governance
- playbooks for domain modeling, boundaries, workflows, trusted data, aggregate design, persistence boundaries, business event discovery, failure taxonomy, and cross-context contracts
- review checklists and repo quality gates, including event/contract artifact review
- reusable templates for event catalogs, trust boundaries, aggregate decisions, contracts, and change-impact analysis
- a first exemplar domain: subscription renewal, expanded with event catalogs, contract notes, persistence/projection guidance, and change scenarios
- lightweight validation scripts for manifests and doc budgets
- contribution guidance, CI validation, releases, and `/todos`-based backlog management

## Recommended next steps after v0.2.0

- apply the framework to an external project or context pack and see where the playbooks still feel thin
- add a second exemplar domain only if it teaches genuinely different modeling lessons
- revisit export automation later if manual reuse becomes painful
- add polyglot micro-examples only when a language-specific lesson is worth the extra context
- see `CONTRIBUTING.md` and `docs/publication-and-maintenance.md` for maintenance guidance
