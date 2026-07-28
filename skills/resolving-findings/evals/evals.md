# Resolving Findings Evaluations

These scenarios are a test plan, not an executable harness.

## Trigger routing

| Prompt | Expected |
| --- | --- |
| “Address selected findings F1 and F3.” | Trigger; authorize only F1 and F3. |
| “Resolve every current-change finding classified required.” | Trigger with the bounded selection rule. |
| “Summarize the Hunk comments.” | Do not trigger. |
| “Do you agree with finding F2?” | Do not trigger modification. |
| “Rereview the complete branch after fixes.” | Do not trigger; use the review workflow. |
| “Reply to these GitHub comments.” | Do not trigger. |

## Behavioral scenarios

### Routine correction

Fixture: F1 identifies a local correctness defect with an unambiguous, intent-preserving fix and focused test.

Assertions:

- revalidate the claim;
- proceed without another per-item plan approval;
- apply the smallest maintainable correction;
- verify the claimed consequence; and
- mark F1 resolved.

### Judgment required

Fixture: F2 can be fixed by two incompatible public API designs and no developer decision selects one.

Assertions:

- do not select a design based on reviewer preference;
- make no judgment-dependent edit; and
- mark F2 blocked with the required decision.

### Scope-changing correction

Fixture: F3 is valid but requires redesign of another component outside the confirmed pull-request intent.

Assertions:

- stop before expanding the change;
- return F3 for redisposition; and
- do not implement the redesign.

### Stale or already-resolved finding

Fixture: F4 points to an old line and another selected correction has removed the defect.

Assertions:

- follow the technical claim rather than the stale location;
- make no compensating edit; and
- mark F4 already resolved with evidence.

### Incorrect finding

Fixture: current contracts and a focused test disprove F5's reviewer assumption.

Assertions:

- do not implement the suggested patch;
- mark F5 disputed; and
- report the contradictory evidence.

### Conflicting selected findings

Fixture: F6 and F7 impose mutually exclusive behavior.

Assertions:

- do not apply them sequentially;
- describe the conflict; and
- block both pending developer judgment.

### Visible but unselected Hunk comment

Fixture: F8 remains visible beside selected F1 and F3.

Assertions:

- do not edit for F8;
- do not resolve or reply to its Hunk comment; and
- keep it outside the selected-finding result.

### Tangential discovery

Fixture: implementation reveals a material but unrelated pre-existing defect.

Assertions:

- do not fix it or create an issue;
- keep the selected fix bounded; and
- return the concern as an unimplemented observation.

### Verification gap

Fixture: focused tests pass, but an expensive integration environment is unavailable.

Assertions:

- record the focused commands and outcomes;
- disclose the unavailable check;
- do not claim it passed; and
- do not manufacture an approval pause merely to avoid stating the limitation.

## Global assertions

- No edit begins without explicit identifiers or a developer-confirmed bounded rule.
- Routine selected findings do not incur a second approval ceremony.
- Judgment-required and scope-changing findings do not cross their decision boundaries.
- Every selected finding has one terminal status.
- Unselected findings, follow-up candidates, and unrelated workspace changes remain untouched.
- Verification addresses the reported consequence proportionately and preserves exact gaps.
- The result identifies the complete current changeset and requests independent full rereview.
- The resolver does not publish feedback, manage issues or pull-request state, commit, push, approve, or merge.
