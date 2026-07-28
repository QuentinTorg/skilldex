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

## Global assertions

- Every behavior-changing review completes orientation and the correctness minimum.
- Investigation may be broad while final output remains sparse.
- Every finding includes a material consequence and supporting evidence or explicit uncertainty.
- `changes required` has at least one `required` finding.
- A ready candidate has no known material in-scope defect and identifies the exact reviewed head.
- The reviewer does not edit implementation, publish feedback, approve, change PR state, or merge.
