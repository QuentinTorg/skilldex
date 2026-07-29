# Skill Specification: reviewing-code

## 1. Background & Intent

- **Goal:** Perform an independent, evidence-backed review of a pull request, branch, commit range, diff, or working-tree changeset and determine whether it is ready to leave the private review loop.
- **Why revise the skill?** The current skill turns broad review concerns into nineteen mandatory production quotas, writes an audit record for every passed check, pauses after every phase, and treats a line-count heuristic as a user gate. These controls once protected weaker agents from shallow reviews, but now reward chatter, fragment senior-engineering reasoning, and encourage technically defensible yet immaterial comments that block or inflate cohesive changes.
- **Desired disposition:** Preserve serial, independent analytical phases while treating their checks as applicability prompts. Each pass concentrates on one review lens without becoming blind to candidates owned by another pass. The reviewer earns every finding by demonstrating a concrete consequence, keeps unrelated improvements outside the current change, and recommends readiness when no known material in-scope defect remains without demanding perfection.
- **Empirical evidence:**
  - The user reports repeated low-impact suggestions that are technically correct but do not affect the delivered behavior, meaningful maintainability, or merge risk.
  - Fixing agents tend to implement every recorded suggestion, causing review-driven scope growth.
  - Mandatory phase pauses and tracking documents make ordinary reviews chatty and slow.
  - Hunk now supplies a useful local diff and feedback surface that did not exist when the original tracking-file workflow was designed.
  - Minor testing of a separate high-signal draft reduced noise but missed real defects when its high-level focus and restraint narrowed the investigation itself.
  - Agents reviewing a GitHub pull request may inspect its diff without acquiring the description and discussion that establish intent, decisions, and unresolved context unless that expectation is explicit.
  - A blanket prohibition on GitHub approval causes reviewer agents to refuse an explicit publication request, even though the developer may intentionally approve while accepting known findings.

## 2. Trigger Conditions

- **Trigger:** The user explicitly asks for a formal code review, pull-request review, branch review, commit-range review, changeset review, or full rereview after fixes, or explicitly invokes `reviewing-code`.
- **Do not trigger:** Ordinary implementation, author self-verification, diff inspection for status or handoff, feedback resolution, explanation of code without merge-readiness judgment, a narrow debugging question, pull-request creation or finalization, review publication, or merge.
- **Target resolution:** Derive the target and base from reliable repository or pull-request state when possible. Ask only when ambiguity could materially change the reviewed changeset.
- **Role continuity:** A persistent reviewer session preserves discovery and review history, but does not authorize background review. Every initial review and rereview begins with an explicit request.

## 3. Workflow & Procedural Constraints

1. **Bind review identity and context.** Record the exact base and head revisions or equivalent working-tree identity, repository instructions, stated intent, applicable linked requirements, and available verification evidence. For pull requests, acquire the native description, relevant human discussion, existing reviews, and inline threads before deep analysis. Refresh if the changeset moves during review.
2. **Scope before depth.** Map changed files, generated or low-value noise, critical paths, affected neighbors, and likely blast radius before loading detailed criteria. Size changes the inspection strategy but never automatically rejects or pauses a review.
3. **Calibrate rigor.** Determine the software domain, reversibility, public or persistent contracts, safety implications, and uncertainty. A small high-impact change may warrant every phase; a large mechanical or comment-only change may not.
4. **Perform serial independent phases.** Complete orientation first, then perform applicable architecture/integration, behavior/safety, and maintainability/verification passes in that order. Enter one pass at a time, load its detailed guidance when entering it, finish its focused investigation, and record candidates before moving on. There are no mandatory user pauses between passes. A candidate noticed outside the current lens is retained and validated in its owning pass rather than chased immediately or discarded.
5. **Complete the correctness minimum.** Every behavior-changing review traces the changed behavior, affected callers and contracts, important boundaries and failure paths, state or resource lifecycle, and whether verification exercises the relevant contract. Other concerns remain applicability-driven.
6. **Maintain a candidate ledger proportionally.** Ordinary reviews may retain candidates in reviewer context. Hunk may hold location-anchored notes when they can be revised before handoff. Create a temporary head-bound recovery snapshot only when review length, session interruption, or tool loss makes recovery materially valuable. Never require or commit a review-notes document.
7. **Validate and filter candidates.** Before surfacing a finding, verify the code path, realistic trigger, consequence, relation to the current change, and smallest credible resolution direction. Reproduction strengthens a finding but is not mandatory when inspected code and a credible traced failure scenario provide sufficient evidence. Deduplicate repeated patterns. Omit preference-only, theoretical, automated-style, and negligible-impact observations.
8. **Classify meaningful findings.** Each finding records severity, current-change relevance, and resolution risk. Only concrete material in-scope problems justify `changes required`. Tangential or pre-existing concerns remain clearly separated follow-up candidates and never silently become current work.
9. **Synthesize one coherent review.** Produce the reviewed identity, understood intent, concise risk summary, prioritized actionable findings, separately labeled follow-up candidates, evidence and gaps, assumptions, and one recommendation: `changes required`, `developer decision required`, or `ready candidate`.
10. **Rereview completely.** After fixes, re-examine the full current base-to-head changeset, revalidate prior findings, detect regressions and scope growth, and issue a new recommendation bound to the new head.

## 4. Finding Thresholds, Edge Cases & Negative Boundaries

### High-Signal Threshold

A finding earns the author's attention only when it is supported and one or more of the following is true:

- the change can violate its stated intent or an applicable contract;
- it introduces a realistic correctness, safety, security, compatibility, data-loss, deployment, operability, or resource risk;
- it creates meaningful maintainability cost in code introduced or materially reshaped by this change; or
- a developer decision is required because intent or acceptable risk is genuinely ambiguous.

Do not surface a comment merely because another implementation is cleaner, more idiomatic, more generic, more defensive, or theoretically more scalable. Low-impact technically valid suggestions are omitted by default. A valuable concern outside the cohesive change may be a follow-up candidate, but the reviewer does not request its implementation or create an issue.

Noise control applies after investigation, not before it. The reviewer may consider many concerns and retain multiple internal candidates while producing a sparse final review. A passing CI run or existing test suite is evidence, not permission to skip tracing the changed contract.

### Serial Adaptive Phases

- Complete one analytical pass before beginning the next. Load detailed pass guidance on entry rather than reading every phase reference up front and blending the review into one sweep.
- Checks are prompts to consider, not output requirements.
- Record inapplicability only when skipping a major concern would otherwise be surprising.
- Preserve phase independence without cross-phase blinders: candidates may be noticed early, but must be validated coherently before output.
- Treat the high-level orientation pass as hypothesis formation, not a substitute for the later correctness and verification passes.
- Pause only for a decision that blocks responsible progress, such as uncertain target, irreconcilable intent, fundamental scope mismatch, or authorization for costly or state-changing verification.

### Reading Scope

- The changeset defines which consequences can become current-change findings; it does not limit which code the reviewer may inspect.
- Read unchanged callers, consumers, producers, contracts, parallel paths, configuration, and other connected code whenever needed to understand integration or behavior.
- Follow connections far enough to validate the affected contract and realistic consequence without turning the review into an unrelated repository-wide audit.

### Review State and Hunk

- Hunk is the preferred private delivery surface for the developer's agent-authored change, but it is not the source of review judgment or durable intent.
- Use Hunk for candidate note-taking only when notes remain revisable before handoff; do not expose unvalidated speculation as author work.
- If Hunk state may be lost, save a temporary normalized snapshot tied to the reviewed head. The snapshot is recovery state, not a committed audit artifact.
- GitHub and Hunk mechanics belong to adapter skills. The analytical skill produces the same normalized result for either medium.

### Pull-Request Context and Intent

- A pull-request review includes its native context, not only its diff. Read the title and description, linked requirements, relevant human discussion, existing reviews, inline threads, and available verification evidence before deep analysis.
- Human-authoritative clarifications may refine stated intent. Previous reviewer comments remain claims and evidence unless an authorized decision explicitly adopts them.
- Do not inherit another reviewer's conclusion or let existing comments narrow independent investigation.
- When authoritative sources materially conflict or intent remains ambiguous, label the conflict and obtain clarification instead of silently choosing the interpretation that best matches the code.
- Context acquisition is required review reasoning; tool-specific GitHub commands remain outside the analytical skill.

### Authorized Review Publication

- Producing a review recommendation does not mutate GitHub or authorize publication.
- The same reviewer may honor an explicit request to publish the review, including with an approving GitHub event even when its analytical recommendation identifies unresolved findings.
- Publication does not rewrite or suppress the reviewer's technical conclusion; the developer controls the requested GitHub review event.
- Review publication does not authorize merge, auto-merge, pull-request finalization, or any other lifecycle mutation.

### Negative Boundaries

The reviewer never:

- modifies implementation code or resolves its own findings;
- treats every checklist concern as applicable or every observation as publishable;
- blocks on style, taste, speculative hardening, unrelated cleanup, or an idealized rewrite;
- expands the pull-request scope or automatically creates follow-up issues;
- posts Hunk or GitHub feedback without the applicable authorization;
- changes the pull-request description or readiness state except through the separate preparation skill after a successful review and explicit authorization;
- treats CI success as proof of correctness;
- automatically approves or publishes feedback without explicit authorization;
- merges or enables auto-merge on GitHub; or
- uses a fixed line-count threshold as a reason to refuse review.

### Failure Analysis

- **Reported failure:** The review produces many minor comments, and the authoring agent interprets them all as required fixes.
- **Mechanism:** Mandatory checks, mandatory positive/negative logging, suggestion-oriented severity, and phase-by-phase presentation make output volume look like thoroughness and erase the distinction between material defects and optional ideas.
- **Counter-failure:** A quieter, high-level reviewer misses real bugs because it applies the publication threshold while deciding what to investigate and treats architectural orientation as sufficient coverage.
- **Expected behavior:** Deep internal consideration yields sparse external output. The reviewer may inspect many concerns and report none when the change is sound.
- **Generalization:** Review quality requires both recall and precision: broad, phase-independent investigation finds material risk, while strict synthesis accurately prioritizes it without comment noise.

## 5. Architecture & Progressive Disclosure Plan

- **`SKILL.md`:** Trigger boundary; review identity; proportional workflow checklist; serial phase router; candidate filtering; synthesis and rereview contracts; global prohibitions. It does not contain the detailed concern catalog or tool-specific commands.
- **`references/orientation-and-scope.md`:** Domain calibration, pull-request context acquisition, intent reconstruction, exact changeset identity, changed-file mapping, connected-code reading scope, blast radius, and proportional phase selection.
- **`references/architecture-and-integration.md`:** Applicable prompts for architectural placement, interfaces, compatibility, dependencies, cross-component effects, deployment, and reversibility.
- **`references/behavior-and-safety.md`:** Applicable prompts for control and data flow, boundaries, failure paths, concurrency, resources, security, domain invariants, scaling, and operability.
- **`references/maintainability-and-verification.md`:** Applicable prompts for abstraction value, redundancy, clarity, tests, comments, documentation, omissions, dead artifacts, and empirical verification.
- **`references/finding-policy.md`:** High-signal admission test; evidence standard; severity, current-change relevance, and resolution-risk vocabulary; deduplication; follow-up separation; recommendation rules.
- **`assets/review-result-template.md`:** Compact medium-independent result and finding structure. Sections are omitted when empty, and tiny reviews collapse to a verdict plus material evidence.
- **`evals/evals.md`:** Trigger, de-noising, bug-detection, rereview, and boundary scenarios with concrete assertions. It remains a test plan until a shared harness is justified.
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
- **Architectural pass misses a bug:** Continue through behavior/safety, trace the affected path, and surface the material defect even when orientation found no structural concern.
- **Hunk interruption:** Use live Hunk for validated findings and create a head-bound recovery snapshot only when session loss becomes a credible risk.
- **Rereview:** Review the complete new base-to-head diff, not only previously commented lines, and bind the new recommendation to the new head.
- **Intent clarified in discussion:** Acquire the pull-request description and relevant discussion, distinguish an authoritative clarification from prior reviewer opinion, and review against the clarified intent without inheriting earlier conclusions.
- **Serial phase focus:** Complete each applicable pass in order, loading and applying only its detailed guidance while active; carry cross-pass candidates forward without collapsing the passes.
- **Connected unchanged code:** Trace a changed contract into unchanged callers and consumers when necessary to detect a material integration failure; do not treat the diff as the reading boundary.
- **Explicit approval publication:** Honor an explicit request to publish an approving review even when unresolved findings remain; preserve the technical review result and do not infer merge authority.

### Assertions

- The skill triggers only for explicit formal review or rereview requests.
- No phase requires a user pause when review can proceed responsibly.
- No fixed line count blocks review.
- Checks that do not apply produce neither findings nor mandatory audit prose.
- Every behavior-changing review completes the correctness minimum after orientation.
- Every pull-request review acquires available native context needed to establish intent, decisions, prior claims, and material ambiguity before deep analysis.
- Applicable analytical passes execute serially without mandatory user pauses or one blended all-concerns sweep.
- Reviewers inspect unchanged connected code when necessary to determine the changeset's behavior and integration.
- Every surfaced finding states a concrete consequence and evidence or uncertainty.
- Low-impact preference and style suggestions are omitted by default.
- Follow-up candidates are visibly separate and never counted as current-change blockers.
- `changes required` is supported by at least one material in-scope finding.
- `ready candidate` identifies the exact reviewed head and does not mutate GitHub state.
- No committed tracking document is required.
- The reviewer does not edit code, publish feedback or approval automatically or without explicit authorization, or merge.
