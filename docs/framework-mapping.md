# Framework Mapping

This standard is intentionally a composition of established practices rather than a replacement for them.

| Standard capability | Primary reference | How this standard uses it |
|---|---|---|
| Secure development lifecycle | NIST SSDF | Secure planning, implementation, verification and release practices |
| Application security verification | OWASP ASVS 5.0.0 | Risk-based application security verification and evidence |
| Static analysis | Semgrep | Pattern-based SAST and project-specific rules |
| Semantic analysis | CodeQL | Deeper source/data-flow analysis where supported |
| Supply-chain security | SLSA 1.2 | Provenance and build/release integrity for applicable systems |
| Open-source supply-chain hygiene | OpenSSF Scorecard | Objective signals for repository and workflow security |
| GenAI/agent security | OWASP GenAI Security Project | AI-specific threats, red teaming and agent controls |
| Architecture/planning | Blueprint | Structured planning before implementation |
| Test-driven development | Matt Pocock TDD practices | Behavior-first implementation and regression discipline |

## Important distinction

The mapping is informative and does not imply formal compliance.

A project may satisfy a practice in this repository without satisfying every requirement of the referenced framework, and vice versa.

Projects with contractual or regulatory obligations must verify the actual applicable framework requirements independently.

## Version policy

External standards evolve. Projects MUST record the version used for release evidence when a specific version matters.

Avoid silently replacing a versioned verification baseline with a newer draft.

## Current references

- NIST SP 800-218 SSDF 1.1 is final; SP 800-218 Rev. 1 / SSDF 1.2 is a draft at the time this standard was updated.
- OWASP ASVS 5.0.0 is the current stable ASVS release.
- SLSA 1.2 is an approved specification.
- OWASP GenAI resources evolve rapidly; projects should use the current applicable guidance and record the edition used.
