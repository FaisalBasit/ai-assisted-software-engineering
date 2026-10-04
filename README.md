# AI-Assisted Software Engineering

A disciplined, security-first engineering standard for building production software with AI coding agents.

## Why this exists

AI coding agents can dramatically increase implementation speed. Speed without engineering discipline increases the speed of producing defects, security vulnerabilities, unclear requirements, and hard-to-review changes.

This repository defines a reusable workflow that combines:

- rigorous requirements discovery ("grill me")
- explicit project specifications and user journeys
- architecture and implementation planning ("blueprint")
- backend/API/data contracts as the source of truth
- test-driven development (TDD)
- adversarial API and workflow testing
- human code review
- Semgrep and CodeQL analysis
- OWASP ASVS-based security verification
- evidence-based release gates
- production observability and feedback

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
CI GATES
   ↓
DEPLOY
   ↓
OBSERVE → ITERATE
```

## Core principles

1. **Spec before code.** Requirements and user journeys are explicit before implementation.
2. **Human owns decisions.** AI is an implementation partner, not the product owner, architect of record, security authority, or release approver.
3. **Backend is the source of truth.** Authorization, validation, business rules, state transitions, and persistence invariants are enforced server-side.
4. **TDD by vertical slice.** Build tested behavior end-to-end rather than producing a large unverified backend or frontend.
5. **Every bug becomes a regression test.**
6. **AI must be adversarially tested.** Ask the agent to abuse authorized test environments and discover edge cases.
7. **Security is continuous.** Threat modeling, secure coding, automated analysis, ASVS verification, and human review reinforce each other.
8. **No green CI, no merge.**
9. **Small, reviewable changes.** Avoid unrelated refactors and giant AI-generated diffs.
10. **Evidence over confidence.** "Looks good" is not a verification method.

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
  → Security scan
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

## Security model

This standard uses complementary controls:

- **OWASP ASVS** for a structured security verification baseline.
- **Semgrep** for fast pattern-based static analysis and custom rules.
- **CodeQL** for semantic analysis and deeper data-flow queries.
- threat modeling and secure architecture
- dependency and secrets controls
- API/DAST and adversarial testing where appropriate
- human review and independent testing for higher-risk systems

Passing a scanner is not proof that an application is secure. ASVS verification is evidence-based and risk-aware.

## AI agent contract

Before modifying code, an agent should:

1. read the relevant project specification
2. identify the affected user journey/workflow
3. state the acceptance criteria
4. state the intended files/modules to change
5. identify tests to add or update
6. identify security and data-flow implications
7. avoid unrelated refactors
8. stop and ask when requirements conflict or are ambiguous

After implementation, the agent should report:

- tests run and results
- files changed
- security considerations
- scan findings
- unresolved risks
- follow-up work

See [docs/ai-agent-contract.md](docs/ai-agent-contract.md).

## References

- [Matt Pocock](https://github.com/mattpocock) — disciplined TypeScript and TDD practices
- [Matt Pocock TDD skill](https://www.skills.sh/mattpocock/skills/tdd)
- [Imbue Blueprint](https://github.com/imbue-ai/blueprint) — structured planning
- [OWASP ASVS](https://github.com/OWASP/ASVS) — application security verification
- [Semgrep](https://github.com/semgrep/semgrep) — static analysis
- [Semgrep Rules](https://github.com/semgrep/semgrep-rules) — security rules
- [CodeQL](https://github.com/github/codeql) — semantic code analysis

## Status

Draft v0.1 — intended to evolve through community review, real-world projects, and security practice.
