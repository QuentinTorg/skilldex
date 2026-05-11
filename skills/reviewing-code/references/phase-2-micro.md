# Phase 2: Micro & Implementation

This document outlines the deep technical inspection criteria for micro-implementation details.

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
