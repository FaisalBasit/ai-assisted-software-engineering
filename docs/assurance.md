# Assurance and Release Evidence

A release decision should be based on evidence appropriate to the project's risk class.

## Release evidence package

For production releases, retain as applicable:

- specification/version
- acceptance criteria
- test results
- regression results
- API compatibility results
- code review evidence
- threat-model status
- Semgrep results
- CodeQL results
- dependency/vulnerability results
- secrets-scan results
- ASVS verification
- DAST/API test results
- SBOM
- build provenance
- migration validation
- backup/restore evidence
- smoke-test results
- rollback procedure
- unresolved risk/exception register
- release approval

## Evidence status

Each control should be one of:

- **Pass** — required evidence is present and satisfactory.
- **Fail** — evidence identifies an unresolved blocking problem.
- **Not applicable** — documented reason proves the control does not apply.
- **Accepted risk** — exception is approved, owned, time-bounded, and documented.

"Skipped" is not a release status.

## Blocking findings

At minimum, the following SHOULD block release unless formally accepted at the appropriate authority level:

- critical security vulnerabilities
- broken authentication/authorization
- exploitable cross-tenant data access
- exposed secrets
- failed critical user journeys
- unsafe migrations
- missing rollback for a high-risk change
- unbounded high-impact agent actions
- unresolved release-critical dependency vulnerabilities

## Production feedback

After release, operational evidence feeds back into:

`incident → reproduction → regression test → fix → scan → release evidence`

The goal is not only to repair incidents, but to improve the standard of future changes.
