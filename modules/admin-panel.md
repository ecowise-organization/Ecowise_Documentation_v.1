# Admin panel

> Operational surfaces for the platform team.

## Overview

The admin panel is the platform-operations surface, restricted to administrators. It rolls up
the admin dashboard (KPIs, country atlas, recent activity, and an AI-generated platform brief),
the verification queue for organisations and governments, the moderation queues for projects,
issues, and solutions (with takedown and restore), an LLM-powered moderation scanner that
sweeps for likely policy violations, and a "create hub" that lets an admin create issues,
projects, or hubs on behalf of other users.

It is the tool the team uses to keep Ecowise healthy.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Dashboard KPIs and AI brief.
- Approve / reject organisation and government verifications.
- Take down and restore projects, issues, solutions, users, and reels.
- Run an LLM moderation scan over flagged or recent content.
- Create on behalf of users via the create hub.
- Force a matching-engine reload.

## Who uses it

Administrators only. All routes are gated behind the ADMIN role.

## Key features

- One scanner endpoint sweeps across entity types so the team can triage in one place.
- Takedown and restore are symmetric — every removal is reversible.
- AI brief gives a plain-English read of the platform without a dashboard tour.

## Related documentation

- [analytics-dashboards.md](analytics-dashboards.md)
- [security.md](../security.md)
- [user-and-role-management.md](user-and-role-management.md)
- [Back to index](../README.md)
