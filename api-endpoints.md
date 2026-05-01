# API endpoints

This document is a high-level summary of the API surface the Ecowise platform exposes. It
describes the categories of endpoints offered by each module rather than listing exact paths,
methods, or request/response shapes — those live in the source repositories and are not
mirrored here.

## Table of contents

- [Conventions](#conventions)
- [Authentication](#authentication)
- [User profile and roles](#user-profile-and-roles)
- [Projects](#projects)
- [AI features](#ai-features)
- [Pledges](#pledges)
- [Issues and solutions](#issues-and-solutions)
- [Project planning](#project-planning)
- [Events and volunteering](#events-and-volunteering)
- [Reels](#reels)
- [Messaging](#messaging)
- [Calendar and recommendations](#calendar-and-recommendations)
- [Government report](#government-report)
- [Admin](#admin)
- [Skills and lookups](#skills-and-lookups)
- [Python intelligence service](#python-intelligence-service)
- [Related documentation](#related-documentation)

## Conventions

All endpoints sit under a versioned API prefix. Authenticated requests carry a bearer token;
a small whitelist (login, registration, password reset, public catalogues, health) is open.
Role gates run at the router layer for every protected endpoint, with ownership checks layered
inside the relevant service. Errors return appropriate 4xx/5xx codes and a human-readable
message.

## Authentication

The authentication surface covers login, three role-specific signup flows, email verification
by one-time passcode, password reset by one-time passcode, password change while logged in,
and account-settings updates.

## User profile and roles

The profile surface covers reading and updating per-role profiles (individual, organisation,
government), uploading and deleting profile photos, looking up and searching users, listing
the dynamic roles a user holds, and toggling the Investor role grant. Individual users can
also manage their personal skill list.

## Projects

The project surface covers list, get, create, update, and soft-delete operations. List
endpoints accept scope filters so the dashboard, the comparison picker, and the owner panel
can each fetch the right shape. A separate family of endpoints manages required skills on a
project.

## AI features

AI features include a single-shot project generator, on-demand project analysis with history,
pairwise project comparison with history, and the per-project chatbot.

## Pledges

The pledge surface lets investors create and withdraw pledges, lists a user's own pledges,
and gives project owners an inbox where they accept or decline incoming pledges.

## Issues and solutions

The issues surface covers the full collaboration loop — government issue create/update/delete,
solution create/update/delete, upvotes and contributor interest by individuals, acceptance by
the issue owner, and promotion of an accepted solution to a full project. Read endpoints serve
public listings, filtered listings, and per-user views (my upvotes, my contributing).

## Project planning

The planning surface lets owners create and reorder sections and tasks, edit nodes with
optimistic concurrency, and soft-delete subtrees. Task assignees can update status and add
comments. A "my tasks" endpoint lists tasks assigned to the calling individual across all
projects.

## Events and volunteering

The events surface covers a cursor-paginated feed, search, detail reads, comments, and
reactions for any authenticated user. Hosts (organisations, governments, administrators)
create, edit, publish, cancel, and soft-delete events; manage roster decisions; and upload or
delete cover media. Individuals register and withdraw their own registrations.

## Reels

Reels endpoints support a feed, individual reel reads, upload, view counters, reactions,
comments, reports, and author deletion. The feature is gated off in mobile by a build flag.

## Messaging

The messaging surface lists conversations with last-message previews and unread counts; opens
direct or group threads (direct openings are idempotent); sends, lists, and marks messages
read; manages group participants; and exposes a global unread counter.

## Calendar and recommendations

The calendar endpoint accepts a date range and returns a heterogeneous list — RSVPed events,
hosted events, assigned tasks — keyed by item kind. Recommendation endpoints return matched
projects, issues, collaborator candidates, solver candidates, and task assignee suggestions,
with a lane parameter that lets one user view through different role lenses. Owner-only refresh
endpoints request a re-rank.

## Government report

A single endpoint generates a sustainability report bound to the calling government account.

## Admin

The admin surface is restricted to administrators and includes the dashboard overview, an
LLM-generated platform brief, a paged verifications queue with approve/reject decisions,
takedown and restore actions across projects, issues, solutions, users, and reels, an LLM
moderation scan, and a forced reload of the matching engine snapshot.

## Skills and lookups

A read-only catalogue surface returns the platform's skill list, sustainability sectors, and
project lifecycle stages. The skill catalogue is publicly readable so the signup wizard can
populate its picker before the user has a token.

## Python intelligence service

The Go backend calls the Python intelligence service over HTTP for matching, ranking, and
related operations. The exact endpoint shape lives in the Ecowise-Matching-ML repository.

## Related documentation

- [code-structure.md](code-structure.md)
- [security.md](security.md)
- [database-schema.md](database-schema.md)
- [Back to index](README.md)
