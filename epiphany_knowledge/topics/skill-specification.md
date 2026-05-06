# Skill Specification

This topic details the required structure, configuration, and file formats for an Agent Skill.

## Directory Structure
A skill is a directory containing, at minimum, a `SKILL.md` file. Other optional directories can be included to bundle related resources ([Source](../parsed/imports/agentskills.io_skill_specification.md), [Source](../parsed/imports/claud_skills_best_practices.md), [Source](../parsed/imports/gemini_skills_best_practices.md)):
- `SKILL.md`: Required file containing metadata (frontmatter) and instructions. Keep this lean (< 500 lines) to serve as the high-level brain.
- `scripts/`: Optional directory for executable code agents can run. Code should be self-contained or clearly document dependencies. Supported languages depend on the agent (e.g., Python, Bash, JavaScript). Do not bundle general library code here.
- `references/`: Optional directory for additional documentation loaded on demand (e.g., `REFERENCE.md`, `FORMS.md`). Keep contents strictly **one level deep** (no nested subfolders) to enforce simplicity ([Source](../parsed/imports/mgechev_skills_README.md)).
- `assets/`: Optional directory for static resources (templates, images, data files). Keep contents strictly **one level deep** ([Source](../parsed/imports/mgechev_skills_README.md)).
- `config.json`: Optional file for first-run user setup or auxiliary configuration avoiding context pollution ([Source](../parsed/imports/perplexity_agent_skills.md)).

*Note: Skills are for agents, not humans. Do not create human-centric documentation like `README.md`, `CHANGELOG.md`, or `INSTALLATION_GUIDE.md` within the skill directory ([Source](../parsed/imports/mgechev_skills_README.md)).*

## `SKILL.md` Format
The `SKILL.md` file must contain YAML frontmatter followed by Markdown content ([Source](../parsed/imports/agentskills.io_skill_specification.md)).

### Frontmatter
The YAML frontmatter provides essential metadata for the skill. **Strict Constraint:** The frontmatter must be the very first content in `SKILL.md`. The file will be skipped if there is any preceding text, titles, or even a blank line before the opening `---`. Additionally, the skill's name is derived strictly from the `name:` field in the frontmatter, regardless of the parent directory's name.

| Field | Required | Constraints |
| --- | --- | --- |
| `name` | Yes | 1-64 characters. Lowercase letters (`a-z`), numbers, and hyphens (`-`) only. Must not start, end with, or contain consecutive hyphens. Must match parent directory name. Cannot contain XML tags or agent-specific reserved words. Consider **gerund form** (verb + -ing) like `processing-pdfs` ([Source](../parsed/imports/opencode_skills.md)). |
| `description` | Yes | 1-1024 characters. Describes what the skill does and when to use it (trigger conditions). Cannot contain XML tags ([Source](../parsed/imports/opencode_skills.md)). |
| `license` | No | License name or reference to a bundled license file. |
| `compatibility` | No | Max 500 characters. For specific environment requirements (intended product, system packages). Note: Priority agents are Gemini (Primary), Codex, Cursor, and Claude Code. |
| `metadata` | No | Arbitrary map from string keys to string values for custom metadata. |
| `allowed-tools` | No | Experimental space-delimited list of pre-approved tools. |
| `paths` | No | **(Cursor only)** Glob patterns (comma-separated string or list) that scope the skill to matching files. Replaces legacy `globs` field. ([Source](../parsed/imports/cursor_skills_docs.md)) |
| `disable-model-invocation` | No | **(Cursor only)** Boolean. If `true`, the skill acts as a traditional slash command, requiring explicit `/skill-name` invocation to enter context, preventing automatic application. ([Source](../parsed/imports/cursor_skills_docs.md)) |

### Body Content
The Markdown body after the frontmatter contains the skill instructions. The entire `SKILL.md` is loaded upon activation.
It is recommended to include:
- Step-by-step instructions
- Examples of inputs and outputs
- Common edge cases

## Progressive Disclosure
Skills are designed to use an agent's context efficiently through progressive disclosure ([Source](../parsed/imports/agentskills.io_what_are_skills.md), [Source](../parsed/imports/agentskills.io_skill_specification.md), [Source](../parsed/imports/claude_skills_overview.md)):
1. **Level 1: Discovery (Metadata)** (~100 tokens): Agents load only the skill's `name` and `description` frontmatter at startup.
2. **Level 2: Activation (Instructions)** (< 5000 tokens recommended): When a task matches the description, the agent reads the full `SKILL.md` instructions via a filesystem read. Only then does the content enter context.
3. **Level 3: Execution (Resources and Code)** (as needed): The agent follows instructions and dynamically loads references, scripts, or assets only when required. Executable scripts are run via bash; the script code itself never enters the context window, only its output consumes tokens.

*Tip: Keep the main `SKILL.md` under 500 lines and move detailed material to referenced files.*

## File References
When referencing other files within the skill (e.g., in `references/` or `scripts/`), use relative paths from the skill root. 
Example: `[the reference guide](references/REFERENCE.md)` or `scripts/extract.py`.
Keep file references one level deep from `SKILL.md` to avoid nested reference chains ([Source](../parsed/imports/agentskills.io_skill_specification.md)). Always use forward slashes for paths (`/`), avoiding Windows-style backslashes.

## Validation
Use the `skills-ref` reference library to validate a skill's formatting, naming conventions, and frontmatter ([Source](../parsed/imports/agentskills.io_skill_specification.md)).). Always use forward slashes for paths (`/`), avoiding Windows-style backslashes.

## Validation
Use the `skills-ref` reference library to validate a skill's formatting, naming conventions, and frontmatter ([Source](../parsed/imports/agentskills.io_skill_specification.md)).