# AI and Agent Security

AI features and coding agents introduce risks that ordinary application controls do not fully capture.

## Applicability

This document applies when a system:

- uses an LLM or foundation model
- retrieves untrusted content
- executes tools or functions
- changes state autonomously
- delegates work between agents
- stores model context or memory
- processes model-generated code or commands
- uses AI to make consequential decisions

## Core controls

### 1. Treat model output as untrusted

Model output MUST NOT be treated as a trusted security decision merely because it came from an approved model.

Validate:

- schema
- authorization
- business invariants
- allowed tools
- allowed destinations
- data classification
- state transitions

### 2. Least-privilege tools

Agents SHOULD receive only the tools and permissions required for the current task.

Separate:

- read from write capabilities
- low-impact from high-impact actions
- planning from execution
- user-authorized from autonomous actions

High-impact actions SHOULD require explicit authorization or human approval.

### 3. Prompt injection resistance

Treat external documents, webpages, emails, retrieved text, and tool results as potentially adversarial.

Do not allow untrusted content to silently redefine:

- system policy
- authorization
- tool permissions
- data-handling rules
- release decisions

### 4. Data boundaries

Define which data an AI feature may:

- read
- retain
- retrieve
- send to providers
- expose to users
- use for training or evaluation

Prevent cross-tenant and cross-user retrieval.

### 5. Agent execution controls

Use:

- tool allowlists
- argument validation
- timeouts
- rate limits
- budgets
- recursion/step limits
- sandboxing where needed
- audit logs
- approval gates
- kill switches for high-impact systems

### 6. Memory and context

Treat persistent memory as application data and an attack surface.

Define:

- ownership
- provenance
- retention
- update authorization
- deletion
- isolation
- poisoning defenses

### 7. AI red teaming

For applicable systems, test:

- prompt injection
- data exfiltration
- tool misuse
- privilege escalation
- unsafe tool arguments
- indirect prompt injection
- memory/context poisoning
- excessive agency
- denial of service/cost abuse
- model-output validation bypass
- cross-user data leakage

Every confirmed vulnerability becomes a regression test where practical.

## External guidance

Projects SHOULD track current OWASP GenAI guidance and applicable AI security frameworks. For agentic systems, the OWASP Top 10 for Agentic Applications and Agent Control Standard are relevant references.

AI security does not replace conventional application security; it extends it.
