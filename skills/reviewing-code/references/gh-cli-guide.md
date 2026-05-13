# GitHub CLI (gh) Reference Guide for Code Review

This guide outlines the specific commands and payload structures required to interact with GitHub Pull Requests during a code review, ensuring context efficiency and proper inline commenting.

## 1. Gathering Context Safely

Do not use `gh pr view` or `gh pr diff` blindly without understanding the scope, as massive diffs will blow out your context window.

**Step 1: Assess the Scope**
Use the `--name-only` flag to get a list of changed files first.
```bash
gh pr diff <pr_number> --name-only
```
Review this list and explicitly ignore massive generated files, lockfiles (`Cargo.lock`, `package-lock.json`), or binary assets.

**Step 2: Fetch Targeted Diffs**
If the PR is small, you can fetch the full diff. If it is large, fetch diffs for specific files of interest.
*(Note: `gh pr diff` doesn't natively support filtering by path easily without piping, so you may need to use standard git commands like `git diff <base>...<head> -- <path>` if working locally).*

## 2. Submitting the Review (Inline Comments)

**Context-Aware Stripping (CRITICAL):**
When converting your drafted review into a GitHub payload, you MUST actively strip redundant headers from the `body` field. 
- Remove the "Recommendation", "Overall Summary", and "Total [BLOCKER] issues" lines. 
- The GitHub UI naturally conveys this state (e.g., via the green "Approved" badge driven by the `event` parameter). 
- Only include the actual descriptive prose in the main body.

The standard `gh pr review` command does **not** support posting targeted inline comments. You must use `gh api` to construct and submit a raw JSON payload to the GitHub REST API.

**The Endpoint:**
`POST /repos/{owner}/{repo}/pulls/{pull_number}/reviews`

*Note on Repository Hostnames (GitHub Enterprise):*
While many repositories are on public `github.com`, some organizations use self-hosted GitHub Enterprise instances. If you encounter connectivity, "not found", or authentication errors when using the `gh` CLI:
1. Verify the repository's hostname by running `git remote -v` or `gh repo view --json url`.
2. If necessary, direct the `gh api` command to the specific enterprise host using the `--hostname <enterprise-url>` flag (e.g., `gh api --hostname git.internal.company.com repos/...`).

**The Payload Structure (`payload.json`):**
You must construct a JSON file with the following strict structure:

```json
{
  "body": "This is the overall executive summary of the review. It uses a collaborative tone.",
  "event": "APPROVE", 
  "comments": [
    {
      "path": "src/main.rs",
      "line": 42,
      "body": "### [BLOCKER] Data Race\n**Observation:** ...\n**Alternative:** ...\n**Advantage:** ..."
    },
    {
      "path": "config/settings.yaml",
      "line": 12,
      "body": "### [SUGGESTION] Typo\n**Observation:** ...\n**Alternative:** ...\n**Advantage:** ..."
    }
  ]
}
```

*Important Constraints for the Payload:*
- `event`: MUST be exactly one of: `APPROVE`, `REQUEST_CHANGES`, or `COMMENT`.
- `body`: The overall executive PR summary. **Context Stripping Required:** Do NOT include redundant headers like "Overall Summary", "Recommendation: Approve", or "Total BLOCKER issues: 0" in this body text. The `event` parameter already dictates the visual state in the GitHub UI. Only include the actual descriptive prose.
- `comments.path`: The relative file path from the root of the repository.
- `comments.line`: The specific line number in the modified file.
- `comments.body`: The human-readable, formatted inline comment.

**Execution:**
Once the `payload.json` file is created locally, execute the API call:

```bash
gh api repos/{owner}/{repo}/pulls/{pull_number}/reviews --input payload.json
```
After successfully submitting, clean up the temporary `payload.json` file.
