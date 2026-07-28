# Verification and Handoff

Verification demonstrates that selected findings were resolved without claiming that the pull request has passed independent rereview.

## Verify the consequence

Start from each finding's realistic failure:

1. reproduce or trace the original behavior when practical;
2. exercise the corrected behavior;
3. inspect nearby failure paths that share the changed contract; and
4. record exact evidence and remaining gaps.

Use the narrowest evidence that credibly supports the correction, then broaden it according to blast radius:

- run focused tests or static checks for local logic;
- compile affected targets when signatures, templates, headers, or build inputs change;
- run relevant integration checks when state crosses component boundaries;
- inspect compatibility or migration behavior when persistent or external contracts change; and
- use repository-prescribed Docker or local build workflows rather than inventing substitutes.

An unavailable or expensive check is an explicit limitation. Do not claim it passed, but do not add ceremony solely to avoid reporting the gap.

## Identify the resulting changeset

Report the current branch and head commit when committed. For working-tree changes, identify the base or starting head and state that the handoff includes the current staged and unstaged tracked changes relevant to the feature. Note unrelated preserved changes so the reviewer can exclude them.

If edits occurred after verification, rerun affected checks or disclose that evidence as stale.

## Report every selected finding

Use [Resolution Result Template](../assets/resolution-result-template.md) proportionally. Each selected finding receives exactly one terminal status:

- `resolved`;
- `already resolved`;
- `disputed`; or
- `blocked`.

For resolved findings, state the correction and verification evidence. For other statuses, state why no edit was appropriate and what decision or evidence would unblock progress.

Keep newly discovered or unselected observations separate. Do not silently convert them into completed work, create issues, or imply that the reviewer requested them.

## Return to independent rereview

Hand the complete current base-to-head changeset back to the same reviewer when possible. Ask for a full rereview, not a delta-only inspection, because fixes can interact with unchanged portions of the feature or expand scope.

The resolver may say that selected findings are addressed. It must not:

- declare the changeset reviewed or merge-ready;
- approve or merge;
- publish review feedback;
- change pull-request readiness or description;
- resolve external threads; or
- commit or push unless separately and explicitly requested through the appropriate workflow.
