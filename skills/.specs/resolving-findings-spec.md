# Skill Specification: resolving-findings

## 1. Background & Intent

- **Goal:** Let the original author safely modify the current changeset to resolve review findings selected for this pull request, then return an evidence-backed handoff to the independent reviewer for a complete rereview.
- **Why a new skill?** The existing feedback skill combines ingestion, exhaustive categorization, repeated approval loops, implementation, commits, GitHub replies, issue creation, and thread processing. That breadth turns review feedback into a second project-management workflow, loses the author's original design context, and encourages agents to implement every technically valid observation regardless of current scope.
- **Desired behavior:** The persistent author revalidates selected findings as technical claims, proceeds autonomously with routine bounded corrections, pauses for judgment or scope changes, verifies the result proportionately, and reports exact status without performing reviewer or GitHub-adapter work.
- **Empirical evidence:**
  - The user reports that the current feedback skill is intrusive and often gets in the way more than it helps.
  - Fixing agents tend to address every documented observation, inflating the pull request beyond its original intent.
  - Per-item plans, simulated diffs, commits, replies, and validation pauses create unnecessary churn for obvious local fixes.
  - The original author retains design intent and repository discovery, making it a better fixer than a fresh third agent.
  - Hunk now provides a private feedback surface, removing the need to use GitHub threads as agent scratch state.
  - The revised review skill already classifies current-change relevance and resolution risk, so the resolver should consume that contract rather than recategorize the review from scratch.

## 2. Trigger Conditions

- **Trigger:** The user explicitly asks an agent to modify code to resolve selected review findings, comments, or feedback, or explicitly invokes `resolving-findings`.
- **Do not trigger:** Merely viewing, summarizing, discussing, triaging, or reviewing feedback; performing the original code review; debugging unrelated code; publishing or replying to review comments; resolving threads; creating issues; committing or pushing without a resolution request; changing pull-request state; or merging.
- **Expected session:** The original author normally invokes the skill in its existing session. A reviewer that produced the findings must not use this skill to implement them.
- **Selection requirement:** Explicit finding identifiers are preferred. A bounded rule such as “resolve all current-change required findings” is also a selection. An unclassified request such as “address all comments” requires one concise proposed disposition and developer confirmation before editing; it does not trigger the old exhaustive categorization workflow.

## 3. Workflow & Procedural Constraints

1. **Bind the target.** Confirm the repository, feature branch, intended base, current revision or working-tree state, change intent, repository instructions, and unrelated local changes that must be preserved. Never switch, sync, or discard state blindly.
2. **Acquire the selected set.** Consume stable finding identifiers and their observation, consequence, evidence, current-change relevance, resolution risk, and developer decisions. Adapter metadata may point to Hunk, GitHub, or a sidecar, but transport does not change authorization.
3. **Check authorization.** Only findings selected for this pull request are eligible. Follow-up candidates, no-change dispositions, informational observations, and unresolved developer decisions remain untouched.
4. **Revalidate each claim.** Inspect current code and relevant contracts. Mark a finding `already resolved`, `disputed`, or `blocked` instead of editing when it is stale, unsupported, conflicts with another finding, or cannot be resolved inside the authorized boundary.
5. **Calibrate resolution risk.** A selected `routine` correction may proceed without another plan approval. `Judgment required` pauses unless the developer already supplied the necessary decision. `Scope changing` always returns for redisposition or replanning.
6. **Implement cohesively.** Make the smallest maintainable correction consistent with confirmed intent and repository standards. Related selected findings may share one fix when separate edits would conflict or duplicate work. The finding's suggested direction is evidence, not a command to reproduce a particular patch.
7. **Control scope continuously.** Do not bundle adjacent cleanup, follow-up candidates, speculative improvements, or newly noticed tangential issues. Return those as observations for developer disposition.
8. **Verify the consequence.** Reproduce the defect when practical, demonstrate the corrected behavior, and check nearby failure paths proportionately. Broaden verification when shared interfaces, state, build configuration, or components change. Record exact commands, outcomes, and gaps.
9. **Produce the rereview handoff.** Report the new changeset identity, status of every selected finding, implemented changes, verification evidence, decisions, limitations, and unimplemented observations. Return the complete changeset to the same reviewer; do not mark it reviewed yourself.

## 4. Edge Cases & Negative Boundaries

### Selection and Disposition

- A reviewer classification recommends current-change relevance; the developer controls final disposition.
- “Resolve F1 and F3” selects only those findings even if F2 remains visible in Hunk.
- “Resolve all required findings” selects findings classified current-change `required`, but still does not authorize judgment or scope-changing decisions.
- For raw unclassified comments, propose only the minimal disposition needed to identify the editable set. Do not force the user through a full re-presented matrix or per-comment approval ceremony.
- Selection authorizes investigation and an appropriately bounded fix, not changes to product intent, public behavior, compatibility, architecture, or pull-request scope.

### Revalidation

- Inline locations are anchors to the reviewed changeset and may be stale after edits. Stable finding identity and technical claim matter more than the old line number.
- A valid finding may already be resolved by another selected correction; preserve traceability and mark it accordingly.
- Conflicting findings or incorrect reviewer assumptions return as `disputed` with evidence rather than being implemented mechanically.
- Newly discovered material defects are observations, not implicit additions to the selected set.

### Autonomy

- **Routine:** Local, intent-preserving, and mechanically verifiable; proceed after selection.
- **Judgment required:** Multiple materially different valid solutions or effects on interfaces, architecture, compatibility, deployment, or user-visible behavior; obtain a developer decision unless already supplied.
- **Scope changing:** Cannot remain within the cohesive change; stop and request redisposition.
- Effort does not determine risk. A large mechanical update may be routine, while a one-line contract change may require judgment.

### Negative Boundaries

The resolver never implicitly:

- implements unselected findings or follow-up candidates;
- performs a broad second code review;
- weakens tests, warnings, validation, or type safety to make checks pass;
- rewrites unrelated author or workspace changes;
- creates or closes issues;
- replies to, resolves, or publishes review threads;
- commits, pushes, rebases, amends, or force-updates history;
- changes the pull-request description or readiness state;
- approves or merges; or
- skips the independent complete rereview.

Separately explicit requests for reversible Git or adapter actions may be handled by the appropriate workflow after resolution, but they are not consequences of activating this skill.

### Failure Analysis

- **Reported failure:** An agent treats every review comment as current work and expands a focused change into cleanup or redesign.
- **Mechanism:** The old workflow conflates feedback ingestion, disposition, authorization, implementation, external communication, and future-work tracking. Its repeated approval ceremony also makes simple fixes expensive while still encouraging total comment closure.
- **Expected behavior:** Developer selection establishes the editable set. The author fixes routine validated findings with minimal friction, escalates only real decisions, and leaves tangential work untouched.
- **Generalization:** Finding resolution is a bounded implementation operation, not review management or lifecycle orchestration.

## 5. Architecture & Progressive Disclosure Plan

- **`SKILL.md`:** Trigger boundary; author/reviewer separation; target and selection checks; compact resolution checklist; risk routing; scope control; verification and handoff; external-action prohibitions.
- **`references/finding-intake.md`:** Normalized selected-finding inputs, bounded-rule selection, raw-feedback fallback, changeset identity, adapter boundaries, and stale-location handling.
- **`references/resolution-policy.md`:** Revalidation statuses, routine/judgment/scope-changing rules, cohesive implementation, conflict handling, and continuous scope control.
- **`references/verification-and-handoff.md`:** Consequence-based verification, when to broaden checks, exact evidence recording, and complete-rereview handoff requirements.
- **`assets/resolution-result-template.md`:** Compact per-finding status and changeset handoff structure. Empty sections are omitted.
- **`evals/evals.md`:** Trigger near misses, routine autonomy, judgment escalation, stale and conflicting findings, scope pressure, Hunk selection, verification, and external-action boundaries. It remains a test plan until a shared harness is justified.
- **Scripts:** None. Finding sources, build systems, and verification commands vary by repository; Hunk and GitHub commands remain in adapter skills.
- **Migration boundary:** Create `resolving-findings` without modifying or deleting `addressing-review-feedback`. Retire the old skill only after the complete workflow has been exercised and the user explicitly chooses migration timing.

## 6. Testing & Assertions

### Trigger Cases

- “Address selected findings F1 and F3.” → trigger and limit authorization to F1 and F3.
- “Resolve all current-change required findings from this review.” → trigger with bounded-rule selection.
- “Summarize the Hunk comments.” → do not trigger.
- “Do you agree with finding F2?” → do not trigger modification.
- “Rereview the branch after fixes.” → do not trigger; use `reviewing-code`.
- “Reply to these GitHub comments.” → do not trigger.

### Behavior Cases

- **Routine correction:** A selected local correctness finding is current and mechanically verifiable. Proceed without another plan approval, apply the smallest maintainable fix, verify it, and report status.
- **Judgment required:** A selected finding admits incompatible API designs. Stop for the missing developer decision; do not choose based on reviewer preference.
- **Scope changing:** A valid finding requires redesign outside the cohesive PR. Return it for redisposition without editing.
- **Stale finding:** The referenced line moved and the issue is already resolved. Mark it `already resolved`; do not create a compensating edit.
- **Incorrect finding:** Current code disproves the reviewer assumption. Mark it `disputed` with evidence.
- **Conflicting findings:** Two selected directions cannot both hold. Stop and present the conflict rather than applying them sequentially.
- **Visible but unselected Hunk comment:** Leave it untouched and exclude it from implementation.
- **Tangential discovery:** Return the observation without fixing it or creating an issue.
- **Verification gap:** Report an unavailable expensive integration check without claiming success or blocking a routine fix solely to produce ceremony.

### Assertions

- No implementation begins without an explicitly selected set or confirmed bounded rule.
- Routine selected findings do not require another per-item plan approval.
- Judgment-required and scope-changing findings do not proceed without the required developer decision.
- Every selected finding receives a terminal handoff status: `resolved`, `already resolved`, `blocked`, or `disputed`.
- Unselected findings and follow-up candidates remain unchanged.
- The implementation remains within confirmed intent and the cohesive pull-request boundary.
- Verification exercises the finding's claimed consequence where practical and records exact gaps.
- The handoff identifies the complete current changeset for independent rereview.
- The resolver does not publish feedback, create issues, commit, push, change PR state, approve, or merge.
