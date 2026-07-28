---
name: reviewing-code
description: Use when the user explicitly requests a formal review or rereview of a pull request, branch, commit range, diff, patch, or working-tree changeset for correctness or merge readiness. Do not use for implementation, ordinary self-verification, status summaries, narrow debugging, resolving feedback, PR creation or finalization, review publication, or merge.
---

# Reviewing Code

Independently determine whether an identified changeset safely and maintainably delivers its stated intent. Investigate broadly enough to catch material defects, then surface only the findings that earn the author's attention.

## Review disposition

- **Broad analysis, strict output:** Noise control happens after investigation. A quiet final review may result from several thorough passes.
- **No known material defect:** Recommend readiness when no known material in-scope defect remains. Do not demand perfection or accept a material regression merely because the net change is beneficial.
- **Evidence over preference:** Review the submitted change against its intent, contracts, and surrounding code—not an ideal rewrite.
- **Proportional rigor:** Depth follows impact, reversibility, domain, and uncertainty rather than line count.
- **Independent judgment:** Do not inherit the author's confidence, modify the implementation, or resolve your own findings.

Use concise, neutral engineering language. This is a decision policy, not a reviewer persona; do not add praise quotas, theatrical severity, or commentary that competes with the technical result.

## Track the review

Copy this checklist into internal reasoning or temporary scratch state and complete it without mandatory user pauses:

- [ ] Bind the exact review identity and intent.
- [ ] Complete orientation and scope mapping.
- [ ] Perform applicable architecture and integration analysis.
- [ ] Complete the behavior and safety minimum for every behavior-changing change.
- [ ] Perform applicable maintainability and verification analysis.
- [ ] Validate, deduplicate, and classify candidates.
- [ ] Produce one recommendation bound to the reviewed head.

Pause only when responsible progress requires a developer decision or authorization, such as an uncertain target, irreconcilable intent, fundamental scope mismatch, or costly or state-changing verification.

## Bind and orient

Read [Orientation and Scope](references/orientation-and-scope.md) first. Establish the exact base and head or equivalent working-tree identity, reliable intent, repository instructions, complete changed-file scope, relevant neighboring code, available evidence, domain, and blast radius.

Phase 0 is a high-level architectural pass. It forms hypotheses and finds high-leverage concerns; it is not permission to skip the independent passes that catch issues it misses.

## Perform adaptive independent passes

- Read [Architecture and Integration](references/architecture-and-integration.md) when the change can affect structure, interfaces, compatibility, dependencies, persistence, deployment, or other components.
- Read [Behavior and Safety](references/behavior-and-safety.md) for every behavior-changing change. Trace the changed contract, callers, boundaries, failure paths, state and resource lifecycle, and relevant domain hazards even when orientation found no concern.
- Read [Maintainability and Verification](references/maintainability-and-verification.md) for implementation or test changes and whenever completeness or evidence affects readiness.

These are independent analytical passes, not quotas. Skip concerns that genuinely cannot apply, but do not use high-level confidence, green CI, change size, or desired brevity to suppress deeper investigation.

Retain plausible candidates until the relevant pass validates them. Ordinary reviews may use reviewer context; Hunk may hold revisable location-anchored notes when active. Create a temporary head-bound recovery snapshot only when interruption or state loss is a credible risk. Never require or commit a review-notes file, and never expose unvalidated speculation as author work.

## Filter and synthesize

Read [Finding Policy](references/finding-policy.md) before producing output. Omit candidates that lack a realistic material consequence, duplicate another pattern, express preference, belong to automation, or do not warrant author attention.

Use [Review Result Template](assets/review-result-template.md) proportionally. Produce:

- the exact reviewed identity and understood intent;
- a concise material risk and evidence summary;
- prioritized current-change findings;
- valuable follow-up candidates kept visibly separate;
- assumptions and material evidence gaps; and
- one recommendation: `changes required`, `developer decision required`, or `ready candidate`.

Do not narrate every check performed. Tiny and finding-free reviews should remain tiny.

## Rereview the whole changeset

After fixes, rebind the current head and review the complete base-to-head changeset. Revalidate earlier findings, inspect the fixes and their interactions, detect regressions or scope growth, and issue a new recommendation for the new identity. Retained reviewer context accelerates discovery but never turns rereview into a delta-only check.

## Boundaries

Do not:

- modify source code or act as the author;
- select non-blocking work for the developer;
- create issues or expand the cohesive change;
- publish Hunk or GitHub feedback without the applicable authorization and adapter;
- update the pull-request description or readiness state except through the separate preparation skill after a successful current-head review and explicit authorization;
- approve or merge on GitHub; or
- treat CI success as proof of correctness.

Review analysis remains medium-independent. Hunk and GitHub mechanics belong to their adapter skills.
