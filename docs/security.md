# Security Standard

Security is a layered engineering discipline. No scanner, checklist, AI review, or ASVS assessment proves that software is secure.

## Security lifecycle

```
Threat model
    ↓
Secure architecture
    ↓
Secure implementation
    ↓
Tests + regression controls
    ↓
Semgrep / CodeQL / dependency / secrets analysis
    ↓
API / DAST / adversarial testing
    ↓
ASVS verification
    ↓
Human review
    ↓
Release evidence
    ↓
Production monitoring
    ↓
Incident → regression → control improvement
```

## Control layers

1. Threat modeling and secure architecture
2. Authentication and authorization design
3. Input validation and output handling
4. Secure state transitions and persistence invariants
5. Dependency and software supply-chain controls
6. Secrets management
7. Static analysis
8. API/DAST and abuse testing
9. OWASP ASVS verification
10. AI/agent security controls when applicable
11. Human review
12. Independent security testing when risk warrants it

## Tool roles

### OWASP ASVS

Use ASVS as a structured application-security verification baseline. Map applicable requirements to implementation and evidence.

The current stable ASVS baseline is 5.0.0. Projects should record the exact version used rather than relying on an unversioned checklist.

### Semgrep

Use Semgrep for fast pattern-based analysis, including project-specific rules.

### CodeQL

Use CodeQL for semantic analysis and deeper source/data-flow security queries where language support is available.

### Dependency and secrets analysis

Use appropriate ecosystem tooling for:

- known vulnerable dependencies
- malicious or suspicious packages
- leaked credentials
- unsafe configuration
- infrastructure/container dependencies where applicable

### AI security

When AI or agents are part of the system, additionally assess:

- prompt injection
- indirect prompt injection
- tool misuse
- excessive agency
- unsafe tool arguments
- data leakage
- cross-tenant retrieval
- memory/context poisoning
- output validation bypass
- denial-of-service and cost abuse

See [docs/ai-security.md](ai-security.md).

## Supply chain

For applicable projects, address:

- dependency review
- SBOM
- provenance
- CI token permissions
- action/dependency pinning
- protected branches
- release integrity

See [docs/supply-chain.md](supply-chain.md).

## Findings

A security finding must be:

1. fixed and verified;
2. documented as an accepted risk with accountable owner, rationale, compensating controls and expiry; or
3. otherwise resolved under the project's security process.

Do not use blanket suppressions to make CI green.

## Security exceptions

Exceptions must state:

- control being bypassed
- reason
- risk
- compensating controls
- owner
- expiry/review date
- approval authority

An expired exception is an open finding.

## Important limitation

A clean scanner result, passing ASVS checklist, or successful AI review does not prove security. Security assurance is contextual and depends on architecture, implementation, deployment, operations, threat landscape, and independent validation where warranted.
