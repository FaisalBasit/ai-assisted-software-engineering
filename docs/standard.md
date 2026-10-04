# Engineering Standard

## 1. Purpose

This standard defines how to use AI coding agents to design, implement, test, review, secure, release, and operate production software.

The standard is technology-agnostic. Framework-specific commands belong in the consuming project.

## 2. Normative model

The words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** define conformance expectations.

The standard is risk-based. Not every control applies to every project, but non-applicability must be reasoned and documented where the control is material.

## 3. Roles and accountability

The AI agent is an implementation partner. It must not silently become:

- product owner
- architect of record
- security authority
- compliance approver
- release approver

Humans own requirements, risk acceptance, architectural decisions, security exceptions, and production release decisions.

## 4. Phase 0 — Grill-Me

Before implementation, challenge the problem.

Ask about:

- users and actors
- business goal and measurable outcome
- non-goals
- major user journeys
- state transitions
- failure modes
- data ownership and lifecycle
- authentication and authorization
- trust boundaries
- integrations and external dependencies
- expected scale and availability
- privacy and security requirements
- operational constraints
- acceptance criteria
- migration and rollback requirements

Output a clarified problem statement, assumptions, decisions, and unresolved questions.

## 5. Phase 1 — Project specification

Create `your-project-spec/`.

At minimum document:

- product scope
- users/actors
- major user journeys
- backend workflows
- frontend routes/subroutes
- API contracts
- data model and invariants
- authorization matrix
- acceptance criteria
- edge cases
- security requirements
- observability requirements

A feature is Ready only when its externally observable behavior can be described clearly enough to test.

## 6. Phase 2 — Blueprint / architecture

Produce an architecture plan before significant implementation.

Cover:

- system boundaries
- modules/services
- entities and invariants
- API boundaries
- authentication/authorization
- integrations
- failure handling
- observability
- migrations
- testing strategy
- security controls
- implementation order
- rollback strategy

For consequential decisions, create an ADR.

## 7. Phase 3 — Backend and data contracts

The backend is authoritative for:

- authentication
- authorization
- input validation
- business rules
- state transitions
- persistence invariants
- external integrations
- audit/security events

"Backend-first" means build tested vertical slices from the backend contract outward. It does not mean writing an entire untested backend before the frontend.

## 8. Phase 4 — TDD vertical slices

For each behavior:

1. write the test from the specification
2. confirm the test fails for the expected reason
3. implement the smallest change
4. make the test pass
5. refactor while preserving behavior
6. run the relevant suite
7. update the specification when behavior intentionally changes

Prefer tests against public behavior and contracts over implementation details.

## 9. Phase 5 — Frontend integration

The frontend consumes backend contracts.

Frontend owns:

- presentation
- navigation
- interaction
- UX validation
- loading/error/empty states
- safe optimistic UI
- rendering server state

Frontend validation improves UX but never replaces server-side security validation.

## 10. Phase 6 — Code review

Review:

- correctness
- requirements coverage
- maintainability
- complexity
- duplication
- error handling
- race conditions
- authorization boundaries
- sensitive data handling
- logging
- tests
- API compatibility
- migrations
- observability
- security implications
- AI-generated behavior and assumptions

AI-generated code receives normal or increased scrutiny; it is never trusted merely because an agent produced it.

## 11. Phase 7 — AI abuse and adversarial testing

In an authorized test environment, ask an agent to attack the implemented workflows.

Probe:

- malformed and missing inputs
- wrong types
- oversized payloads
- duplicates and replay
- stale state
- concurrent requests
- unauthorized object IDs
- horizontal privilege escalation / IDOR / BOLA
- vertical privilege escalation
- invalid or expired credentials
- rate limits
- pagination/filtering/sorting abuse
- state-transition bypass
- webhook forgery/replay
- file-upload abuse
- prompt injection
- indirect prompt injection
- tool/API abuse
- secret leakage
- excessive error disclosure
- memory/context poisoning
- excessive agent autonomy
- cost and resource abuse

Every valid defect becomes a regression test before the fix is accepted.

## 12. Phase 8 — Static analysis and dependency security

Run applicable static and dependency security controls.

At minimum for production projects, consider:

- Semgrep
- CodeQL where language support is available
- dependency vulnerability scanning
- secrets scanning
- SBOM generation for releasable software where appropriate

Every finding must be:

- fixed
- documented as an accepted risk with owner, rationale and expiry
- or otherwise resolved according to project policy

Do not normalize scanner failures with blanket suppressions.

## 13. Phase 9 — OWASP ASVS verification

Use **OWASP ASVS 5.0.0 or the current applicable stable release** and select the verification level based on project risk.

For each applicable requirement, record:

- requirement identifier
- applicability
- implementation/evidence
- test or review evidence
- status
- owner
- exception/risk acceptance when applicable

ASVS is a verification baseline, not a substitute for threat modeling or penetration testing.

## 14. Phase 10 — Release evidence and gates

Before release, verify:

- specification and acceptance criteria are current
- critical tests pass
- regression suite passes
- API contracts are compatible
- static/dependency/secrets findings are triaged
- security requirements are verified
- ASVS evidence is complete for applicable controls
- migrations are reviewed
- secrets/configuration are ready
- observability is present
- rollback is understood
- smoke tests are defined
- required release evidence is recorded

Higher-risk systems may additionally require independent security review, DAST, penetration testing, backup/restore validation, disaster recovery testing, supply-chain provenance, or formal compliance evidence.

## 15. Phase 11 — Deploy and operate

Monitor:

- errors
- latency
- availability
- resource consumption
- authentication anomalies
- security events
- failed business workflows
- external integration failures
- AI/model/agent failures
- cost anomalies

Production findings feed back into specifications, regression tests, threat models, and backlog items.

## 16. Definition of Ready / Done

See [Definition of Ready and Definition of Done](definition-of-ready-done.md).

A change is not Ready because a prompt exists, and it is not Done because code compiles or a UI appears to work locally.

## 17. Change management and traceability

Prefer small changes with explicit intent.

Material changes should be traceable:

`requirement → user journey → workflow → architecture/ADR → implementation → test → security evidence → release → operational evidence`

Exceptions must be explicit rather than hidden in prompts or undocumented agent decisions.

## 18. Conformance

See [docs/governance.md](governance.md) for assurance levels, normative language, exceptions, and maintenance of this standard.
