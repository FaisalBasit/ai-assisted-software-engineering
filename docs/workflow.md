# Operating Workflow

Use this procedure for every meaningful feature.

## 1. GRILL

Challenge the requirement until users, outcomes, workflows, edge cases, constraints, permissions, data, and failure behavior are clear.

**Output:** clarified requirement and open questions.

## 2. SPEC

Update `your-project-spec/`.

**Output:** user journey, workflow, API contract, acceptance criteria, routes, and relevant security/operational requirements.

## 3. BLUEPRINT

Design boundaries, data flow, modules, APIs, authorization, failure handling, observability, migrations, tests, and implementation order.

**Output:** implementation plan and ADRs when needed.

## 4. TEST

Write a failing test for the next behavior.

**Rule:** test the contract/behavior, not private implementation details.

## 5. IMPLEMENT

Make the smallest change that satisfies the failing test.

## 6. VERIFY

Run focused tests, then the relevant broader suite.

## 7. REVIEW

Review the diff for correctness, maintainability, security, data exposure, authorization, race conditions, compatibility, and unnecessary changes.

## 8. ABUSE

In an authorized test environment, ask the AI agent to actively break the workflow using malformed inputs, privilege escalation, replay, concurrency, boundary conditions, prompt injection, and integration failures.

## 9. SCAN

Run Semgrep and, where applicable, CodeQL.

## 10. ASVS

Verify applicable OWASP ASVS controls and record evidence.

## 11. FIX

Any discovered defect follows:

`reproduce → failing regression test → fix → green → scan`

## 12. REVERIFY

Repeat tests and security verification after fixes. Do not trust a fix that has not been re-tested.

## 13. RELEASE

Only release when required quality/security gates are green and unresolved risks are explicitly accepted.

## 14. OPERATE

Monitor production and turn incidents, vulnerabilities, and recurring defects into durable engineering controls.

## Agent change contract

Before changing code, an AI agent should report:

- relevant specification
- affected workflow
- acceptance criteria
- intended files/modules
- tests to add/update
- security implications
- assumptions
- unresolved questions

After changing code, it should report:

- tests executed
- results
- changed files
- scan results
- security considerations
- known limitations
- remaining risks

Never accept "looks good" as evidence.
