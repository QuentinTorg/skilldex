# Agent Skills Overview

Agent Skills are a lightweight, open format for extending AI agent capabilities with specialized knowledge and workflows ([Source](../parsed/imports/agentskills.io_what_are_skills.md)).

## Structure & Configuration
For detailed information on how skills are structured (including `SKILL.md` frontmatter, optional directories like `scripts/`, and progressive disclosure mechanisms involving metadata, instructions, and resources), see [Skill Specification](../topics/skill-specification.md).

## Environments & Security
Skills run in diverse environments that carry different constraints (e.g., network access, package installation). Because they can execute code, they also pose security risks if they fetch untrusted data or execute malicious commands.
- For details on environment constraints and platform-specific implementations (e.g., Claude API vs Claude Code), see [Skill Environments and Constraints](../topics/skill-environments.md).
- For best practices on securing skills and auditing external dependencies, see [Skill Security](../topics/skill-security.md).

## Characteristics
- **Self-documenting**: Easy to read and understand.
- **Extensible**: Can include simple text or complex executable code.
- **Portable**: File-based format makes them easy to edit, version, and share.
- **Progressive Disclosure**: Agents typically only load skill metadata (name and description) initially. Detailed instructions and resources are loaded only when the skill is explicitly activated, saving context tokens ([Source](../parsed/imports/gemini_skills.md)).

## When to Build a Skill
- **When You Need One:** When the agent would get a task wrong without special context, or when there's an inconsistency or specific taste/style you need applied consistently ([Source](../parsed/imports/perplexity_agent_skills.md)).
- **When You Don't:** If the model already knows how to do it (e.g., standard git commands), if it just recapitulates the global system prompt, or if the underlying tool changes faster than you can maintain the skill.
- **The Skill Tax:** Every skill carries a context cost (its description must be loaded into the index for every session). If a sentence in a skill doesn't change the agent's behavior for the better, it shouldn't be there. A good skill is as short as it can be.

## Why Use Agent Skills?
Skills provide agents with access to procedural knowledge and specific context (company, team, user) that they lack out-of-the-box, loadable on demand. 
- **Build once, run anywhere:** Deploy across compatible agents.
- **Capture knowledge:** Package organizational knowledge into portable, version-controlled formats.
- **Enable new abilities:** Domain expertise, repeatable workflows, and tool integrations (e.g., building MCP servers) ([Source](../parsed/imports/agentskills.io_overview.md)).

## Origin & Adoption
Originally developed by Anthropic and released as an open standard, Agent Skills are supported by a growing ecosystem of AI tools. Compatible agents include:
- **Gemini CLI** (Primary Target)
- **Codex**
- **Cursor**
- **Claude Code**
*(Note: See [Source](../parsed/imports/agentskills.io_overview.md) for full list of supported agents).*
