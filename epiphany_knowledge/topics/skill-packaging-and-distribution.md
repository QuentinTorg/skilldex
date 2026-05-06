# Skill Packaging and Distribution

Agent Skills can be bundled, packaged, and distributed as part of broader extensions. This allows creators to distribute a skill alongside required custom commands, context files, or MCP servers that the skill might depend on.

## Extensions as a Distribution Mechanism
Extensions provide a standardized way to package prompts, MCP servers, custom commands, themes, hooks, sub-agents, and agent skills into a single installable unit. 
- **Bundling Skills:** To include an agent skill within an extension, place the skill definition (`SKILL.md`) in a subdirectory under a `skills/` folder at the root of the extension (e.g., `skills/security-audit/SKILL.md`) ([Source](../parsed/imports/gemini_extensions_reference.md), [Source](../parsed/imports/gemini_extensions_writing.md)).
- **Auto-Discovery:** Agents (like Gemini CLI) automatically discover and load skills bundled with installed extensions. These are treated as "Extension Skills" in the discovery hierarchy ([Source](../parsed/imports/gemini_extensions_writing.md)).

## Repository Architecture: Monorepo vs. Polyrepo
When managing multiple independent skills, the industry consensus strongly favors a **Monorepo** architecture (packaging all skills into a single extension repository) over a Polyrepo approach ([Source](../parsed/imports/monorepo_vs_polyrepo_for_ai_agents.md)).
- **The Context Tax:** Polyrepos create a "blind spot" for AI agents, as they cannot easily trace logic or dependencies across repository boundaries, leading to fragmented context and higher coordination overhead.
- **Unified Context:** Monorepos allow agents to perform cross-project refactors and understand the entire system's dependencies (often aided by tools like Nx or Bazel) in a single session.
- **Scale:** As monorepos grow, agents rely on hierarchical instructions (nested `AGENTS.md` files) and Just-in-Time (JIT) context retrieval rather than loading the entire repository into the context window.

## Distribution & Release Channels *(Gemini Specific)*
*Note: The following distribution mechanisms and commands are specific to Gemini CLI extensions.*

Gemini CLI extensions can be distributed directly via Git or GitHub.

- **Git Repositories:** Users can install directly from a Git repository using `gemini extensions install <repo-url> [--ref <branch-or-tag>]`. This allows creators to manage release channels (e.g., `stable` vs `dev`) using standard Git branches ([Source](../parsed/imports/gemini_extensions_releasing.md)).
- **GitHub Releases:** Distributing via GitHub Releases offers a faster installation experience as it downloads a pre-built archive instead of cloning the repository.
  - Useful for packaging platform-specific binaries alongside skills.
  - The CLI checks for the "Latest" release on GitHub by default.
  - Ensure the `gemini-extension.json` manifest is at the root of the release archive ([Source](../parsed/imports/gemini_extensions_releasing.md)).
- **Gallery Listing:** Public extensions hosted on GitHub are automatically discovered and listed in the Gemini CLI extension gallery if the repository includes the `gemini-cli-extension` topic ([Source](../parsed/imports/gemini_extensions_releasing.md)).
- **Migrations:** If an extension changes its repository location or name, creators can use the `migratedTo` property in the `gemini-extension.json` file. The CLI will detect this during updates and automatically migrate users to the new repository and update the extension name ([Source](../parsed/imports/gemini_extensions_releasing.md)).

## Local Development *(Gemini Specific)*
To develop and test an extension containing skills without reinstalling after every change, use the `gemini extensions link <path>` command. This creates a symbolic link from the development directory to the CLI's extensions directory ([Source](../parsed/imports/gemini_extensions_writing.md), [Source](../parsed/imports/gemini_extensions_reference.md)).