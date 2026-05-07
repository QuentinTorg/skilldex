# Extension Architectures

Extension and plugin architectures expand an agent's capabilities by adding custom tools, context, sub-agents, and specialized skills. They are typically packaged into shareable units.
*Note: Gemini uses the term "extensions". Codex, Cursor, Claude, and OpenCode use "plugins".*

## Universal Concepts
- **Manifest Files:** Configuration files (e.g., `gemini-extension.json`, `plugin.json`) defining metadata, permissions, and entry points.
- **MCP Servers:** Extensions often host Model Context Protocol servers to expose new tools.
- **Context Injection:** Persistent system instructions (`GEMINI.md`) loaded automatically.
- **Agent Skills:** Bundled workflows dynamically activated. When managing multiple independent skills within an extension or workspace, the industry consensus strongly favors a **Monorepo** architecture (packaging all skills into a single extension repository) over a Polyrepo approach to prevent context fragmentation.
- **Packaging:** Distributed via Git repositories or custom archives with semantic versioning.

## Gemini CLI Extensions (Primary Focus)
Gemini CLI extensions package prompts, MCP servers, commands, and skills.
- **Manifest (`gemini-extension.json`):** Defines tools, settings, themes, and tool exclusions (`excludeTools`) for security.
- **Structure:**
  - `skills/`: Agent skills (e.g., `skills/security-audit/SKILL.md`).
  - `commands/`: Custom user commands.
  - `policies/`: Policy Engine rules for tier 2 execution.
- **Management:** Commands like `gemini extensions install`, `link` (for local dev), `disable`, and `update`.

## Other Agent Implementations

### Codex Plugins
- **Structure:** Uses `.codex-plugin/plugin.json`.
- **Distribution:** Distributed via JSON catalogs (marketplaces), installed to `~/.codex/plugins/cache/`.

### Claude Code Plugins
- **Structure:** `.claude-plugin/plugin.json`. Skills are automatically namespaced (`/plugin-name:skill-name`).
- **Capabilities:** Can include background monitors (`monitors/`) and custom MCP/LSP servers.

### OpenCode Plugins
- **Structure:** OpenCode plugins are JavaScript/TypeScript modules exporting an initialization function rather than declarative files.
- **Features:** Subscribe to events, inject `.env` variables, and define custom tools via the `tool()` function. Automatically installs npm dependencies.
