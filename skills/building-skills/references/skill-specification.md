# Skill Specification Requirements

This document details the required structure, configuration, and file formats for an Agent Skill.

## Directory Structure
A skill is a directory containing, at minimum, a `SKILL.md` file. 
**Discovery Constraint:** The `SKILL.md` file must be at the root of the skills directory (e.g., `.gemini/skills/my-skill/SKILL.md`) or at most one directory deep. Deeper nesting prevents the agent from discovering the skill.
- `SKILL.md`: Required file containing YAML frontmatter and instructions. Keep this lean (< 500 lines).
- `scripts/`: Optional. Executable code agents can run. Code should be self-contained.
- `references/`: Optional. Additional documentation loaded on demand. **Keep contents strictly one level deep** (no nested subfolders).
- `assets/`: Optional. Static resources (templates, images, data). **Keep contents strictly one level deep**.

*Note: Skills are for agents, not humans. Do not create human-centric documentation like `README.md`, `CHANGELOG.md`, or `INSTALLATION_GUIDE.md`.*

## `SKILL.md` Format
The `SKILL.md` file must start exactly with YAML frontmatter followed by Markdown content.

### Frontmatter
**Strict Constraint:** The frontmatter must be the very first thing in the file. No preceding blank lines, titles, or whitespace. The `name` and `description` fields are strictly required for discovery.

| Field | Required | Constraints |
| --- | --- | --- |
| `name` | Yes | 1-64 chars. Lowercase letters (`a-z`), numbers, and hyphens (`-`) only. Must match parent directory name. Consider **gerund form** (verb + -ing). |
| `description` | Yes | 1-1024 chars. Describes what the skill does and when to use it (trigger conditions). |
| `compatibility` | No | Max 500 chars. For specific environment requirements. |
| `paths` | No | **(Cursor only)** Glob patterns that scope the skill to matching files. |
| `disable-model-invocation` | No | **(Cursor only)** Boolean. If `true`, prevents automatic application; acts as a slash command. |

### Body Content
The entire `SKILL.md` is loaded upon activation. Include step-by-step instructions, examples, and edge cases.

## Progressive Disclosure Architecture
Skills manage agent context via a three-level system:
1. **Discovery (Metadata):** Agents load only `name` and `description` to decide if the skill is relevant.
2. **Activation (Instructions):** If relevant, the agent reads the `SKILL.md` body.
3. **Execution (Resources):** The agent follows instructions to read `references/` or execute `scripts/` only when needed.

## File References
When referencing other files (e.g., `[reference](references/REF.md)`), always use relative paths from the skill root. Use forward slashes (`/`). Keep references one level deep.
**Critical Gotcha:** Do NOT use `@` links (e.g., `@references/REF.md`) in agent environments like Cursor or Claude that support them. The `@` syntax force-loads files immediately into context upon discovery, destroying the benefits of progressive disclosure and burning context limits before the file is even needed. Use standard markdown links instead.
