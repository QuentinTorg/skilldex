# Skill Specification: preparing-pull-requests

## 1. Background & Intent

- **What is the goal?** Reliably create a structured draft GitHub pull request from an authored changeset, then let the independent reviewer reconcile reviewer-owned context and mark that same pull request ready only after a successful current-head review and explicit human authorization.
- **Why is a skill needed?** A normal request such as “make a PR” does not reliably load an uncommitted template or produce the durable intent, implementation, verification, and limitation context needed by a separate reviewer. The same gap appears at finalization: independent risk and review guidance should enrich the pull request without allowing the reviewer to rewrite human-owned intent. Keeping this behavior in a narrow skill avoids adding the entire development workflow to persistent repository instructions.
- **Empirical Evidence:**
  - The user reported that ordinary author agents may create underspecified pull requests even when their implementation conversation contains the required design intent and verification evidence.
  - The user values the rich risk, impact, testing, and reviewer guidance produced by [No Mistakes](https://github.com/kunchenguid/no-mistakes), but does not want its unbounded controller or automatic lifecycle ownership.
  - Existing Skilldex skills demonstrate the failure mode of broad triggers and bundled responsibilities: unrelated GitHub operations can activate rigid workflows or turn one task into review, fixing, issue creation, commits, and publication.
  - The approved workflow contracts require a two-stage pull-request description: the author creates the durable draft handoff, while the reviewer later enriches derived sections without changing confirmed intent.

## 2. Trigger Conditions (Metadata)

- **When should this trigger?** When the user explicitly asks to create, prepare, update, or open a new draft GitHub pull request for the current changeset; prepare a branch for independent review by creating its pull request; finalize a successfully reviewed pull-request description; or mark a reviewed pull request ready after explicit authorization.
- **When should this NOT trigger?** When the user merely mentions, views, summarizes, explains, checks, or reviews a pull request; asks to inspect CI; asks to post a code review; discusses or resolves feedback; edits implementation code; requests an issue; or asks to merge.
- **Mode selection:** The request must identify either draft creation or authorized finalization. A mention of readiness, a reviewer recommendation, or an existing draft does not itself authorize a GitHub mutation.

## 3. Workflow & Procedures

1. **Determine mode and authority.** Select draft creation or finalization from the explicit request. Refuse merge behavior and clarify ambiguous shared-state mutations.
2. **Establish repository identity.** Inspect repository instructions, current branch, intended base, remotes, existing pull requests, working-tree state, and current head. Never operate from `main` or discard unrelated changes.
3. **Acquire authoritative context.** Reconcile developer-confirmed intent, the complete base-to-head changeset, implementation facts, available verification evidence, submodule or dependent-repository revisions, and existing pull-request content. Label inferred intent rather than silently promoting it.
4. **Select the presentation structure.** Preserve and populate an applicable repository or organization pull-request template. Use the bundled proportional default only when no applicable template exists.
5. **Prepare before mutation.** Draft the proposed title and body locally, identify missing or contradictory information, and verify that the change is cohesive. Stop for human clarification when intent or scope would change.
6. **Execute draft creation.** With explicit draft-creation authority, publish the feature branch as needed and create or update exactly one draft pull request. Report the URL, head identity, and disclosed gaps.
7. **Execute finalization.** Require a ready-candidate review bound to the current head plus explicit human authorization. Preserve the semantics of intent, acceptance criteria, constraints, and non-goals; reconcile implementation, verification, risk, limitations, deferred work, and human-review guidance; then mark the pull request ready.
8. **Verify shared state.** Re-read the pull request after mutation, confirm its state and head, report exact changes, and handle partial failure without blind retries or duplicate pull requests.

## 4. Edge Cases & Negative Boundaries

- **Existing templates:** Repository and organization templates control presentation. Preserve required policy sections and human-authored content instead of replacing the body wholesale.
- **Proportional output:** A trivial documentation or comment change should not receive a large boilerplate body. Omit conditional sections that carry no material information while retaining enough intent and verification context for review.
- **Existing pull request:** Detect an existing pull request for the branch before creation. Update only when the user requested the applicable mode; never create a duplicate to recover from uncertainty.
- **Stale review:** If the head differs from the reviewed head, finalization returns to review and must not mark the pull request ready.
- **Intent conflict:** If delivered code and confirmed intent disagree, stop for the human. The reviewer cannot make the pull request “consistent” by rewriting intent to match the implementation.
- **Missing intent:** Ask for confirmation when intent cannot be recovered reliably. Code and commit messages are evidence, not authority for unstated product decisions.
- **Submodules and coordinated repositories:** Record exact reviewed revisions and relevant linked pull requests. A parent pointer diff is not a substitute for child-repository context.
- **Partial GitHub failure:** Report which mutations succeeded, re-read current state, and retry only the missing idempotent operation.
- **Negative Boundaries:** Never merge, approve, enable automatic merge, bypass checks, push directly to `main`, force-push protected history, resolve review threads, create issues, publish code-review comments, modify implementation code, begin another feature, or treat a previous authorization as permission for a later state change.

### Failure Analysis

- **Reported Failure:** The author can hold the complete design conversation yet produce a generic pull-request body that is insufficient for an independent agent or human reviewer. Conversely, a reviewer that generates all PR content may overwrite or reinterpret the human's intent.
- **Actual vs. Expected:** Without a dedicated transition, generic agent behavior summarizes recent code or commits opportunistically. Expected behavior preserves confirmed intent, distinguishes author facts from reviewer conclusions, respects repository templates, and makes only the requested GitHub state transition.
- **Root Cause/Rationalization:** The information contract is not discoverable from an ordinary “make a PR” request, and broad GitHub workflows conflate artifact preparation with review, fixing, or merge readiness.
- **Generalization:** A mode-aware, explicitly triggered skill can provide consistent handoffs across repositories while keeping intent authority, review judgment, and merge execution separate.

## 5. Architecture & Progressive Disclosure Plan

- **`SKILL.md` (Core Instructions):** Concise mode router, common evidence authority, progressive resource routing, mutation-authorization rule, and non-negotiable scope boundaries. Mode references own lifecycle semantics; GitHub Operations owns repository preflight and shared-state verification. Target well below 500 lines.
- **`references/draft-mode.md`:** Draft-specific context gathering, cohesive-scope check, proportional content rules, existing-PR behavior, and draft handoff requirements. Read only in draft mode.
- **`references/finalization-mode.md`:** Ready-candidate input contract, reviewed-head validation, section authority, intent-conflict handling, reviewer enrichment, and ready transition. Read only in finalization mode.
- **`references/template-policy.md`:** How to discover and preserve repository or organization templates, map required information into existing headings, scale content for trivial through high-risk changes, and preserve human edits.
- **`references/github-operations.md`:** Safe, idempotent Git and GitHub CLI procedures using body files rather than shell interpolation; existing-PR detection; post-mutation verification; partial-failure recovery; GitHub Enterprise considerations.
- **`assets/pull-request-template.md`:** A concise default template with core intent, delivered-change, and verification sections plus clearly conditional risk, limitations, and human-review guidance sections.
- **`scripts/`:** None initially. GitHub CLI operations are environment-sensitive and remain inspectable agent actions. Add a script only if evaluations show repeated unsafe command construction or non-idempotent recovery.
- **Dependency boundary:** The skill consumes a reviewer readiness result during finalization but does not load or reproduce the code-review skill. It does not depend on Hunk.

## 6. Testing & Assertions (Eval-Driven)

- **Trigger Scenario — draft:** “The implementation and tests are done; create a draft PR for this branch.” The description alone should route to this skill and draft mode.
- **Trigger Scenario — finalization:** “I authorize you to finalize PR #42 from your current review and mark it ready.” The description should route to this skill and finalization mode.
- **Near Misses:** “Review PR #42,” “summarize this PR,” “check whether CI is green,” “address these review comments,” and “merge this PR” must not route to this skill.
- **Behavior Scenario — trivial change:** A comment-only diff with no repository template produces a short draft with accurate intent and verification, omitting empty risk boilerplate.
- **Behavior Scenario — normal bug fix:** A C++ regression fix with tests produces a draft that distinguishes confirmed intent, implementation facts, exact verification, known gaps, and preliminary risk.
- **Behavior Scenario — repository template:** A repository template with mandatory policy headings is preserved and populated without replacement or duplicated sections.
- **Behavior Scenario — finalization:** A ready-candidate review for the current head enriches risk, limitations, and human-review guidance while preserving the semantics of developer-owned intent, then marks the pull request ready only after authorization.
- **Pressure Scenario — stale head:** The branch changes after review. Finalization refuses the ready transition and requires rereview.
- **Pressure Scenario — existing PR and partial failure:** The agent detects the existing draft, avoids duplicate creation, re-reads shared state after a simulated failed mutation, and retries only the missing action.

### Assertions

- The skill is selected for both positive trigger prompts and rejected for every listed near miss.
- Draft creation never produces a ready pull request.
- Finalization requires both a ready-candidate result bound to the current head and explicit human authorization.
- Developer-owned intent is not semantically changed during finalization.
- Existing repository-template headings and human-authored content remain present.
- Output contains no claims of tests, review, or risk validation that were not evidenced.
- No operation merges, approves, force-pushes, pushes to `main`, creates an issue, resolves a thread, or publishes review comments.
- Repeated execution does not create a second pull request for the same branch.
- Every successful mutation is followed by a read-back that confirms current head, pull-request state, and resulting body.
