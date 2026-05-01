# UI screenshots and design system

This document inventories the primary pages on the web and mobile clients and documents the
design tokens shared across them. Screenshot files live under `assets/ui/`; placeholders below
mark the canonical capture surface for each page.

## Table of contents

- [Capture conventions](#capture-conventions)
- [Web pages](#web-pages)
- [Mobile screens](#mobile-screens)
- [Design tokens](#design-tokens)
- [Related documentation](#related-documentation)

## Capture conventions

> Screenshots are captured by the engineering team. Web at 1440 px wide, mobile at 414 px wide
> (iPhone reference frame). Light mode unless noted.

## Web pages

| Page | Capture |
| --- | --- |
| Landing | `assets/ui/web-landing.png` |
| Login | `assets/ui/web-login.png` |
| Signup hub | `assets/ui/web-signup-hub.png` |
| Dashboard | `assets/ui/web-dashboard.png` |
| Projects list | `assets/ui/web-projects.png` |
| Project overview | `assets/ui/web-project-overview.png` |
| Project plan | `assets/ui/web-project-plan.png` |
| Project compare | `assets/ui/web-project-compare.png` |
| Issues list | `assets/ui/web-issues.png` |
| Issue detail | `assets/ui/web-issue-detail.png` |
| Events feed | `assets/ui/web-events-feed.png` |
| Event detail | `assets/ui/web-event-detail.png` |
| Messages | `assets/ui/web-messages.png` |
| Calendar | `assets/ui/web-calendar.png` |
| Profile (individual) | `assets/ui/web-profile-individual.png` |
| Profile (organisation) | `assets/ui/web-profile-org.png` |
| Profile (government) | `assets/ui/web-profile-gov.png` |
| Investor dashboard | `assets/ui/web-investor.png` |
| Government report | `assets/ui/web-gov-report.png` |
| Admin dashboard | `assets/ui/web-admin-dashboard.png` |
| Admin verifications | `assets/ui/web-admin-verifications.png` |
| Admin moderation | `assets/ui/web-admin-moderation.png` |

## Mobile screens

| Screen | Capture |
| --- | --- |
| Splash | `assets/ui/mob-splash.png` |
| Onboarding | `assets/ui/mob-onboarding.png` |
| Login | `assets/ui/mob-login.png` |
| Dashboard | `assets/ui/mob-dashboard.png` |
| Issues list | `assets/ui/mob-issues.png` |
| Issue detail | `assets/ui/mob-issue-detail.png` |
| Projects list | `assets/ui/mob-projects.png` |
| Project overview | `assets/ui/mob-project-overview.png` |
| Project plan (list) | `assets/ui/mob-project-plan.png` |
| Inbox | `assets/ui/mob-inbox.png` |
| Thread | `assets/ui/mob-thread.png` |
| Profile | `assets/ui/mob-profile.png` |
| Events feed | `assets/ui/mob-events-feed.png` |
| Event detail | `assets/ui/mob-event-detail.png` |
| Calendar | `assets/ui/mob-calendar.png` |
| Investor dashboard | `assets/ui/mob-investor.png` |
| Admin dashboard | `assets/ui/mob-admin-dashboard.png` |

## Design tokens

The two clients use parallel design systems that share the same visual identity. The web
client expresses the system as CSS custom properties; the mobile client expresses it as a
typed theme module.

### Colour palette

| Role | Hue |
| --- | --- |
| Brand primary | Deep evergreen |
| Brand secondary | Teal |
| Surface | White |
| Background | Near-white grey |
| Text primary | Near-black |
| Border | Light grey |
| Danger | Red |

### Typography

A modern humanist sans-serif provides the body type, paired with a geometric display face for
headings on mobile and a single neutral sans on the web. A monospace face is reserved for
small numeric and code-style content.

### Spacing scale

Both clients use a four-unit base scale stepping up through twenty-four units, used uniformly
for padding, gaps, and margins.

### Radius and elevation

Both clients use a five-step radius scale from extra-small to extra-large, plus a fully
rounded option for circular elements. Elevations cover four steps from a subtle shadow to a
maximum elevation reserved for floating UI.

## Related documentation

- [user-manual.md](user-manual.md)
- [code-structure.md](code-structure.md)
- [Back to index](README.md)
