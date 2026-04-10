# agent-context-tenets

> Working title for a reusable, language-agnostic AI agent context framework.

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
   - domain events and edge-bound persistence

3. **John Ousterhout — _A Philosophy of Software Design_**
   - strategic programming
   - deep modules
   - information hiding
   - error prevention over error handling
   - comments/ADRs as design tools

## Repository stance

### Canonical content

The canonical layer should be mostly:

- prose principles
- checklists
- decision records
- manifests and schemas
- maps and glossaries

### Examples policy

Current recommended default:

- **no large codebases inside the core framework**
- **small pseudocode snippets** when behavior matters more than syntax
- **optional polyglot micro-examples** only in isolated example folders

That keeps the framework language agnostic while still showing trade-offs between languages when useful.

## Repository map

- `docs/repository-plan.md` — implementation roadmap
- `docs/research/source-synthesis.md` — distilled design inputs
- `docs/research/context-window-strategy.md` — large-repo operating model for agents
- `docs/adr/0001-example-strategy.md` — decision on code vs pseudocode vs polyglot examples
- `context/00-map.md` — how an agent should navigate the future context corpus
- `context/manifests/project-manifest.yaml` — machine-readable load map
- `.pi/todos/` — implementation backlog for the repo itself

## Success criteria for v0

A good v0 should let an agent:

1. understand the framework without loading the whole repo
2. find the right context by topic and task
3. reason about domains, boundaries, and workflows in a language-neutral way
4. apply the framework to a new project with minimal adaptation
5. evolve over time through ADRs, manifests, and small focused documents

## Current status

The repository has been bootstrapped with:

- git initialization
- planning documents
- research notes
- a context navigation skeleton
- `/todos`-based implementation backlog stored in-repo

If you want, the next step can be to start authoring the first canonical context packs and templates.
