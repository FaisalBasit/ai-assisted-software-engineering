# Threat Model

## System

Describe the system, major components, and data flows.

## Assets

List sensitive or business-critical assets.

## Actors

- anonymous users
- authenticated users
- privileged users
- administrators
- service accounts
- external providers
- malicious actors

## Trust boundaries

Document where trust changes between:

- browser/client and API
- API and database
- application and third-party services
- users and privileged operations
- AI agents and tools/data

## Threats

For each important flow consider:

- spoofing
- tampering
- repudiation
- information disclosure
- denial of service
- elevation of privilege
- prompt injection/tool abuse for AI systems
- data poisoning or unsafe model/tool inputs

## Mitigations

For every significant threat document prevention, detection, response, and verification.

## Residual risk

Record accepted risks, owners, compensating controls, and review dates.
