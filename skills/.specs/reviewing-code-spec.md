# Skill Specification: Interactive Code Reviewer

## Intent
Create a highly interactive, methodical code review skill that enforces deep technical validation. The skill acts as a code review buddy, maintaining a user-in-the-loop process to discuss findings before generating a final report.

## Core Requirements
- **Name:** `reviewing-code`
- **Context Acquisition:** 
  - **Identify the Target:** Ask the user for the PR number (if GitHub) or branch name (if local). If a GitHub PR, use `gh pr view <number>` to gather initial description, summary, and past comments. If local, check local git structure or ask the user to confirm the target base branch.
  - **Workspace Setup:** Ensure access to a safe workspace. If using a temporary clone or worktree, set it up. If using the current directory, the agent MUST NOT modify any untracked files in the workspace.
  - **Sync State:** Actively ensure the local environment is fully synced. The agent must make sure that both the local feature branch and the base branch are fetched and up-to-date with the remote repository before beginning the review, ensuring no stale code is reviewed. (Note: This fetch requirement may be skipped if explicitly performing a purely local, offline review).
  - **Pre-flight Checks:** Use `gh pr checks` (if applicable) to verify that GitHub CI checks (especially required ones) are successful or in progress. If failed checks are observed, pause and ask the user if they should proceed with the review or fix the tests first.
  - **Empirical Discovery:** Read architectural/requirement docs, `CONTRIBUTING.md`, and `README.md` to gather overall intent. However, the reviewer MUST NOT rely solely on documentation to understand the architecture. It must perform an empirical exploration of the project structure and sample the actual source code (neighboring files, core domain logic, interfaces) to validate the architectural reality before rendering Phase 0 judgment. Trust the code over the blueprints.
  - Read PR descriptions and existing comments to validate intent and ensure previous feedback is addressed.
  - **Triage & PR Size (The 400-Line Rule):** Assess diff scopes first (e.g., `--name-only`). If the core logic exceeds ~400 lines, issue a warning and provide actionable advice on how to split the PR. Ask the user whether to proceed. If forced to review a massive PR, explicitly protect context by chunking the review (e.g., reviewing core data structures first, supporting files later) and communicate this triage protocol to the user. Explicitly ignore binary files and massive low-value text files (e.g., lockfiles, generated code) before pulling full diffs.
- **State Tracking:**
  - Maintain tracking notes in a visible markdown file in the workspace (e.g., `PR-123-review-notes.md` or `branchname-review-notes.md`).
  - Enforce a structured template for all documented findings. Every recorded issue MUST include: the file path/line numbers, severity tag, local code context, the factual observation, the technical alternative, and the architectural advantage. This ensures the final synthesis has full context without needing to re-read files.
- **Workflow (User-in-the-loop) & Verification:**
- Follow a strict step-by-step procedural checklist structured into logical phases (Macro -> Micro -> Code Health -> Verification).
- The reviewer must copy the explicitly provided inline checklist into the tracking document and check off items *one by one*.
- **Intra-Phase Lockstep:** The reviewer must execute analysis for *only one check at a time*. It must evaluate the code against a single check, update the tracking document, check off the item, and *only then* move to the next check within the same phase.
- **Redundancy & Factoring Check:** Actively look for duplicated code within the same file, existing shared utilities, and similar functionality in neighboring files that could be factored out.  - **Omissions Check (Ghost Code):** Explicitly check for missing implementation details (e.g., unhandled enum variants, missing tests for new features, missing error handling).
  - **Empirical Validation:** If a bug or logic error is suspected, the reviewer must attempt to write a failing unit test or run a local quick script to *prove* the issue, and include this proof in the review.
  - **Batched Interactions & Execution Holds:** Enforce a strict **HOLD STATE** after completing all checks for a *Phase*. To ensure portability across environments (Gemini, Claude, Codex), the reviewer must explicitly halt response generation and await a user reply, rather than relying on specific UI tools.
  - **Strict Scope of Progression:** Any affirmative progression command from the user (e.g., "continue", "next", "looks good") grants permission to execute *ONLY the very next phase*. The reviewer is strictly forbidden from interpreting approval as a mandate to complete the remainder of the review in one shot.
  - If a fundamental blocking flaw is discovered, proactively ask the user if they wish to short-circuit the remaining checks and finalize the review.
- **Output Generation:** 
  - Regroup all findings by File and Line Number for the final output. Do not present the review grouped by the procedural check phases.
  - Draft a high-level summary for the overall PR comment. Highlight major themes, total blockers, and the final recommendation.
  - **Tone & The "You" Rule:** The tone must be professional, dry, and constructive. Explicitly ban the use of the word "You" in critiques (e.g., use "The code" or "Using a Map"). Do not be overly congratulatory or use exclamation points.
  - **Anti-Nitpick Mandate:** Point out severe style/naming/spacing inconsistencies if noticed, but generally defer to automated linters/formatters for standard formatting nits. Do not nitpick formatting in the final output.
  - Present the intended output (both the summary and inline comments) to the user. Each inline comment must explicitly state its file and line location and seamlessly include the factual observation, alternative code/proof, and architectural advantage.
  - Ask the user whether to post the review to GitHub OR save it as a Markdown document. If posting to GitHub, the reviewer MUST post targeted inline comments attached to specific files and lines (e.g., via `gh api`) rather than dumping all findings into a single mega-comment. The overall PR body should only contain the high-level executive summary, and the API payload must explicitly include the `event` status (`APPROVE`, `REQUEST_CHANGES`, or `COMMENT`) to officially apply the recommendation.

## Edge Cases & Gotchas
- **Agent Speed-Running / Batching:** LLMs naturally optimize for task completion and will attempt to execute all review phases in a single turn if given the opportunity.
  - *Mitigation:* The review protocol is strictly split into separate phase files. The reviewer must only read the reference file for the current phase, making it impossible to "batch" analysis for upcoming phases it hasn't seen yet.
  - *Mitigation:* Explicit definitions constraining the scope of user progression commands ("continue" only means "do one more phase").

## Proposed Skill Architecture
1. **`SKILL.md` (The Orchestrator):** 
   - Defines the step-by-step loop (Setup -> Context -> Analysis Steps -> Final Output).
   - Enforces the strict "halt generation" behavior at the end of each phase.
   - Constrains user progression commands to a single phase.
2. **`references/phase-1-macro.md`**, **`references/phase-2-micro.md`**, **`references/phase-3-health.md`**, **`references/phase-4-verification.md`**: 
   - The deep technical inspection criteria (formerly `review-protocol.md`) are split into independent files. The reviewer is instructed to read these files progressively (one per phase) to structurally prevent context batching and token waste.
3. **`references/gh-cli-guide.md`:**
   - Teaches the reviewer exactly how to interact with the GitHub API for targeted scope mapping and executing complex JSON payloads for inline commenting.