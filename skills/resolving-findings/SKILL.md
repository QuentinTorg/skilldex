---
name: resolving-findings
description: Use when the user explicitly asks the original author to modify the current changeset to resolve selected review findings, comments, or feedback. Do not use merely to view, summarize, discuss, triage, or review feedback; publish or reply to comments; resolve threads; create issues; commit or push; manage pull-request state; or merge.
---

# Resolving Findings

Modify the current changeset only for developer-selected review findings. Revalidate each claim, make bounded intent-preserving corrections, verify their consequences, and return the complete result to the independent reviewer.

## Preserve role separation

The original author normally resolves findings in the session that retains the feature's design intent and repository context. A reviewer must not implement findings it produced. If you are acting as that reviewer, hand the selected findings back to the author instead of switching roles.

Developer selection controls what may change. A visible, open, severe, or technically valid comment is not automatically selected.

## Track the resolution

Use this compact checklist in internal reasoning or temporary scratch state:

- [ ] Bind the current changeset, confirmed intent, instructions, and unrelated local changes.
- [ ] Establish the exact selected-finding set.
- [ ] Revalidate every selected technical claim against current code.
- [ ] Route each finding as routine, judgment required, or scope changing.
- [ ] Implement only authorized cohesive corrections.
- [ ] Verify the reported consequences proportionately.
- [ ] Report every selected finding and return the complete changeset for rereview.

Do not add a mandatory pause between steps. Pause only for a missing selection, a required developer decision, a scope-changing correction, or authority needed for a consequential action.

## Bind selection and context

Read [Finding Intake](references/finding-intake.md). Confirm the repository, feature branch or workspace, intended base, current changeset identity, change intent, repository instructions, and unrelated edits that must remain untouched.

Accept explicit identifiers or a clear bounded rule such as “all current-change findings classified required.” For raw “address all comments” requests, propose the minimal editable set and obtain one developer confirmation before changing code.

Hunk, GitHub, pasted text, and sidecar files are input media only. Do not mutate those systems as a consequence of resolving findings.

## Revalidate and route

Read [Resolution Policy](references/resolution-policy.md). Inspect the current implementation and relevant contracts before accepting a finding's location, assumption, consequence, or suggested direction.

- Proceed autonomously with a selected routine correction.
- Pause for judgment unless the necessary developer decision is already supplied.
- Stop and request redisposition when a correct fix would expand the cohesive change.
- Mark stale, unsupported, conflicting, or inaccessible findings `already resolved`, `disputed`, or `blocked` with evidence instead of forcing an edit.

Effort is not risk. Do not introduce per-item plans or approval loops for mechanically verifiable, intent-preserving fixes.

## Implement cohesively

Make the smallest maintainable correction that resolves the validated consequence and preserves confirmed intent. Related selected findings may share one fix when separate edits would conflict or duplicate work.

Continuously exclude:

- unselected comments and follow-up candidates;
- adjacent cleanup and style preferences;
- speculative improvements;
- newly discovered tangential issues; and
- unrelated author or workspace changes.

Return new observations for developer disposition. Never weaken tests, validation, warnings, or type safety to obtain a passing result.

## Verify and hand off

Read [Verification and Handoff](references/verification-and-handoff.md). Exercise each finding's claimed consequence where practical, broaden checks according to blast radius, and record exact commands, outcomes, and unavailable evidence.

Use [Resolution Result Template](assets/resolution-result-template.md) proportionally. Give every selected finding exactly one status: `resolved`, `already resolved`, `disputed`, or `blocked`. Identify the resulting changeset and request that the same reviewer perform a complete rereview, not merely inspect the latest edits.

Addressing selected findings does not establish review readiness.

## Boundaries

Do not implicitly:

- perform a new broad code review;
- select or implement non-blocking work for the developer;
- publish, reply to, or resolve review comments;
- create or close issues;
- commit, push, rebase, amend, or rewrite history;
- update pull-request descriptions or readiness state;
- approve or merge; or
- declare the changeset independently reviewed.

Separately explicit Git or adapter requests belong to their applicable workflow after resolution; they are not automatic consequences of this skill.
