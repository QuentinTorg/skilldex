# Skill Specification: reviewing-code

## 1. Background & Intent

- **Goal:** Perform an independent, evidence-backed review of a pull request, branch, commit range, diff, or working-tree changeset and determine whether it is ready to leave the private review loop.
- **Why revise the skill?** The current skill turns broad review concerns into nineteen mandatory production quotas, writes an audit record for every passed check, pauses after every phase, and treats a line-count heuristic as a user gate. These controls once protected weaker agents from shallow reviews, but now reward chatter, fragment senior-engineering reasoning, and encourage technically defensible yet immaterial comments that block or inflate cohesive changes.
- **Desired disposition:** Preserve independent analytical phases for substantial reviews while treating their checks as applicability prompts. The reviewer earns every finding by demonstrating a concrete consequence, keeps unrelated improvements outside the current change, and approves net-improving code without demanding perfection.
- **Empirical evidence:**
  - The user reports repeated low-impact suggestions that are technically correct but do not affect the delivered behavior, meaningful maintainability, or merge risk.
  - Fixing agents tend to implement every recorded suggestion, causing review-driven scope growth.
  - Mandatory phase pauses and tracking documents make ordinary reviews chatty and slow.
  - Hunk now supplies a useful local diff and feedback surface that did not exist when the original tracking-file workflow was designed.
  - The untracked `better-reviewing-code` draft demonstrates a promising high-signal disposition, proportional rigor, and net-improvement approval bar; it is reference material, not an implementation to copy wholesale.

## 2. Trigger Conditions

- **Trigger:** The user explicitly asks for a formal code review, pull-request review, branch review, commit-range review, changeset review, or full rereview after fixes, or explicitly invokes `reviewing-code`.
- **Do not trigger:** Ordinary implementation, author self-verification, diff inspection for status or handoff, feedback resolution, explanation of code without merge-readiness judgment, a narrow debugging question, pull-request creation or finalization, review publication, or merge.
- **Target resolution:** Derive the target and base from reliable repository or pull-request state when possible. Ask only when ambiguity could materially change the reviewed changeset.
- **Role continuity:** A persistent reviewer session preserves discovery and review history, but does not authorize background review. Every initial review and rereview begins with an explicit request.

## 3. Workflow & Procedural Constraints

1. **Bind review identity.** Record the exact base and head revisions or equivalent working-tree identity, repository instructions, stated intent, applicable linked requirements, and available verification evidence. Refresh if the changeset moves during review.
2. **Scope before depth.** Map changed files, generated or low-value noise, critical paths, affected neighbors, and likely blast radius before loading detailed criteria. Size changes the inspection strategy but never automatically rejects or pauses a review.
3. **Calibrate rigor.** Determine the software domain, reversibility, public or persistent contracts, safety implications, and uncertainty. A small high-impact change may warrant every phase; a large mechanical or comment-only change may not.
4. **Perform adaptive independent phases.** Use orientation, architecture/integration, behavior/safety, and maintainability/verification as distinct analytical passes when applicable. There are no mandatory user pauses between phases. A candidate discovered in one phase may be carried forward and validated where it belongs.
5. **Maintain a candidate ledger proportionally.** Ordinary reviews may retain candidates in reviewer context. Hunk may hold location-anchored notes when they can be revised before handoff. Create a temporary head-bound recovery snapshot only when review length, session interruption, or tool loss makes recovery materially valuable. Never require or commit a review-notes document.
6. **Validate and filter candidates.** Before surfacing a finding, verify the code path, realistic trigger, consequence, relation to the current change, and smallest credible resolution direction. Deduplicate repeated patterns. Omit preference-only, theoretical, automated-style, and negligible-impact observations.
7. **Classify meaningful findings.** Each finding records severity, current-change relevance, and resolution risk. Only concrete material in-scope problems justify `changes required`. Tangential or pre-existing concerns remain clearly separated follow-up candidates and never silently become current work.
8. **Synthesize one coherent review.** Produce the reviewed identity, understood intent, concise risk summary, prioritized actionable findings, separately labeled follow-up candidates, evidence and gaps, assumptions, and one recommendation: `changes required`, `developer decision required`, or `ready candidate`.
9. **Rereview completely.** After fixes, re-examine the full current base-to-head changeset, revalidate prior findings, detect regressions and scope growth, and issue a new recommendation bound to the new head.

## 4. Finding Thresholds, Edge Cases & Negative Boundaries

### High-Signal Threshold

A finding earns the author's attention only when it is supported and one or more of the following is true:

- the change can violate its stated intent or an applicable contract;
- it introduces a realistic correctness, safety, security, compatibility, data-loss, deployment, operability, or resource risk;
- it creates meaningful maintainability cost in code introduced or materially reshaped by this change; or
- a developer decision is required because intent or acceptable risk is genuinely ambiguous.

Do not surface a comment merely because another implementation is cleaner, more idiomatic, more generic, more defensive, or theoretically more scalable. Low-impact technically valid suggestions are omitted by default. A valuable concern outside the cohesive change may be a follow-up candidate, but the reviewer does not request its implementation or create an issue.

### Adaptive Phases

- Checks are prompts to consider, not output requirements.
- Record inapplicability only when skipping a major concern would otherwise be surprising.
- Preserve phase independence without cross-phase blinders: candidates may be noticed early, but must be validated coherently before output.
- Pause only for a decision that blocks responsible progress, such as uncertain target, irreconcilable intent, fundamental scope mismatch, or authorization for costly or state-changing verification.

### Review State and Hunk

- Hunk is the preferred private delivery surface for the developer's agent-authored change, but it is not the source of review judgment or durable intent.
- Use Hunk for candidate note-taking only when notes remain revisable before handoff; do not expose unvalidated speculation as author work.
- If Hunk state may be lost, save a temporary normalized snapshot tied to the reviewed head. The snapshot is recovery state, not a committed audit artifact.
- GitHub and Hunk mechanics belong to adapter skills. The analytical skill produces the same normalized result for either medium.

### Negative Boundaries

The reviewer never:

- modifies implementation code or resolves its own findings;
- treats every checklist concern as applicable or every observation as publishable;
- blocks on style, taste, speculative hardening, unrelated cleanup, or an idealized rewrite;
- expands the pull-request scope or automatically creates follow-up issues;
- posts Hunk or GitHub feedback without the applicable authorization;
- changes the pull-request description or readiness state except through the separate preparation skill after a successful review and explicit authorization;
- treats CI success as proof of correctness;
- approves or merges on GitHub; or
- uses a fixed line-count threshold as a reason to refuse review.

### Failure Analysis

- **Reported failure:** The review produces many minor comments, and the authoring agent interprets them all as required fixes.
- **Mechanism:** Mandatory checks, mandatory positive/negative logging, suggestion-oriented severity, and phase-by-phase presentation make output volume look like thoroughness and erase the distinction between material defects and optional ideas.
- **Expected behavior:** Deep internal consideration yields sparse external output. The reviewer may inspect many concerns and report none when the change is sound.
- **Generalization:** Review quality is measured by material risk found and accurately prioritized, not by phase count, comment count, or changes induced.

## 5. Architecture & Progressive Disclosure Plan

- **`SKILL.md`:** Trigger boundary; review identity; proportional workflow checklist; adaptive phase router; candidate filtering; synthesis and rereview contracts; global prohibitions. It does not contain the detailed concern catalog or tool-specific commands.
- **`references/orientation-and-scope.md`:** Domain calibration, intent reconstruction, exact changeset identity, scope mapping, affected-neighbor discovery, blast radius, and proportional phase selection.
- **`references/architecture-and-integration.md`:** Applicable prompts for architectural placement, interfaces, compatibility, dependencies, cross-component effects, deployment, and reversibility.
- **`references/behavior-and-safety.md`:** Applicable prompts for control and data flow, boundaries, failure paths, concurrency, resources, security, domain invariants, scaling, and operability.
- **`references/maintainability-and-verification.md`:** Applicable prompts for abstraction value, redundancy, clarity, tests, comments, documentation, omissions, dead artifacts, and empirical verification.
- **`references/finding-policy.md`:** High-signal admission test; evidence standard; severity, current-change relevance, and resolution-risk vocabulary; deduplication; follow-up separation; recommendation rules.
- **`assets/review-result-template.md`:** Compact medium-independent result and finding structure. Sections are omitted when empty, and tiny reviews collapse to a verdict plus material evidence.
- **Removed from analytical core:** `gh-cli-guide.md`, mandatory tracking-file formats, hard phase holds, the nineteen-item checklist, and the 400-line gate. Hunk and GitHub command mechanics remain in adapter skills.
- **Scripts:** None. Repository exploration and verification vary by language and project; repeated mechanical behavior should be added only after real use demonstrates a stable need.

## 6. Testing & Assertions

### Trigger Cases

- “Review PR #42 for merge readiness.” → trigger initial review.
- “Rereview the complete branch after the fixes.” → trigger rereview.
- “Show me what changed in PR #42.” → do not trigger.
- “Fix the review comments in Hunk.” → do not trigger.
- “Run the tests and make a draft PR.” → do not trigger.

### Behavior Cases

- **Comment-only change:** Review accuracy and context briefly; do not load irrelevant security, deployment, or concurrency quotas; produce no synthetic suggestions.
- **Small C++ correctness bug:** Trace the realistic failure, classify the material in-scope finding, and request changes even though the diff is tiny.
- **Large mechanical refactor:** Chunk context intelligently without invoking a line-count gate or manufacturing findings to justify review effort.
- **Tangential issue:** Keep a valuable pre-existing problem separate as a follow-up candidate; do not block or recommend fixing it in the current change.
- **Preference-only alternative:** Omit a technically valid alternative when the submitted implementation is correct, maintainable in context, and does not create material cost.
- **Hunk interruption:** Use live Hunk for validated findings and create a head-bound recovery snapshot only when session loss becomes a credible risk.
- **Rereview:** Review the complete new base-to-head diff, not only previously commented lines, and bind the new recommendation to the new head.

### Assertions

- The skill triggers only for explicit formal review or rereview requests.
- No phase requires a user pause when review can proceed responsibly.
- No fixed line count blocks review.
- Checks that do not apply produce neither findings nor mandatory audit prose.
- Every surfaced finding states a concrete consequence and evidence or uncertainty.
- Low-impact preference and style suggestions are omitted by default.
- Follow-up candidates are visibly separate and never counted as current-change blockers.
- `changes required` is supported by at least one material in-scope finding.
- `ready candidate` identifies the exact reviewed head and does not mutate GitHub state.
- No committed tracking document is required.
- The reviewer does not edit code, publish feedback, approve, or merge.
