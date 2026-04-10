# Example Linking Patterns

## Summary

- Examples should teach one lesson at a time and point back to canonical guidance.
- Good example linking reduces duplication and keeps examples secondary.
- These patterns help maintain a healthy relationship between principles, playbooks, patterns, and examples.
- Use them whenever adding or revising illustrative material.

## Load this when

- creating a new example area
- connecting an example to canonical docs
- reviewing whether examples are becoming the hidden specification

## Pattern 1: Canonical First, Example Second

### Use when
An example is being introduced for a concept that already has canonical documentation.

### Shape
- point to the relevant principles or playbooks first
- only then provide the example

### Benefits
- preserves the canonical source of truth
- keeps the example from absorbing too much explanatory load

## Pattern 2: One Example, One Lesson Cluster

### Use when
A domain example could teach many things at once.

### Shape
- keep the example area cohesive
- keep each example file focused on one lesson cluster such as glossary, boundaries, workflows, or pseudocode

### Benefits
- supports selective loading
- reduces example bloat

### Risks
- too much fragmentation can make the example hard to follow end-to-end

## Pattern 3: Pattern-to-Example Bridge

### Use when
A reusable pattern has a concrete illustration in an example.

### Shape
- name the pattern in the pattern doc
- point to the example that shows it
- let the example point back to the pattern and principle docs

### Benefits
- helps agents move from general shape to specific illustration
- reinforces reuse over copy-paste imitation

## Pattern 4: Pseudocode Before Polyglot

### Use when
An example can be taught without committing to a language.

### Shape
- start with structured prose or pseudocode
- add a language-specific micro-example only if the language teaches a unique lesson

### Benefits
- keeps context cost low
- preserves language neutrality longer

### Risks
- pseudocode can become too vague if not tied to concrete decisions and states

## Review prompts

- Could this lesson be understood without the example?
- Does the example clearly point back to the canonical docs?
- Is the example teaching a reusable shape or only a one-off story?
- Would a language-specific version add real value or just more maintenance?

## Related docs

- `context/review/04-example-acceptance-criteria.md`
- `examples/00-map.md`
- `examples/subscription-renewal/00-map.md`
- `docs/adr/0001-example-strategy.md`
