# Sample tests

This document describes three representative tests in the Ecowise test suite, at three
different levels — a frontend unit test, a backend integration test, and a matching scenario
log. The intent is to communicate what the tests cover and how, not to mirror their source
code.

## Table of contents

- [Frontend unit test — plan tree builder](#frontend-unit-test--plan-tree-builder)
- [Backend integration test — pledge lifecycle](#backend-integration-test--pledge-lifecycle)
- [Matching scenario log](#matching-scenario-log)
- [Related documentation](#related-documentation)

## Frontend unit test — plan tree builder

The web frontend converts the flat plan rows it receives from the backend into a tree of nodes
and edges that the interactive flow chart renders. A unit suite covers every shape the
backend can return: empty plans, a lone root section, parent-child edges, serial-section
chains, parallel siblings, deeply nested hierarchies, orphan children, and sort-order
enforcement across siblings. The suite runs in the project's test runner as part of the
standard test command.

The test exists because the tree builder is the most algorithmic piece of plan rendering and
because shape regressions are easy to introduce when the flat input grows new fields. Keeping
this suite green means the visualisation always matches the backend's truth.

## Backend integration test — pledge lifecycle

The backend ships an integration test that exercises the pledge lifecycle end-to-end against a
fixture-loaded test database. The flow covers an investor creating a pledge against a
project, the project owner accepting the pledge, and the investor failing to withdraw it once
it has moved out of the pending state. The test ensures the state machine matches the
behaviour the product expects and catches accidental relaxations of the transitions.

This is one of several integration suites. Together they exercise the most consequential
state machines on the platform — pledge lifecycle, registration lifecycle, issue acceptance
and promotion, plan task transitions — against the real database, not a mock.

## Matching scenario log

The intelligence service writes a per-pair log every time it scores a candidate against an
entity. A representative log shows the per-dimension scores (semantic, skills, sectors, SDG
alignment, location, availability), the combined weighted score, the threshold the result
crossed, and a short rationale describing why the score landed where it did. The log makes
the otherwise-opaque ranking auditable — engineers can replay a scenario to understand why a
particular candidate appeared (or did not appear) in a recommendation list.

## Related documentation

- [test-logs.md](test-logs.md)
- [modules/project-planning.md](modules/project-planning.md)
- [modules/matching-engine.md](modules/matching-engine.md)
- [Back to index](README.md)
