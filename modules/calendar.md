# Calendar

> A unified per-user calendar of events and tasks.

## Overview

The calendar pulls three sources into a single chronological view: events the user has
registered for, events the user is hosting, and project tasks assigned to the user. There is
no separate calendar to maintain — the items appear automatically as registrations happen and
tasks are assigned. The view supports a date-range query so the same screen powers
day, week, and month views.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Aggregates RSVPed events, hosted events, and assigned tasks into one feed.
- Filters by a from/to date range.
- Tags each item with its kind so the client can render distinct visuals.

## Who uses it

Every authenticated user.

## Key features

- Read-only — there is nothing to edit on the calendar; you change the underlying registration
  or task and the calendar follows.
- Same endpoint serves the web and mobile clients.

## Related documentation

- [events-and-volunteering.md](events-and-volunteering.md)
- [project-planning.md](project-planning.md)
- [analytics-dashboards.md](analytics-dashboards.md)
- [Back to index](../README.md)
