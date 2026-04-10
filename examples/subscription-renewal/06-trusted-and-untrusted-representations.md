# Subscription Renewal Trusted and Untrusted Representations

## Summary

- The example uses explicit trust boundaries so the lifecycle model can rely on narrower internal representations.
- Raw API requests and raw provider outcomes are not treated as trusted domain data.
- Trust is earned through parsing, validation, and classification steps.
- This keeps repeated defensive checks out of the core workflow.

## Renewal request trust flow

| Stage | Meaning | Notes |
|---|---|---|
| raw renewal request payload | external input from UI or API | untrusted shape |
| parsed renewal request | input shape recognized and normalized | still not fully domain-safe |
| renewal command | trusted lifecycle input | safe for core workflow assumptions |

Examples of checks before trust:
- subscription identity exists and is well-formed
- request timestamp is usable
- required fields are present
- the request belongs to an allowed renewal channel

## Billing outcome trust flow

| Stage | Meaning | Notes |
|---|---|---|
| raw provider response | vendor-specific payload | untrusted and edge-owned |
| classified billing outcome | Billing has translated provider detail into a stable category | trusted enough for the Billing context |
| lifecycle-relevant billing outcome | Lifecycle receives only the distinctions it cares about | no gateway code leakage |

Examples of classifications:
- success
- failure with retry still plausible
- failure that should end in lapse
- outcome unavailable / unresolved

## Why this matters here

Without these trust stages, the Subscription Lifecycle context would need to understand raw request shape problems and gateway-specific detail. That would blur the model and increase repeated validation.

## Related docs

- `examples/subscription-renewal/04-workflows-and-state.md`
- `context/playbooks/05-trusted-and-untrusted-representations-playbook.md`
- `context/principles/07-type-shaped-models-and-illegal-states.md`
