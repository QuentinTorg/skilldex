# Draft Pull Request Mode

## Gather the handoff

Recover the following from the developer conversation, repository documentation, branch diff, commits, and verification output:

- developer-confirmed intent and acceptance criteria;
- important non-goals and scope boundaries;
- delivered behavior and implementation approach;
- tests, builds, linters, or manual checks that actually ran;
- known limitations, unverified assumptions, and deferred work;
- exact revisions and related pull requests for submodules or coordinated repositories.

## Check cohesion

Read the complete base-to-head diff. If the branch combines unrelated changes, conflicts with confirmed intent, or lacks enough context for an independent review, explain the problem and ask the human how to proceed. Do not silently redefine the pull request to fit the code.

## Compose proportionally

Follow [Template Policy](template-policy.md). Keep a comment-only or similarly trivial pull request brief. For a normal change, capture enough context that a reviewer who did not share the authoring conversation can understand its purpose, boundaries, implementation, and evidence. Add risk and review guidance only when it carries useful information.

The draft description may contain preliminary author assessments, but it must distinguish them from conclusions that require independent review.

## Publish the draft

Follow [GitHub Operations](github-operations.md). Create exactly one draft pull request, or update the existing draft only when the user asked for that mutation. Never mark it ready in draft mode.

Report:

- pull request URL and number;
- base branch and exact head revision;
- whether the branch was pushed;
- missing context, unrun verification, or other disclosed gaps;
- the next expected transition: independent review.
