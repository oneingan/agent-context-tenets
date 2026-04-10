# Domain Modeling Playbook

## Summary

- Start with language and business change, not with tables, endpoints, or classes.
- Capture nouns, verbs, events, invariants, and boundaries before examples grow.
- Produce a compact artifact set that other playbooks can refine.
- Use this playbook to discover structure, not to lock every detail too early.

## Use this when

- starting a new exemplar domain
- modeling a new capability
- refactoring a vague or overloaded domain description

## Inputs

- problem statement or product goal
- sample scenarios or use cases
- domain expert language, if available
- known constraints or policies

## Steps

### 1. Set the modeling scope

Write a short scope statement.

Answer:
- what part of reality are we modeling?
- what is intentionally out of scope?
- what decision or workflow pressure makes this worth modeling now?

### 2. Harvest the language

Collect the important nouns, verbs, and events used by domain experts or source materials.

Look for:
- core nouns
- business verbs
- state words
- overloaded or disputed terms

### 3. Capture business events and outcomes

List the events that matter to the business.

Examples:
- order placed
- claim approved
- renewal failed

These help reveal workflows and state transitions.

### 4. Identify candidate concepts

Group what you found into:
- core concepts
- supporting concepts
- external actors or systems
- obvious edge concerns

### 5. Note invariants and forbidden situations

Write what must always be true and what must never happen.

Examples:
- confirmed bookings cannot be confirmed twice
- rejected applications do not become approved without re-entry

### 6. Sketch workflows

For each important verb or event, note:
- trigger
- inputs
- outputs
- major decisions
- state changes
- edge interactions

### 7. Propose bounded contexts

Ask where language meaning changes, where rules diverge, and where change pressure differs.

Start small. Split only when the seam protects meaning.

### 8. Produce the minimum artifact set

Create or update:
- glossary entries
- a context overview
- workflow notes
- invariant list
- boundary assumptions

## Minimum outputs

- scope statement
- term list or glossary seed
- event list
- workflow inventory
- invariant list
- candidate bounded contexts

## Lightweight artifact shape

```text
Domain: Subscription Renewal
Key terms: subscription, renewal window, billing attempt, lapse
Key events: renewal requested, renewal paid, renewal failed, subscription lapsed
Invariants: active subscriptions have a valid time window; lapsed subscriptions are not billable as active
Candidate contexts: Subscription Lifecycle, Billing, Notifications
```

## Review questions

- Did we start from business meaning instead of technical structure?
- Are the important verbs and events visible?
- Are invariants explicit enough to guide later playbooks?
- Are candidate contexts based on meaning and change pressure?

## Related docs

- `context/principles/02-ubiquitous-language-and-naming.md`
- `context/principles/03-bounded-contexts-and-boundaries.md`
- `context/principles/04-workflows-invariants-and-state.md`
