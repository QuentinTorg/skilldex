---
name: preparing-pull-requests
description: Use when the user explicitly asks to create, prepare, update, or open a new draft GitHub pull request for an authored changeset, or explicitly authorizes finalizing a successfully reviewed current-head pull request and marking it ready. Do not use for viewing, summarizing, checking, reviewing, fixing, approving, or merging pull requests.
---

# Preparing Pull Requests

Create a durable handoff from authoring to independent review, then support an explicitly authorized transition from reviewed draft to ready pull request. Preserve human-confirmed intent while keeping implementation facts and reviewer conclusions accurate.

## Select exactly one mode

- **Draft mode:** The user explicitly asks to create, prepare, update, or open a new draft pull request for the current changeset. Read [Draft Pull Request Mode](references/draft-mode.md).
- **Finalization mode:** The human explicitly authorizes the current reviewer to finalize a successful current-head review and mark the pull request ready. Read [Finalization Mode](references/finalization-mode.md).

Do not infer a GitHub mutation from discussion, a readiness recommendation, green CI, or the existence of a draft. If the requested mode or authority is ambiguous, clarify before changing shared state.

Developer statements are authoritative for desired intent, acceptance criteria, constraints, and non-goals. The diff and command output are authoritative for what changed and what was verified. Label inferences and gaps; never invent intent, test results, review conclusions, or risk validation.

Treat each shared-state mutation as separately authorized. Previous authorization does not carry forward. The selected mode supplies its lifecycle rules and routes to the template and GitHub-operation references when required.

## Never expand this skill into adjacent work

Do not:

- implement or modify product code;
- perform the independent code review;
- resolve review findings or review threads;
- publish a GitHub code review;
- create follow-up issues;
- approve, merge, enable auto-merge, or bypass repository policy;
- push directly to `main` or force-push protected history;
- begin another feature or automatically advance the workflow.

The human and repository policy retain merge authority.
