# Skill Specification: building-skills

## 1. Background & Intent
- **What is the goal?** Create a dedicated `building-skills` skill that acts as an expert guide and collaborative mentor for users creating, critiquing, reviewing, auditing, or improving agent skills in this repository. It replaces the previous directives found in `AGENTS.md`.
- **Why is a skill needed?** The previous guidelines in `AGENTS.md` lacked sufficient detail and clarity for an agent to act as a highly effective mentor. Critical best practices and agent architecture differences were siloed in an external `epiphany_knowledge` database. A rigorous workflow is needed to ensure skills are general, precise, and adhere to established best practices.
- **Empirical Evidence:** Issues tracking poor skill generation from native 'skill-creator' agents, and the fragmentation of knowledge between `AGENTS.md` and the `epiphany_knowledge` database.

## 2. Trigger Conditions (Metadata)
- **When should this trigger?** Whenever the user asks to build a new skill, refine an existing `SKILL.md`, critique a workflow, perform an alignment audit, or improve a skill's architecture/instructions. Also triggers broadly for questions, brainstorming, or conceptual discussions about skills. **CRITICAL: Must override the native 'skill-creator' built-in skill.**
- **When should this NOT trigger?** When the user is asking for general programming help or to execute an existing skill that doesn't involve meta-skill development.

## 3. Workflow & Procedures
The agent must follow a rigorous, six-step workflow, but exercise flexibility by skipping to Step 6 (Final Audit) if the user only requests a partial review.
1. **Preparation:** Read `skill-creation-best-practices.md` and copy the 6-step checklist to the internal scratchpad.
2. **Step 1: Collaborative Requirements & Scope Gathering:** Act as a strict interviewer using the 4-part Discovery Rubric (Trigger, Context, Constraints, Boundaries). Demand empirical evidence. Do NOT write the spec prematurely.
3. **Step 2: Architecture & Progressive Disclosure Planning:** Decide where information lives (`SKILL.md` vs `references/` vs `scripts/`) using `skill-specification.md` and get user approval.
4. **Step 3: Metadata & Trigger Design:** Write YAML frontmatter optimizing for routing triggers.
5. **Step 4: Resource Implementation:** Implement the supporting cast (`references/`, `assets/`, `scripts/`) first.
6. **Step 5: Core Instruction Drafting:** Write the main `SKILL.md` body.
7. **Step 6: Final Audit & Generality Check:** Perform a holistic "Structural & Cohesion Audit" across all files to find redundancies, progressive disclosure violations, and scattered context. Verify specification sync.

## 4. Edge Cases & Negative Boundaries
- **Constraints/Gotchas:** 
  - Do NOT use `@` links in `SKILL.md` as they break progressive disclosure.
  - Do NOT accept a brief prompt at face value; engage in multiple conversational turns.
- **Negative Boundaries:** 
  - **NEVER** write walls of text guessing at the full specification during Step 1.
  - **NEVER** copy-paste user feedback directly into the skill; always generalize patterns.
  - **NEVER** summarize the workflow in the YAML description; it is strictly a routing trigger.

### Failure Analysis
- **Reported Failure:** The agent previously missed structural redundancies (e.g., redundant checklists in templates) because it only read files surgically. The agent also failed to trigger for simple brainstorming inquiries.
- **Actual vs. Expected:** The agent was expected to trigger for any skill-related discussion and act as a holistic mentor, but it functioned too narrowly.
- **Root Cause/Rationalization:** The description was too action-oriented, missing inquiry triggers. The final audit step lacked explicit instructions to zoom out and check across multiple files for cohesion.
- **Generalization:** By updating the trigger to include "brainstorming/questions" and mandating a holistic "Structural & Cohesion Audit" in Step 6, we fix this class of narrow, task-fixated behavior for all future interactions.

## 5. Architecture & Progressive Disclosure Plan
- **`SKILL.md` (Core Instructions):** Contains the 6-step workflow, the Discovery Rubric, and the "Preparation" checklist.
- **`references/` (Detailed Rules):** 
  - `skill-creation-best-practices.md`
  - `skill-specification.md`
  - `skill-description-optimization.md`
  - `skill-scripts-and-environments.md`
  - `extension-architectures.md`
  - `skill-evaluation.md`
- **`assets/` (Templates):** `skill-spec-template.md` (used in Step 1/Step 2).
- **`scripts/` (Executable Logic):** None currently required.

## 6. Testing & Assertions (Eval-Driven)
- **Test Scenarios:** 
  1. User asks: "I want to make a skill that writes unit tests." (Tests Step 1 sequential interview).
  2. User asks: "Can you review my existing skill?" (Tests jumping to Step 6 audit).
  3. User asks: "How do I make a good description?" (Tests triggering on inquiry).
- **Assertions:** 
  1. Agent does NOT immediately write `skill-spec.md`.
  2. Agent asks questions aligning with the 4-part Discovery Rubric.
  3. Agent catches structural redundancies in an existing skill package.