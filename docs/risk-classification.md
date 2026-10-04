# Risk Classification

Risk determines how much engineering evidence and security assurance is required.

## Classification

| Class | Typical impact | Minimum assurance |
|---|---|---|
| R0 — Low | Internal tooling, experiments, non-sensitive data | Level 1 |
| R1 — Moderate | Customer-facing software, ordinary business data | Level 2 |
| R2 — High | Sensitive data, financial workflows, privileged administration, important integrations | Level 2 + independent security review where warranted |
| R3 — Critical | Safety-critical, highly regulated, systemic privilege, material financial/security impact | Level 3 and formal risk/compliance review |

Classification is based on the highest credible impact, not the average feature.

## Risk factors

Evaluate:

- confidentiality impact
- integrity impact
- availability impact
- privilege/administrative power
- personal or regulated data
- financial impact
- external exposure
- dependency on third parties
- automation/autonomy
- AI agent tool access
- blast radius
- recovery difficulty
- regulatory/contractual obligations

## Change risk

A low-risk project can still contain a high-risk change. Reassess risk for:

- authentication/authorization changes
- payment or financial logic
- sensitive data handling
- external integrations
- migrations
- infrastructure changes
- agent/tool permissions
- security control changes
- cryptography
- major dependency changes

## Evidence principle

Higher risk requires stronger evidence, not simply more documentation.

Evidence may include tests, code review, security scans, threat-model decisions, ASVS verification, DAST results, penetration-test findings, restore tests, signed artifacts, and operational drills.
