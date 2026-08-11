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

Use the smallest body that preserves an independent handoff:

- **Trivial:** concise intent, exact change, and proportionate verification. Omit empty conditional sections.
- **Routine:** intent, scope, implementation summary, verification, material limitations, and focused review guidance.
- **High-risk or cross-repository:** add affected boundaries, rollout or compatibility implications, exact dependent revisions, residual risk, and explicit human-review focus.

Risk is driven by potential impact and uncertainty, not line count alone. A one-line concurrency or ABI change may merit more context than a large mechanical edit.
