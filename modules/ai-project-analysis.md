# AI project analysis

> A standing AI assessment of a project's sustainability impact and SDG fit.

## Overview

AI project analysis runs a structured assessment over a single project and produces an
overall tier (Bronze / Silver / Gold / Platinum), a list of insights, and a mapping of
relevant UN Sustainable Development Goals. The result is persisted, so a project owner can
see the assessment evolve as they edit. Multiple analyses can exist per project; the latest
appears by default with a history view available.

The assessment is a useful sanity check and pitch helper — it surfaces gaps a project owner
might not have considered and gives investors a quick visual of how the project rates.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Runs an LLM analysis over the project's metadata, plan, and required skills.
- Persists the result with insights and SDG mappings.
- Exposes a latest-only view and a history view.

## Who uses it

Organisation and administrator accounts.

## Key features

- History preserved — owners can see how the assessment changes over edits.
- Structured SDG mapping makes it easy to filter or report.

## Related documentation

- [ai-project-comparison.md](ai-project-comparison.md)
- [llm-schemas.md](../llm-schemas.md)
- [project-onboarding.md](project-onboarding.md)
- [Back to index](../README.md)
