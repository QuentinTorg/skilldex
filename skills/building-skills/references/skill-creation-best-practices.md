# Skill Creation Best Practices

Creating effective Agent Skills requires grounding instructions in real expertise and managing agent context efficiently. These best practices apply generally across all supported agents (e.g., Gemini, Codex, Cursor, Claude Code).

## Core Principles

- **Grounding in Real Expertise:** Synthesize skills from hands-on tasks, conversation history, API schemas, code reviews, issue trackers, version control history, and internal runbooks. A skill synthesized from actual team incident reports outperforms one from generic articles. Do not rely solely on generic prompts or LLM training knowledge.
- **Manage Context Efficiently:** The context window is a public good. Include only project-specific procedures, non-obvious edge cases, and specific tools. Omit general knowledge.
- **Progressive Disclosure:** Keep the core `SKILL.md` concise (< 500 lines). Skills are tiered into metadata (triggering), instructions (loaded on activation), and resources (loaded on demand). Move detailed references to separate files (`references/`) to prevent context bloat.
  - *Keep References Shallow:* Keep file references one level deep from `SKILL.md`.

## Instructional Design

- **Match Specificity to Fragility:** 
  - **High freedom:** Use text-based instructions when multiple approaches are valid.
  - **Medium freedom:** Use pseudocode or parametrizable scripts when a preferred pattern exists.
  - **Low freedom:** Use specific, rigid scripts when operations are fragile or a specific sequence MUST be followed.
- **Explain the Why:** Explain the *why* behind instructions instead of relying on heavy-handed MUSTs where possible, allowing the LLM's theory of mind to handle variations.
- **Provide Defaults:** Pick a primary default tool or approach and mention alternatives briefly rather than providing equal menus.
- **Favor Procedures over Declarations:** Teach the agent *how to approach* a class of problems rather than giving the specific answer for a single instance.

## Structural Patterns

- **Validation Loops:** Instruct the agent to perform work, run a validation script, fix errors, and loop until it passes.
- **Plan-Validate-Execute:** For destructive/batch tasks, require an intermediate plan that is validated before execution.
- **Gotchas Section:** Create a specific section for environment-specific facts that defy reasonable assumptions. These aren't general advice ("handle errors") but concrete corrections to mistakes the agent will make without being told otherwise (e.g., "The `users` table uses soft deletes"). When an agent makes a mistake you have to correct, add it to this section.
- **Checklists for Progress:** Use explicit checklists for workflows. Instruct the agent to copy the checklist into its internal reasoning or scratchpad and check off items to track multi-step progress without losing its place.
- **Concrete Templates:** Agents pattern-match exceptionally well. Instead of spending paragraphs describing how a JSON output or document should look, provide a concrete template. Short templates can live inline in `SKILL.md`; longer templates (like `assets/report-template.md` or `assets/schema.json`) should be stored in the `assets/` directory and referenced.
- **Examples Pattern:** Provide concrete input/output examples within the skill, similar to few-shot prompting. Prefer one excellent example over multiple mediocre ones.
- **Bundled Scripts:** If the agent repeatedly reinvents logic, bundle it into `scripts/` to save time.

## Bulletproofing & Anti-Patterns

- **Bulletproofing against Rationalizations:** Agents may rationalize skipping steps under pressure (especially for discipline-enforcing skills like TDD). Close every loophole explicitly. State foundational rules like: *"Violating the letter of the rules is violating the spirit of the rules."*
- **Rationalization Tables & Red Flags:** Document excuses agents use during baseline testing in a table, and create a "Red Flags" list (e.g., "If you think 'I already manually tested it', STOP and start over.") to help agents self-correct.
- **No Narrative Examples:** Avoid narrative storytelling (e.g., *"In session 2025-10-03, we found..."*). It's too specific and not reusable.
- **No Multi-Language Dilution:** Do not implement examples in 5+ languages. Choose the most relevant language for the domain.
- **Semantic Naming:** Avoid generic labels (e.g., `helper1`, `step3`). Use names with semantic meaning.

## Iteration and Testing (Eval-Driven Loop)
Creating a robust skill requires a rigorous Test-Driven Development (TDD) loop. *No skill should be built without a failing test first.* For the complete mechanical workflow (RED/GREEN/REFACTOR phases) and how to validate with LLMs, consult `[Skill Evaluation](skill-evaluation.md)`.
