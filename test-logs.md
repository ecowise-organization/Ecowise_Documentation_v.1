# Test logs

This document summarises the platform's testing categories at a high level and records a short
bug-fix history. It is intended as evidence for testing claims made elsewhere in the
documentation set.

## Table of contents

- [Categories](#categories)
- [Frontend unit tests](#frontend-unit-tests)
- [Backend unit and integration tests](#backend-unit-and-integration-tests)
- [Role-based access tests](#role-based-access-tests)
- [Matching engine validation](#matching-engine-validation)
- [LLM schema validation](#llm-schema-validation)
- [Bug-fix history](#bug-fix-history)
- [Related documentation](#related-documentation)

## Categories

| Category | Scope |
| --- | --- |
| Frontend unit | Pure logic helpers — tree builders, layout, filters, formatters. |
| Backend unit | Service-layer logic in isolation. |
| Integration | Service-layer against a fixture-loaded database. |
| Role-based access | Role gates and ownership checks across protected endpoints. |
| Matching | Per-dimension scoring sanity through scenario logs. |
| LLM schema | Language model responses parse cleanly into typed schemas. |
| Mobile smoke | Boot path renders. |

## Frontend unit tests

Unit tests cover the algorithmic pieces of the web frontend — building the plan tree from flat
rows, laying out the resulting graph, counting characters for text measurement, validating
event filters, formatting relative times, and grouping consecutive messages by author.
Together these guard the parts of the rendering pipeline most prone to silent regression.

## Backend unit and integration tests

Each service package carries its own unit and integration tests. The integration tests boot
against a fixture-loaded database and exercise the most consequential state machines on the
platform — pledge lifecycle, registration lifecycle, issue acceptance and promotion, plan task
transitions — against the real database, not a mock.

## Role-based access tests

Each role-gated route is covered by tests that assert a wrong-role caller is rejected, an
unauthenticated caller is rejected, and a correctly-roled caller receives the expected
response shape. This catches both routing-layer gate regressions and ownership-check
regressions inside services.

## Matching engine validation

End-to-end matcher runs are checked against a small fixture set with known top-N results. The
per-pair scenario log makes the otherwise-opaque ranking auditable.

## LLM schema validation

Every AI feature has a schema-validation test that feeds canned language model responses
through the parser. Malformed responses must produce a hard error rather than partial
persistence.

## Bug-fix history

| Phase | Issue | Resolution |
| --- | --- | --- |
| Polish | Mobile back-button contrast on light app bars | Stand-alone visual audit; standardised on a dark ink for back-icon colour. |
| Polish | Legacy analysis route returned an error on missing project | Redirect now degrades gracefully. |
| Late development | Optimistic plan edits dropped on rapid double-edit | Added optimistic-concurrency conflict detection. |
| Late development | Investor role token not refreshing on enable | Role grant now reissues the token and the client persists it. |
| Mid development | Project compare timed out on large projects | Server-side trim of project text before model call. |
| Mid development | Match results stale after skill edits | Refresh trigger on user-skill writes. |

## Related documentation

- [sample-tests.md](sample-tests.md)
- [requirements.md](requirements.md)
- [uat-feedback.md](uat-feedback.md)
- [Back to index](README.md)
