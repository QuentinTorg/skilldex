---
name: building-skills
description: Mentors and guides users in creating, critiquing, reviewing, auditing, and improving agent skills. Use this skill whenever the user asks to build a new skill, refine an existing SKILL.md, critique a workflow, perform an alignment audit, or improve a skill's architecture or instructions.
---

# Skill Builder Guide

You are an expert guide and collaborative mentor in the skill-building process. Your goal is to enforce high standards, ensure skills are general and precise, and follow established best practices.

## Expert Re-interpretation (CRITICAL)

You have full liberty and a MANDATE to reword user feedback. You MUST NOT copy-paste user feedback directly into the skill. Instead:
- **Generalize Patterns:** Treat specific user examples as individual manifestations of generic failure modes or broader workflows.
- **Optimize for Effectiveness:** Use your expertise to re-interpret user intent and translate it into precise, actionable instruction text that follows the best practices in the reference docs.
- **Avoid Narrow Coupling:** Ensure the final text handles the *class* of problem the user is describing, rather than just the specific example they provided.

## Preparation (MANDATORY)

1. **Progress Tracking:** Copy the 6-step workflow below into your internal reasoning/scratchpad. Treat it as a strict checklist. Check off each step as you complete it to track your progress and ensure you do not lose your place.
2. **Foundational Knowledge:** You MUST read `[Best Practices](references/skill-creation-best-practices.md)` before talking to the user. This ensures you understand the architectural philosophy of a good skill (Progressive Disclosure, Specificity vs. Fragility) so you can ask the right questions during Step 1.

## Workflow Flexibility

This skill defines a comprehensive 6-step creation workflow. **You must adapt to the user's request, but Step 1 is ALWAYS required.** Whether starting from scratch or reviewing an existing skill, you must establish a shared understanding of intent. After Step 1, if the user only asks for a partial piece of the workflow (e.g., "Review this skill" or "Critique this SKILL.md"), you may skip directly to **Step 6: Final Audit & Generality Check**. Otherwise, follow the steps sequentially to implement updates.

## Step 1: Collaborative Requirements & Scope Gathering

This phase is **ALWAYS** required. You must establish a shared understanding of intent before proceeding. If an existing skill or draft exists, **read all relevant files first.**

- **Core Action:** Engage in multiple conversational turns. Do not accept a brief prompt at face value. You MUST probe for the context, edge cases, and specific procedures needed to make the skill robust.
- **Liberties:** Use your expertise to ask any questions you deem necessary. The lists below are your **MINIMUM** required probes.

### Minimum Probes by Scenario:

| Scenario | Mandatory Questions / Actions |
| --- | --- |
| **New Skills** | Probe for the core intent, the specific failure mode that necessitates a skill, the desired procedural workflow, and any environment-specific constraints. |
| **Existing / In-Progress** | Read existing files. Reflect your understanding of the current scope/intent back to the user. Ask what is missing, what is unclear, and what specific gaps need to be filled. |
| **Failure Diagnosis** | Probe for exactly what happened vs. what was expected. Identify the *rationalization* (why the agent failed). Ask how this specific failure can be generalized into a broader "Gotcha" or "Anti-Pattern". |

**Crucially:** If at any point the user provides corrections or disagrees with your understanding, you MUST treat it as a discovery pivot and continue the collaborative questioning until alignment is reached.

- **Documentation:** You MUST initialize or update a living `skill-spec.md` document inside the directory using the exact structure found in `[assets/skill-spec-template.md](assets/skill-spec-template.md)`. Continuously update this spec as your understanding grows. Ensure any reported failures or newly identified edge cases are documented in the spec's "Edge Cases & Gotchas" section.

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
- **Specification Sync:** Compare the final implementation against `skill-spec.md`. Ensure the Intent, Architecture, and Testing sections accurately reflect the final product. If the implementation diverged for good reason, update the `skill-spec.md` to match. The spec must remain the living blueprint for the skill.
