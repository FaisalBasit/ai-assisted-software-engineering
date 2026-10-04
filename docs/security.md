# Security Standard

Security is a layered engineering discipline. No scanner, checklist, or AI review proves that software is secure.

## Control layers

1. Threat modeling and secure architecture
2. Authentication and authorization design
3. Input validation and output handling
4. Secure state transitions and persistence invariants
5. Dependency and supply-chain controls
6. Secrets management
7. Static analysis
8. API/DAST and abuse testing
9. OWASP ASVS verification
10. Human review
11. Independent security testing when risk warrants it

## Tool roles

### OWASP ASVS

Use ASVS as a structured application-security verification baseline. Map applicable requirements to implementation and evidence.

### Semgrep

Use Semgrep for fast pattern-based analysis, including project-specific rules.

### CodeQL

Use CodeQL for semantic analysis and deeper source/data-flow security queries where language support is available.

### Relationship

```
Threat model
    ↓
Secure design
    ↓
Secure implementation
    ↓
Semgrep ─────┐
             ├→ findings → fix → regression test → verify
CodeQL ──────┘
    ↓
ASVS verification
    ↓
Human review
    ↓
Independent testing when warranted
```

A clean scanner result does not mean an application is secure.

## Security exceptions

Exceptions must state:

- control being bypassed
- reason
- risk
- compensating controls
- owner
- expiry/review date
