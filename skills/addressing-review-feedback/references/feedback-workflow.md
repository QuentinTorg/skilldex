# Feedback Workflow & Constraints

This document details the rigid CLI and Git workflow you MUST follow when addressing review feedback.

## 1. Pre-requisite State & Intent Check
**Goal:** Ensure you are operating on the correct branch and understand the PR's goal before modifying any code.
- **Determine PR State:** Use `gh pr view` to see the current PR branch and description.
- **Sync Local State:**
  ```bash
  git status # Check for uncommitted changes. Do NOT lose them.
  git fetch origin
  git checkout <pr-branch>
  git pull origin <pr-branch>
  ```
- **Understand Intent:** Read the PR description and `gh pr diff` to understand the original goal. *You must use this context to assign Impact (Low/Medium/High) later.*

## 2. Extraction & Context Gathering
- **Fetch Feedback:** 
  - `gh pr view --comments` or `gh pr review` to get the raw comments.
  - If the user provides a local markdown file, read that instead.
- **Gather Context:** For each comment, identify the file and line number. Use the appropriate file reading tools to fetch the surrounding code snippet. *Never present a comment to the user without its code context.*

## 3. GitHub Operations (Issues & Replies)
When processing "Defer to Issues" or "Decline", or after committing an "Address Now" item:
- **Create an Issue (Deferred):**
  ```bash
  gh issue create --title "Deferred: <Short Title>" --body "Deferred from PR #<ID>. Original comment: <Comment text>"
  ```
- **Reply to a PR Comment:**
  You must document your actions by replying to the original review thread. Look up the specific comment ID.
  ```bash
  # To reply to a specific review comment thread:
  gh api repos/{owner}/{repo}/pulls/{pull_number}/comments/{comment_id}/replies -f body="Created issue #<IssueID> to address this."
  ```

## 4. Git Negative Boundaries
- **NEVER use destructive git commands:** No `git commit --amend`, no `git rebase`, no `git reset --hard`, no `git push --force`. 
- **Standard Commits Only:** Make your changes, then standard `git add <file>` and `git commit -m "fix: <description>"`.
