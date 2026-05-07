# Skill Scripts and Environments

Skills can instruct agents to run shell commands and bundle reusable scripts. This enhances capability by moving complex logic into isolated, testable executable files within a `scripts/` directory.

## Execution Models
1. **One-off Commands:** Leverage ecosystem tools (e.g., `uvx`, `npx`) directly in `SKILL.md`. State runtime prerequisites in the `compatibility` frontmatter.
2. **Bundled Scripts:** Store custom logic in `scripts/`. Always use **relative paths** and **forward slashes** from the skill root. List available scripts explicitly in `SKILL.md`.
3. **Self-Contained Scripts:** Prefer scripts that declare their dependencies inline (e.g., PEP 723 for Python, Deno URL imports) to avoid installation steps.

## Designing Scripts for Agentic Ergonomics
Scripts must be designed to accommodate non-human agent behaviors:
- **Solve, Don't Punt:** Handle errors explicitly (e.g., create missing default files) rather than throwing raw errors for the agent to fix.
- **LLM-Friendly Output:** Suppress verbose tracebacks. Provide concise success/failure messages.
- **No Interactive Prompts:** Accept all input via flags, environment variables, or `stdin`. Agents will hang on interactive prompts.
- **Helpful `--help`:** Clearly document usage; this is how agents learn the interface.
- **Actionable Error Messages:** Explain what failed, what was expected, and how to correct the input.
- **Structured Output:** Prefer JSON, CSV, or TSV for `stdout`. Send diagnostics to `stderr`.
- **Predictable Size:** Prevent context truncation. Use pagination (`--offset`) or file output for large data.

## Environmental Constraints by Agent
Skill capabilities vary based on the host agent environment:

### General Constraints & Security
- **Network:** Cloud APIs may block outbound requests. Do not assume external network access.
- **Packages:** Locked-down environments prohibit runtime package installation. Rely on pre-installed dependencies or self-contained scripts.
- **Security:** Never hardcode secrets in scripts or `SKILL.md`. Be aware that skills have tool/filesystem access, so untrusted external dependencies or dynamically fetched content can introduce prompt injection or malicious code.

### Agent-Specific Behaviors
- **Gemini CLI (Primary Focus):** 
  - Discovery: `~/.gemini/skills/`, `.gemini/skills/`, `.agents/skills/`.
  - Activation & Security: Uses the `activate_skill` tool. It enforces a consent model where the user must approve the activation and grant directory access every time a skill is triggered.
- **Cursor:**
  - Discovery: Scopes skills implicitly based on directory nesting.
  - Features: Supports glob `paths` in frontmatter and `disable-model-invocation` (acts as slash command).
- **Claude Code:**
  - Has full network access but global package installation is discouraged.
  - **MCP Caveat:** If a skill uses MCP tools, always use fully qualified tool names (e.g., `BigQuery_toolName`) to avoid "tool not found" errors when multiple servers are available.
- **OpenCode:**
  - Discovers by walking up the git worktree. Activates via a specific `skill({ name: "..." })` tool.
