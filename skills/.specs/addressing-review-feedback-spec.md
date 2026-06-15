# Skill Specification: addressing-review-feedback

## 1. Background & Intent
- **What is the goal?** To systematically process code review feedback (from GitHub PRs or local Markdown), evaluate the intent of the PR, categorize comments by action (Address/Defer/Decline), Implementation Risk, and Impact, collaborate with the user on categorization and resolution plans, execute approved changes, create issues for deferred items, and document progress via replies.
- **Why is a skill needed?** Agents often struggle to manage large batches of review feedback cohesively. They may modify code on the wrong branch, fail to understand the PR's original goal (leading to out-of-scope changes), or treat a complex architectural fix with the same low-care approach as a typo. A rigid, multi-dimensional categorization workflow prevents data loss, aligns scope, and allows users to triage fixes by risk and impact.
- **Empirical Evidence:** The user noted past failures where agents would modify the wrong branch, assume approval after discussing one element, or rewrite git history leading to data loss. The user also noted the need to distinguish between low-risk obvious bugs and high-risk design changes.

## 2. Trigger Conditions (Metadata)
- **When should this trigger?** When the user asks the agent to address, process, or handle PR review feedback, review comments, or feedback from a markdown file.
- **When should this NOT trigger?** When the user is asking the agent to *perform* a code review on a PR (trigger `reviewing-code`), or asking a single isolated git question.

## 3. Workflow & Procedures
1. **Pre-requisite State & Intent Check:** 
   - Determine the target branch of the PR. Checkout the branch locally and pull the latest changes from the remote to ensure parity with the PR state. Acknowledge and preserve any existing local uncommitted changes.
   - **Understand PR Intent:** Read the PR description and initial diff to understand the goal of the PR. This is required to properly filter comments for importance and scope.
2. **Extraction & Context Gathering:** Fetch feedback using `gh` CLI or a local Markdown file. Gather surrounding code context for each comment.
3. **Multi-Dimensional Analysis:** For each comment, analyze and assign three tags:
   - **Action Category:** 
     - *Address Now:* Critical issues or small changes that simplify the diff.
     - *Defer to Issues:* Style/cleanup, nice-to-haves, out of PR scope.
     - *Decline/Do Nothing:* Misaligned goals, incorrect feedback, observations.
   - **Implementation Risk:** 
     - *Low:* Obvious mistakes, clear fixes, isolated changes.
     - *Medium:* Moderate changes.
     - *High:* Far-reaching bugs, requires extensive thought or design decisions.
   - **Impact/Importance:** 
     - *Low/Medium/High:* Agent's independent evaluation of how impactful the comment is to the overall functionality and the PR's intent (regardless of reviewer tone).
4. **Presentation & Alignment Loop:** Present the fully categorized list (including Risk and Impact) with code context using `assets/categorization-template.md`. 
5. **Categorization Discussion Loop:** Ask the user if they agree with the list. (e.g., The user might choose to auto-approve all "Low Risk / Address Now" items but require discussion on "High Risk" items). Incorporate adjustments and **re-present the entire updated list**. Do not proceed until explicit final approval of the whole list is granted.
6. **Processing Deferred & Declined Items:** 
   - **Defer to Issues:** Create a GitHub issue (`gh issue create`), then reply to the comment linking the issue.
   - **Decline:** Reply to the comment explaining why it is not being addressed.
7. **Execution & Validation Loop (Address Now):** For each item in "Address Now":
   - **Plan Approval:** Propose the exact resolution plan to the user. Wait for explicit approval before modifying any files (unless the user explicitly pre-approved "Low Risk" items as a batch).
   - **Execution:** Make the approved code changes.
   - **Commit:** Commit the updates securely.
   - **Document:** Reply to the associated review comment documenting the update.
   - **Validation:** Present the change to the user and wait for agreement before moving to the next item.

## 4. Edge Cases & Negative Boundaries
- **Constraints/Gotchas:** 
  - Ensure local uncommitted changes aren't lost when checking out branches or pulling.
  - The PR intent must serve as the primary filter for the "Impact" evaluation.
- **Negative Boundaries:**
  - **NEVER modify the wrong branch.** Always sync with the PR branch first.
  - **NEVER rewrite git history.** Do not use `git commit --amend`, `git rebase`, `git push --force`, etc.
  - **NEVER modify code before scope AND plan are finalized.** Both the categorical list and the individual resolution plans must be explicitly approved.
  - **NEVER move to next steps implicitly.** Do not assume that discussing one item means the whole list is approved.

## 5. Architecture & Progressive Disclosure Plan
- **`SKILL.md` (Core Instructions):** Details the 7-step workflow, trigger constraints, and boundaries.
- **`references/feedback-workflow.md`:** Detailed guidelines on how to use `gh`, state management (checkout/pull), understanding PR intent, creating issues, and PR replies.
- **`assets/categorization-template.md`:** Format for presenting the categorized comment list (including Action, Risk, and Impact) and their context.

## 6. Testing & Assertions (Eval-Driven)
- **Test Scenarios:** Provide a mock PR. Verify the agent evaluates PR intent first, categorizes comments with Risk/Impact, and stops for plan approval before writing code.
- **Assertions:** No code is written before user approves both the category list and the resolution plan.