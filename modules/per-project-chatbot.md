# Per-project chatbot

> A conversational helper that already knows the project.

## Overview

The per-project chatbot is a context-aware assistant attached to every project page. It
already has the project's metadata, plan, required skills, and analysis history loaded, so
users can ask things like "what skills are we still missing?", "summarise the plan", or "draft
a stakeholder update" without re-explaining the project each turn. Replies can include
navigation suggestions — short pointers to other parts of the app, like the pledge inbox or
the analysis page.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Accepts a free-text turn from the user along with the active project ID.
- Returns a free-text reply plus optional navigation hints.
- Re-checks per-project visibility on every turn so the bot doesn't leak data.

## Who uses it

Any authenticated user viewing a project they have access to.

## Key features

- Visibility-aware — owner, contributor, connected government, and admin views see different
  context surfaces.
- Navigation suggestions reduce the click cost of acting on a reply.

## Related documentation

- [llm-schemas.md](../llm-schemas.md)
- [project-onboarding.md](project-onboarding.md)
- [project-planning.md](project-planning.md)
- [Back to index](../README.md)
