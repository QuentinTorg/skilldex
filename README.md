<p align="center">
  <img src="assets/skilldex_banner.png" alt="SkillDex Banner" />
</p>

A public collection of agent skills for daily use, along with a dedicated workspace and framework for building, refining, and tuning highly effective skills.

**What are Agent Skills?**
Agent skills are a lightweight, open format for extending AI CLI agents (like Gemini, Cursor, and Claude Code) with specialized knowledge and workflows. Under the hood, they act as advanced, file-based prompts (`SKILL.md`) that the agent can discover and autonomously trigger whenever it recognizes that the skill applies to your current task. This ensures the agent consistently follows your specific conventions and best practices without needing to be manually instructed every time.

## Available Skills

- **[building-skills](./skills/building-skills/)**: Mentors and guides users in creating, critiquing, reviewing, and improving agent skills using a rigorous, 6-step granular workflow.
- **[reviewing-code](./skills/reviewing-code/)**: Use this skill whenever you need to review a Pull Request, branch, or perform a deep technical inspection of code. It guides the agent through a methodical, interactive review process.
- **[writing-specifications](./skills/writing-specifications/)**: Teach the agent to act as an architectural sounding board and expert technical writer to brainstorm, structure, and iteratively draft high-quality design documents and specifications from scratch or messy notes.

## How to Use This Repository

This repository serves a dual purpose:
1. **A Library of Skills:** Browse the `skills/` directory to find ready-to-use agent skills you can install in your own environments.
2. **A Development Workspace:** A sandbox to create new skills and improve existing ones, backed by a comprehensive `epiphany_knowledge/` database containing best practices, architectural patterns, and evaluation strategies.

## Installation & Live Tuning

You can install skills from this repository to use across a variety of compatible AI agent providers. Most agents support copying the skill directory into their specific configuration folders.

When you are developing or tuning a skill within this repository, you'll want to test it locally without constantly re-installing it. You can **link** or symlink the skill so that any modifications you make are immediately reflected in your agent sessions.

<details>
<summary><b>Gemini CLI</b></summary>

### Installing Skills
**Install a Specific Skill:**
You can use the CLI to install the skill by path:
```bash
gemini skills install ./skills/<skill-name>
```
*Note: You can optionally add `--scope workspace` to install it only for your current project rather than globally.*

**Install All Skills:**
Manually copy the contents of the `skills/` directory into your global `~/.gemini/skills/` directory.

### Linking for Live Tuning
**From your terminal:**
```bash
gemini skills link ./skills/<skill-name>
```

**From within an active Gemini CLI session:**
```text
/skills link ./skills/<skill-name>
```
</details>

<details>
<summary><b>Cursor</b></summary>

### Installing Skills
**Install a Specific Skill:**
Copy the skill's folder from the `skills/` directory into your project's `.cursor/skills/` or `.agents/skills/` directory, or your global `~/.cursor/skills/` directory.

**Install All Skills:**
Manually copy the contents of the `skills/` directory into your global or project-specific `.cursor/skills/` directory.

### Linking for Live Tuning
To test skills live in Cursor, you can create a symbolic link (symlink) from your project's `.cursor/skills/` directory back to the specific skill directory within your SkillDex workspace.
```bash
ln -s /path/to/skilldex/skills/<skill-name> .cursor/skills/<skill-name>
```
</details>

<details>
<summary><b>Claude Code</b></summary>

### Installing Skills
**Install a Specific Skill:**
Copy the skill's folder from the `skills/` directory into your project's `.claude/skills/` or `.agents/skills/` directory.

**Install All Skills:**
Manually copy the contents of the `skills/` directory into your project-specific `.claude/skills/` directory.

### Linking for Live Tuning
To test skills live in Claude Code, you can create a symbolic link (symlink) from your project's `.claude/skills/` directory back to the specific skill directory within your SkillDex workspace.
```bash
ln -s /path/to/skilldex/skills/<skill-name> .claude/skills/<skill-name>
```
</details>

<details>
<summary><b>Codex</b></summary>

### Installing Skills
**Install a Specific Skill:**
Copy the skill's folder from the `skills/` directory into your Codex skills directory (e.g., `~/.codex/skills/`, `.codex/skills/`, or `.agents/skills/`).

**Install All Skills:**
Manually copy the contents of the `skills/` directory into your global or project-specific `.codex/skills/` directory.

### Linking for Live Tuning
To test skills live in Codex, you can create a symbolic link (symlink) from your project's `.codex/skills/` directory back to the specific skill directory within your SkillDex workspace.
```bash
ln -s /path/to/skilldex/skills/<skill-name> .codex/skills/<skill-name>
```
</details>

## Developing Your Own Skills

SkillDex is designed to be the perfect place to build and refine your skills. It includes a dedicated **[building-skills](./skills/building-skills/)** skill and an embedded knowledge base (`epiphany_knowledge/`) that the AI agent uses to mentor and guide you.

To start developing:
1. Open this repository in your terminal.
2. Start a session with your AI agent (e.g., Gemini CLI).
3. If not already active, trigger the mentor skill: *"Activate the building-skills skill."*
4. The agent will actively guide you through a rigorous, **6-step granular workflow** (documented in the skill and `AGENTS.md`), leveraging local best practice references to ensure your skill is robust, well-described, and properly structured.
