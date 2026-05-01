# Matching engine

> Recommends projects, candidates, and assignees using semantic matching.

## Overview

The matching engine is the AI service that powers every "recommended for you" surface on
Ecowise. It is a separate Python intelligence service that takes user profiles, projects, and
issues, turns them into vectors using a semantic-similarity model, and scores how well any
two pair on dimensions like sector, skills, SDG alignment, location, and availability. The
backend triggers a re-rank when a user updates skills or a project changes scope, and
persists the ranked output for fast read-side serving.

Volunteers see "projects for you"; project owners see "candidates for your project"; issue
owners see "solvers for your issue"; task owners see "best people to assign this task to."

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Loads candidates (users, projects, issues) from the shared database.
- Composes typed profiles from raw rows.
- Embeds text fields into vectors using a semantic-similarity model.
- Scores per-dimension and combines into a single rank.
- Persists results for fast retrieval and refreshes on relevant changes.

## Who uses it

Indirectly, every user — through the recommendation lists on the dashboard, project pages,
and issue pages. Administrators can force a snapshot reload from the admin panel.

## Key features

- Multi-dimension scoring rather than a single semantic score.
- Persisted results table makes reads cheap; only re-ranks pay the model cost.
- Lane selection (`as=volunteer`, `as=investor`, …) lets one user view recommendations
  through different role lenses.

## Related documentation

- [ai-project-analysis.md](ai-project-analysis.md)
- [analytics-dashboards.md](analytics-dashboards.md)
- [code-structure.md](../code-structure.md)
- [Back to index](../README.md)
