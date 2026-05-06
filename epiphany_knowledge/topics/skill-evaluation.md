# Skill Evaluation

Evaluating agent skills ensures they produce reliable, high-quality outputs across varied prompts and edge cases, using an eval-driven iteration loop ([Source](../parsed/imports/agentskills.io_evaluating_skills.md), [Source](../parsed/imports/claud_skills_best_practices.md)).

## Evaluation-Driven Development
Build evaluations *before* writing extensive documentation to ensure the skill solves real problems rather than imagined ones ([Source](../parsed/imports/perplexity_agent_skills.md)):
1. Identify gaps by running the agent on tasks without the skill (RED phase). Watch the agent fail and document their exact choices and rationalizations.
2. Build a "hero query set" with realistic user pressure scenarios. Good pressure scenarios combine 3+ pressures (e.g., time limits, sunk cost, authority overrides, exhaustion) to force explicit choices when testing discipline-enforcing skills.
3. Create evaluations testing these gaps, starting with both positive and negative examples (negative examples are extremely powerful).
4. Establish a baseline performance by running the scenarios without the skill.
5. Write minimal instructions to pass the evaluations (GREEN phase) addressing the specific rationalizations observed.
6. Iterate, refactor to plug new loopholes, and compare against the baseline (REFACTOR phase).

**(Perplexity-Specific Context):**
Ensure that evaluations are run across all target model families (e.g., GPT vs Claude Opus vs Claude Sonnet). Different models behave fundamentally differently when it comes to loading and interpreting skills, so cross-model evaluations prevent behavior drift ([Source](../parsed/imports/perplexity_agent_skills.md)).

## Test Cases
A test case (`evals/evals.json`) consists of:
- **Prompt:** A realistic user message.
- **Expected Behavior / Output:** Verifiable descriptions of success.
- **Input Files:** (Optional) Files the skill needs to process.

Determine if the skill has objectively verifiable outputs (benefits from test cases) or subjective outputs (e.g., writing style, better evaluated qualitatively without assertions) ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)). Start with 2-3 varied prompts covering standard use and edge cases. Avoid vague prompts.

## Running Evals
Run each test case twice: once **with the skill** and once **without it** (baseline). For an existing skill, the baseline is the previous version ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- If supported by your environment, spawn all with-skill and baseline runs in parallel using subagents to save time ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **Agent-Specific Workaround (Claude.ai):** Claude.ai lacks subagents, so execute tests sequentially, run only the with-skill version (skip baselines), and focus entirely on qualitative human review since quantitative baselines aren't meaningful ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- Ensure a clean context for each run so the agent only follows the `SKILL.md` instructions.
- Structure workspaces into iterations (`iteration-N/`), separating `with_skill` and `without_skill` outputs.
- **Timing Data:** Record `total_tokens` and `duration_ms` for each run to evaluate the cost-benefit tradeoff.

## LLM Collaboration Validation
Since LLMs will use your skills, an effective way to validate them is to collaborate with LLMs directly, simulating execution and testing boundaries ([Source](../parsed/imports/mgechev_skills_README.md)):
1. **Discovery Validation:** Provide the agent only your `name` and `description` YAML frontmatter. Ask it to generate 3 user prompts that should trigger the skill, 3 that shouldn't, and critique the description's scope.
2. **Logic Validation:** Feed the full `SKILL.md` to an agent and ask it to simulate a realistic request step-by-step. Have it output an "internal monologue" highlighting any "Execution Blockers" where instructions force it to guess or hallucinate missing information.
3. **Edge Case Testing:** Ask an agent to act as a "ruthless QA tester" whose goal is to break the skill. Have it generate 3-5 highly specific, challenging questions about unsupported configurations, legacy dependencies, or failure states.
4. **Architecture Refinement:** Ask the agent to rewrite the skill enforcing "Progressive Disclosure" based on the edge cases found, moving dense config/rules into `references/` or `assets/` directories.

## Assertions & Grading
Assertions are objectively verifiable statements about expected output (e.g., "The output file is valid JSON"). 
- Draft assertions and give them descriptive names while the test runs are in progress ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- Add assertions after observing the first round of outputs. 
- Avoid subjective assertions (e.g., "The output is good"). Subjective outputs should rely entirely on human judgment.
- Evaluate assertions manually, via verification scripts, or by spawning a grader subagent that evaluates the assertions and saves results to a `grading.json` file ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **Critique the Evaluations:** A passing grade on a weak assertion creates false confidence. Flag assertions that are trivially satisfied, and identify important outcomes that lack assertion coverage ([Source](../parsed/imports/anthropic_skill_creator_agents_grader.md)).
- **Substance Over Form:** PASS expectations only when evidence reflects genuine task completion, not just surface-level compliance (e.g., correct filename but empty content) ([Source](../parsed/imports/anthropic_skill_creator_agents_grader.md)).
- **Implicit Claims:** Beyond predefined expectations, extract and verify implicit claims (factual, process, or quality claims) from the outputs to catch issues that rigid assertions might miss ([Source](../parsed/imports/anthropic_skill_creator_agents_grader.md)).
- Remove assertions that always pass without the skill, as they don't reflect the skill's added value. The burden of proof to pass is on the expectation; when uncertain, fail ([Source](../parsed/imports/anthropic_skill_creator_agents_grader.md)).

## Aggregating Results
Calculate aggregate statistics (pass rate, time, tokens) in a `benchmark.json` file. The **delta** between the baseline and the skill run demonstrates the cost versus the value added. Look for patterns across multiple runs: assertions that always pass/fail (may not differentiate value), high variance (flakiness), or outlier resource usage ([Source](../parsed/imports/anthropic_skill_creator_agents_analyzer.md)).

## Advanced: Blind Comparison
For situations requiring rigorous comparison between two versions of a skill, use a blind comparison where an independent subagent judges two outputs without knowing which version produced which ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).

When performing a blind comparison ([Source](../parsed/imports/anthropic_skill_creator_agents_comparator.md)):
- Use a **Two-Dimensional Rubric** evaluating both **Content** (correctness, completeness, accuracy) and **Structure** (organization, formatting, usability) on a 1-5 scale.
- Prioritize overall rubric score and task completion as primary evidence. Use assertion pass rates only as secondary evidence.
- Be decisive. If both outputs fail, pick the one that fails less badly. If both are excellent, pick the one that's marginally better. Ties should be rare.

## Iteration Loop
Improve the skill based on primary signals from evaluations: failed assertions, human feedback, and execution transcripts. You can develop skills iteratively by having one agent instance ("Agent A") help write and refine the skill, while another instance ("Agent B") tests it in a clean environment.

Pay attention to how the agent navigates the skill:
- **Unexpected exploration paths:** Is the structure unintuitive?
- **Missed connections:** Are file references prominent enough?
- **Ignored content:** Should bundled files be removed or better signaled?

**Post-hoc Analysis:** When comparing transcripts of successful vs. failed runs, analyze instruction adherence. Where did the agent diverge? What tools were used differently? Generate actionable improvement suggestions categorized by: `instructions` (prose changes), `tools` (scripts to add), `examples` (inputs/outputs to include), `error_handling` (fallback guidance), `structure`, and `references` ([Source](../parsed/imports/anthropic_skill_creator_agents_analyzer.md)).

Provide feedback loops alongside the `SKILL.md` to an LLM to propose improvements. Focus on generalizing from feedback, keeping instructions lean, explaining *why* an instruction exists, and bundling repeated work into helper scripts. Stop iterating when satisfied or when improvements plateau.