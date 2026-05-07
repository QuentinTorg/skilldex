# Skill Description Optimization

The `description` field in a `SKILL.md` frontmatter is crucial because agents read only the description initially to decide if a skill should be triggered for a task.

## Writing Effective Descriptions

- **It is a Routing Trigger:** The description is a routing trigger, not internal documentation. Write it as instructions to the model for *when* to load the skill. Start descriptions with "Use when...".
- **NEVER Summarize Workflow:** Do not summarize the skill's internal process or workflow in the description. Doing so creates a shortcut; the agent may read the summary and skip loading the full skill body, missing crucial details. Limit the description strictly to triggering conditions.
- **Be Specific & Pushy:** Use keywords likely to appear in user prompts. Explicitly list contexts where the skill applies ("Make sure to use this skill whenever...").
- **Keyword Coverage:** Include specific error messages (e.g., "Hook timed out", "ENOTEMPTY"), symptoms ("flaky", "hanging"), synonyms ("timeout/hang/freeze"), and tools/file types.
- **Write in the Third Person:** Use objective phrasing ("Processes files", not "I can process").
- **Focus on User Intent:** Describe what the user is trying to achieve (e.g., "watch CI"), not the mechanical step (e.g., "runs git log"). Describe the *problem* not just language-specific symptoms unless the skill is tech-specific.
- **Naming Conventions:** Use active voice, verb-first, and preferably gerunds (-ing) for processes (e.g., `creating-skills`, `condition-based-waiting`).
- **Keep it Concise:** Max 1024 characters. Target 50 words or fewer for most descriptions. For getting-started workflows, target <150 words total context to preserve tokens.

## Trigger Evaluation Workflow

Systematically test the description using an evaluation set of queries to ensure it triggers correctly without overfitting.

### Creating Evaluation Queries
- **Should-trigger queries:** The best positive examples are those where the skill is needed but the connection isn't immediately obvious. Make queries concrete and specific (e.g., include file paths, typos).
- **Should-not-trigger queries:** The best negative examples are "near-misses"—queries that share keywords but require different capabilities.

### Preventing Overfitting
- **Train set (~60%):** Use these to identify failures and refine the description.
- **Validation set (~40%):** Use these *only* to check if the generalizations work.

## The Optimization Loop
1. Evaluate against train and validation sets multiple times to compute a trigger rate.
2. Identify failures strictly in the *train set*.
3. Revise the description:
   - If false negatives: broaden the scope.
   - If false positives: add specificity or clarify boundaries.
   - Do not add exact keywords from failed queries; address the concept.
4. Repeat until the train set passes or improvements plateau.
5. Select the best description based on validation pass rate.
