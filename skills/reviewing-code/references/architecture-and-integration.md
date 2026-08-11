# Architecture and Integration

Use these prompts as an independent pass when the change can affect structure, interfaces, dependencies, persistent state, deployment, or other components. They are investigation lenses, not finding quotas.

## Premise and placement

- Does the change belong in this module and architectural layer?
- Does it preserve separation between domain policy and I/O, transport, persistence, presentation, or process control?
- Does a new abstraction reduce consumer burden for a current need, or erase a useful contract for speculative flexibility?
- Does the design follow applicable repository decisions without treating historical patterns as unquestionable?

Review against the surrounding system, not an ideal rewrite. A different design is not a finding without a material consequence.

## Interfaces and compatibility

Inspect affected public and internal contracts, including APIs and ABIs, library exports, schemas, wire formats, files, stored state, CLI behavior, configuration, environment variables, events, and build interfaces.

Trace relevant producers, consumers, and transition ordering. Determine whether compatibility breaks are intentional, disclosed, migratable, and safe across mixed versions when that can occur.

## Dependencies and cross-component effects

For changed dependencies, evaluate necessity, maintenance and security posture, license compatibility, size or resource cost, and whether an existing facility already satisfies the need. Scale this investigation to the dependency's actual role and provenance.

For submodules or coordinated repositories, review the referenced revisions and integration order rather than only pointer changes. Identify assumptions that cannot be validated from the current repository.

## Deployment and reversibility

When the change affects deployed or persistent behavior, consider rollout order, feature control, migrations, downgrade behavior, mixed-version operation, observability during rollout, and recovery from partial failure.

Do not demand heavyweight rollout machinery for a low-risk or naturally atomic change. Flag only a realistic failure or an unresolved decision whose consequence matters.
