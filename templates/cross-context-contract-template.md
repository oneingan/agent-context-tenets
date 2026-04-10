# <Producer or Caller> ↔ <Consumer or Callee> Contract

## Contract summary

| Facet | Value |
|---|---|
| Purpose | <why this interaction exists> |
| Direction | <request / response / event / bidirectional> |
| Relationship model | <shared vocabulary / supplier-owned / consumer-driven / anti-corruption> |
| Contract owner | <who defines the stable shape> |
| Trigger | <what starts the interaction> |

## Shared and translated terms

| Term | Meaning on side A | Meaning on side B | Handling |
|---|---|---|---|
| <term> | <meaning> | <meaning> | <shared / translated / private> |

## Interaction surface

| Name | Meaning | Required fields | Success outcomes | Failure envelope |
|---|---|---|---|---|
| <message or request> | <business meaning> | <minimal field set> | <stable outcomes> | <stable failures> |

## Anti-corruption notes

- where translation happens
- which foreign details stay hidden
- which identifiers or categories are preserved inward

## Ownership and change notes

- data or state owned by each side
- compatibility expectations
- how contract changes should be introduced and reviewed
