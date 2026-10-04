# Software Supply Chain

AI-assisted development increases the amount of code and dependency decisions produced at machine speed. Supply-chain controls therefore apply to source, dependencies, CI workflows, build systems, and release artifacts.

## Minimum controls

Projects SHOULD:

- pin CI actions to immutable commit SHAs for high-assurance environments
- review dependency additions and major upgrades
- remove unused dependencies
- monitor known vulnerabilities
- protect package registries and publishing credentials
- prevent secrets from entering source control
- generate an SBOM for releasable software where practical
- preserve build and release provenance for high-risk systems
- use protected release branches/tags
- restrict CI token permissions to the minimum required
- review third-party GitHub Actions and automation
- avoid downloading and executing untrusted artifacts during builds

## Provenance

For higher-risk systems, use a provenance framework such as SLSA and make release artifacts traceable to reviewed source and controlled build processes.

## SBOM

An SBOM SHOULD identify direct and transitive components and their versions. For released software, prefer publishing the SBOM with release artifacts rather than treating a repository copy as the sole source of truth.

## Dependency updates

Automated dependency updates are allowed, but they do not bypass:

- tests
- security analysis
- compatibility review
- release gates

A dependency update that changes security boundaries requires explicit review.

## Open-source project hygiene

Projects SHOULD periodically assess:

- branch protection
- code review
- CI tests
- SAST
- dependency vulnerabilities
- pinned dependencies
- token permissions
- signed releases
- SBOM availability

OpenSSF Scorecard can provide an automated signal for many of these controls. It is evidence, not certification.
