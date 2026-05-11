# Skill Specification: [Skill Name]

## 1. Background & Intent
- **What is the goal?** [Brief description of what the user wants to achieve]
- **Why is a skill needed?** [e.g., The agent fails without it, specific formatting is required, a rigorous discipline must be enforced]
- **Empirical Evidence:** [Links to chat logs, code snippets, or incident reports proving the need]

## 2. Trigger Conditions (Metadata)
- **When should this trigger?** [Specific keywords, errors, or workflows the user will mention]
- **When should this NOT trigger?** [Near-miss scenarios where another skill or general knowledge is better]

## 3. Workflow & Procedures
*(A step-by-step breakdown of how the agent should approach the task)*
1. [Step 1]
2. [Step 2]
3. [Step 3]

## 4. Edge Cases & Negative Boundaries
- **Constraints/Gotchas:** [List specific environment facts that defy reasonable assumptions, e.g., "The database uses soft deletes"]
- **Negative Boundaries:** [What are explicit anti-patterns or things the skill must NEVER do?]

### Failure Analysis (If applicable)
- **Reported Failure:** [What did the user say happened?]
- **Actual vs. Expected:** [What did the previous agent actually do vs. what was the intended behavior?]
- **Root Cause/Rationalization:** [Identify the underlying reason: e.g., vague instruction, tool hallucination, or rationalizing away a constraint]
- **Generalization:** [How does this fix the *class* of problem for all users?]

## 5. Architecture & Progressive Disclosure Plan
- **`SKILL.md` (Core Instructions):** [What goes here? Keep < 500 lines]
- **`references/` (Detailed Rules):** [List files to create, e.g., `references/api-schema.md`]
- **`assets/` (Templates):** [List files to create, e.g., `assets/report-template.md`]
- **`scripts/` (Executable Logic):** [List scripts to create, e.g., `scripts/validate.py`]

## 6. Testing & Assertions (Eval-Driven)
- **Test Scenarios:** [Define 2-3 realistic pressure scenarios to test]
- **Assertions:** [Define objectively verifiable success criteria, e.g., "Output is valid JSON"]