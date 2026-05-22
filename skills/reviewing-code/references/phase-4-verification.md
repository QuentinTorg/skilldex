# Phase 4: Verification, Docs & Synthesis

This document outlines the deep technical inspection criteria for verification, documentation, and emergent patterns.

## 15. Test Rigor
Code without tests is incomplete. Ensure tests cover:
- The happy path.
- Known edge cases and boundary conditions.
- Failure modes (e.g., network timeouts, invalid input).
- **Behavior over Implementation:** Ensure tests actually *assert* the contract and behavior, not just execution or mirroring the implementation details.
- **Regression Guarding:** Ensure that if a bug fix is introduced, it is accompanied by a specific regression test that fails without the fix.

## 16. Comment Accuracy & Intent Documentation
Ensure all code comments accurately reflect the current implementation. Verify that the code performs exactly what the comments describe. Actively protect against outdated comments (doc rot). Furthermore, insist that any complex or unintuitive code blocks are accompanied by comments clearly stating their *intent* (the "why"), serving as a reliable surrogate for future maintainers to understand the logic.

## 17. Omissions & Contract Parity
Actively look for what is *missing* from the implementation. Evaluate the completeness of the change by considering the secondary effects of the primary logic modifications. If a core data structure, architectural boundary, or public interface is altered, you must verify that all downstream consumers, corresponding tests, and external contracts (such as consumer documentation or exported schemas) are updated to reflect the new reality. Identify unhandled edge cases, missing failure states, or incomplete feature footprints that leave the system in a partially implemented state.

## 18. Uncategorized Observations & Emergent Patterns
Take a step back from the micro-level checks and evaluate the holistic "vibe" or trajectory of the PR. Are there emergent architectural smells (e.g., a file getting too large, a namespace becoming a dumping ground, or a creeping anti-pattern) that don't fit neatly into the previous constraints? Use this check to document broad, high-level structural observations, refactoring suggestions for future sprints, or general technical praise that falls outside the rigid checklist. This is your escape hatch for providing senior-engineer intuition.
