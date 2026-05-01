# AI project generator

> One prompt → a complete project, plan, and skill list.

## Overview

The AI project generator turns a short description (a few sentences) into a fully-formed
project: a written description, sector and stage tags, the skills it needs, and a
hierarchical plan with sections and tasks. It is intended to remove the cold-start barrier
for organisations who know what problem they want to address but have not yet broken it down.

The output is structured — the LLM is constrained to match a Go schema — so what comes back
can be inserted directly into the platform's tables in a single transaction.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Accepts a short prompt and the caller's role context.
- Calls the LLM, validates the response against a Go schema, and inserts the project, plan,
  and required skills atomically.
- Returns the new project's identifier so the client can navigate to it.

## Who uses it

Organisation and administrator accounts.

## Key features

- Schema-validated output — the database stays in third normal form even when the LLM is the
  source.
- Single round-trip — no multi-step wizard.

## Related documentation

- [project-onboarding.md](project-onboarding.md)
- [project-planning.md](project-planning.md)
- [llm-schemas.md](../llm-schemas.md)
- [Back to index](../README.md)
