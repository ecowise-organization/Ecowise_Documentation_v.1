# UML diagrams

This document collects conceptual diagrams for the most important flows and lifecycles on the
platform. Diagrams use Mermaid so GitHub renders them inline. The diagrams describe behaviour
at a feature level — they are not derived from the source code structure.

## Table of contents

- [Investor pledge submission](#investor-pledge-submission)
- [AI project analysis pipeline](#ai-project-analysis-pipeline)
- [Matcher load and re-rank](#matcher-load-and-re-rank)
- [Issue → solution → acceptance → promotion](#issue--solution--acceptance--promotion)
- [Event registration lifecycle](#event-registration-lifecycle)
- [Related documentation](#related-documentation)

## Investor pledge submission

```mermaid
sequenceDiagram
  participant Investor
  participant Client as Web/Mobile
  participant Platform
  Investor->>Client: Open project, choose Pledge
  Client->>Platform: Submit pledge
  Platform-->>Client: Pledge created, status pending
  Client-->>Investor: Confirmation; visible in pledge inbox
```

## AI project analysis pipeline

```mermaid
sequenceDiagram
  participant Owner
  participant Platform
  participant LLM as Language model
  Owner->>Platform: Request analysis
  Platform->>Platform: Gather project context
  Platform->>LLM: Structured prompt + schema
  LLM-->>Platform: Structured response
  Platform->>Platform: Validate against schema
  Platform-->>Owner: Analysis with tier, insights, SDG mapping
```

## Matcher load and re-rank

```mermaid
sequenceDiagram
  participant Platform
  participant Matcher as Intelligence service
  Platform->>Matcher: Refresh request
  Matcher->>Matcher: Load candidates
  Matcher->>Matcher: Compose, embed, score
  Matcher-->>Platform: Persisted ranked results
  Platform-->>Platform: Read top-N for clients
```

## Issue → solution → acceptance → promotion

```mermaid
flowchart TD
  A[Government publishes issue] --> B[Organisations submit solutions]
  B --> C[Individuals upvote and register interest]
  C --> D{Government accepts?}
  D -- yes --> E[Winning organisation promotes to project]
  D -- no --> B
  E --> F[Project enters planning, matching, pledges]
```

## Event registration lifecycle

```mermaid
stateDiagram-v2
  [*] --> Pending: individual registers
  Pending --> Approved: host approves
  Pending --> Declined: host declines
  Approved --> CheckedIn: on event day
  Approved --> NoShow: after event window
  Pending --> Withdrawn: individual withdraws
  Approved --> Withdrawn: individual withdraws
  CheckedIn --> [*]
  NoShow --> [*]
  Declined --> [*]
  Withdrawn --> [*]
```

## Related documentation

- [use-cases.md](use-cases.md)
- [database-schema.md](database-schema.md)
- [modules/project-planning.md](modules/project-planning.md)
- [Back to index](README.md)
