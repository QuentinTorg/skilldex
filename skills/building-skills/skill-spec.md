# Skill Specification: building-skills

## Background
Currently, guidelines for building and refining skills in the SkillDex repository reside in `AGENTS.md`. These directives lack sufficient detail and clarity for an agent to act as a highly effective mentor. Critical best practices and agent architecture differences were previously siloed in an external `epiphany_knowledge` database.

## Intent
Create a dedicated `building-skills` skill that acts as an expert guide and collaborative mentor for users creating, critiquing, reviewing, or improving skills in this repository. This skill replaces the directives in `AGENTS.md`. It enforces a rigorous, six-step workflow to ensure skills are general, precise, and adhere to established best practices.

## Flexibility and Triggering
- **Trigger Optimization:** The YAML description must explicitly include triggers for "critiquing", "reviewing", and "improving" existing skills, in addition to creating new ones.
- **Workflow Flexibility:** While the skill defines a total 6-step creation workflow, the agent must understand that it can and should skip steps depending on the user's specific request. If the user only wants a review of an existing `SKILL.md`, the agent can skip directly to Step 6 (Final Audit & Generality Check).

## Reference Architecture (Progressive Disclosure)
The skill must utilize Progressive Disclosure by leveraging detailed best practices in its `references/` directory. The main `SKILL.md` will index these references and mandate the agent to consult them at specific phases. 
*The following reference documents have been successfully migrated and are available in `skills/building-skills/references/`:*
- `skill-creation-best-practices.md`
- `skill-specification.md`
- `skill-description-optimization.md`
- `skill-scripts-and-environments.md`
- `extension-architectures.md`
- `skill-evaluation.md`

## The 6-Step Granular Workflow (Checklist for Implementation)

The final `SKILL.md` must instruct the agent to strictly follow these six sequential steps, adapting or skipping steps only if the user requests a partial review.

### Step 1: Collaborative Requirements & Scope Gathering
- [ ] **Objective:** Deeply understand the intended skill, background, workflow, and edge cases.
- [ ] **Action:** This phase MUST be highly collaborative. The user depends on your expertise. Do not accept a brief prompt at face value. Engage in multiple conversational turns, proactively asking targeted questions to draw out the necessary context, edge cases, and specific procedures.
- [ ] **Documentation:** Maintain a living `skill-spec.md` document, continuously updating it as your understanding grows through the conversation.

### Step 2: Architecture & Progressive Disclosure Planning
- [ ] **Reference Grounding:** Consult `skill-specification.md`.
- [ ] **Action:** Decide *where* information should live to prevent context bloat. Update the `skill-spec.md` to explicitly map out what goes in the main `SKILL.md` (high-level workflow) versus what must be split into `references/` (detailed guidelines) or `scripts/`.
- [ ] **Checkpoint (User Approval):** Explicitly stop and ask the user for approval of the finalized `skill-spec.md` architecture map. You MUST NOT write the `SKILL.md` or scripts until approved.

### Step 3: Metadata & Trigger Design
- [ ] **Reference Grounding:** Consult `skill-description-optimization.md`.
- [ ] **Action:** Write *only* the YAML frontmatter (`name` and `description`).
- [ ] **Self-Review:** Pause and verify: *Is this description a routing trigger instructing the model when to load the skill, or did I accidentally summarize the workflow?* Adjust if necessary.

### Step 4: Resource Implementation (The Supporting Cast)
- [ ] **Reference Grounding:** Consult `skill-scripts-and-environments.md`.
- [ ] **Action:** Implement the `references/` files and `scripts/` mapped out in Step 2 *first*. Building these detailed files first provides concrete assets to link to when writing the core instructions.

### Step 5: Core Instruction Drafting
- [ ] **Reference Grounding:** Consult `skill-creation-best-practices.md`.
- [ ] **Action:** Write the body of the `SKILL.md`. Ensure you match *specificity to fragility* (e.g., using rigid commands for fragile steps) and link correctly to the resources created in Step 4.

### Step 6: Final Audit & Generality Check
- [ ] **Action:** Read the complete skill package.
- [ ] **Generality Review:** Explicitly check if the language is too closely coupled to the exact examples discussed in Step 1. Ensure the terminology is generic enough to handle all valid use cases, not just the narrow examples provided.
- [ ] **Specification Sync:** Compare the final implementation against `skill-spec.md`. Ensure the Intent, Architecture, and Testing sections accurately reflect the final product. If the implementation diverged, update `skill-spec.md`. The spec must remain the living blueprint.

## Open Questions for Refinement
- None. The workflow is fully defined and the knowledge base has been successfully converted into local reference documents.
