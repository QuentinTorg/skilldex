# Safe GitHub Operations

Use inspectable, idempotent Git and GitHub CLI operations. Adapt the GitHub host and CLI authentication to the repository; do not assume `github.com` when the remote identifies GitHub Enterprise.

## Preflight

Inspect before mutation:

1. repository instructions and applicable pull-request templates;
2. current branch, working-tree state, remotes, and exact local head;
3. intended base and its merge base with the branch;
4. complete base-to-head diff and commits;
5. existing open or closed pull requests for the head branch;
6. remote head state and authentication.

Never create a feature pull request from `main`, push directly to `main`, discard unrelated changes, or force-push protected history. If currently on `main`, require the work to be placed on a feature branch first.

Do not assume local uncommitted changes will appear in a pull request. Explain and resolve that mismatch before publishing.

## Prepare content safely

Write the proposed title and body to local temporary files and inspect them before the GitHub mutation. Pass body content using file arguments such as `--body-file`; never interpolate multiline or untrusted content into a shell command.

Prefer explicit repository, base, and head arguments. Record the local and remote head revisions used for the operation.

## Draft creation

Before creating, query for a pull request associated with the head branch. If one exists, do not create another. Update it only when the user's request authorizes the applicable draft mutation.

Push the feature branch only when necessary for the requested pull request. Use an ordinary upstream-setting push; never use force by default. Create the pull request explicitly as a draft.

## Finalization

Immediately before editing or marking ready, fetch or query the pull request again. Confirm:

- it is the intended pull request and is still a draft;
- its head revision equals the reviewed revision;
- the base branch is still correct.

Update the body first, verify it, and only then mark the pull request ready.

## Read-back and partial failures

After every mutation, query the pull request and confirm its URL, state, base, head revision, title, and body. Treat command success as insufficient without this read-back.

If an operation partially fails:

1. report the operation and observed failure;
2. re-read GitHub state before retrying;
3. identify which mutation, if any, already succeeded;
4. retry only the missing idempotent action;
5. never create a replacement pull request merely because state is uncertain.
