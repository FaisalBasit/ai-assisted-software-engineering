# Frontend–Backend Contract

## Principle

The backend is the authoritative source of business behavior and persisted state.

## Backend owns

- authentication
- authorization
- input validation
- business rules
- state transitions
- persistence invariants
- integrations
- audit/security events
- server-side rate and abuse controls

## Frontend owns

- presentation
- navigation
- interaction
- UX validation
- loading/error/empty states
- safe optimistic UI
- rendering server state

Client-side validation is a UX optimization, never a security boundary.

## API contracts should define

- method and path
- purpose
- authentication
- authorization
- request schema
- response schema
- error model
- idempotency behavior
- pagination
- filtering/sorting rules
- rate limits where relevant
- side effects
- consistency expectations

Generated/shared types can reduce drift, but they do not replace server-side validation.
