# Maintainability and Verification

Use this pass for implementation and test changes and whenever maintainability, completeness, or verification affects readiness. Apply the prompts selectively and produce no audit prose for concerns that do not matter.

## Abstractions and code health

- Does each new abstraction solve a present problem and preserve a discoverable contract?
- Can the language, type system, standard library, or an established project primitive enforce the invariant more directly?
- Does duplication represent repeated knowledge that will drift, or merely similar-looking code with different responsibilities?
- Did the change leave dead code, obsolete configuration, orphaned tests, or unused compatibility paths?
- Are names and comments accurate, with comments explaining non-obvious intent rather than narrating syntax?

Do not request factoring, idiom changes, defensive layers, or generalized hooks without meaningful current cost. Formatting, lint, and mechanical style belong to configured automation.

## Verification quality

Assess whether verification is proportionate to the behavior and risk:

- A bug fix should normally have a regression check that distinguishes broken from corrected behavior.
- Tests should assert observable contracts rather than mirror implementation details.
- Important boundaries and failure paths need coverage when their failure would be material.
- Tests should be deterministic and meaningful; execution alone is not an assertion.
- Broader builds or integration checks matter when shared interfaces, configuration, or components change.

Do not demand exhaustive tests for trivial or naturally low-risk code. Conversely, green CI does not excuse a test suite that never exercises the changed contract.

## Completeness and parity

Look for secondary effects of the primary change: all variants handled, parallel implementations updated, consumers migrated, schemas or generated artifacts refreshed, documentation corrected, and old paths retired when intended.

An omission is a finding only when it leaves the delivered behavior materially incomplete, inconsistent, or unsafe. Improvements unrelated to the stated change remain outside the pull request.
