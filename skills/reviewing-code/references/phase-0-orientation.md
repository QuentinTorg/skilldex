# Phase 0: Orientation, Exploration & The Architect's Pass

This document outlines the initial calibration and exploratory steps required before diving into the rigorous checklists of the subsequent phases.

**Goal:** Establish the domain, map the blast radius, verify the *actual* intent, and perform an empirical, open-ended architectural review.

## Check 0: Domain Calibration, Intent & The Architect's Pass

**1. The Senior Mindset:** Before reading the diff line-by-line, adopt the disposition of a senior architect walking a site. Your goal in this phase is to evaluate leverage and structure, not microscopic syntax. Validate the premise before the syntax. Do not review against an ideal rewrite; review against the intent and the surrounding code.

**2. Domain Calibration & Stakes:** Explicitly identify what kind of software this is (e.g., embedded/systems, web service, library, CLI, data pipeline, mobile app). Bring the domain's native concerns (e.g., memory constraints and hardware limits for embedded, idempotent state for infrastructure, scaling and concurrency for services) to the forefront of your mind. Match your rigor to the stakes and blast radius of the change.

**3. Verify Intent:** Read the description and any linked issues to infer what the change is *for*. Ensure the code implementation actually satisfies the core requirements and acceptance criteria of the issue, not just what the PR author claims in their description.

**4. Empirical Exploration (The Architect's First Pass):** Conduct an open-ended, high-level review of the codebase. You MUST NOT rely solely on documentation or READMEs to understand the architecture. You are expected to proactively inspect the reality of the codebase: explore the project structure, read key modules, and sample neighboring files or domain logic. Trust your own eyes on the code over the blueprints. Focus on high-leverage architectural questions:
- **Does it belong?** Should this change exist here at all, or does it belong in a different layer/module? Is core logic properly separated from I/O, transport, and presentation boundaries?
- **Is it earning its complexity?** Are new abstractions, data structures, or interfaces solving a real problem today, or are they speculative "future-proofing" that erases a simpler contract?
- **Domain Logic Reality:** Apply your domain knowledge to the logic you have explored. Are there fundamental flaws in how the domain is modeled (e.g., physical geometry, protocol limits, real-time assumptions) that supersede line-by-line code safety?

Document any high-level findings, structural observations, architectural smells, or domain-logic errors discovered during this empirical exploration in your tracking document before moving to the specific checklists.