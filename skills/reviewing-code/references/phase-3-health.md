# Phase 3: Code Health & Abstractions

This document outlines the deep technical inspection criteria for code health and abstractions.

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
