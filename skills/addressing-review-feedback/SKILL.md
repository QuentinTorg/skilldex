---
name: addressing-review-feedback
description: Triggers when the user asks to address, process, or handle code review comments or PR feedback. Systematically categorizes comments by action (Address/Defer/Decline), risk, and impact, and securely guides you through implementing and documenting the resolutions.
---

# Addressing Review Feedback

You are an expert software engineer managing code review feedback. Your goal is to systematically process comments, evaluate their impact on the PR's original intent, categorize them, and safely execute approved resolutions without data loss.

You MUST copy the following 7-step checklist into your internal reasoning and check off each step as you complete it. Never skip a step.

## 📋 The 7-Step Feedback Processing Checklist

- [ ] **Step 1: Pre-requisite State & Intent Check** (Ensure correct branch and understand the PR's original intent).
- [ ] **Step 2: Extraction & Context Gathering** (Fetch raw comments and local code snippets).
- [ ] **Step 3: Multi-Dimensional Analysis** (Tag each comment with Action, Risk, and Impact).
- [ ] **Step 4: Presentation Loop** (Present categorized list to user).
- [ ] **Step 5: User Alignment Loop** (Re-present list after adjustments; wait for final approval).
- [ ] **Step 6: Process Deferred/Declined Items** (Create issues, reply to comments).
- [ ] **Step 7: Execution & Validation Loop** (For each "Address Now" item: Plan -> Approve -> Execute -> Commit -> Reply).

---

## Detailed Execution Rules

### 1. Pre-requisite State & Intent Check
Before modifying any files or analyzing comments, you MUST execute the steps defined in `[Feedback Workflow & Constraints](references/feedback-workflow.md)`. You must sync the branch locally and read the PR description to understand the original intent.

### 2 & 3. Extraction, Context, and Analysis
Fetch the comments (via `gh` or file). For each comment, you MUST read the surrounding code to gather context. 
Analyze each comment across three dimensions based on the PR's intent:
- **Action:** Address Now (critical/small), Defer to Issues (out of scope/nice to have), Decline/Do Nothing (misaligned).
- **Implementation Risk:** Low (obvious/isolated), Medium, High (architectural/far-reaching).
- **Impact/Importance:** Low, Medium, High (agent's evaluation of actual impact).

### 4. Presentation
You MUST present the fully analyzed list of comments to the user using the exact formatting defined in `[Categorization Template](assets/categorization-template.md)`. Do not omit the code context or your reasoning.

### 5. Alignment Loop
Ask the user for approval. If the user suggests changes, update your list and **re-present the entire updated list**. You MUST explicitly ask for and receive final approval of the whole list before proceeding. 
*(Violating this rule and moving on after discussing just one item is an explicit anti-pattern).*

### 6. Process Deferred & Declined Items
For "Defer" and "Decline" items, perform the required `gh` operations as defined in `[Feedback Workflow & Constraints](references/feedback-workflow.md)`.

### 7. Execution & Validation Loop
For each item in the "Address Now" category, perform a strict loop:
1. **Plan Approval:** Propose the exact code changes you intend to make. Wait for the user's explicit approval. (Exception: The user may grant batch approval for all "Low Risk" items during Step 5).
2. **Execute:** Modify the code.
3. **Commit:** Commit the changes. **Never rewrite history** (see Git Constraints in `references/feedback-workflow.md`).
4. **Document:** Reply to the review thread on GitHub stating the issue is resolved in the recent commit.
5. **Validate:** Ask the user if the comment was properly addressed before moving to the next item.

---

## 🚫 Negative Boundaries (DO NOT DO THIS)
- **NEVER** modify the wrong branch. Sync first.
- **NEVER** rewrite git history (`--amend`, `rebase`, `--force`).
- **NEVER** write code before the scope (the category list) AND the plan are explicitly approved by the user.