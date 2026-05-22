# Phase 2: Micro & Implementation

This document outlines the deep technical inspection criteria for micro-implementation details.

## 6. Control & Data Flow
Trace the lifecycle of key variables and external resources from initialization to teardown. Look for boundary condition violations, unhandled invalid/empty states, and logical errors in iteration or state transitions. **Explicitly trace initialization failures:** ensure that if a resource fails to initialize, the system handles this invalid initial state safely and predictably in subsequent operations without silent failures.

## 7. State & Concurrency
If the application is multi-threaded or highly asynchronous, ruthlessly analyze for data races, deadlocks, and unsafe mutable state sharing.

## 8. Contract & Boundary Trust
Identify all "trust boundaries" in the PR where data enters from outside the immediate execution context. Actively search for untrusted data sinks, access control flaws, and credential exposure. **Broaden the definition of boundary trust:** Verify that structural integrity, mathematical limits, and physical/protocol constraints are enforced exactly at the perimeter before the data interacts with core logic. Never trust external input.

## 9. Systemic Resilience, Scaling & Auditability
- **Resilience:** Verify that failures are handled gracefully and simulate system dynamics under stress. Identify broken backpressure mechanisms, and synchronous operations blocking asynchronous event loops.
- **Resource Scaling:** Evaluate the code's behavior as data volume scales. Actively hunt for unbounded iterations, unconstrained data loading, and operations whose time or memory complexity degrades disproportionately relative to the input size.
- **Auditability & Visibility:** Evaluate how the code communicates its internal state when things go wrong. Ensure critical state transitions and failure paths emit sufficient diagnostic signals without leaking sensitive operational configurations or user data across execution boundaries.
