# Finding Intake

Establish exactly what may be changed before editing. Review media provide evidence and anchors; they do not grant authority.

## Bind the changeset

Record:

- repository and current branch or workspace;
- intended base and the current head commit, or a precise working-tree identity;
- the confirmed change intent;
- applicable repository instructions; and
- unrelated local changes that must be preserved.

If the reviewed identity differs from the current changeset, treat locations and conclusions as potentially stale. Never switch branches, sync, discard changes, or rewrite history merely to recreate the old state.

## Normalize selected findings

Prefer findings with stable identifiers and these fields:

- observation and realistic consequence;
- evidence and location or affected contract;
- current-change relevance;
- resolution risk;
- suggested direction, if any; and
- developer decisions already supplied.

Missing fields are investigation gaps, not permission to invent reviewer intent. The technical claim remains authoritative over a stale inline location, and a suggested direction is not a prescribed patch.

## Establish the editable set

Selection may be:

- explicit identifiers, such as “resolve F1 and F3”; or
- a bounded rule, such as “resolve every current-change finding classified required.”

A bounded rule selects only findings that unambiguously satisfy it. It does not authorize unresolved product, compatibility, architecture, or scope decisions.

For raw or unclassified feedback, inspect only enough context to propose a concise disposition:

1. identify which comments appear to request a current-change correction;
2. separate informational, follow-up, and unclear comments;
3. ask the developer to confirm the proposed editable set once; and
4. begin only after confirmation.

Do not recreate an exhaustive feedback matrix or require separate approval for each routine item.

## Keep adapters passive

Hunk comments, GitHub threads, pasted reviews, and sidecar files are interchangeable inputs. Adapter identifiers may be retained for traceability, but this workflow does not:

- publish or reply to comments;
- resolve threads;
- create issues; or
- infer selection from visibility, open status, severity, or reviewer wording.

When a location is stale, find the current implementation from the stable finding claim and changeset history. If the claim cannot be mapped confidently, mark the finding blocked rather than guessing.
