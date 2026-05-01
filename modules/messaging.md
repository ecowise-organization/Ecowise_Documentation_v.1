# Messaging

> Direct and group conversations between platform users.

## Overview

Messaging is Ecowise's in-app communication channel. Any two users can start a direct
conversation; any user can start a group with several others. Conversations carry an ordered
stream of text messages with optional attachment links. Read receipts are per-participant —
each user maintains a "last read" marker, which drives unread badges on the inbox row and the
global tab badge.

There is no real-time push; clients poll the inbox every 15 seconds and the unread counter
every 30 seconds.

## Table of contents

- [What it does](#what-it-does)
- [Who uses it](#who-uses-it)
- [Key features](#key-features)
- [Related documentation](#related-documentation)

## What it does

- Start a direct conversation (idempotent — re-opening returns the existing thread).
- Create a group conversation with multiple participants.
- Send and read messages with cursor pagination back through history.
- Mark a conversation read; per-conversation and global unread counts.
- Add or remove group participants (creator / self-leave).

## Who uses it

Every authenticated user. Direct messaging is open across user types — organisations and
volunteers can chat directly without a project handshake.

## Key features

- Same API serves the React web `MessagesPage` and the Flutter mobile `InboxScreen` /
  `ThreadScreen`.
- Polling keeps the implementation simple; no WebSocket infrastructure to operate.

## Related documentation

- [api-endpoints.md](../api-endpoints.md)
- [user-and-role-management.md](user-and-role-management.md)
- [admin-panel.md](admin-panel.md)
- [Back to index](../README.md)
