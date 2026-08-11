# Review Result

- **Reviewed changeset:** `<base>..<head>` or equivalent working-tree identity
- **Understood intent:** `<confirmed intent and labeled assumptions>`
- **Recommendation:** `changes required | developer decision required | ready candidate`

## Risk and evidence summary

`<Concise material risk, verification performed, important evidence gaps, and readiness basis.>`

## Current-change findings

### F1 — `<concise title>`

- **Location:** `<file:line or changeset-level>`
- **Classification:** `<severity> | <current-change relevance> | <resolution risk>`
- **Observation:** `<what the inspected code or contract does>`
- **Consequence:** `<realistic affected scenario and material impact>`
- **Evidence:** `<code path, contract, command result, or traced failure; include uncertainty>`
- **Direction:** `<smallest credible resolution direction, not a prescribed rewrite>`

## Follow-up candidates

### F2 — `<concise title>`

- **Location:** `<file:line or changeset-level>`
- **Classification:** `<severity> | follow-up candidate | <resolution risk>`
- **Observation:** `<what the inspected code or contract does>`
- **Consequence:** `<realistic affected scenario and material impact>`
- **Evidence:** `<support and uncertainty>`
- **Why outside this change:** `<scope boundary; do not request implementation>`

## Assumptions and limitations

- `<context or evidence the reviewer could not obtain>`

## Human review focus

- `<areas where domain-owner judgment remains most valuable>`

Omit empty sections. For a tiny or finding-free review, collapse the result to the reviewed identity, recommendation, and short risk/evidence summary.
