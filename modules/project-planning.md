# Project planning

> Sections and tasks under each project, with assignees and status.

## Overview

Project planning is the body of work inside each project. A plan is a tree of section and
task nodes with serial/parallel section semantics, due dates, durations, assignees pulled
from the user directory, and status transitions. The web client renders the plan as an
interactive flow chart; the mobile client renders a hierarchical list.

Tasks can carry their own required skills, which feed into the assignee recommender.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Create, edit, and reorder sections and tasks.
- Assign tasks to platform users; track status transitions.
- Show "my tasks" — every task assigned to the current user across projects.
- Visualise the plan as a flow on the web; as an indented list on mobile.

## Who uses it

Project owners (organisations), task assignees (individuals), and connected government users
who follow a related issue.

## Key features

- Optimistic concurrency — last-write-wins is rejected with a row-version conflict.
- Assignee recommender stacks the matcher output with task skills and live workload.
- Status transitions writable by both the owner and the assignee for accountability.

## Related documentation

- [project-onboarding.md](project-onboarding.md)
- [ai-project-generator.md](ai-project-generator.md)
- [sample-tests.md](../sample-tests.md)
- [Back to index](../README.md)
