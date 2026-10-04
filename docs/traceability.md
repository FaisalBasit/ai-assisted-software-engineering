# Traceability and Evidence

Production engineering should make important decisions and verification results traceable.

## Required chain

For material functionality, maintain this chain:

`requirement → user journey → workflow → architecture/ADR → API/data contract → implementation → test → security evidence → release → operational evidence`

Not every node is required for a trivial change, but omissions must be intentional.

## Traceability identifiers

Projects SHOULD assign stable IDs:

- `REQ-###` — requirement
- `UJ-###` — user journey
- `WF-###` — workflow
- `API-###` — API contract
- `SEC-###` — security control
- `TEST-###` — verification
- `ADR-###` — architecture decision
- `RISK-###` — risk/exception

## Evidence quality

Evidence should be:

- specific
- reproducible
- attributable
- current
- linked to the requirement/control
- retained for the appropriate project lifecycle

"Tests exist" is weaker evidence than "TEST-014 passed against the acceptance criteria for UJ-007 in CI run X."

## Change impact

When a requirement or contract changes, identify affected:

- journeys
- workflows
- APIs
- data migrations
- tests
- security controls
- operational procedures

A change is not complete until affected evidence is refreshed.
