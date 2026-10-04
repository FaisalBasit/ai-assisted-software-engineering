# AI Agent Contract

This document is a reusable instruction contract for AI coding agents.

## Before coding

The agent MUST:

1. read the applicable project specification
2. identify the exact user journey/workflow
3. restate acceptance criteria
4. inspect relevant existing code and tests
5. identify intended files/modules
6. identify tests to add or change
7. identify security and data-flow implications
8. identify migrations or compatibility risks
9. state assumptions
10. stop when requirements conflict or critical information is missing

## While coding

The agent SHOULD:

- make small, coherent changes
- preserve existing behavior unless the specification changes it
- follow repository conventions
- avoid unrelated refactors
- prefer explicit error handling
- keep authorization server-side
- add regression tests for defects
- avoid disabling security controls to make tests pass
- avoid broad dependency upgrades unless requested

## After coding

The agent MUST report:

- changed files
- tests executed and results
- static-analysis results
- security considerations
- migrations/configuration changes
- unresolved risks
- follow-up work

## Forbidden shortcuts

Do not:

- claim tests passed without running them
- claim a scanner passed without running it
- hide failures with blanket `continue-on-error`
- remove validation to satisfy a test
- weaken authorization to simplify a workflow
- expose secrets in logs or test fixtures
- silently change requirements
