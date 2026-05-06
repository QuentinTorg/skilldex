# Agent Skill Environments and Constraints

Agent skills run in varying environments depending on the platform, agent, and surface. It is important to understand the constraints of the runtime environment when developing and deploying skills.

## Common Constraints

### Network Access
Network access varies significantly across environments:
- **Full Access**: Some environments (like local CLI tools) provide the skill with the same network access as the host machine.
- **Partial/No Access**: Cloud APIs or web interfaces may restrict or completely block outbound network requests. Skills should not assume external API access is always available.

### Package Installation
- **Runtime Installation**: Some environments allow skills to dynamically install packages during execution. When doing so, prefer local installation to avoid polluting the host's global environment.
- **Pre-configured Only**: Many locked-down environments (like secure cloud containers) prohibit runtime package installation. Skills running here must rely exclusively on pre-installed dependencies.

### Synchronization and Sharing
- **No Automatic Sync**: Custom skills typically do not sync automatically across different surfaces (e.g., between a web UI, an API, and a local CLI tool). You generally need to manage and upload skills separately for each surface.
- **Sharing Scopes**: The visibility of a skill depends on the platform. It might be limited to an individual user, shared workspace-wide, or local to a specific project directory.

## Agent-Specific Details

### Gemini CLI
- **Skill Discovery**: Discovers skills from built-in skills, extensions, user directories (`~/.gemini/skills/` or `~/.agents/skills/`), and workspace directories (`.gemini/skills/` or `.agents/skills/`). The `.agents/skills/` alias takes precedence within a tier.
- **Activation Mechanism**: Gemini CLI injects skill names and descriptions into the system prompt. When a task matches, it calls the `activate_skill` tool, which prompts for user consent to inject `SKILL.md` and grants directory access.
- **Management**: Skills can be managed interactively via `/skills` slash commands (e.g., `list`, `link`, `disable`, `enable`, `reload`) or terminal commands (e.g., `gemini skills list`, `install`, `uninstall`).

**Source:** [gemini_skills.md](../parsed/imports/gemini_skills.md)

### Cursor
- **Skill Locations and Discovery**: Discovers skills based on context or explicit `/` commands. Looks in project-level (`.cursor/skills/`, `.agents/skills/`), global-level (`~/.cursor/skills/`, `~/.agents/skills/`), and compatibility paths (`.claude/skills/`, `.codex/skills/`).
- **Directory Scoping**: Implicit nested scoping. Skills in nested directories are automatically scoped to those directories (e.g., a skill in `apps/web/.cursor/skills/` is only surfaced when the agent works with files under `apps/web/`).
- **Migration Tools**: Cursor provides a `/migrate-to-skills` command in Agent chat to convert existing dynamic rules and slash commands into skills. Slash commands are converted with `disable-model-invocation: true`.

**Source:** [cursor_skills_docs.md](../parsed/imports/cursor_skills_docs.md)

### Cowork
- **Display Constraints**: Cowork environments typically lack a browser or display. When generating HTML reports or viewer tools, configure scripts to write standalone HTML files (e.g., using `--static` flags) rather than launching a server. The user can then open the file locally.
- **Feedback Collection**: Interactive review loops must rely on downloading/uploading JSON feedback files rather than direct browser interaction.

**Source:** [anthropic_skill_creator_SKILL.md](../parsed/imports/anthropic_skill_creator_SKILL.md)

### Claude
- **Claude API**: Requires specific beta headers for code-execution (`code-execution-2025-08-25`), skills functionality (`skills-2025-10-02`), and files (`files-api-2025-04-14`). The environment has no network access and no runtime package installation. Skills are workspace-wide.
- **Claude Code**: Supports custom skills via filesystem discovery (e.g., `~/.claude/skills/` or `.claude/skills/`). It has full network access, but global package installation is discouraged.
- **Claude.ai**: Custom skills are per-user (no workspace-wide sharing). Varying network access depending on settings.

**Source:** [claude_skills_overview.md](../parsed/imports/claude_skills_overview.md)

### OpenCode
- **Skill Discovery**: Discovers skills by walking up from the current directory to the git worktree, and from global config directories.
  - Project paths: `.opencode/skills/`, `.claude/skills/`, `.agents/skills/`.
  - Global paths: `~/.config/opencode/skills/`, `~/.claude/skills/`, `~/.agents/skills/`.
- **Activation Mechanism**: Available skills are dynamically listed in the `<available_skills>` section of the native `skill` tool description. Agents load a skill's full content on-demand by calling the tool (e.g., `skill({ name: "skill-name" })`).

**Source:** [opencode_skills.md](../parsed/imports/opencode_skills.md)
