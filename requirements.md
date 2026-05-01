# Requirements

This document enumerates the functional and non-functional requirements that the Ecowise
platform commits to, grouped by module. Functional requirements describe what the platform
does. Non-functional requirements describe how it behaves under load and what it guarantees.

## Table of contents

- [Conventions](#conventions)
- [Functional requirements](#functional-requirements)
- [Non-functional requirements](#non-functional-requirements)
- [Related documentation](#related-documentation)

## Conventions

Each requirement has a stable ID used elsewhere in the documentation set. The Validation
column points at the test category or manual verification path that demonstrates conformance.

## Functional requirements

### User and role management

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-01 | A visitor can sign up as Individual, Organisation, or Government. | UAT — signup flows |
| FR-02 | A user can verify their email via a one-time code. | manual — verify-email flow |
| FR-03 | A user can reset a forgotten password by one-time code. | manual — forgot-password flow |
| FR-04 | A user can change password while logged in. | manual — account settings |
| FR-05 | A user can edit their profile metadata and photo. | manual — profile screens |
| FR-06 | Any user can opt into the Investor role and opt back out. | manual — investor toggle |

### Projects and planning

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-07 | An organisation can create a project manually. | manual — project edit |
| FR-08 | An organisation or admin can generate a project from a single prompt. | manual — generator |
| FR-09 | A project owner can edit project metadata. | manual — edit form |
| FR-10 | A project owner can soft-delete a project. | manual — delete |
| FR-11 | A project owner can attach required skills with priority. | manual — skills picker |
| FR-12 | A project plan supports nested sections and tasks. | unit — plan tree builder |
| FR-13 | Plan sections can be marked serial or parallel. | unit — plan tree builder |
| FR-14 | Tasks can be assigned to platform users. | manual — assignee picker |
| FR-15 | Task assignees can change task status and add comments. | manual — task drawer |
| FR-16 | The web client renders the plan as an interactive flow. | manual — plan page |
| FR-17 | The mobile client renders the plan as a hierarchical list. | manual — plan screen |

### AI features

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-18 | A project carries an AI-generated overall tier. | manual — analysis page |
| FR-19 | AI analysis produces structured insights and SDG mappings. | schema — analysis result |
| FR-20 | Two projects can be compared side-by-side with scored dimensions. | manual — compare page |
| FR-21 | A per-project chatbot answers questions with project context loaded. | manual — chatbot widget |
| FR-22 | Chatbot replies may include navigation suggestions. | manual — observation |

### Issues and solutions

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-23 | A government user can publish a sustainability issue. | manual — issue create |
| FR-24 | An organisation can submit a solution to an issue. | manual — solution composer |
| FR-25 | An individual can upvote a solution. | manual — upvote button |
| FR-26 | An individual can register contributor interest. | manual — contribute button |
| FR-27 | A government user can accept the winning solution. | manual — accept dialog |
| FR-28 | An organisation can promote an accepted solution into a project. | manual — promote action |

### Investor and donor

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-29 | An investor can pledge against a project. | manual — pledge composer |
| FR-30 | A pledger can withdraw a pending pledge. | manual — withdraw |
| FR-31 | A project owner can accept or decline a pledge. | manual — pledge inbox |

### Events and volunteering

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-32 | A host can create, publish, edit, and cancel events. | manual — composer |
| FR-33 | An individual can register as attendee or volunteer. | manual — RSVP |
| FR-34 | A host can decide on registrations (approve, decline, check-in, no-show). | manual — roster |
| FR-35 | Events support comments and reactions. | manual — detail page |
| FR-36 | The events feed supports cursor pagination. | manual — feed |

### Messaging

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-37 | Any two users can start a direct conversation. | manual — start direct |
| FR-38 | A user can create a group conversation. | manual — start group |
| FR-39 | Per-participant unread state drives conversation and global badges. | manual — read markers |
| FR-40 | Group creators can add or remove participants. | manual — group settings |

### Calendar and recommendations

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-41 | A unified calendar lists RSVPed events, hosted events, and assigned tasks. | manual — calendar |
| FR-42 | The matcher returns recommended projects, issues, and candidates. | matcher scenario log |
| FR-43 | Recommendations expose role lanes (volunteer, investor, …). | manual — lane toggle |

### Government report

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-44 | A government user can generate a sustainability report for their account. | manual — report page |

### Admin

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-45 | Admins can approve or reject organisation and government verifications. | manual — verifications queue |
| FR-46 | Admins can take down and restore projects, issues, solutions, users, and reels. | manual — moderation |
| FR-47 | Admins can run an LLM moderation scan over flagged content. | manual — scan |
| FR-48 | Admins can create issues, projects, or hubs on behalf of others. | manual — create hub |
| FR-49 | The admin dashboard surfaces an LLM-generated platform brief. | manual — admin home |
| FR-50 | Admins can force the matcher to reload its in-memory snapshot. | manual — reload action |

### Cross-cutting

| ID | Requirement | Validation |
| --- | --- | --- |
| FR-51 | The web and mobile clients call the same backend API. | code review |
| FR-52 | Mobile achieves route parity with web. | parity roadmap |
| FR-53 | Auth tokens carry role claims. | code review |
| FR-54 | Public endpoints are explicitly whitelisted. | code review |
| FR-55 | The skill catalogue is read-only and seeded. | code review |
| FR-56 | Profile photos persist to managed object storage when configured. | code review |
| FR-57 | The platform supports a feature-flagged reels capability. | code review |

## Non-functional requirements

| ID | Requirement | Validation |
| --- | --- | --- |
| NFR-01 | Passwords are stored as salted, slow hashes. | code review |
| NFR-02 | Authentication tokens expire and clients refresh on focus. | code review |
| NFR-03 | Auth-protected endpoints reject anonymous callers. | RBAC tests |
| NFR-04 | Role-protected endpoints reject wrong-role callers. | RBAC tests |
| NFR-05 | The HTTP layer enforces a default CORS allowlist. | code review |
| NFR-06 | Database connection timeouts are configurable. | code review |
| NFR-07 | The schema targets third normal form. | docs — database-schema |
| NFR-08 | Critical state changes write to an immutable audit log. | code review |
| NFR-09 | Profile photo storage degrades gracefully when not configured. | manual — empty config boot |
| NFR-10 | Calls to the intelligence service have a bounded timeout. | code review |
| NFR-11 | LLM responses are validated against a typed schema before persistence. | schema tests |
| NFR-12 | Web bundles are code-split per major dependency. | code review |
| NFR-13 | Mobile reaches route parity with web. | parity roadmap |

## Related documentation

- [test-logs.md](test-logs.md)
- [uat-feedback.md](uat-feedback.md)
- [api-endpoints.md](api-endpoints.md)
- [Back to index](README.md)
