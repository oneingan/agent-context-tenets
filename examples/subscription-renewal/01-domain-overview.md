# Subscription Renewal Domain Overview

## Summary

- This exemplar focuses on renewing time-bounded subscriptions.
- It is intentionally small, but rich enough to show boundaries, workflows, invariants, and failure handling.
- The example is pseudocode-first and secondary to the canonical framework docs.
- The main business pressure is to renew subscriptions reliably without collapsing domain logic into billing or notification details.

## Use this when

- orienting yourself to the exemplar domain
- deciding whether the example is relevant to a current design task
- looking for a compact multi-context example

## Scope

This example models the decision space around renewing an existing subscription.

It includes:
- renewal eligibility
- renewal initiation
- billing outcome handling
- grace period and lapse behavior
- notification-triggering outcomes

It does not include:
- sign-up and acquisition flows
- detailed pricing models
- invoice generation details
- customer support operations
- full notification content design

## Why this domain was chosen

This domain is useful because it demonstrates:
- a clear ubiquitous language
- multiple bounded contexts with different change pressures
- state transitions with long-running behavior
- domain-significant failures that are distinct from operational failures
- edge responsibilities such as billing and messaging without needing a large codebase

## Business pressure

A business wants to keep subscriptions active when renewal is valid, avoid charging cancelled or lapsed subscriptions incorrectly, and communicate outcomes clearly without letting payment or messaging technology dictate the core model.

## Key events

- renewal requested
- renewal initiated
- billing succeeded
- billing failed
- renewal retry scheduled
- subscription renewed
- subscription lapsed
- notification requested

## Candidate bounded contexts

- **Subscription Lifecycle**
  - owns renewal eligibility, subscription state, grace period, and lapse decisions
- **Billing**
  - owns charge attempts, payment outcomes, and gateway interaction details
- **Notifications**
  - owns audience communication after business outcomes are determined

## Related docs

- `examples/subscription-renewal/02-glossary.md`
- `examples/subscription-renewal/03-bounded-contexts.md`
- `context/playbooks/01-domain-modeling-playbook.md`
