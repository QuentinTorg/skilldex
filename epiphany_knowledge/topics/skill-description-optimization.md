# Skill Description Optimization

The `description` field in a `SKILL.md` frontmatter is crucial because agents use progressive disclosure, reading only the description initially to decide if a skill should be triggered for a task ([Source](../parsed/imports/agentskills.io_skill_creator_optimizing_skill_descriptions.md), [Source](../parsed/imports/claud_skills_best_practices.md)).

## Writing Effective Descriptions
- **It is a Routing Trigger:** The description is a routing trigger, not internal documentation for what the skill does or why it's useful. Write it as instructions to the model for *when* to load the skill ([Source](../parsed/imports/perplexity_agent_skills.md)). Agents only consult skills for tasks they can't easily handle directly; simple, one-step queries may not trigger a skill even with a perfect description ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **NEVER Summarize Workflow:** Do not summarize the skill's process or workflow in the description. Doing so creates a shortcut; the agent may read the summary and skip loading the full skill body, missing crucial details. Limit the description strictly to triggering conditions.
- **Be Specific:** Use keywords that are likely to appear in user prompts (e.g., "audit," "security," "refactor," "migration") ([Source](../parsed/imports/gemini_skills_best_practices.md)).
- **Define the Trigger:** Clearly state *when* the skill should be used (e.g., "Use this skill when the user asks to review a PR for performance regressions") ([Source](../parsed/imports/gemini_skills_best_practices.md)).
- **Avoid Overlap:** Ensure your skill descriptions are distinct from one another and from the general capabilities of the model ([Source](../parsed/imports/gemini_skills_best_practices.md)).
- **Write in the Third Person:** Descriptions should be objective (e.g., "Processes Excel files", not "I can process Excel files"). This is crucial because it is injected directly into the system prompt.
- **Use imperative phrasing:** Tell the agent when to act (e.g., "Load when...", "Use this skill when...").
- **Err on the side of being pushy:** Explicitly list contexts where the skill applies, even if the user doesn't use the exact domain name or terminology. For example, "Make sure to use this skill whenever the user mentions dashboards... even if they don't explicitly ask for a 'dashboard'" ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **Focus on user intent:** Describe what the user is trying to achieve rather than the skill's internal mechanics (e.g., "watch CI" instead of "runs git log"). Include specific triggers or context keywords.
- **Keep it concise:** Descriptions must be under the 1024-character limit. Target 50 words or fewer for optimal signal-to-noise ratio in the context index ([Source](../parsed/imports/perplexity_agent_skills.md)).

## Trigger Evaluation Workflow
To ensure a skill triggers correctly without overfitting, you should systematically test the description using an evaluation set of queries.

### Creating Evaluation Queries
Design realistic user prompts labeled with `should_trigger` (true/false).
- **Should-trigger queries:** Vary phrasing, explicitness, detail, and task complexity. The best positive examples are those where the skill is needed but the connection isn't immediately obvious. Make queries concrete and specific (e.g., including file paths, company names, backstory, or typos). Avoid abstract requests like "Format this data" ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- **Should-not-trigger queries:** The best negative examples are "near-misses"—queries that share keywords or concepts but actually require different capabilities or adjacent domains. Avoid negative queries that are obviously irrelevant to the skill ([Source](../parsed/imports/anthropic_skill_creator_SKILL.md)).
- Include realistic contexts (file paths, personal contexts, casual language, typos).

### Preventing Overfitting (Train/Validation Split)
Split your query set to avoid overfitting the description to specific phrasings:
- **Train set (~60%):** Use these to identify failures and guide your improvements.
- **Validation set (~40%):** Keep these aside and use them *only* to check if the description generalizations work.

## The Optimization Loop
1. Evaluate the current description against both train and validation sets (run multiple times, e.g., 3 runs, to compute a trigger rate since models are nondeterministic).
2. Identify failures strictly in the *train set* (false positives or false negatives).
3. Revise the description:
   - If should-trigger queries fail, broaden the scope.
   - If should-not-trigger queries falsely trigger, add specificity or clarify boundaries.
   - Do not add exact keywords from failed queries; instead, address the underlying concept.
4. Repeat the loop until the train set passes or improvements plateau (usually ~5 iterations).
5. Select the best description based on its validation pass rate.

**Note on Agents:** Agent observability for checking tool execution/skill loading varies by client (e.g., Gemini, Codex, Cursor, Claude Code).