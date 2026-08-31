# Finding Policy

Broad investigation and sparse output are separate responsibilities. Retain plausible candidates while analyzing; apply this policy only after the relevant paths and consequences have been examined.

## Admission test

Surface a finding only when it is sufficiently supported and at least one condition holds:

- the change can violate stated intent or an applicable contract;
- it introduces a realistic correctness, safety, security, compatibility, data-loss, deployment, operability, or resource risk;
- it creates meaningful maintainability cost in code introduced or materially reshaped by the change; or
- a developer decision is required because intent or acceptable risk is genuinely ambiguous.

Omit preference-only alternatives, theoretical hardening, automated style concerns, negligible-impact observations, and improvements whose only benefit is subjective cleanliness. Do not create comments merely to demonstrate that a concern was considered.

## Evidence standard

State the inspected behavior, realistic trigger, concrete consequence, and supporting code, contract, verification result, or traced failure path. Reproduction strengthens confidence but is not mandatory when it is unsafe, unavailable, or disproportionate. State material uncertainty instead of overstating or suppressing the finding.

Deduplicate repeated instances into one representative finding and describe the affected scope. Recheck line locations and head identity before delivery.

## Classification

Use three independent fields:

- **Severity:** `critical`, `major`, or `moderate`, based on consequence rather than effort. Do not surface low-severity observations.
- **Current-change relevance:** `required`, `developer decision`, or `follow-up candidate`.
- **Resolution risk:** `routine`, `judgment required`, or `scope changing`.

`Required` means the material problem belongs in the current cohesive change. `Developer decision` means readiness depends on intent or risk judgment. `Follow-up candidate` is valuable but outside the current change; it never blocks and does not authorize issue creation.

## Recommendation

- **Changes required:** At least one supported finding is classified `required`.
- **Developer decision required:** No required finding remains, but readiness depends on an unresolved developer decision.
- **Ready candidate:** No known material in-scope defect remains after the completed review.

Readiness does not require perfection or unrelated cleanup. Aggregate net improvement is not sufficient when the change introduces a material regression.

## Communication

Use concise, neutral engineering language. A useful finding follows observation → consequence → smallest credible resolution direction. Critique the change, not its author. Do not impose a persona, praise quota, rhetorical flourish, or artificial severity.

Prefer an exact replacement when it is small, validated, and confined to one contiguous location. Use the delivery medium's directly applicable format, such as a GitHub suggestion, or include the replacement snippet in Hunk or plain output. Use prose when resolution spans locations, requires surrounding edits, or depends on developer judgment.

Positive evidence belongs in the risk summary only when it explains why an area is acceptable. Questions belong in findings only when their answer can change readiness.
