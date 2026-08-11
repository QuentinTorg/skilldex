# Orientation and Scope

Use this first pass to establish what is under review, what it intends to accomplish, and where deeper analysis should concentrate. It forms hypotheses; it does not replace later correctness and verification passes.

## Bind the review

- Identify the exact repository, base, and head revisions. For working-tree changes, record the base plus the relevant staged, unstaged, and untracked state.
- Confirm that the target is current enough for the requested review. Do not silently fetch, switch branches, or disturb the author's workspace merely to make it current.
- Read applicable repository instructions, the pull-request description or change brief, and linked requirements that define stated intent.
- Label inferred intent and unresolved ambiguity. Ask only when the uncertainty would materially change the review.

If the target changes during analysis, refresh affected work or restart rather than issuing a stale recommendation.

## Acquire pull-request context

When the target is a pull request, its native context is part of the review input rather than optional background. Before deep analysis, inspect:

- the title and description;
- linked requirements, issues, or specifications;
- relevant human discussion and clarified decisions;
- existing review summaries and inline threads; and
- available verification or check evidence.

Acquire enough history to identify material decisions, prior claims, and unresolved questions. De-emphasize automated timeline noise, but do not skip the discussion merely because the diff is locally available.

Treat sources according to their authority. Explicit decisions from the author or another authorized stakeholder may clarify intent. Previous review comments are unverified claims or evidence unless an authorized decision adopts them. They must not replace independent investigation or silently narrow its scope.

If authoritative sources conflict materially, label the conflict and ask for clarification rather than selecting whichever interpretation makes the implementation appear correct. Tool-specific retrieval mechanics remain outside this analytical skill.

## Map the change before reading deeply

The changeset limits which consequences belong to the current review; it does not limit what may be read. Inspect unchanged callers, consumers, producers, contracts, base abstractions, parallel paths, configuration, and build wiring when they are needed to understand how the change integrates or behaves. Follow connections far enough to establish the affected contract without turning the review into a general audit of unrelated code.

Inspect the complete changed-file set and distinguish:

- behavior and critical-path logic;
- public or persistent contracts;
- tests and verification infrastructure;
- build, deployment, configuration, and dependency changes;
- generated, vendored, binary, lockfile, or mechanical noise; and
- submodule or coordinated-repository revisions.

Generated and mechanical files may receive less direct attention, but their source change and resulting integration effect still matter. A parent submodule pointer is not a review of the child changeset.

Large changes require a context strategy, not a refusal threshold. Review in dependency order—contracts and data structures, then behavior, then consumers, tests, and operational files—and retain complete changeset coverage.

## Calibrate domain and stakes

Identify the software domain and the concerns native to it. Estimate:

- blast radius and affected users or components;
- reversibility and rollout constraints;
- safety, security, privacy, real-time, or resource implications;
- compatibility obligations; and
- uncertainty caused by missing context or verification.

A small ABI, concurrency, schema, or state-transition change can merit deeper analysis than a large mechanical edit.

## Perform the high-level pass

Assess whether the change solves the stated problem in the right place and whether its overall shape is coherent. Inspect directly affected neighbors, callers, consumers, and existing patterns rather than relying only on documentation or names.

Consider:

- whether the implementation belongs in this layer or component;
- whether new abstractions earn their complexity;
- whether the proposed scope remains cohesive;
- whether dependencies still point in maintainable directions; and
- whether the change appears to solve the actual requirement rather than a narrower proxy.

Carry plausible concerns into the candidate ledger. Do not publish them until the owning pass validates their consequence and current-change relevance.

## Select subsequent depth

After completing orientation, enter each applicable pass in order:

1. Read [Architecture and Integration](architecture-and-integration.md) when structure, interfaces, dependencies, persistence, deployment, or cross-component behavior may be affected. Complete that focused pass before moving on.
2. Read [Behavior and Safety](behavior-and-safety.md) for every behavior-changing change; expand into its domain-specific prompts as applicable, then complete the correctness pass.
3. Read [Maintainability and Verification](maintainability-and-verification.md) for implementation or test changes and whenever maintainability, completeness, or evidence affects readiness. Complete it before final synthesis.

Load a pass's detailed guidance when entering it rather than preloading all phase references. Focus on the active lens. If another kind of concern becomes visible, retain the candidate and validate it during its owning pass instead of chasing it immediately or ignoring it.

Record an omitted major pass only when its inapplicability would not otherwise be obvious. Phase boundaries are internal review discipline, not user approval gates.
