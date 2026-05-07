# Code Review Protocol

This document outlines the deep technical inspection criteria to be used during the Analysis Phase of the code review, organized from macro-architectural concerns down to micro-implementation details.

# Phase 1: Macro & Architecture

## 1. Architecture & Design Document Compliance
Search the workspace for relevant design documents, Architecture Decision Records (ADRs), or Request For Comments (RFCs) that relate to the PR. Ensure that the structural changes and new features comply strictly with the documented architectural decisions, intended design, and established workspace patterns.

## 2. Backward Compatibility & Breaking Changes
Identify if the changes alter public-facing APIs, database schemas, serialized data formats, or persistent storage. If so, rigorously verify that the change is backward compatible. If it introduces a breaking change, ensure that a clear migration path, versioning strategy, or deprecation plan is included and well-documented to prevent breaking downstream clients.

## 3. Dependency & Supply Chain Scrutiny
If dependency files (e.g., `package.json`, `requirements.txt`, `Cargo.toml`, `go.mod`) are modified, explicitly evaluate the new dependencies using the following discipline matrix:
1. **Necessity:** Can the standard library or existing utilities solve this? (Prefer existing solutions).
2. **Impact:** What is the bundle size impact?
3. **Maintenance:** Is the dependency actively maintained? (Check last commit, open issues).
4. **Security:** Does it have known vulnerabilities?
5. **License:** Is the license compatible with the project?
Every new dependency is a liability; push back if it is not strictly justified.

## 4. Layering Violations & Separation of Concerns
Evaluate whether functionality is implemented at the correct architectural layer. Core domain logic and data transformations should be deterministic and isolated from external state. Identify and hoist side effects (I/O, environmental access, process control) to the appropriate orchestration boundaries or infrastructure layers. Ensure components rely on dependency injection or higher-level coordination rather than initiating unauthorized external interactions from deep within the call stack.

# Phase 2: Micro & Implementation

## 5. Control Flow & Data Flow
Trace the lifecycle of key variables. Look for boundary condition violations, unhandled invalid/empty states, and logical errors in iteration or state transitions.

## 6. State & Concurrency
If the application is multi-threaded or highly asynchronous, ruthlessly analyze for data races, deadlocks, and unsafe mutable state sharing.

## 7. Security & Boundary Trust
Identify all "trust boundaries" in the PR where data enters from outside the immediate execution context. Actively search for untrusted data sinks, access control flaws, and credential exposure. Verify that structural integrity, type safety, and domain validation are enforced exactly at the perimeter before the data is allowed to interact with core logic or memory. Never trust external input.

## 8. Systemic Resilience, Scaling & Auditability
- **Resilience:** Verify that failures are handled gracefully and simulate system dynamics under stress. Identify broken backpressure mechanisms, and synchronous operations blocking asynchronous event loops.
- **Resource Scaling:** Evaluate the code's behavior as data volume scales. Actively hunt for unbounded iterations, unconstrained data loading, and operations whose time or memory complexity degrades disproportionately relative to the input size.
- **Auditability & Visibility:** Evaluate how the code communicates its internal state when things go wrong. Ensure critical state transitions and failure paths emit sufficient diagnostic signals without leaking sensitive operational configurations or user data across execution boundaries.

# Phase 3: Code Health & Abstractions

## 9. Redundancy & Factoring Check
Actively scrutinize newly introduced functions or logic blocks for redundancy. Look for duplicated code within the same file, similar functionality in neighboring files, or existing shared logic elsewhere in the codebase. If a new block of logic could be factored out into a common utility or abstraction rather than reinventing the wheel, recommend doing so.

## 10. Idiomatic Primitives & Compile-Time Guarantees
Ensure code trusts underlying language or framework primitives. Prefer utilizing the type system to enforce invariants at compile-time over complex data structures requiring manual runtime validation.

## 11. Hunt for "Belt and Suspenders" Anti-Patterns
Actively look for code that manually rebuilds functionality already provided by the language, standard library, or framework. Identify redundant state machines or validation logic implemented to guard against conditions already natively handled by underlying dependencies. Trust the underlying primitives.

## 12. Scrutinize Overengineering & "Just in Case" Code
Reject logic, features, or abstractions built for theoretical future requirements or impossible edge cases. Complexity must buy measurable functionality *now*. Every line of code must justify its existence through current, verifiable utility.

**The "Just in Case" Audit Checklist:**
Use the following criteria to evaluate whether a change is "over-engineered" or "premature":

1. **Functional Utility (The "Dead Weight" Check):** Reject any logic, functions, or features that are not explicitly leveraged within this PR. If it doesn't solve a current problem or act as a strictly required building block for the logic in this specific branch, it is "dead weight."
2. **Future Scaffolding:** Flag code that adds "hooks," "placeholders," or infrastructure for features that "we might implement one day." This includes empty interfaces, unused configuration flags, or generic dispatchers with no current subscribers.
3. **Contract Integrity (The "Flexibility Trap"):** Reject "contract-erasing" abstractions that trade a strict, discoverable contract for a container that could represent "anything" but defines "nothing" (e.g., swapping a struct for a generic Map, or an explicit API for an opaque ID/Value pair). This is often an abdication of design hidden behind a mask of "flexibility."
4. **Inner Platform Effect:** Flag code that manually rebuilds basic system-level functionality (like routing, discovery, or type-checking) within a custom data structure just to achieve "dynamic" behavior.
5. **Burden of Complexity:** Does the new pattern increase the cognitive load or validation burden on downstream consumers? A good abstraction reduces the consumer's burden; a poor one increases it by requiring them to know a "magic" runtime-defined contract.

**Final Recommendation:**
Ensure the code remains strict and opinionated. Favor established conventions and "boring" implementations over "future-proof" ambiguity. If a feature or abstraction isn't needed today, it shouldn't be in the PR.

## 13. Dead Code & Orphaned Artifacts
After any refactoring or implementation change, explicitly hunt for code that is now unreachable or unused (e.g., old functions replaced by new ones, obsolete constants, or unused UI components). Explicitly list these orphaned artifacts in your review and ask the author to clean them up. Do not leave dead code lying around.

# Phase 4: Verification & Docs

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
