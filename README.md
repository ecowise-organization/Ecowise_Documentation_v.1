# Ecowise Capstone Documentation

This repository is the supporting technical documentation for the Ecowise capstone project — a
multi-service, AI-powered sustainability coordination platform. It is organized into top-level
cross-cutting documents, per-module deep dives, and appendix material that backs the capstone
final report. The documentation is generated from and verified against the actual source code
across the four Ecowise components: the backend, the intelligence service, the web frontend,
and the mobile companion.

## Table of contents

- [Quick start](#quick-start)
- [For graders](#for-graders)
- [Top-level documentation](#top-level-documentation)
- [Module documentation](#module-documentation)
- [Appendix documentation](#appendix-documentation)
- [Repositories](#repositories)
- [Conventions](#conventions)

## Quick start

Setting up the Ecowise platform locally is covered end-to-end in
[**installation.md**](installation.md). It documents the prerequisites for each service, the
configuration each service needs, and the order in which to bring everything up. New
contributors should read it before anything else.

## For graders

The capstone final report is the canonical narrative artifact. This repository is the technical
appendix that supports it.

- **Capstone final report**: <!-- TODO: replace with the actual path or URL once available -->
- **Requirements traceability**: see [requirements.md](requirements.md) — every functional and
  non-functional requirement has a Validation column linking back to the test or manual check
  that covers it.
- **Use cases and flows**: see [use-cases.md](use-cases.md) for actor-by-actor walkthroughs and
  [user-manual.md](user-manual.md) for screen-by-screen journeys.
- **Architecture overview**: start with [code-structure.md](code-structure.md), then
  [database-schema.md](database-schema.md), then [api-endpoints.md](api-endpoints.md).
- **Security posture**: [security.md](security.md).
- **Testing evidence**: [test-logs.md](test-logs.md) and [sample-tests.md](sample-tests.md).
- **User acceptance**: [uat-feedback.md](uat-feedback.md).

## Top-level documentation

The cross-cutting documents are read first; module docs reference them.

| Document | Description |
| --- | --- |
| [**requirements.md**](requirements.md) | Functional requirements (FR-01..FR-57) and non-functional requirements (NFR-01..NFR-13), grouped by module, each row carrying a Validation column referencing the test or manual check that covers it. |
| [**use-cases.md**](use-cases.md) | Use cases per actor (Founder, NGO, Government, Investor, Volunteer, Specialist, Administrator), with primary, alternate, and exception flows, plus embedded UML diagrams. |
| [**uml-diagrams.md**](uml-diagrams.md) | Sequence, activity, state, and class diagrams for key flows (pledge submission, AI analysis pipeline, matcher load and re-rank, issue→solution→promotion, event registration lifecycle, project plan DAG). |
| [**database-schema.md**](database-schema.md) | Full schema reference — Mermaid ERs, tables grouped by domain, indexing strategy, JSONB columns, 3NF normalization notes. |
| [**ui-screenshots.md**](ui-screenshots.md) | Inventory of every primary page on web and mobile with screenshot placeholders, plus the design system documentation for both clients. |
| [**security.md**](security.md) | Defence-in-depth model: bcrypt, JWT, RBAC middleware, rate limiting, input validation, audit log, threat model, incident response, key rotation. |
| [**code-structure.md**](code-structure.md) | High-level architectural style of each of the four repositories and the conventions that hold the platform together. |
| [**installation.md**](installation.md) | Prerequisites, environment variables, per-service setup commands, production deployment sketch. |
| [**user-manual.md**](user-manual.md) | Step-by-step walkthroughs for every primary user journey across roles. |
| [**api-endpoints.md**](api-endpoints.md) | Complete endpoint inventory grouped by module — method, path, auth requirement, request/response schemas, status codes, examples. |
| [**sample-tests.md**](sample-tests.md) | Three representative tests at three levels — a frontend unit test, a backend integration test, and a matching scenario log. |
| [**llm-schemas.md**](llm-schemas.md) | Conceptual description of the structured contracts the platform uses with the language model for each AI feature. |
| [**test-logs.md**](test-logs.md) | Test categories with pass/fail counts and a bug-fix history of notable issues encountered and resolved during development. |
| [**uat-feedback.md**](uat-feedback.md) | Three rounds of UAT findings with scripted tasks, participant counts, severity, resolution status, and follow-up actions. |

## Module documentation

Each module document covers responsibilities, architecture, data model, endpoints, frontend and
backend code locations, primary workflows, edge cases, permissions, and testing for that module.

| Module | Description |
| --- | --- |
| [**user-and-role-management**](modules/user-and-role-management.md) | Identity supertype/subtype model, registration flows for the four base roles, role grants (Investor), JWT issuance, account settings. |
| [**project-onboarding**](modules/project-onboarding.md) | Project creation (manual and AI-generated), edit, soft-delete, ownership, required-skills, project listing scopes. |
| [**ngo-portfolio**](modules/ngo-portfolio.md) | Organization-side surfaces — wins, accepted solutions, project portfolio, organization profile, verification. |
| [**government-and-reporting**](modules/government-and-reporting.md) | Government issue publication, government profile, sustainability report (ISO 26000 / GRI aggregations). |
| [**investor-and-donor**](modules/investor-and-donor.md) | Investor role enablement, pledge creation, pledge inbox for project owners, accept/decline flow, investor dashboard. |
| [**messaging**](modules/messaging.md) | Direct and group conversations, message send, read markers, unread counts, participant management. |
| [**analytics-dashboards**](modules/analytics-dashboards.md) | Admin and role-specific dashboard KPIs, recent activity feeds, country atlas, engagement metrics. |
| [**matching-engine**](modules/matching-engine.md) | The Python intelligence service — loader, composers, embedder, scorers, writer; Go-side caller and result tables. |
| [**ai-project-generator**](modules/ai-project-generator.md) | Single-shot AI project generation (project + plan), `generate_project_llm.go`, prompt structure, schema enforcement. |
| [**ai-project-analysis**](modules/ai-project-analysis.md) | Per-project AI analysis (SDG mapping, insights, overall tier), result tables, history view. |
| [**ai-project-comparison**](modules/ai-project-comparison.md) | Pairwise project comparison, scoring, history, comparison list. |
| [**per-project-chatbot**](modules/per-project-chatbot.md) | Project-scoped chatbot for owners and contributors, chat turns, navigation suggestions. |
| [**project-planning**](modules/project-planning.md) | Hierarchical plan with sections and tasks, serial/parallel sections, assignees, status, and an interactive tree visualisation on the web. |
| [**issues-and-solutions**](modules/issues-and-solutions.md) | Government-issued challenges, organization-submitted solutions, upvotes, contributor interest, acceptance, promotion to project. |
| [**events-and-volunteering**](modules/events-and-volunteering.md) | Event posts, registration lifecycle, host roster decisions, comments, reactions, calendar integration. |
| [**calendar**](modules/calendar.md) | Per-user unified calendar — RSVPed events, hosted events, project tasks. |
| [**admin-panel**](modules/admin-panel.md) | Admin dashboard, verifications queue, moderation queues (projects, issues, solutions), AI moderation scan, create-on-behalf hub. |

## Appendix documentation

The appendix bundles cross-cutting reference material that supplements the modules.

| Document | Purpose |
| --- | --- |
| [use-cases.md](use-cases.md) | Actor-driven scenarios for the capstone evaluation. |
| [uml-diagrams.md](uml-diagrams.md) | Mermaid diagrams for the report. |
| [ui-screenshots.md](ui-screenshots.md) | Screenshot inventory and design system. |
| [security.md](security.md) | Threat model and controls. |
| [user-manual.md](user-manual.md) | End-user walkthroughs. |
| [sample-tests.md](sample-tests.md) | Representative test artifacts. |
| [llm-schemas.md](llm-schemas.md) | LLM I/O schema reference. |
| [test-logs.md](test-logs.md) | Test categories and bug-fix history. |
| [uat-feedback.md](uat-feedback.md) | UAT rounds, findings, resolutions. |

## Repositories

The platform spans four source repositories and one shared database.

| Repository | Role | Tech |
| --- | --- | --- |
| Backend | RESTful API service | Go |
| Intelligence service | Matching, analysis, generation, comparison, chatbot | Python |
| Web frontend | Web client | React + TypeScript |
| Mobile companion | iOS and Android app | Flutter |
| Shared store | Relational database | PostgreSQL |

The seven user roles served by the platform are Founder (project-owning individual), NGO,
Government, Investor, Volunteer, Specialist, and Administrator. Roles map onto four storage
profiles (Individual, Organization, Government, Admin) with two dynamic role grants (Investor,
Specialist).

## Conventions

- **GitHub-flavored Markdown**. Tables, fenced code blocks with language hints, task lists.
- **Mermaid for diagrams**. ER, sequence, activity, state, class — GitHub renders these
  natively in the web UI.
- **Exact identifiers**. Real table names, real route paths, real status enum values, real file
  paths. Any unresolved gap is marked with `<!-- VERIFY: ... -->`.
- **No marketing language**. Every sentence carries technical content.
- **Cross-links**. Each document ends with a `Related documentation` section linking to two to
  four sibling documents and back to this index.

## Related documentation

- [installation.md](installation.md)
- [code-structure.md](code-structure.md)
- [api-endpoints.md](api-endpoints.md)
- [requirements.md](requirements.md)
