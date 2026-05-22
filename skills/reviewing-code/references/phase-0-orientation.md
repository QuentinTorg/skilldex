# Phase 0: Orientation, Exploration & The Architect's Pass

This document outlines the initial calibration and exploratory steps required before diving into the rigorous checklists of the subsequent phases.

**Goal:** Establish the domain, map the blast radius, verify the *actual* intent, and perform an open-ended, high-level architectural review.

## Check 0: Domain Calibration, Intent & The Architect's Pass

**1. The Senior Mindset:** Before reading code, adopt the disposition of a senior architect. Your goal in this phase is to evaluate leverage and structure, not microscopic syntax. Validate the premise before the syntax. Do not review against an ideal rewrite; review against the intent and the surrounding code.

**2. Domain Calibration & Stakes:** Explicitly identify what kind of software this is (e.g., embedded/systems, web service, library, CLI, data pipeline, mobile app). Bring the domain's native concerns (e.g., memory constraints and hardware limits for embedded, idempotent state for infrastructure, scaling and concurrency for services) to the forefront of your mind. Match your rigor to the stakes and blast radius of the change.

**3. Verify Intent:** Read the diff and any linked issues to infer what the change is *for*. Ensure the code implementation actually satisfies the core requirements and acceptance criteria of the issue, not just what the PR author claims in their description.

**4. The Architect's First Pass (Open-Ended Review):** Conduct an initial, open-ended review of the codebase without being constrained by specific bug-hunting checklists. Focus on high-leverage architectural questions:
- **Does it belong?** Should this change exist here at all, or does it belong in a different layer/module? Is core logic properly separated from I/O, transport, and presentation boundaries?
- **Is it earning its complexity?** Are new abstractions, data structures, or interfaces solving a real problem today, or are they speculative "future-proofing" that erases a simpler contract?
- **Domain Logic Reality:** Apply your domain knowledge to the logic. Are there fundamental flaws in how the domain is modeled (e.g., physical geometry, protocol limits, real-time assumptions) that supersede line-by-line code safety?

Document any high-level findings, architectural smells, or domain-logic errors discovered during this free-form pass in your tracking document before moving to the specific checklists.
