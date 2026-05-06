# Code Review Protocol

This document outlines the deep technical inspection criteria to be used during the Analysis Phase of the code review, organized from macro-architectural concerns down to micro-implementation details.

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

## 5. Control Flow & Data Flow
Trace the lifecycle of key variables. Look for boundary condition violations, unhandled invalid/empty states, and logical errors in iteration or state transitions.

## 6. State & Concurrency
If the application is multi-threaded or highly asynchronous, ruthlessly analyze for data races, deadlocks, and unsafe mutable state sharing.

## 7. Security
Actively search for untrusted data sinks, access control flaws, credential exposure, and unsafe data processing or deserialization.

## 8. Systemic Resilience & Error Handling
Verify that failures are handled gracefully and simulate system dynamics under stress. Evaluate resource constraints under load variations. Identify unbounded memory growth, broken backpressure mechanisms, and synchronous operations blocking asynchronous event loops. Ensure errors are routed with sufficient debugging context.

## 9. Redundancy & Factoring Check
Actively scrutinize newly introduced functions or logic blocks for redundancy. Look for duplicated code within the same file, similar functionality in neighboring files, or existing shared logic elsewhere in the codebase. If a new block of logic could be factored out into a common utility or abstraction rather than reinventing the wheel, recommend doing so.

## 10. Idiomatic Primitives & Compile-Time Guarantees
Ensure code trusts underlying language or framework primitives. Prefer utilizing the type system to enforce invariants at compile-time over complex data structures requiring manual runtime validation.

## 11. Hunt for "Belt and Suspenders" Anti-Patterns
Actively look for code that manually rebuilds functionality already provided by the language, standard library, or framework. Identify redundant state machines or validation logic implemented to guard against conditions already natively handled by underlying dependencies. Trust the underlying primitives.

## 12. Scrutinize Overengineering & "Just in Case" Code
Reject complex abstractions built for theoretical future flexibility or impossible edge cases. Avoid superfluous wrapper layers, premature dynamic dispatch, or fallback logic for invariants already guaranteed by the architecture or type system. Complexity must buy measurable functionality *now*. 

**Crucially, explicitly evaluate the systemic cost of new abstractions:**
- Does this new pattern or structure push the burden of complexity onto downstream consumers or API clients?
- Is the author creating a generalized solution for a specific problem that doesn't actually exist yet?
- Ensure the API and data structures remain strict and opinionated, favoring established conventions over "future-proof" ambiguity.

## 13. Dead Code & Orphaned Artifacts
After any refactoring or implementation change, explicitly hunt for code that is now unreachable or unused (e.g., old functions replaced by new ones, obsolete constants, or unused UI components). Explicitly list these orphaned artifacts in your review and ask the author to clean them up. Do not leave dead code lying around.

## 14. Test Rigor
Code without tests is incomplete. Ensure tests cover:
- The happy path.
- Known edge cases and boundary conditions.
- Failure modes (e.g., network timeouts, invalid input).
- Ensure tests actually *assert* correctness, not just execution.

## 15. Comment Accuracy & Intent Documentation
Ensure all code comments accurately reflect the current implementation. Verify that the code performs exactly what the comments describe. Actively protect against outdated comments (doc rot). Furthermore, insist that any complex or unintuitive code blocks are accompanied by comments clearly stating their *intent* (the "why"), serving as a reliable surrogate for future maintainers to understand the logic.

## 16. Omissions (The Ghost Code)
Actively look for what is *missing* from the implementation. Did the author add a new enum variant but forget to update a match statement elsewhere? Did they add a feature but forget tests or documentation? Did they add a new API endpoint but forget to add authorization middleware?