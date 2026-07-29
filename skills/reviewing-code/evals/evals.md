# Reviewing Code Evaluations

These scenarios are a test plan. They are not an executable harness.

## Trigger routing

| Prompt | Expected |
| --- | --- |
| “Review PR #42 for merge readiness.” | Trigger initial review. |
| “Rereview the complete branch after the fixes.” | Trigger rereview. |
| “Show me what changed in PR #42.” | Do not trigger. |
| “Fix the review comments in Hunk.” | Do not trigger. |
| “Run the tests and make a draft PR.” | Do not trigger. |

## Behavioral scenarios

### Comment-only change

Review the changed statement for accuracy and consistency. Do not load irrelevant security, concurrency, or deployment concerns and do not manufacture optional improvements.

### Architectural pass misses a C++ bug

Fixture: a structurally appropriate, small C++ change introduces a lifetime or boundary defect not obvious during orientation.

Assertions:

- orientation does not terminate the review;
- behavior and safety traces the affected path and callers;
- the credible failure is surfaced as a material current-change finding;
- lack of a runnable reproduction does not suppress the finding when the trace is sufficient.

### Preference-only alternative

Fixture: the implementation differs from the reviewer's preference but is correct, locally conventional, and maintainable.

Assertions:

- the alternative is omitted from findings and follow-up candidates;
- no comment is produced merely to prove the maintainability pass occurred.

### Tangential issue

Fixture: review reveals a material pre-existing concern not introduced, worsened, or relied upon by the change.

Assertions:

- it does not block the current change;
- it appears only as a follow-up candidate when preserving it is genuinely valuable;
- the reviewer neither requests implementation nor creates an issue.

### Large mechanical change

Chunk the review in dependency order without using a fixed line threshold, refusing the review, or generating findings to justify the effort.

### Rereview

Review the complete new base-to-head changeset, revalidate earlier findings, inspect for regressions and scope growth, and bind the recommendation to the new head.

### Intent clarified in pull-request discussion

Fixture: the pull-request description states a broad goal, a later author comment establishes a material non-goal, and an existing reviewer requests behavior outside that boundary.

Assertions:

- acquire the description and relevant discussion before deep review;
- treat the authorized clarification as intent context;
- treat the previous review request as an unverified claim rather than a requirement;
- independently assess the complete changeset against the clarified intent; and
- surface a conflict or ambiguity when the source authority is not clear.

### Serial phase focus

Fixture: a behavior-changing pull request has architectural, correctness, and verification implications.

Assertions:

- complete orientation before entering a detailed pass;
- enter applicable architecture, behavior, and maintainability passes in order;
- load and apply each pass's detailed guidance when that pass begins rather than preloading all phase references;
- finish the active lens before moving to the next pass;
- retain a cross-pass candidate for validation by its owning pass; and
- synthesize findings only after all applicable passes complete.

### Connected unchanged code

Fixture: a changed function is locally plausible, but an unchanged caller relies on the previous contract and now mishandles its result.

Assertions:

- inspect the unchanged caller and relevant contract even though they are outside the diff;
- trace the realistic integration consequence;
- surface the issue when it is material and introduced or exposed by the changeset; and
- do not expand into a general audit of unrelated unchanged code.

## Global assertions

- Every behavior-changing review completes orientation and the correctness minimum.
- Every pull-request review acquires available native context needed to establish intent and material prior decisions.
- Applicable analytical passes complete serially, with detailed guidance loaded on entry and no mandatory user pause.
- The diff limits current-change relevance, not access to connected code needed for review.
- Investigation may be broad while final output remains sparse.
- Every finding includes a material consequence and supporting evidence or explicit uncertainty.
- `changes required` has at least one `required` finding.
- A ready candidate has no known material in-scope defect and identifies the exact reviewed head.
- The reviewer does not edit implementation, publish feedback, approve, change PR state, or merge.
