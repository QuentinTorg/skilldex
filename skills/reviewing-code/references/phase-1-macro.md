# Phase 1: Macro & Architecture

This document outlines the deep technical inspection criteria for macro-architectural concerns.

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
