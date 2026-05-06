# Monorepo vs. Polyrepo for AI Agents [DISTILLED]

**Summary:** This document analyzes the trade-offs between Monorepo and Polyrepo architectures for AI agent development, concluding that monorepos provide superior "Unified Context" and allow for atomic cross-project changes, despite requiring more intelligent CI/CD infrastructure. Distilled into [Skill Packaging and Distribution](../topics/skill-packaging-and-distribution.md).

**Source:** Web Search Synthesis (See References below)

The relationship between AI agents and repository architecture (monorepo vs. polyrepo) is defined by a fundamental trade-off between **contextual visibility** and **infrastructure complexity**.

### 1. The "Context Tax" and Repository Choice
AI agents perform best when they have a unified view of the system. The choice of architecture significantly impacts their effectiveness:

*   **Monorepos (The AI Preference):**
    *   **Unified Context:** Agents can trace logic across the entire stack (e.g., from a frontend button click to a backend database update) in a single session.
    *   **Atomic Changes:** Agents can perform cross-project refactors in a single commit, ensuring the system never enters a broken state.
    *   **Dependency Awareness:** Tools like Nx or Bazel provide agents with a "map" (project graph) of the codebase, allowing them to understand the blast radius of a change without reading every file.
*   **Polyrepos (The AI Blind Spot):**
    *   **Fragmented Context:** Agents are often "blind" to cross-project impacts. A change in a shared library repository might break a consumer in another repository that the agent cannot see.
    *   **Coordination Overhead:** Implementing a single feature across multiple repos requires the agent (or human) to manage multiple PRs, versioning, and deployment sequencing, which is highly error-prone for current AI.
    *   **The "Memento Problem":** Without extra tooling, agents lose context when switching between repositories, forcing them to "re-learn" the environment each time.

### 2. Managing Context in Large Codebases
As monorepos grow, they can exceed even the largest context windows (e.g., 200k+ tokens). Effective agents use **Context Engineering** rather than "sending everything":

*   **Nested Instructions (`AGENTS.md` / `CLAUDE.md`):** Large monorepos use hierarchical instruction files. An agent reads the root file for global rules and nested files for project-specific context (e.g., `/apps/web/AGENTS.md`).
*   **Just-in-Time (JIT) Context:** Instead of loading the whole repo, agents use tools (grep, semantic search, file listing) to dynamically pull in only the relevant "high-signal" tokens for the current task.
*   **Sub-Agent Delegation:** Complex tasks are broken down. A "researcher" agent might map the dependencies in a monorepo and pass a concise summary to an "implementer" agent, keeping the main context window lean.

### 3. The New Trade-off: AI vs. DevOps
While monorepos make AI agents more powerful, they shift the burden to infrastructure:
*   **AI Gain:** Agents work 3x–4x faster in monorepos because they don't have to wait for cross-repo CI or manual coordination.
*   **DevOps Pain:** Monorepos require "intelligent" CI/CD that can calculate the exact blast radius of a change to avoid running 45-minute test suites for minor edits.

### References
*   [Monorepo Tools Overview](https://monorepo.tools/ai)
*   [AI Agents in Monorepos (Medium)](https://medium.com/@arohitu/monorepo-vs-polyrepo-for-multi-stack-vibe-coding-a-developers-decision-framework-06d535fb110e)
*   [Faros AI Code Quality](https://www.faros.ai/blog/monorepo-vs-polyrepo-benchmark-data)
*   [Augment Code CI/CD Verifier](https://www.augmentcode.com/learn/monorepo-vs-polyrepo-ai-s-new-rules-for-repo-architecture)
*   [Nx Dev AI Coordination](https://nx.dev/blog/the-missing-multiplier-for-ai-agent-productivity)