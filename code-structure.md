# Code structure

This document describes how the Ecowise platform is organised across its four source
repositories at a conceptual level. It explains the architectural style each repository uses
and the conventions that hold the platform together. Internal directory listings, file paths,
and package names are not mirrored here — the source repositories themselves are the
authoritative reference.

## Table of contents

- [Repository inventory](#repository-inventory)
- [Go backend](#go-backend)
- [Python intelligence service](#python-intelligence-service)
- [React web frontend](#react-web-frontend)
- [Flutter mobile companion](#flutter-mobile-companion)
- [Cross-repo conventions](#cross-repo-conventions)
- [Related documentation](#related-documentation)

## Repository inventory

| Repo | Tech | Style |
| --- | --- | --- |
| Backend | Go | Layered (router, middleware, service, repository, data) |
| Intelligence service | Python | Pipeline (load, compose, embed, score, write) |
| Web frontend | React + TypeScript | Domain modules (pages, API clients, hooks, components) |
| Mobile companion | Flutter | Feature folders with co-located data and presentation |

## Go backend

The Go backend is organised in layers. Requests enter through the HTTP router, pass through
authentication, role-gate, and CORS middleware, and reach a thin handler that unmarshals the
request, calls a service, and serialises the response. Business logic lives in service
packages that depend on a code-generated query layer and never on each other (a single admin
package is the exception, since it composes other services for cross-domain reads).

The query layer is generated from SQL using a code-generation step run during the build, so
typed query functions never go stale relative to the schema.

## Python intelligence service

The intelligence service follows a five-stage pipeline. The loader pulls the candidates it
needs from the shared database; the composers turn raw rows into typed profile objects; the
embedder produces vectors using a sentence-transformer model; the scorers combine per-dimension
scores into a single rank; and the writer persists the ranked output into matcher result
tables. The Go backend triggers refreshes and reads the persisted output.

## React web frontend

The web frontend is organised by domain. There is a one-to-one mapping between page components
and URL routes, and a one-to-one mapping between API client modules and backend domains. Hooks
encapsulate data fetching and caching for each domain, with centralised cache keys, optimistic
updates, and conflict handling. Components are grouped by domain with a shared library of
generic UI primitives. A small set of route guards (authenticated, host-only, organisation or
admin, admin-only) is applied at the router level.

## Flutter mobile companion

The mobile companion uses feature folders. Each feature contains a data layer (API client,
DTOs, providers) and a presentation layer (screens). Routing is centralised, with role-aware
redirects that mirror the web frontend's guards. A bottom-nav shell hosts the five primary
tabs, and full-screen routes live outside the shell. Build-time configuration carries the
backend base URL and feature flags.

## Cross-repo conventions

The two clients — web and mobile — call the same backend API and share a common authentication
contract. JWT bearer tokens carry user identity and dynamic role grants. Errors come back with
appropriate HTTP status codes and human-readable messages that both clients map to user-facing
copy. Most endpoints prefer JSON-bodied POST so filters and pagination cursors can travel
cleanly; a small number of catalogue reads use GET.

## Related documentation

- [installation.md](installation.md)
- [api-endpoints.md](api-endpoints.md)
- [database-schema.md](database-schema.md)
- [Back to index](README.md)
