# Cursor Agent Skills [DISTILLED]

**Summary:** Details the specific implementation of Agent Skills in the Cursor IDE, including discovery paths (project, global, compatibility), implicit nested directory scoping, Cursor-specific `SKILL.md` frontmatter keys (`paths`, `disable-model-invocation`), and built-in migration tools for legacy rules. [See: ## Skill Locations and Discovery, ## SKILL.md Frontmatter Extensions]

**Source:** https://cursor.com/docs/skills

# Cursor Agent Skills Documentation

This document outlines how the open Agent Skills standard is specifically implemented and extended within the Cursor IDE environment.

## Skill Locations and Discovery
Cursor automatically discovers and surfaces skills based on context or explicit `/` commands.
- **Project-level:** `.cursor/skills/`, `.agents/skills/`
- **Global-level:** `~/.cursor/skills/`, `~/.agents/skills/`
- **Compatibility Paths:** Cursor also reads from `.claude/skills/` and `.codex/skills/`.

## Directory Scoping
Skills in nested directories are automatically scoped to those directories. For example, a skill located at `apps/web/.cursor/skills/deploy-web/SKILL.md` is only surfaced when the agent works with files under `apps/web/`.

## SKILL.md Frontmatter Extensions
Cursor supports the standard `name` and `description`, along with specific extensions:
- `paths`: Glob patterns (comma-separated string or list) that scope the skill to matching files. It replaces the legacy `globs` field.
- `disable-model-invocation`: A boolean. When set to `true`, the skill behaves like a traditional slash command and is only included in context when explicitly invoked via `/skill-name` in chat, preventing automatic application.

## Viewing and Installing Skills
- **Viewing:** Discovered skills can be viewed in **Cursor Settings → Rules** under the "Agent Decides" section.
- **GitHub Import:** Skills can be imported directly from GitHub repositories via **Cursor Settings → Rules → Add Rule → Remote Rule (Github)**.

## Migrating Legacy Rules
Cursor includes a built-in `/migrate-to-skills` command in Agent chat to help convert existing dynamic rules (rules with `alwaysApply: false` and no globs) and workspace/user slash commands to skills. Slash commands are converted to skills with `disable-model-invocation: true`.