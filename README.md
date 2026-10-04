# AI-Assisted Software Engineering

A disciplined, security-first engineering standard for building production software with AI coding agents.

> **Goal:** make AI-assisted development faster without making engineering weaker.

This repository is a reusable methodology. It is not a certification, compliance claim, or replacement for professional security assessment.

## Why this exists

AI coding agents can dramatically increase implementation speed. Speed without engineering discipline increases the speed of producing defects, security vulnerabilities, unclear requirements, and hard-to-review changes.

This standard combines:

- requirements discovery ("grill me")
- explicit project specifications and feature-level user journeys
- architecture and implementation planning ("blueprint")
- backend/API/data contracts as the source of truth
- TDD by vertical slice
- adversarial and AI-specific testing
- human code review
- Semgrep and CodeQL
- OWASP ASVS verification
- NIST SSDF-aligned secure development practices
- software supply-chain controls, SBOMs, and provenance where appropriate
- risk-based assurance and release evidence
- production observability and continuous feedback

## Standard workflow

```
GRILL-ME
   ↓
SPECIFY
   ↓
BLUEPRINT / ARCHITECTURE
   ↓
BACKEND + DATA CONTRACTS
   ↓
TDD VERTICAL SLICE
   ↓
IMPLEMENT
   ↓
CODE REVIEW
   ↓
AI ABUSE / ADVERSARIAL TESTING
   ↓
SEMGREP + CODEQL
   ↓
OWASP ASVS VERIFICATION
   ↓
FIX → TEST → SCAN → VERIFY
   ↓
EVIDENCE + RELEASE GATES
   ↓
DEPLOY
   ↓
OBSERVE → ITERATE
```

## Core principles

1. **Spec before code.** Requirements and user journeys are explicit before implementation.
2. **Human owns decisions.** AI is an implementation partner, not the product owner, architect of record, security authority, compliance approver, or release approver.
3. **Backend is the source of truth.** Authorization, validation, business rules, state transitions, and persistence invariants are enforced server-side.
4. **TDD by vertical slice.** Build tested behavior end-to-end rather than producing a large unverified backend or frontend.
5. **Every bug becomes a regression test.**
6. **AI must be adversarially tested.** Authorized agents should actively search for edge cases and abuse paths.
7. **AI output is untrusted.** Model output, retrieved content, tool results, and generated code require normal validation and authorization controls.
8. **Security is continuous.** Threat modeling, secure coding, automated analysis, ASVS verification, and human review reinforce each other.
9. **No green CI, no merge.**
10. **Evidence over confidence.** "Looks good" is not a verification method.
11. **Risk determines assurance.** High-impact systems require stronger evidence and review.
12. **Small, reviewable changes.** Avoid unrelated refactors and giant AI-generated diffs.

## Project specification

Every consuming project should have a dedicated `your-project-spec/` directory containing:

- product scope and non-goals
- actors and user journeys
- backend workflows and state transitions
- frontend routes and subroutes
- API contracts
- data model and invariants
- authorization rules
- acceptance criteria
- edge and failure cases
- security requirements
- observability requirements
- integration and operational constraints

Every major feature gets its own user journey. Every externally observable behavior gets acceptance criteria.

Recommended structure:

```text
your-project-spec/
├── product-spec.md
├── user-journeys/
├── workflows/
├── api/
├── routes.md
├── data-model.md
├── authorization.md
├── security.md
├── observability.md
└── acceptance-criteria/
```

Use the templates in [templates/spec](templates/spec/).

## Development loop

For each feature or workflow:

```
Spec
  → Plan
  → Failing test
  → Minimal implementation
  → Passing test
  → Refactor
  → Review
  → Security verification
```

For bugs:

```
Reproduce
  → Regression test
  → Fix
  → Green
  → Refactor
  → Scan
  → Review
```

## Assurance levels

- **Level 1 — Disciplined:** specification, TDD, review, regression tests, basic security and CI.
- **Level 2 — Production:** Level 1 plus threat modeling, contracts, security scanning, dependency/secrets controls, release evidence, observability and applicable ASVS verification.
- **Level 3 — High Assurance:** Level 2 plus stronger independent security testing, supply-chain provenance, recovery testing, formal assurance and enhanced AI red teaming where applicable.

See [docs/governance.md](docs/governance.md) and [docs/risk-classification.md](docs/risk-classification.md).

## Security model

This standard uses complementary controls:

- **OWASP ASVS** for structured application-security verification.
- **Semgrep** for fast pattern-based static analysis and custom rules.
- **CodeQL** for semantic analysis and deeper data-flow queries.
- **Threat modeling** for design-time security reasoning.
- **NIST SSDF** as a secure-development practice reference.
- **Supply-chain controls** including dependency hygiene, SBOM and provenance where appropriate.
- **AI-specific security controls** for prompt injection, tool abuse, data leakage, memory/context poisoning and excessive agency.
- **Human review** and independent testing for higher-risk systems.

Passing a scanner is not proof that an application is secure.

## AI agent contract

Before modifying code, an agent should:

1. read the relevant project specification
2. identify the affected user journey/workflow
3. state the acceptance criteria
4. state the intended files/modules to change
5. identify tests to add or update
6. identify security and data-flow implications
7. avoid unrelated refactors
8. stop and ask when requirements conflict or critical information is missing

After implementation, the agent should report:

- tests run and results
- files changed
- security considerations
- scan findings
- unresolved risks
- follow-up work

See [docs/ai-agent-contract.md](docs/ai-agent-contract.md).

## Traceability

Material changes should be traceable:

`requirement → journey → workflow → design → implementation → test → security evidence → release → operations`

See [docs/traceability.md](docs/traceability.md) and [templates/traceability-matrix.md](templates/traceability-matrix.md).

## Supply-chain security

For applicable projects, address:

- dependency vulnerabilities
- secrets
- CI token permissions
- pinned actions/dependencies
- SBOMs
- release provenance
- protected branches/releases
- third-party automation

See [docs/supply-chain.md](docs/supply-chain.md).

## References

- [Matt Pocock](https://github.com/mattpocock) — disciplined TypeScript and TDD practices
- [Matt Pocock TDD skill](https://www.skills.sh/mattpocock/skills/tdd)
- [Imbue Blueprint](https://github.com/imbue-ai/blueprint) — structured planning
- [OWASP ASVS](https://github.com/OWASP/ASVS) — application security verification
- [OWASP GenAI Security Project](https://genai.owasp.org/) — GenAI and agentic security guidance
- [NIST SSDF](https://csrc.nist.gov/projects/ssdf) — secure software development practices
- [SLSA](https://slsa.dev/spec/v1.2/) — supply-chain security and provenance
- [OpenSSF Scorecard](https://github.com/ossf/scorecard) — open-source supply-chain security signals
- [Semgrep](https://github.com/semgrep/semgrep) — static analysis
- [Semgrep Rules](https://github.com/semgrep/semgrep-rules) — security rules
- [CodeQL](https://github.com/github/codeql) — semantic code analysis

## Status

**Draft v0.2** — a reusable engineering standard evolving through review, real-world adoption, and security practice.

The repository intentionally avoids claiming that following the methodology makes software secure or compliant. Assurance is always contextual and evidence-based.
