# Skill Evaluation

Evaluating agent skills ensures they produce reliable, high-quality outputs across varied prompts and edge cases, using an eval-driven iteration loop.

## Evaluation-Driven Development (TDD for Skills)
Build evaluations *before* writing extensive documentation to ensure the skill solves real problems:
1. **RED Phase:** Run the agent on a pressure scenario without the skill. Document its failures and rationalizations.
2. **Baseline:** Establish baseline performance (time, tokens, success) without the skill.
3. **GREEN Phase:** Write the minimal instructions in `SKILL.md` needed to pass the evaluations.
4. **REFACTOR Phase:** Iterate and plug loopholes. Compare performance against the baseline.

## LLM Collaboration Validation
An effective way to validate skills is to collaborate with LLMs directly:
- **Discovery Validation:** Provide only the `name` and `description` to an agent. Ask it to generate 3 triggers and 3 non-triggers to test scope.
- **Logic Validation:** Feed `SKILL.md` to an agent and ask it to output an "internal monologue" simulating a request, highlighting "Execution Blockers" or ambiguous instructions.
- **Edge Case Testing:** Ask an agent to act as a QA tester to generate highly specific, challenging scenarios that might break the skill.
- **Blind Comparison:** Present both the baseline output and the skill output to an LLM judge without revealing which is which. Ask the judge to score holistic qualities (formatting, usability) independently of mechanical assertions.

## Running Evals and Assertions
- **Test Cases:** Define realistic user prompts and verifiable expected behaviors.
- **Assertions:** Create objectively verifiable statements (e.g., "Output is valid JSON"). Avoid subjective assertions ("Output is good"). Require concrete evidence for a PASS; do not give the benefit of the doubt.
- **Execution & Tracking:** Run the test cases both with the skill and without the skill (baseline). If your environment supports it, spawn these in parallel using subagents. Track metrics like `total_tokens` and `duration_ms` for each run.
- **Substance Over Form:** Pass expectations only when evidence reflects genuine completion, not just surface-level compliance.
- **Delta Analysis:** Calculate the delta in pass rate, time, and tokens between the baseline and the skill run. This demonstrates the cost versus value added.
- **Assertion Pruning:** Review assertions after runs. Remove assertions that always pass in both configurations (they don't measure skill value). Investigate assertions that always fail in both (they might be too hard or broken).

## Iteration Loop
- Analyze transcripts of successful vs. failed runs. Where did the agent diverge?
- Generate actionable improvements categorized by: prose instructions, scripts to add, input/output examples, and error handling fallback guidance.
- Ensure the skill generalizes from feedback rather than overfitting to specific test cases. Stop iterating when improvements plateau.
