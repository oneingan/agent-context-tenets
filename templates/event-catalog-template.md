# <Domain or Context> Event Catalog

## Purpose

- what slice of the domain this catalog covers
- why these events matter
- what is intentionally out of scope

## Naming rules

- prefer past-tense fact names
- keep event names in ubiquitous language
- separate commands from events
- note any disputed or overloaded terms

## Catalog

| Event | Meaning | Emitting context | Trigger | Consumers | Contract notes |
|---|---|---|---|---|---|
| <event name> | <plain-language meaning> | <context> | <what caused it> | <contexts / read models> | <translation / contract note> |

## Commands or non-events to keep separate

| Name | Why it is not in the event catalog |
|---|---|
| <command or technical signal> | <reason> |

## Open questions

- <missing event, disagreement, or unresolved consumer>

## Related artifacts

- workflow docs
- bounded-context docs
- contract notes
- example or pseudocode, if relevant
