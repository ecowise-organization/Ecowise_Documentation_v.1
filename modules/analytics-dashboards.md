# Analytics dashboards

> Role-aware home screens with KPIs and quick actions.

## Overview

The dashboards module is what every user sees first after logging in. The content is shaped
by the user's role: an admin sees platform health KPIs, a country atlas, and recent activity;
an organisation sees its wins and quick actions for project creation; a government user sees
its issues and the sustainability report shortcut; an individual sees recommendations and the
event discover feed.

Nothing is owned by this module directly — it is a read-side projection of data from
projects, issues, events, pledges, and users.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Role-aware welcome card with the current date and unread counts.
- Quick-action tiles tailored to the user's role.
- Recommendations feed (projects / issues / collaborators).
- Discover section — recent events for non-admins, pending verifications for admins.

## Who uses it

Every authenticated user.

## Key features

- Single endpoint per dashboard variant — the backend assembles the role-specific shape so
  the client just renders.
- AI brief on the admin dashboard summarises platform state in plain English.

## Related documentation

- [admin-panel.md](admin-panel.md)
- [matching-engine.md](matching-engine.md)
- [calendar.md](calendar.md)
- [Back to index](../README.md)
