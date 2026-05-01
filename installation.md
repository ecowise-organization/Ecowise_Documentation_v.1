# Installation

This document is a high-level guide to getting Ecowise running locally for development. It
covers the prerequisites, the configuration the platform needs, and the order in which to
bring up the services. Exact commands, environment variable names, and script paths live in
each source repository's own README and are not mirrored here.

## Table of contents

- [Prerequisites](#prerequisites)
- [Repositories](#repositories)
- [Configuration](#configuration)
- [Database](#database)
- [Backend](#backend)
- [Intelligence service](#intelligence-service)
- [Web frontend](#web-frontend)
- [Mobile companion](#mobile-companion)
- [Production deployment sketch](#production-deployment-sketch)
- [Related documentation](#related-documentation)

## Prerequisites

| Tool | Used by |
| --- | --- |
| Go (recent toolchain) | Backend |
| Python (recent toolchain) | Intelligence service |
| Node.js (LTS) | Web frontend |
| Flutter SDK (current stable) | Mobile companion |
| Docker and Docker Compose | Local PostgreSQL, optional service containers |
| SQL code-generation CLI | Backend build step |
| Optional Go linter | Backend build step |

## Repositories

Clone the four source repositories side-by-side under a single workspace folder. The shared
PostgreSQL store is provisioned by the backend repository's Docker Compose file.

## Configuration

Each service reads its configuration from process environment variables. At minimum, you will
configure:

- The database connection string.
- The signing secret for authentication tokens.
- The base URL of the intelligence service.
- The base URL the clients use to reach the backend.
- Optional credentials for transactional email and object storage; both degrade gracefully
  when omitted in development.

Production deployments must override the defaults — the development defaults are weak by
design.

## Database

The backend repository ships a Docker Compose file that runs PostgreSQL locally with the
default credentials baked into the development configuration. Once Postgres is up, run the
fixture loader provided by the backend to create the schema, tables, and seed data needed for
tests. Stop the container when you are finished.

## Backend

Build the backend through its build script, which runs the code-generation step, the linter
(if installed), the static checker, and the build itself. Run the test suite against the
fixture-loaded database to verify everything is wired up. The repository ships a pre-push hook
that runs the same build script before allowing a push.

## Intelligence service

Run the Python intelligence service from its own repository. For local development you can
point the backend at the local Python process by overriding the matching service base URL. A
hosted instance is used in production.

## Web frontend

Install dependencies, then start the development server for hot-reloading. A production bundle
can be produced and previewed locally before deployment. The unit test runner exercises the
algorithmic helpers. The production build splits major dependencies into separate bundles to
keep the main entrypoint small.

## Mobile companion

Fetch dependencies and run the app on a connected device or simulator, passing the backend
base URL and any feature flags as build-time defines. Release builds use the same pattern with
production values.

## Production deployment sketch

A deployment-grade topology for Ecowise looks roughly like this:

1. Managed PostgreSQL behind a private network.
2. Containerised backend behind a load balancer, configured from secrets.
3. Containerised intelligence service reachable only from the backend.
4. Static web frontend served from a CDN with the production API URL baked in at build time.
5. Mobile release builds shipped through TestFlight and Play Console.
6. Transactional email through a managed provider.
7. Object storage for profile photos.

## Related documentation

- [code-structure.md](code-structure.md)
- [api-endpoints.md](api-endpoints.md)
- [security.md](security.md)
- [Back to index](README.md)
