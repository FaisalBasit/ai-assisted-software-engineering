# Definition of Ready and Definition of Done

## Definition of Ready

A feature or change is **Ready** when:

- the problem and desired outcome are clear
- scope and non-goals are stated
- affected actors are known
- the relevant user journey exists
- workflows and state transitions are understood
- API/data contracts are defined where applicable
- authorization requirements are defined
- acceptance criteria are testable
- edge/failure cases are identified
- security/privacy implications are understood
- operational constraints are known
- open questions that block implementation are resolved
- the implementation approach is sufficiently planned

## Definition of Done

A feature or change is **Done** when:

- implementation matches the approved specification
- acceptance tests pass
- regression tests exist for discovered defects
- API/data contracts remain consistent
- authorization is enforced server-side
- relevant code review is complete
- Semgrep and applicable static analysis are clean or triaged
- security verification is complete for the change
- observability is sufficient
- migrations/configuration are reviewed
- documentation/specification is updated
- release evidence is captured
- unresolved risks are explicitly accepted or scheduled

A change is not Done merely because the code compiles or the UI works locally.
