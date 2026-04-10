# Repository Plan

## 1. Objective

Create a reusable, language-agnostic agent context framework inspired by `tenets`, but expanded into a documentation-first system for architecture, domain modeling, workflows, review, and knowledge retrieval.

## 2. Design constraints

- agents have limited context windows
- the repo must support progressive loading
- canonical guidance should remain language neutral
- examples must help without dominating the corpus
- the repo should scale to many topics without becoming a giant unreadable handbook

## 3. Recommended content model

The repository should separate content into clear layers:

1. **Maps**
   - tell agents what exists and what to read next
2. **Principles**
   - stable, canonical rules and design tenets
3. **Patterns**
   - reusable structures such as boundaries, workflows, error models, state transitions, integration seams
4. **Playbooks**
   - task-oriented instructions such as modeling a domain, defining a boundary, reviewing a design, or adding an integration
5. **Glossary**
   - ubiquitous language for the framework itself and future exemplar domains
6. **Manifests**
   - machine-readable summaries for retrieval and automation
7. **ADRs**
   - explicit, durable trade-offs
8. **Examples**
   - optional, isolated, non-canonical demonstrations

## 4. Proposed repository shape

```text
agent-context-tenets/
  README.md
  AGENTS.md
  vision.md
  docs/
    repository-plan.md
    research/
      source-synthesis.md
      context-window-strategy.md
    adr/
      0001-example-strategy.md
  context/
    00-map.md
    manifests/
      project-manifest.yaml
    principles/
    patterns/
    playbooks/
    glossary/
    review/
  examples/
  templates/
  tooling/
  .pi/todos/
```

## 5. Content strategy

### Canonical layer

Keep the canonical layer mostly free of language-specific code. Prefer:

- short principle docs
- checklists
- tables
- state diagrams in text form
- schemas/manifests
- pseudocode snippets where needed

### Example layer

Use examples only when they clarify trade-offs that prose alone cannot show.

Recommended order:

1. no code
2. pseudocode
3. tiny polyglot examples in isolated folders

Large framework-specific examples should be a later phase, not part of the core.

## 6. Initial roadmap

### Phase 0 — Bootstrap
- initialize repo
- define vision
- define initial plan
- create backlog
- create navigation skeleton

### Phase 1 — Source synthesis
- distill upstream `tenets`
- extract language-neutral patterns from _Domain Modeling Made Functional_
- extract repository and complexity management patterns from _A Philosophy of Software Design_
- convert all of that into framework principles

### Phase 2 — Information architecture
- define top-level taxonomy
- define document size budgets
- define manifest format
- define load order for agents
- define naming/glossary rules

### Phase 3 — Canonical principles
- author principles for domain language
- author principles for boundaries and modules
- author principles for workflows and state transitions
- author principles for errors, invariants, and integration seams
- author review checklists

### Phase 4 — Playbooks and templates
- domain modeling playbook
- bounded context definition template
- workflow modeling template
- integration review checklist
- ADR template

### Phase 5 — Example corpus
- choose one exemplar domain
- author glossary, boundaries, workflows, invariants
- add pseudocode first
- add optional polyglot micro-examples only where useful

### Phase 6 — Optional tooling
- manifest generator/linter
- doc size checker
- retrieval helper scripts
- optional installers for Claude/Cursor/Copilot/AGENTS flows

## 7. Acceptance criteria for v0

v0 is successful if:

- a new agent can understand the repo by loading fewer than 5 files to start
- each major directory has a clear map or manifest
- core principles are independent of a single programming language
- the first exemplar domain can be navigated without reading everything
- backlog and ADR history make future evolution easy

## 8. Open decisions

### Decision made
- **Default example strategy:** language-neutral docs + pseudocode first + optional polyglot micro-examples

### Still open
- final repository name
- first exemplar domain
- whether to add installation tooling early or late
- whether example snippets should live under `examples/` or next to playbooks

## 9. Backlog link

The actionable implementation backlog for this repo lives in `.pi/todos/`.
