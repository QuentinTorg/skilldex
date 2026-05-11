# Phase 4: Verification & Docs

This document outlines the deep technical inspection criteria for verification and documentation.

## 14. Test Rigor
Code without tests is incomplete. Ensure tests cover:
- The happy path.
- Known edge cases and boundary conditions.
- Failure modes (e.g., network timeouts, invalid input).
- Ensure tests actually *assert* correctness, not just execution.

## 15. Comment Accuracy & Intent Documentation
Ensure all code comments accurately reflect the current implementation. Verify that the code performs exactly what the comments describe. Actively protect against outdated comments (doc rot). Furthermore, insist that any complex or unintuitive code blocks are accompanied by comments clearly stating their *intent* (the "why"), serving as a reliable surrogate for future maintainers to understand the logic.

## 16. Omissions & Contract Parity
Actively look for what is *missing* from the implementation. Evaluate the completeness of the change by considering the secondary effects of the primary logic modifications. If a core data structure, architectural boundary, or public interface is altered, you must verify that all downstream consumers, corresponding tests, and external contracts (such as consumer documentation or exported schemas) are updated to reflect the new reality. Identify unhandled edge cases, missing failure states, or incomplete feature footprints that leave the system in a partially implemented state.
