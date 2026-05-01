# Project onboarding

> Creating, editing, and listing projects on the platform.

## Overview

Project onboarding is how an organisation gets work onto Ecowise. A project can be created two
ways: filled out by hand from the project edit form, or generated end-to-end from a single
prompt by the [AI project generator](ai-project-generator.md). Once a project exists,
organisations can edit its metadata, attach the skills it needs, and either keep it private or
publish it to be discovered by volunteers, collaborators, and investors.

The project list page exposes scopes — projects I own, projects I'm contributing to, projects
recommended for me by the matcher.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Manual project creation through a multi-section form.
- AI-assisted project generation (org & admin only).
- Edit metadata: title, description, sector, stage, funding interest.
- Manage required skills with priority (must-have / nice-to-have).
- Soft-delete with optional cascade to plan and pledges.

## Who uses it

Organisation accounts own projects. Administrators can also create projects on behalf of an
organisation through the [admin create hub](admin-panel.md). Individuals and governments can
view and discover projects, but cannot own them.

## Key features

- Optimistic concurrency on edit — last write wins is rejected with a row-version conflict.
- Rich list shapes for the dashboard and the comparison picker.
- Recommendation lanes powered by the [matching engine](matching-engine.md).

## Related documentation

- [project-planning.md](project-planning.md)
- [ai-project-generator.md](ai-project-generator.md)
- [matching-engine.md](matching-engine.md)
- [Back to index](../README.md)
