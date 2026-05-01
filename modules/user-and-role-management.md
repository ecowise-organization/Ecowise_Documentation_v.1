# User and role management

> Identity, registration, and role grants for every Ecowise user.

## Overview

This module is the front door to Ecowise. Anyone using the platform starts here by signing
up as one of three base account types (Individual, Organization, Government), verifying their
email, and completing the profile fields specific to that type. Existing users come back here
to update account settings, change passwords, and reset forgotten passwords through one-time
codes. A small number of accounts created directly by the team carry the Administrator type.

On top of the base type, users can opt into the dynamic Investor role — a one-tap grant that
unlocks the pledging surfaces. The grant is reversible.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Three signup paths (individual, organisation, government) each with their own profile fields.
- Email verification and password reset by one-time passcode.
- Profile editing (name, bio, location, links, photo) per user type.
- Investor role enable/disable with JWT reissue.

## Who uses it

Every user. The administrator queues in the [admin panel](admin-panel.md) act on rows owned
by this module (verifications, takedowns).

## Key features

- Single email/password login regardless of base type.
- Profile photo upload to managed object storage (degrades gracefully when storage is not configured).
- Lightweight role model: type fixed at signup, dynamic roles layered on top.

## Related documentation

- [security.md](../security.md)
- [admin-panel.md](admin-panel.md)
- [Back to index](../README.md)
