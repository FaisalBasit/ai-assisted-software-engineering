# Governance and Conformance

## Purpose

This repository defines an engineering standard for AI-assisted software development. It is a methodology, not a certification scheme and not a substitute for applicable law, regulation, contractual controls, or independent security assessment.

## Normative language

The words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are used in their normal normative sense.

- **MUST / MUST NOT** — required for conformance.
- **SHOULD / SHOULD NOT** — expected unless a documented project-specific reason exists.
- **MAY** — optional.

## Conformance levels

### Level 1 — Disciplined

Required:

- project specification
- user journeys
- acceptance criteria
- TDD for material behavior
- code review
- regression tests for defects
- basic security review
- CI quality gates

### Level 2 — Production

Level 1 plus:

- threat model
- authorization matrix
- API/data contracts
- security scanning
- dependency and secrets controls
- release evidence
- rollback plan
- observability
- ASVS verification appropriate to risk

### Level 3 — High Assurance

Level 2 plus, where applicable:

- independent security review
- DAST/API security testing
- penetration testing
- supply-chain provenance/SBOM
- backup and restore validation
- disaster-recovery testing
- formal compliance evidence
- enhanced AI red-team evaluation
- stronger separation of duties

A project MAY adopt a higher level selectively for high-risk components.

## Exceptions

A deviation from a MUST requirement requires:

1. affected control
2. reason
3. risk assessment
4. compensating controls
5. accountable owner
6. expiry or review date
7. approval by the project's designated authority

Expired exceptions are treated as open findings.

## Standard maintenance

The standard itself follows the same discipline it recommends:

- changes are proposed through pull requests
- consequential decisions use ADRs
- normative changes include rationale and verification
- security-sensitive changes receive security review
- releases are versioned
- obsolete guidance is deprecated explicitly
- references to external standards are versioned or described as "current applicable version"

The standard must never claim certification or compliance merely because a project follows this repository.
