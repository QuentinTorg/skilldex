# Skill Creation Best Practices

Creating effective Agent Skills requires grounding instructions in real expertise and managing agent context efficiently ([Source](../parsed/imports/agentskills.io_skill_creator_best_practices.md), [Source](../parsed/imports/claud_skills_best_practices.md)). These best practices apply generally across all supported agents (e.g., Gemini, Codex, Cursor, Claude Code).

## Grounding in Real Expertise
- **Capture Intent First:** Synthesize skills from hands-on tasks and conversation history (tools used, sequence of steps, corrections, observed I/O formats) before asking the user for details ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **Extract from Tasks:** Synthesize skills from hands-on tasks instead of generic prompts. Pay attention to successful steps, manual corrections, specific I/O formats, and project-specific context.
- **Synthesize from Artifacts:** Use internal documentation, API schemas, runbooks, code reviews, and failure resolutions to ground the skill.

## Refining with Execution
- Run early drafts of the skill against real tasks and feed execution traces back into the design process.
- **Identify Failures:** Look for false positives, vague instructions causing the agent to waste time, or excessive options.
- **Test Across Models:** Test the skill with all underlying models you plan to use (e.g., Opus for reasoning vs. Haiku for speed) to ensure the guidance level is appropriate for each.
- **Generalize from Feedback:** Avoid overfitting to specific test cases. Use feedback to broaden metaphors and approaches rather than adding brittle constraints ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **Keep Prompts Lean:** Remove unproductive instructions that cause the model to waste time, as identified from execution transcripts ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).

## Managing Context Efficiently
- **Add What's Missing:** Include only project-specific procedures, non-obvious edge cases, and specific tools. Omit general knowledge the agent already possesses. The context window is a public good.
- **Coherent Units:** Scope skills like functions. They should encapsulate a coherent unit of work without becoming overly broad or too narrow.
- **Progressive Disclosure:** Keep the core `SKILL.md` concise (< 500 lines). Skills are tiered into metadata (triggering), instructions (loaded on activation), and resources (loaded on demand). Move detailed references to separate files to prevent "context bloat" ([Source](../parsed/imports/meta_development_skill_creator.md)). Useful patterns include:
  - **High-level guide with references:** Basic usage in `SKILL.md`, linking to detailed docs.
  - **Domain-specific organization:** Split references by domain (e.g., `reference/sales.md`, `reference/finance.md`) so the agent only loads what's relevant.
  - **Conditional details:** Only point to advanced files if a specific condition is met.
  - **Keep References Shallow:** Keep file references one level deep from `SKILL.md` to avoid partial reads or nested navigation issues. For files over 100 lines, include a Table of Contents at the top.

## Calibrating Control
- **Explain the Why:** Try to explain the *why* behind instructions instead of relying on heavy-handed MUSTs. Use the LLM's theory of mind to handle variations more humanely and effectively ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **Match Specificity to Fragility:** Give the agent freedom (explain *why*) when tasks tolerate variation. Be rigidly prescriptive for fragile or sequential operations. Match the level of instruction specificity to the task's fragility ([Source](../parsed/imports/gemini_skills_best_practices.md)):
  - **High freedom (text-based instructions):** Use when multiple approaches are valid or decisions depend heavily on context.
  - **Medium freedom (pseudocode or scripts with parameters):** Use when a preferred pattern exists but some variation is acceptable.
  - **Low freedom (specific scripts, few parameters):** Use when operations are fragile and error-prone, or a specific sequence MUST be followed.
- **Provide Defaults:** Instead of presenting equal menus of tools or approaches, pick a primary default and mention alternatives briefly. Avoid giving too many options.
- **Favor Procedures over Declarations:** Teach the agent *how to approach* a class of problems rather than giving the specific answer for a single instance.

## Meta-Development and the Skill-Creator Pattern
"Meta-development" is the paradigm of using AI agents to build, refine, and manage their own capabilities.
- **The Skill-Creator:** Rather than writing skills manually, use a specialized "meta-skill" (like the `skill-creator`) to scaffold the directory structure and the `SKILL.md` file. It uses guided interviews to capture intent and optimizes the description for accurate triggering ([Source](../parsed/imports/meta_development_skill_creator.md)).
- **Self-Augmentation & Orchestration:** Agents can use skill-creators to learn new project patterns without model retraining. In advanced workflows, agents handle routine implementation and testing while humans act as reviewers ([Source](../parsed/imports/meta_development_skill_creator.md)).

## Structural Patterns
- **TDD for Process Documentation:** Creating a skill is like Test-Driven Development applied to documentation. Follow the RED (write pressure scenario without skill, watch agent fail), GREEN (write minimal skill addressing specific rationalizations), REFACTOR (plug loopholes) cycle. The Iron Law: *No skill without a failing test first*.
- **Gotchas:** Create a specific section for environment-specific facts or past mistakes to pre-emptively correct the agent.
- **Output Templates:** Provide markdown or JSON templates (inline or in `assets/`) for strict output formatting.
- **Checklists:** Use explicit step-by-step checklists for multi-step workflows. Instruct the agent to copy the checklist and track progress.
- **Examples Pattern:** Provide concrete input/output examples within the skill, similar to few-shot prompting. Prefer one excellent example over multiple mediocre ones.
- **Validation Loops:** Instruct the agent to perform work, run a validation script, fix errors, and loop until it passes.
- **Plan-Validate-Execute:** For destructive/batch tasks, require an intermediate plan (e.g., `changes.json`) that is validated by a script before execution.
- **Bundled Scripts:** Write and bundle reusable scripts (`scripts/`) for logic the agent repeatedly reinvents. If execution transcripts reveal the agent constantly writing the same helper scripts (e.g., `create_docx.py`), bundle them to save time ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).

## Persuasion Principles for Discipline
When writing skills that enforce discipline or have high compliance costs, LLMs respond to human persuasion principles:
- **Authority:** Use imperative, non-negotiable language ("YOU MUST", "No exceptions") to eliminate decision fatigue.
- **Commitment:** Require explicit actions (e.g., announcing skill usage or checking boxes) to force consistency.
- **Social Proof:** Establish universal patterns ("Every time", "Always") and document common failure modes.
- *Note:* Avoid Liking and Reciprocity for compliance, as they conflict with honest feedback cultures.

## Content Guidelines
- **Naming Conventions:** Use active voice, **gerund form** (verb + -ing) for skill names (e.g., `processing-pdfs`, `writing-documentation`) to clearly describe the capability. Name skills by what they *do*, not by generic categories.
- **Skip the Obvious:** Do not write out a series of common commands (e.g., standard git commands) that the model already knows. Instead, describe the *intent* flexibly (e.g., "Cherry-pick the commit onto a clean branch. Resolve conflicts preserving intent") so the model can handle errors natively rather than derailing on brittle prescriptions ([Source](../parsed/imports/perplexity_agent_skills.md)).
- **Avoid Time-Sensitive Info:** Don't include information that will become outdated (like "before August 2025"). Use "Old patterns" or "Legacy" sections instead.
- **Consistent Terminology:** Pick one term (e.g., "API endpoint") and use it strictly throughout the skill to avoid confusing the agent.