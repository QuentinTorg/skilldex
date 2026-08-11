# Behavior and Safety

This is the minimum independent correctness pass for every behavior-changing change. Phase 0 may identify the most important paths, but it does not satisfy this pass.

## Trace changed behavior

Follow the relevant path from entry or caller through state transitions and outputs. Verify:

- the intended behavior is actually reachable;
- conditions, ordering, and transformations match the contract;
- affected callers and consumers still use the result correctly;
- empty, boundary, invalid, and partial states behave deliberately; and
- changed behavior is not contradicted by an unchanged parallel path.

Use names and comments as clues, not proof.

## Failure and lifecycle paths

Trace initialization, success, failure, retry, cancellation, shutdown, and cleanup paths that can realistically occur. Look for swallowed errors, invalid state after partial initialization, resource leaks, double cleanup, unsafe retries, and loss of diagnostic context.

Check state and resource ownership across the full lifecycle rather than reviewing each changed function in isolation.

## Boundaries and domain invariants

At applicable trust boundaries, verify authorization, validation, structural integrity, numeric or physical limits, protocol constraints, secret handling, and data integrity before untrusted values influence core behavior.

Apply domain-native invariants: timing and memory for real-time or embedded systems, ownership and ABI rules for C++ libraries, idempotency for infrastructure, lineage and numerical behavior for data systems, or lifecycle and resource budgets for clients.

## Concurrency, scale, and operability

When shared state or asynchronous execution is involved, examine atomicity, synchronization, ordering, cancellation, lifetime, races, and deadlock paths. When volume matters, examine boundedness and the time or memory behavior of changed paths.

Confirm that material failures remain diagnosable without leaking sensitive information. Do not request generic logging or optimization without a concrete operational consequence.

## Evidence

Inspect tests and available verification for the traced contract. Run proportionate repository-approved checks when authorized and useful. Passing CI is evidence, not proof that the affected path and failure cases are covered.

A runnable reproduction is strongest, but not always possible. Inspected code, a violated contract, or a credible traced failure scenario can support a finding when uncertainty is stated precisely. Never modify product code merely to prove a review candidate.
