# Finalization Mode

## Required inputs

Before any mutation, require all of the following:

- an existing draft pull request;
- an independent ready-candidate review outcome;
- the exact head revision covered by that outcome;
- explicit human authorization for this ready transition.

A review recommendation, green CI, resolved comments, or an existing draft is not authorization. Authorization for an earlier revision or transition does not carry forward.

## Validate freshness

Read the remote pull-request head immediately before finalization and compare it with the reviewed revision. If they differ, stop and require review of the current head. Do not infer that a small or mechanical update is covered.

## Respect section authority

Preserve the semantics of developer-owned content:

- intent and desired outcome;
- acceptance criteria;
- constraints and non-goals;
- product or design decisions confirmed by the human.

The reviewer may correct factual errors and enrich derived content:

- delivered implementation;
- verification evidence;
- risk and impact assessment;
- limitations and deferred work;
- human-review guidance.

If delivered code conflicts with confirmed intent, stop for the human. Never make the description appear coherent by rewriting intent to match the code.

## Finalize

Follow [Template Policy](template-policy.md) and [GitHub Operations](github-operations.md):

1. Reconcile the description with the complete reviewed diff and current evidence.
2. Preserve applicable repository-template sections and meaningful human edits.
3. Follow the ordered update, ready transition, and read-back procedure in GitHub Operations.

Report the final URL, reviewed revision, changed description sections, ready state, residual risks, and the most important areas for the human and team to review.
