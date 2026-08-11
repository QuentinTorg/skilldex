# Resolution Policy

Resolution is bounded implementation by the original author. Revalidate every selected claim against the current code before deciding whether or how to edit.

## Revalidate before editing

For each selected finding:

1. inspect the referenced behavior, surrounding contract, and relevant callers or tests;
2. determine whether the claimed consequence still exists;
3. check whether another correction already resolves it;
4. identify conflicts with other selected findings or confirmed intent; and
5. assign a resolution route.

Use one terminal status:

- **`resolved`:** A validated finding was corrected and its consequence was checked.
- **`already resolved`:** The current changeset no longer exhibits the reported defect; no compensating edit was made.
- **`disputed`:** Evidence shows that the claim or requested consequence is incorrect, incompatible with confirmed intent, or superseded.
- **`blocked`:** Resolution needs missing evidence, authority, environment access, or a developer decision.

Explain `already resolved`, `disputed`, and `blocked` with concrete evidence.

## Route by decision risk

| Route | Test | Action |
| --- | --- | --- |
| Routine | Intent-preserving, bounded to the cohesive change, and mechanically verifiable | Proceed after selection without another plan approval. |
| Judgment required | Materially different valid solutions, or effects on public behavior, interfaces, architecture, compatibility, deployment, or product intent | Pause unless the developer already supplied the decision. |
| Scope changing | A correct resolution cannot remain inside the confirmed cohesive change | Stop and return the finding for redisposition or replanning. |

Effort and line count do not determine the route. A broad mechanical rename can be routine; a one-line contract change can require judgment.

## Implement the smallest cohesive correction

- Preserve confirmed design intent and repository conventions.
- Fix the claimed consequence and the failure paths needed to make that fix maintainable.
- Let multiple selected findings share one correction when separate patches would conflict or duplicate work.
- Treat suggested fixes as evidence, not commands.
- Add or update verification when it is necessary to demonstrate the corrected contract.
- Never weaken warnings, validation, tests, or type safety to obtain a passing result.

Do not bundle nearby cleanup, speculative hardening, style preferences, or follow-up candidates. A material defect discovered during implementation is an observation for developer disposition, not an implicit addition to the editable set.

## Control scope continuously

Reassess the route when implementation reveals a larger blast radius. Stop before crossing the boundary if the fix would:

- change an interface or user-visible contract not already authorized;
- require unrelated component redesign;
- invalidate the pull-request intent;
- overwrite unrelated workspace changes; or
- depend on choosing among materially different designs.

Conflicting selected findings are not processed sequentially. Describe the conflict and mark the affected items blocked until the developer decides which constraint governs.
