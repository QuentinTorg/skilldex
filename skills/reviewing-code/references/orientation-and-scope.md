# Orientation and Scope

Use this first pass to establish what is under review, what it intends to accomplish, and where deeper analysis should concentrate. It forms hypotheses; it does not replace later correctness and verification passes.

## Bind the review

- Identify the exact repository, base, and head revisions. For working-tree changes, record the base plus the relevant staged, unstaged, and untracked state.
- Confirm that the target is current enough for the requested review. Do not silently fetch, switch branches, or disturb the author's workspace merely to make it current.
- Read applicable repository instructions, the pull-request description or change brief, and linked requirements that define stated intent.
- Label inferred intent and unresolved ambiguity. Ask only when the uncertainty would materially change the review.

If the target changes during analysis, refresh affected work or restart rather than issuing a stale recommendation.

## Map the change before reading deeply

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

- Read [Architecture and Integration](architecture-and-integration.md) when structure, interfaces, dependencies, persistence, deployment, or cross-component behavior may be affected.
- Read [Behavior and Safety](behavior-and-safety.md) for every behavior-changing change; expand into its domain-specific prompts as applicable.
- Read [Maintainability and Verification](maintainability-and-verification.md) for implementation or test changes and whenever maintainability, completeness, or evidence affects readiness.

Record an omitted major pass only when its inapplicability would not otherwise be obvious.
