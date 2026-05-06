# Extension Architectures

Extension and plugin architectures are mechanisms designed to expand an agent's or application's behavior by adding custom tools, commands, context, and specialized skills. They are typically packaged into shareable, installable units.

**Note on Terminology:** "Plugin" is the standard industry terminology used by platforms like Codex, Cursor, Claude Code, and OpenCode. Gemini uniquely uses the term "extensions" for this concept.

## Universal Concepts of Extending Agent Behavior

*   **Manifest Files:** A configuration file (e.g., `manifest.json`, `gemini-extension.json`, `plugin.json`) that defines the extension's metadata (name, version, description), required permissions, tool restrictions, and entry points for its features.
*   **Bundling MCP Servers:** Extensions often host Model Context Protocol (MCP) servers. The extension defines how to start the server (command, arguments, working directory), which in turn exposes new tools and data sources to the agent.
*   **Custom Commands:** User-defined shortcuts or macros that execute pre-defined prompts, scripts, or shell commands to automate repetitive tasks.
*   **Context Injection:** Providing persistent system instructions or context files (e.g., `GEMINI.md`) that are automatically loaded into the agent's context window.
*   **Lifecycle Hooks:** Intercepting and customizing behavior at specific events (e.g., before/after a tool call) to automate actions, validate arguments, or log activity.
*   **Specialized Agent Skills:** Bundling specific workflows and instructions (e.g., [Agent Skills](../topics/agent-skills-overview.md)) that the agent can dynamically activate when relevant tasks are identified, preserving the main context window.
*   **Sub-agents:** Providing task-specific sub-agents that users or the main agent can delegate tasks to.
*   **Settings & Configuration:** Mechanisms for users to securely provide environment variables, API keys, or user preferences. Sensitive data should be handled securely (e.g., via the system keychain).
*   **Security & Permissions:** Extensions should follow the principle of least privilege, requesting minimal required permissions, restricting dangerous tools, and validating inputs to prevent arbitrary code execution.
*   **Packaging and Distribution:** Extensions are commonly distributed via Git repositories or custom archives (e.g., GitHub Releases). Distribution often includes semantic versioning (SemVer) and release channels (stable, dev, preview).

## Gemini CLI Extensions

Gemini CLI extensions package prompts, MCP servers, custom commands, themes, hooks, sub-agents, and agent skills into a familiar and user-friendly format.

### Manifest (`gemini-extension.json`)
The manifest file dictates how Gemini CLI loads and uses the extension.
*   **Fields:** Includes `name`, `version`, `description`, `mcpServers`, `contextFileName`, `excludeTools`, `themes`, `settings`, `plan`, and `migratedTo` (for repository migration).
*   **Variables:** Supports variable substitution like `${extensionPath}` and `${workspacePath}`.
*   **Conflict Resolution:** Extension commands have the lowest precedence and are dot-prefixed (`/extension.command`) if they conflict with user or project commands.

### Extension Structure
While simple extensions can contain just a few files, a typical structure includes:
*   `gemini-extension.json`: The manifest file.
*   `GEMINI.md`: Default context file containing persistent system instructions.
*   `commands/`: Directory containing `.toml` files that define custom user commands (e.g., `commands/fs/grep-code.toml` becomes `/fs:grep-code`).
*   `skills/`: Directory containing agent skills (e.g., `skills/security-audit/SKILL.md`).
*   `hooks/`: Contains `hooks.json` to define lifecycle hooks.
*   `policies/`: Contains `.toml` files for Policy Engine rules. These run in tier 2 (extension tier) and can restrict behavior but cannot bypass security measures (e.g., `allow` or `yolo` decisions are ignored).
*   `agents/`: Contains sub-agent definitions (`.md` files).

### CLI Management Commands
Extensions are managed using the `gemini extensions` commands:
*   `install <source>`: Installs from a GitHub URL or local path.
*   `uninstall <name>`: Uninstalls the extension.
*   `disable <name>` / `enable <name>`: Toggles the extension's active state.
*   `update <name>`: Updates the extension to the latest version.
*   `link <path>`: Creates a symbolic link for local development, allowing immediate testing of changes.
*   `new <path> [template]`: Bootstraps a new extension from a template (e.g., `mcp-server`).
*   `config <name> [setting]`: Updates an extension's settings.

### Security
*   **Tool Exclusions:** The `excludeTools` field in the manifest can block specific tools (e.g., `["run_shell_command(rm -rf *)"]`).
*   **Sensitive Settings:** Setting `"sensitive": true` securely stores values in the system keychain and obfuscates them in the UI.

## Codex Plugins

Codex uses the term "plugins" and packages them with a specific directory structure and manifest.

### Structure
*   **Manifest:** `.codex-plugin/plugin.json` containing metadata (`name`, `version`, `description`, `author`, `interface` for UI presentation) and pointers to components.
*   **Components:** `skills/` for agent skills, `.app.json` for app integrations, `.mcp.json` for MCP servers, `hooks/hooks.json` for lifecycle events, and `assets/` for logos/icons.

### Distribution and Management
*   **Marketplaces:** Plugins are distributed via JSON catalogs (marketplaces). Can be scoped to a repository (`$REPO_ROOT/.agents/plugins/marketplace.json` or `$REPO_ROOT/.claude-plugin/marketplace.json`) or globally (`~/.agents/plugins/marketplace.json`).
*   **Installation:** Plugins are installed into a local cache directory (`~/.codex/plugins/cache/`). On/off states are stored in `~/.codex/config.toml`.
*   **CLI Tools:** `codex plugin marketplace add <source>`, `codex plugin marketplace upgrade`. Includes a `$plugin-creator` skill to scaffold plugins.
*   **Source:** [codex_plugins.md](../parsed/imports/codex_plugins.md)

## Cursor Plugins

*(Documentation for Cursor plugins is pending/limited in the current source).*

*   **Source:** [cursor_plugins.md](../parsed/imports/cursor_plugins.md)

## Claude Code Plugins

Claude Code allows for both standalone configuration and packaged plugins.

### Structure
*   **Manifest:** `.claude-plugin/plugin.json` dictates metadata.
*   **Namespacing:** Skills are automatically namespaced (e.g., `/plugin-name:skill-name`).
*   **Components:**
    *   `skills/`: Contains agent skills (each with a `SKILL.md`).
    *   `agents/`: Custom agents.
    *   `hooks/hooks.json`: Lifecycle event hooks.
    *   `monitors/monitors.json`: Background monitors (e.g., `tail -F error.log`).
    *   `.mcp.json` and `.lsp.json`: Configurations for MCP and Language Server Protocol servers.
    *   `bin/`: Executables added to the Bash tool's `PATH`.
    *   `settings.json`: Default settings (e.g., setting a default agent).

### Distribution and Management
*   **Local vs Plugin:** Standalone configs live in `.claude/`. Plugins use `.claude-plugin/plugin.json`.
*   **CLI Tools:** Test locally with `claude --plugin-dir ./my-plugin`. Install via `/plugin install`.
*   **Distribution:** Can be shared via an official Anthropic marketplace.
*   **Source:** [claude_code_plugins.md](../parsed/imports/claude_code_plugins.md)

## OpenCode Plugins

OpenCode plugins are JavaScript or TypeScript modules, differing from the declarative file-based plugins in other systems.

### Structure
*   **Module-Based:** A plugin is a module exporting an initialization function (e.g., `export const MyPlugin = async (ctx) => { ... }`).
*   **Context:** The function receives context (`project`, `directory`, `worktree`, `client`, `$`) and returns an object containing event hooks.
*   **Events:** Plugins subscribe to events like `command.executed`, `file.edited`, `tool.execute.before`, `session.idle`, etc.
*   **Capabilities:** Can define custom tools (`tool()` function), inject environment variables, provide `.env` protection, execute shell commands, and modify compaction context.

### Distribution and Management
*   **Dependencies:** Can declare npm dependencies using a `package.json` in the plugin configuration directory. Bun automatically installs them.
*   **Locations:** Loaded from project-level (`.opencode/plugins/`), global-level (`~/.config/opencode/plugins/`), or from npm packages defined in `opencode.json`.
*   **Source:** [opencode_plugins.md](../parsed/imports/opencode_plugins.md)

### References
*   [Managing Extensions](../parsed/imports/gemini_extensions_manage.md)
*   [Writing Extensions](../parsed/imports/gemini_extensions_writing.md)
*   [Extension Best Practices](../parsed/imports/gemini_extensions_best_practices.md)
*   [Releasing Extensions](../parsed/imports/gemini_extensions_releasing.md)
*   [Extension Reference](../parsed/imports/gemini_extensions_reference.md)
