# Agent Skill Security

Agent skills provide powerful capabilities by supplying instructions, resources, and executable code to agents. Because they run in an environment with tool and filesystem access, they introduce security considerations that must be managed.

## Core Risks
- **Tool Misuse**: Malicious or poorly designed skills can invoke tools (like file operations, bash commands, or code execution) in harmful ways.
- **Data Exposure**: Skills with access to sensitive data could be designed to leak information to external systems or exfiltrate data.
- **External Dependencies**: Skills that fetch data from external URLs are particularly risky. Fetched content could contain malicious prompt injections or instructions, and external dependencies can be compromised over time.

## Environment-Specific Security
- **Gemini CLI Consent Model:**
  - **Installation Consent:** When installing from a remote URL, users must confirm the source to protect the environment.
  - **Activation Consent:** Every time a skill is triggered during a session, the agent must ask for permission to activate it and gain access to its resources ([Source](../parsed/imports/gemini_using_agent_skills.md)).
- **OpenCode Permissions:**
  - **Granular Access:** Controlled via `opencode.json` using pattern-based rules mapping to `allow`, `deny`, or `ask` states.
  - **Agent Overrides:** Permissions can be set globally, overridden per-agent in `opencode.json`, or defined directly in custom agent frontmatter.
  - **Tool Disablement:** The `skill` tool can be completely disabled for specific agents, which entirely hides the `<available_skills>` list from their context ([Source](../parsed/imports/opencode_skills.md)).

## Best Practices
- **Avoid Hardcoded Secrets:** Never include API keys, passwords, or sensitive credentials in your skill's scripts or documentation ([Source](../parsed/imports/gemini_skills_best_practices.md)).
- **Audit Thoroughly:** Always review all files bundled in a skill before use, including `SKILL.md`, scripts, and resources. Look for unusual network calls, file access patterns, or operations that do not match the skill's stated purpose. Review third-party skills carefully before installing them from an untrusted source ([Source](../parsed/imports/gemini_skills_best_practices.md)).
- **Limit Scope:** Design skills to be as focused as possible to minimize the potential impact of errors ([Source](../parsed/imports/gemini_skills_best_practices.md)).
- **Treat Like Software:** Only use skills from trusted sources. Treat adding a new skill to an agent the same way you would treat installing new software on your computer.
- **Exercise Caution in Production:** Be especially careful when integrating skills into systems with access to sensitive data or critical operations.

**Source:** [claude_skills_overview.md](../parsed/imports/claude_skills_overview.md)
