# Using Scripts in Agent Skills

Skills can instruct agents to run shell commands and bundle reusable scripts. This enhances capability by moving complex logic into isolated, testable executable files within a `scripts/` directory ([Source](../parsed/imports/agentskills.io_using_scripts_in_skills.md), [Source](../parsed/imports/claud_skills_best_practices.md)).

## Execution Models
1. **One-off Commands:** Executed directly in `SKILL.md` when an existing package suffices. Leverage ecosystem tools that auto-resolve dependencies.
    - Examples: `uvx`/`pipx` (Python), `npx`/`bunx` (Node.js/Bun), `deno run`, `go run`.
    - **Best Practices:** Pin versions for reproducibility, state runtime prerequisites in `SKILL.md` (via `compatibility` frontmatter), and move complex commands into dedicated scripts. Don't assume packages are available—provide install instructions if necessary.
2. **Bundled Scripts:** Stored in the `scripts/` directory within the skill.
    - **Pathing:** Always use relative paths from the skill directory root in `SKILL.md` instructions and support files. Always use **forward slashes** (Unix-style), even on Windows.
    - **Visibility:** List available scripts explicitly in `SKILL.md` so the agent discovers them. Make it clear whether the agent should *execute* the script or *read* it as reference.
3. **Self-Contained Scripts:** Scripts that declare their dependencies inline, running with a single command without separate installation steps or manifests.
    - Python: PEP 723 inline metadata (e.g., executed with `uv run`).
    - Deno: `npm:` or `jsr:` specifiers in imports.
    - Bun: Auto-installs missing packages at runtime.
    - Ruby: `bundler/inline`.

## Designing Scripts for Agentic Use
Design script interfaces to accommodate non-human agent behaviors:
- **Solve, Don't Punt:** Handle errors explicitly in scripts (e.g., catch `FileNotFoundError` and create a default file) rather than failing and relying on the agent to fix it. Avoid "voodoo constants" (magic numbers); justify parameter choices.
- **Agentic Ergonomics:** Ensure scripts output LLM-friendly `stdout`. Suppress verbose tracebacks and provide clear, concise success/failure messages ([Source](../parsed/imports/gemini_skills_best_practices.md)).
- **No Interactive Prompts:** Agents run in non-interactive shells and will hang on prompts. All input must be accepted via flags, environment variables, or `stdin`.
- **Helpful `--help` Output:** Document usage, descriptions, options, and examples clearly. This is how the agent learns the interface.
- **Actionable Error Messages:** Clearly explain what failed, what was expected, and how the agent can correct the input.
- **Structured Output:** Prefer formats like JSON, CSV, or TSV. Send structured data to `stdout` and all diagnostics/warnings to `stderr`.
- **Idempotency:** Design operations to be safely retriable ("create if not exists").
- **Input Constraints:** Reject ambiguous inputs with explicit errors; use closed sets/enums where possible.
- **Dry-run Support:** Include `--dry-run` flags for destructive or stateful operations.
- **Meaningful Exit Codes:** Use and document distinct codes for different types of failures.
- **Predictable Output Size:** Prevent context truncation by keeping output concise. For large data, default to summaries or require an `--output` flag (file or `-` for stdout), or support pagination (`--offset`).
- **MCP Tools:** If referencing Model Context Protocol (MCP) tools, always use fully qualified tool names (e.g., `ServerName:tool_name`) to prevent "tool not found" errors.

## Advanced Patterns
- **Visual Analysis:** If inputs can be rendered as images (e.g., PDFs to images), create a script to do so and have the agent analyze the images using its vision capabilities.
- **Verifiable Intermediate Outputs:** Implement the plan-validate-execute pattern by having the agent generate an intermediate plan file (like `changes.json`), which is then verified by a separate validation script before applying the final changes.