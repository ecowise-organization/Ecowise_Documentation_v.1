# Security

This document describes Ecowise's defence-in-depth posture. It is an overview of the controls
in place rather than an exhaustive procedural runbook.

## Table of contents

- [Overview](#overview)
- [Password hashing](#password-hashing)
- [Token authentication](#token-authentication)
- [Role-based access control](#role-based-access-control)
- [Input validation](#input-validation)
- [Audit log](#audit-log)
- [Threat model](#threat-model)
- [Incident response](#incident-response)
- [Key rotation](#key-rotation)
- [Related documentation](#related-documentation)

## Overview

Defence is layered. Authentication establishes who is calling. Authorisation checks what they
can do, both at the routing layer and through per-entity ownership checks inside services.
Inputs are validated at the boundary before any business logic runs. Sensitive state changes
write to an immutable audit log. Secrets are scoped so a compromise in one path does not
cascade.

## Password hashing

Passwords are hashed with a slow, salted hashing algorithm before storage. Plaintext passwords
never reach the database or the audit log.

## Token authentication

Logins issue a signed bearer token containing the user's identity and the dynamic roles they
hold. The token is sent on every authenticated request. A middleware layer enforces the
token's presence and validates its signature on all paths except an explicit public whitelist —
login, registration, password reset, the public skill catalogue, and the health probe.

## Role-based access control

Each route declares the roles that may call it. A failed gate returns a permission error before
any handler runs. Inside services, ownership checks add a second layer — for example, even an
organisation user cannot edit a project they do not own. Services are responsible for the
ownership check; the route gate is a coarse first screen.

## Input validation

Request bodies are validated server-side. Bodies that fail validation are rejected with a
structured error before any business logic runs.

## Audit log

Sensitive state changes — verification decisions, takedowns, role grants, pledge accept and
decline — write append-only rows to an audit log. The log is never updated or deleted from
application code.

## Threat model

| Threat | Mitigation |
| --- | --- |
| Stolen authentication token | Short token lifetimes; clients clear on the first failed call; secret rotated on incident. |
| Brute-force login | Slow password hashing slows offline attempts; rate limits expected at the edge. |
| SQL injection | All queries go through a parameterised, code-generated layer; no string concatenation. |
| Privilege escalation | Role gate at the routing layer plus ownership checks inside services. |
| LLM prompt injection | Model responses are validated against a typed schema before persistence. |
| Sensitive data leak | Optional storage credentials degrade to a no-op when omitted; takedowns recorded in the audit log. |

## Incident response

1. Detect — alerts on authentication-failure spikes, takedown bursts, or unusual matcher
   latency.
2. Contain — rotate the token signing secret, which forces all sessions to re-authenticate;
   take down compromised content.
3. Eradicate — patch the cause in code; redeploy.
4. Recover — restore taken-down legitimate content if applicable.
5. Post-mortem — record findings in the bug-fix history.

## Key rotation

The token signing secret is rotated by deploying a new value through configuration. All
currently-issued tokens fail signature checks after rotation, and clients re-authenticate
automatically when the next call returns an authentication error. Third-party API keys
(language model provider, transactional email, object storage) are rotated in their respective
consoles, the new value is updated in configuration, and a redeploy is triggered.

## Related documentation

- [modules/admin-panel.md](modules/admin-panel.md)
- [modules/user-and-role-management.md](modules/user-and-role-management.md)
- [api-endpoints.md](api-endpoints.md)
- [Back to index](README.md)
