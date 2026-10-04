# Testing Standard

## Testing layers

Use the smallest test level that proves the behavior, with critical end-to-end coverage.

1. **Unit tests** — pure logic and isolated rules.
2. **Integration/API tests** — contracts, persistence, authorization, external boundaries.
3. **End-to-end tests** — critical user journeys and high-value workflows.
4. **Adversarial/abuse tests** — deliberate attempts to violate assumptions and security boundaries.

## TDD rules

- derive tests from the specification
- write behavior before implementation
- verify the test fails for the expected reason
- implement the smallest useful change
- keep the test after the bug/feature is fixed
- refactor only after green
- prefer stable public contracts
- keep tests deterministic
- isolate external systems appropriately
- avoid tests that merely mirror implementation structure

## Bug-driven TDD

Every confirmed bug should become a regression test.

```
Reproduce
  ↓
Write failing regression test
  ↓
Fix
  ↓
Green
  ↓
Refactor
  ↓
Security scan
  ↓
Review
```

## AI abuse testing

Abuse testing is complementary to normal TDD. It asks:

> "What can a malicious, careless, concurrent, malformed, or adversarial caller make this system do?"

Use only environments and accounts you are authorized to test.

## Release evidence

At release time retain appropriate evidence for:

- test results
- critical journey coverage
- API contract checks
- security scan results
- ASVS verification
- migration checks
- smoke tests
- unresolved risk acceptance
