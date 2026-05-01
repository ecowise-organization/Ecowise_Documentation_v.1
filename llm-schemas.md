# LLM schemas

This document describes how the Ecowise platform contracts with the language model. Every AI
feature sends a structured prompt and validates the response against a typed schema before
persistence. The schemas themselves live in the source repository; this document explains
their shape conceptually.

## Table of contents

- [Why structured](#why-structured)
- [Project analysis](#project-analysis)
- [Project comparison](#project-comparison)
- [Generated project](#generated-project)
- [Per-project chat turn](#per-project-chat-turn)
- [Operational brief](#operational-brief)
- [Related documentation](#related-documentation)

## Why structured

Free-text language model output is not reliable enough to write directly into a normalised
database. Each AI feature on Ecowise wraps the model with a typed schema: the schema is sent
in the prompt, the response is parsed back into the schema, and a parse failure is treated as
a hard error rather than a silent truncation. This keeps the database in third normal form
even when the language model is the source of the data.

## Project analysis

The project analysis schema carries an overall tier, a list of insights, and a mapping of
relevant Sustainable Development Goals. The tier is one of four stable bands used for
comparison and reporting. Each insight is a short titled paragraph. Each SDG mapping links a
goal code to a short rationale.

## Project comparison

The project comparison schema carries a list of per-dimension metrics with a score for each
side and a list of qualitative insights. Dimensions cover mission alignment, scope,
sustainability impact, capability fit, and execution readiness. The shape supports a clean
side-by-side rendering on the comparison page.

## Generated project

The generated-project schema carries everything needed to insert a complete project in a
single transaction: title, description, sector and stage codes, required skills, and a
hierarchical plan of sections and tasks. The plan piece nests sections and tasks recursively,
so one model round-trip produces a fully-populated project.

## Per-project chat turn

The chat-turn schema carries a free-text reply and an optional list of navigation
suggestions. Each suggestion is a short label plus a destination cue. Navigation suggestions
let the chatbot reduce the click cost of acting on a reply.

## Operational brief

The operational brief schema carries a one-line headline, a small list of highlights, and a
small list of concerns. The shape is what the admin dashboard reads to render its plain-English
platform digest.

## Related documentation

- [modules/ai-project-analysis.md](modules/ai-project-analysis.md)
- [modules/ai-project-comparison.md](modules/ai-project-comparison.md)
- [modules/ai-project-generator.md](modules/ai-project-generator.md)
- [Back to index](README.md)
