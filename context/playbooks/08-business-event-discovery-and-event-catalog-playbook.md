# Business Event Discovery and Event Catalog Playbook

## Summary

- Use business events to discover what the domain notices, not just what the software does.
- Prefer past-tense event names because they describe facts, not commands.
- Distinguish business events from commands, workflow steps, and purely technical notifications.
- Turn the result into a compact event catalog that links to workflows, bounded contexts, and contracts.

## Use this when

- starting a new domain model from interviews or narratives
- extracting event language from an existing process
- clarifying cross-context handoffs
- creating or reviewing an event catalog

## Inputs

- domain narrative, interview notes, or use cases
- candidate glossary terms
- known workflows or state changes
- neighboring contexts or external systems

## Steps

### 1. Set the scope and timeline

Choose the slice of reality you are examining.

Ask:
- which business capability are we modeling?
- what start and end points matter?
- are we cataloging one bounded context or multiple seams?

### 2. Harvest candidate events from the narrative

Read the domain story and underline facts that can be expressed in past tense.

Look for phrases such as:
- order placed
- renewal initiated
- payment failed
- shipment delivered

If the source language is imperative, rewrite it as a fact first.

### 3. Separate events from non-events

Use this distinction table:

| Kind | Typical shape | Example | Keep in event catalog? |
|---|---|---|---|
| command | imperative request | `renew subscription` | no |
| workflow step | internal action | `check eligibility` | no |
| business event | past-tense fact with domain meaning | `subscription renewed` | yes |
| technical notification | protocol or infrastructure signal | `webhook delivered` | only if it has business meaning in scope |

### 4. Group the events by context and timeline

For each event, note:
- which bounded context emits it
- which workflow or decision produced it
- which downstream contexts or read models care about it

This often reveals hidden seams and missing contracts.

### 5. Look for gaps, disagreements, and overloaded terms

Event discovery is valuable partly because it surfaces uncertainty.

Capture:
- events that people describe differently
- places where a trigger is obvious but the resulting fact is unnamed
- places where one team's output becomes another team's input

### 6. Define the minimum event meaning

For each event, record only what readers need to know first:
- event name
- plain-language meaning
- emitting context
- trigger or precondition
- likely consumers
- contract or translation note, if relevant

### 7. Build the event catalog

Use a compact table.

Recommended shape:

| Event | Meaning | Emitting context | Trigger | Consumers | Contract notes |
|---|---|---|---|---|---|
| subscription renewed | renewal completed successfully | Subscription Lifecycle | successful billing outcome | Notifications, reporting | canonical success outcome |

### 8. Link the catalog back to workflows and contracts

An event catalog is not a standalone model.
For each important event, link or point to:
- the workflow that emits it
- the bounded context that owns it
- the contract or translation seam that carries it
- the read model or downstream process that consumes it

## Output checklist

- [ ] event names are written as facts, not commands
- [ ] emitting context is explicit for each important event
- [ ] business events are distinct from technical notifications
- [ ] consumers or downstream readers are identified where relevant
- [ ] open questions or disputed events are recorded instead of hidden

## Review questions

- Are these events truly domain-significant or just implementation traces?
- Does each event belong clearly to one emitting context?
- Which commands or workflow steps are being mistaken for events?
- Did the catalog expose any missing contracts or translations?
- If an event disappeared, would the workflow or reporting story become unclear?

## Related docs

- `context/playbooks/01-domain-modeling-playbook.md`
- `context/principles/03-bounded-contexts-and-boundaries.md`
- `context/principles/04-workflows-invariants-and-state.md`
- `context/patterns/01-boundary-and-decomposition-patterns.md`
- `templates/event-catalog-template.md`
- `examples/subscription-renewal/10-event-catalog.md`
