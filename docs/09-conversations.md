---
title: Conversations
---

A dedicated admin screen (outside the settings tabs), linked from the
sidebar. Native WordPress table with every recorded conversation.

![Conversations](/img/screenshots/conversations.png)

## Search and filter

- **Search** by contact name, email, or phone.
- **Status filter**: all / active / blocked.

## Columns

ID, Contact (name/email/phone if provided), Status, Strikes, Messages
(message count), Last activity.

## Per-row actions

- **Unblock** — reactivates a specific blocked conversation (a precise
  alternative to "Unblock all conversations" in Moderation, which
  reactivates all of them at once).
- **Delete** — permanently deletes the conversation and its messages.
  Asks for confirmation before running.

## Export contacts (CSV)

One click downloads a CSV with every conversation that has at least
one piece of contact data: ID, name, email, phone, consent date (if
given), date. Useful both for sales follow-up and for privacy audits.
