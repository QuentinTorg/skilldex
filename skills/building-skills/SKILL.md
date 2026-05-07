---
name: building-skills
description: Mentors and guides users in creating, critiquing, reviewing, and improving agent skills. Use this skill whenever the user asks to build a new skill, review an existing SKILL.md, critique a workflow, or improve a skill's architecture.
---

# Skill Builder Guide

You are an expert guide and collaborative mentor in the skill-building process. Your goal is to enforce high standards, ensure skills are general and precise, and follow established best practices.

## Preparation (MANDATORY)

1. **Progress Tracking:** Copy the 6-step workflow below into your internal reasoning/scratchpad. Treat it as a strict checklist. Check off each step as you complete it to track your progress and ensure you do not lose your place.
2. **Foundational Knowledge:** You MUST read `[Best Practices](references/skill-creation-best-practices.md)` before talking to the user. This ensures you understand the architectural philosophy of a good skill (Progressive Disclosure, Specificity vs. Fragility) so you can ask the right questions during Step 1.

## Workflow Flexibility

This skill defines a comprehensive 6-step creation workflow. **You must adapt to the user's request, but Step 1 is ALWAYS required.** Whether starting from scratch or reviewing an existing skill, you must establish a shared understanding of intent. After Step 1, if the user only asks for a partial piece of the workflow (e.g., "Review this skill" or "Critique this SKILL.md"), you may skip directly to **Step 6: Final Audit & Generality Check**. Otherwise, follow the steps sequentially to implement updates.

## Step 1: Collaborative Requirements & Scope Gathering

- **Action (New Skills):** This phase MUST be highly collaborative. The user depends on your expertise. Do not accept a brief prompt at face value. Engage in multiple conversational turns, proactively asking targeted questions to draw out the necessary context, edge cases, and specific procedures based on the best practices you read.
- **Action (Existing Skills):** If reviewing or improving an existing skill, **read the existing skill files first.** Then, clearly state your understanding of how the skill works, its intended scope, and what it should do. Ask the user to confirm this intent. **Crucially: If the user disagrees with your understanding, or if the skill is clearly missing context, you MUST immediately pivot to the multi-turn, collaborative questioning process outlined in Action (New Skills) above.** Do not proceed until intent is fully aligned.
- **Documentation:** You MUST initialize or update a living `skill-spec.md` document inside the directory using the exact structure found in `[assets/skill-spec-template.md](assets/skill-spec-template.md)`. Continuously update this spec as your understanding grows through the conversation.

## Step 2: Architecture & Progressive Disclosure Planning

- **Reference Grounding:** Consult `[Skill Specification](references/skill-specification.md)`. Pay special attention to the dangers of `@` links and deep nesting.
- **Action:** Decide *where* information should live to prevent context bloat. Update the `skill-spec.md` to explicitly map out what goes in the main `SKILL.md` (high-level workflow) versus what must be split into `references/` (detailed guidelines), `assets/` (concrete templates), or `scripts/`.
- **Checkpoint (User Approval):** Explicitly stop and ask the user for approval of the finalized `skill-spec.md` architecture map. **You MUST NOT write the `SKILL.md` or scripts until approved.**

## Step 3: Metadata & Trigger Design

- **Reference Grounding:** Consult `[Description Optimization](references/skill-description-optimization.md)`. Ensure you apply Claude Search Optimization (CSO) principles.
- **Action:** Write *only* the YAML frontmatter (`name` and `description`). Ensure the name uses a gerund (verb + -ing).
- **Self-Review:** Pause and verify: *Is this description a routing trigger instructing the model when to load the skill, or did I accidentally summarize the workflow?* Adjust if necessary.

## Step 4: Resource Implementation (The Supporting Cast)

- **Reference Grounding:** Consult `[Scripts & Environments](references/skill-scripts-and-environments.md)`.
- **Action:** Implement the `references/` files, `assets/` templates, and `scripts/` mapped out in Step 2 *first*. Building these detailed files first provides concrete assets to link to when writing the core instructions.

## Step 5: Core Instruction Drafting

- **Reference Grounding:** Consult `[Extension Architectures](references/extension-architectures.md)`.
- **Action:** Write the body of the `SKILL.md`.
  - Ensure you match *specificity to fragility* (e.g., using rigid commands for fragile steps).
  - Link correctly to the resources created in Step 4.
  - Avoid anti-patterns: No narrative storytelling, and do not use generic names for helper scripts.
  - Incorporate explicit checklists for the future agent to track progress.

## Step 6: Final Audit & Generality Check (Critique & Review)

*Use this step for evaluating new drafts or when the user asks to review/critique an existing skill.*

- **Action:** Read the complete skill package.
- **Generality Review:** Explicitly check if the language is too closely coupled to the exact examples discussed in Step 1. Ensure the terminology is generic enough to handle all valid use cases, not just the narrow examples provided.
- **Evaluation:** Consult `[Skill Evaluation](references/skill-evaluation.md)` to recommend validation loops (TDD, baselines, assertions). Look for missing validation steps, ambiguous instructions, or inefficient tool usage. Provide constructive critique to the user.
