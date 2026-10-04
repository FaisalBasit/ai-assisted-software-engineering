# Engineering Standard

## 1. Purpose

This standard defines how to use AI coding agents to design, implement, test, review, secure, release, and operate production software.

The standard is deliberately technology-agnostic. Framework-specific commands belong in the consuming project.

## 2. Roles and accountability

The AI agent is an implementation partner. It must not silently become:

- product owner
- architect of record
- security authority
- compliance approver
- release approver

Humans own requirements, risk acceptance, architectural decisions, security exceptions, and production release decisions.

## 3. Phase 0 — Grill-Me

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

## 4. Phase 1 — Project specification

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

A feature is not ready for implementation if its externally observable behavior cannot be described clearly enough to test.

## 5. Phase 2 — Blueprint / architecture

Produce a lightweight architecture plan before significant implementation.

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

For consequential decisions, create an ADR.

## 6. Phase 3 — Backend and data contracts

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

## 7. Phase 4 — TDD vertical slices

For each behavior:

1. write the test from the specification
2. confirm the test fails for the expected reason
3. implement the smallest change
4. make the test pass
5. refactor while preserving behavior
6. run the relevant suite
7. update the specification when behavior intentionally changes

Prefer tests against public behavior and contracts over implementation details.

## 8. Phase 5 — Frontend integration

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

## 9. Phase 6 — Code review

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

AI-generated code deserves the same or greater scrutiny as human-generated code.

## 10. Phase 7 — AI abuse testing

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
- prompt injection against AI features
- tool/API abuse
- secret leakage
- excessive error disclosure
- unsafe agent autonomy

Every valid defect becomes a regression test before the fix is accepted.

## 11. Phase 8 — Static analysis

Run Semgrep on relevant changes and in CI.

Use custom rules when project-specific security or correctness patterns matter.

Use CodeQL where the language is supported and deeper semantic/data-flow analysis is valuable.

Every finding must be:

- fixed
- documented as an accepted risk with owner and rationale
- or otherwise resolved according to project policy

Do not normalize scanner failures with blanket suppressions.

## 12. Phase 9 — OWASP ASVS verification

Use the applicable current ASVS version and verification level.

For each applicable requirement, record:

- requirement identifier
- applicability
- implementation/evidence
- test or review evidence
- status
- owner
- exception/risk acceptance when applicable

ASVS is a verification baseline, not a substitute for threat modeling or penetration testing.

## 13. Phase 10 — Release gates

Before release, verify:

- specification and acceptance criteria are current
- critical tests pass
- regression suite passes
- API contracts are compatible
- static analysis findings are triaged
- security requirements are verified
- ASVS evidence is complete for applicable controls
- migrations are reviewed
- secrets/configuration are ready
- observability is present
- rollback is understood
- smoke tests are defined

Higher-risk systems may additionally require independent security review, DAST, penetration testing, backup/restore validation, disaster recovery testing, or formal compliance evidence.

## 14. Phase 11 — Deploy and operate

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

Production findings feed back into specifications, regression tests, threat models, and backlog items.

## 15. Change management

Prefer small changes with explicit intent.

A change should be traceable from:

`requirement → design → implementation → test → security evidence → release`

Exceptions must be explicit rather than hidden in prompts or undocumented agent decisions.
