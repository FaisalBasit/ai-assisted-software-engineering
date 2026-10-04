# Operating Workflow

Use this procedure for every meaningful feature or change.

## 1. GRILL

Challenge the requirement until users, outcomes, workflows, edge cases, constraints, permissions, data, and failure behavior are clear.

**Output:** clarified requirement, assumptions, decisions and open questions.

## 2. SPEC

Update `your-project-spec/`.

**Output:** user journey, workflow, API contract, acceptance criteria, routes, and relevant security/operational requirements.

## 3. CLASSIFY

Assign a project/change risk class.

**Output:** assurance level and required evidence.

## 4. BLUEPRINT

Design boundaries, data flow, modules, APIs, authorization, failure handling, observability, migrations, tests, security controls, and implementation order.

**Output:** implementation plan and ADRs when needed.

## 5. READY CHECK

Confirm the change satisfies the Definition of Ready.

**Output:** implementation-ready change.

## 6. TEST

Write a failing test for the next behavior.

**Rule:** test the contract/behavior, not private implementation details.

## 7. IMPLEMENT

Make the smallest change that satisfies the failing test.

## 8. VERIFY

Run focused tests, then the relevant broader suite.

## 9. REVIEW

Review the diff for correctness, maintainability, security, data exposure, authorization, race conditions, compatibility, migrations, observability, and unnecessary changes.

## 10. ABUSE

In an authorized test environment, ask the AI agent to actively break the workflow using malformed inputs, privilege escalation, replay, concurrency, boundary conditions, prompt injection, memory poisoning, tool abuse, and integration failures.

## 11. SCAN

Run applicable:

- Semgrep
- CodeQL
- dependency vulnerability scanning
- secrets scanning
- SBOM generation
- supply-chain checks

## 12. ASVS

Verify applicable OWASP ASVS controls and record evidence.

## 13. FIX

Any discovered defect follows:

`reproduce → failing regression test → fix → green → scan`

## 14. REVERIFY

Repeat tests and security verification after fixes. Do not trust a fix that has not been re-tested.

## 15. EVIDENCE

Update traceability and release evidence.

**Rule:** evidence must be specific and reproducible.

## 16. RELEASE

Only release when required quality/security gates are green and unresolved risks are explicitly accepted by the appropriate authority.

## 17. OPERATE

Monitor production and turn incidents, vulnerabilities, and recurring defects into durable engineering controls.

## Agent change contract

Before changing code, an AI agent should report:

- relevant specification
- affected workflow
- risk classification
- acceptance criteria
- intended files/modules
- tests to add/update
- security implications
- assumptions
- unresolved questions

After changing code, it should report:

- tests executed and results
- changed files
- scan results
- security considerations
- migrations/configuration
- known limitations
- remaining risks
- evidence updated

Never accept "looks good" as evidence.
