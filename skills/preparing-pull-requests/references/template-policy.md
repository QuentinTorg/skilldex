# Pull Request Template Policy

## Choose the template

Discover applicable repository or organization guidance before composing a body. Check repository instructions and conventional GitHub template locations, including:

- `.github/pull_request_template.md`;
- `.github/PULL_REQUEST_TEMPLATE/`;
- `docs/pull_request_template.md`;
- `pull_request_template.md`.

If the user selected a template, use it. If multiple templates exist and no choice can be inferred safely, ask which applies. Use [the bundled default](../assets/pull-request-template.md) only when no applicable template exists.

## Preserve structure and authorship

- Retain required headings, checklists, policy declarations, comments, and repository-specific instructions.
- Map intent, delivered change, verification, risk, limitations, and review guidance into the closest existing sections instead of appending duplicate headings.
- Preserve meaningful human-authored content. Correct factual staleness without erasing rationale or changing confirmed intent.
- Do not claim compliance, test results, review completion, or risk validation without evidence.
- Leave a required item explicitly incomplete when it cannot be substantiated.

## Scale to the change

Write a reviewer-facing explanation, not a work log. Complement the diff and commit history: explain the problem and why it matters, the solution's central idea, and the non-obvious behavior, tradeoffs, or caveats needed to review it. Avoid file-by-file narration and inventories of safeguards or intermediate fixes. Do not invent rationale that the authoring context does not establish.

Keep routine descriptions readable in about a minute: a few short paragraphs or focused bullets, not dense prose or exhaustive lists. This is a guideline, not a quota or hard limit; add detail when it materially changes understanding or a review decision. Link durable supporting documentation or evidence instead of embedding logs and long explanations. Keep essential caveats in the body.

Validation should give a teammate a practical way to reproduce the relevant checks: repository-relative commands or manual steps, necessary prerequisites (or a setup link), observed results, and material gaps. Omit incidental local paths, environment troubleshooting, and exhaustive test-case inventories. Distinguish suggested checks from checks actually run; do not claim an adapted command was executed.

When updating or finalizing, consolidate into a coherent description of the current change rather than appending a history of review rounds. Preserve meaningful human content and confirmed intent.

Scale the explanation to the change:

- **Trivial:** concise intent, exact change, and proportionate verification. Omit empty conditional sections.
- **Routine:** why the change matters, how the approach addresses it, and reproducible validation. Include boundaries and review guidance where they affect understanding, not as a checklist to fill.
- **High-risk or cross-repository:** add affected boundaries, rollout or compatibility implications, exact dependent revisions, residual risk, and explicit human-review focus.

Risk is driven by potential impact and uncertainty, not line count alone. A one-line concurrency or ABI change may merit more context than a large mechanical edit.
