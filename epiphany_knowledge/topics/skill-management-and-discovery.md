# Skill Management and Discovery

This topic outlines the universal concepts and specific mechanics for installing, discovering, and activating Agent Skills across environments.

## Skill Discovery & Loading
Agents discover skills by scanning specific directories (e.g., `.gemini/skills` or `.agents/skills`).
- **Discovery Tiers:** *(Gemini specific)* Skills are discovered in precedence order (lowest to highest): Built-in Skills -> Extension Skills -> User Skills (`~/.gemini/skills/` or `~/.agents/skills/`) -> Workspace Skills (`.gemini/skills/` or `.agents/skills/`) ([Source](../parsed/imports/gemini_creating_skills.md)).
- **Discovery Aliases:** The `.agents/skills` folder is supported as an alternative to agent-specific folders (like `.gemini/skills`) for compatibility with the Agent Skills standard ([Source](../parsed/imports/gemini_creating_skills.md)).
- **Path Layout:** The skill definition file (`SKILL.md`) must be at the root of the skills directory or one directory deep. Deeper nesting prevents discovery.
- **Troubleshooting Missing Skills:**
  - **Filename:** The file must be exactly `SKILL.md` (case-sensitive).
  - **Frontmatter:** It must be the very first thing in the file (no preceding blank lines or titles). Both `name:` and `description:` must be present.
  - **Trust/Security:** For some agents (like Gemini CLI), workspace-level skills are only loaded if the folder is explicitly trusted (e.g., via `/trust`).
- **Reloading:** To refresh the list of available skills without restarting a session, agents typically offer a reload command. *(Gemini specific: use `/skills list` to view and `/skills reload` to refresh).*

## Skill Activation Flow
1. **Trigger:** The user asks a natural language question or requests a task.
2. **Matching:** The agent compares the request against the `description:` frontmatter of all discovered skills.
3. **Activation:** If matched, the agent invokes an internal tool (e.g., `activate_skill`) to read the full `SKILL.md` instructions into context.
4. **Consent:** *(Gemini specific)* The user is prompted to approve the skill's execution.
5. **Execution:** The agent runs the bundled scripts or executes the prescribed workflow using its standard tools (like shell command execution) ([Source](../parsed/imports/gemini_skills_getting_started.md)).

## Skill Creation Tools
Many agents provide built-in assistance to scaffold new skills. For example, triggering a `skill-creator` skill by asking the agent to "create a new skill" will automatically generate the directory structure and boilerplate `SKILL.md` ([Source](../parsed/imports/gemini_skills_getting_started.md), [Source](../parsed/imports/gemini_creating_skills.md)).

## Managing Skills (Gemini CLI)
*Note: These commands and scripts are specific to the Gemini CLI environment.*

**In-Session Management (Slash Commands):**
- **List skills:** `/skills list` shows discovered skills. Use `/skills list all` to include internal built-in skills, or `/skills list nodesc` to hide descriptions ([Source](../parsed/imports/gemini_using_agent_skills.md)).
- **Reload skills:** `/skills reload` (or `/skills refresh`) to scan for new or modified skills without restarting the CLI ([Source](../parsed/imports/gemini_using_agent_skills.md)).
- **Toggle status:** `/skills disable <name>` prevents a skill from being triggered, and `/skills enable <name>` re-enables it ([Source](../parsed/imports/gemini_using_agent_skills.md)).
- **Link local skills:** `/skills link <path> [--scope user|workspace]` to immediately use a skill you are developing ([Source](../parsed/imports/gemini_using_agent_skills.md)).

**Terminal Utilities (`gemini skills`):**
- **Testing Skills:** Check if a skill is correctly loaded by running the `/skills` command ([Source](../parsed/imports/gemini_creating_skills.md)).
- **Install:** `gemini skills install <url-or-path>` (You can install from standalone Git repositories). Defaults to user profile; use `--scope workspace` for project-specific installation ([Source](../parsed/imports/gemini_creating_skills.md), [Source](../parsed/imports/gemini_using_agent_skills.md)).
- **Link:** `gemini skills link <path>` (Useful for local development, links a separate directory to the user skills directory without copying files) ([Source](../parsed/imports/gemini_creating_skills.md), [Source](../parsed/imports/gemini_using_agent_skills.md)).
- **Uninstall:** `gemini skills uninstall <name>` ([Source](../parsed/imports/gemini_using_agent_skills.md)).
- **Creation Scripts:** Gemini Core provides node scripts for advanced development: `init_skill.cjs <name> --path <dir>`, `validate_skill.cjs <path>`, and `package_skill.cjs <path>` (creates a `.skill` zip file) ([Source](../parsed/imports/gemini_creating_skills.md)).