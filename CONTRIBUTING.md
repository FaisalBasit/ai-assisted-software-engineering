# Contributing

Contributions should improve the clarity, rigor, safety, or practical usefulness of this standard.

## Before opening a PR

- explain the problem or gap
- identify the affected standard section/template
- avoid unrelated changes
- provide authoritative evidence or references for security/process claims
- consider how the change affects AI-assisted development workflows
- identify whether the change is normative
- include migration guidance for breaking normative changes

## Review expectations

Reviewers should check:

- technical correctness
- applicability across stacks
- security implications
- clarity and actionable guidance
- consistency with the existing workflow
- whether new requirements have appropriate verification evidence
- whether external references are current and versioned where necessary
- whether the change accidentally implies certification or compliance

Changes that weaken security or testing gates require explicit rationale and risk discussion.

## Normative changes

Changes to MUST/MUST NOT requirements should include:

- rationale
- affected sections/templates
- security impact
- migration guidance
- updated examples/evidence
- changelog entry

Use an ADR for consequential architectural or governance decisions.

## Quality bar

A contribution should be understandable and usable by an engineer who did not participate in its design. Prefer concrete procedures, templates, examples, and evidence criteria over vague advice.

See [docs/governance.md](docs/governance.md) and [docs/versioning.md](docs/versioning.md).
