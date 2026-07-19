---
title: Chat Behavior
sidebar_position: 7
---

Two sub-tabs: Behavior and Spend Limit.

## Behavior

![Chat Behavior — Behavior](/img/screenshots/chat-behavior-behavior.png)

- **Conversation timeout (minutes)** — minutes of inactivity before
  the next message starts a new conversation instead of continuing
  the previous one. Defaults to 60 (1 hour). Examples: 30 = half an
  hour, 1440 = 24 hours.
- **Max messages per conversation** — hard cap on messages within a
  single conversation (default 40, range 2–500), independent of the
  time-based limit. Protects against the cost of an abnormally long
  conversation. This is a total-length cap, not an abuse control —
  starting a new conversation resets it. See "Messages per session"
  below for the actual abuse throttle.
- **Conversation limit message** — what the visitor sees once that cap
  is reached. Contacts and the WhatsApp number are appended
  automatically, same as the other limit messages on this page.
- **Messages per session (abuse prevention)** — blocks a visitor who
  sends more messages than this within the time window below (default
  20 messages). This is a sliding window: each new message extends it,
  so an active abuser never earns a fresh quota by simply waiting it
  out. It resets on its own once the window passes with no new messages.
- **Session limit window (minutes)** — the sliding time window the
  count above is measured over (default 10).
- **Rate limit message** — what the visitor sees while rate-limited.
  Contacts and the WhatsApp number are appended automatically here too.

## Spend Limit

![Chat Behavior — Spend Limit](/img/screenshots/chat-behavior-spend-limit.png)

The budget "kill switch": measures **actual** spend (input, output,
and cache tokens reported by Anthropic, each at its real rate), not
an estimate.

- **Daily spend limit (USD)** — 0 = no limit. Next to the field, the
  **live estimated spend for today** is shown.
- **Spend limit message** — what the visitor sees once the limit is
  reached. Contacts and the WhatsApp number (Widget & WhatsApp) are
  automatically appended at the end — no need to repeat them here.
- **Notification email** — who to notify when the limit is reached or
  the account runs out of credits. Empty = uses the site admin's
  email. At most one email per day per cause.
- **Editable subject/body** for the two cases separately: "Daily
  Limit Reached" and "Account Out of Credits". Today's spend, the
  limit, and a link to these settings are automatically appended
  below the text you write.

### What happens when the limit is reached

The assistant stops replying for the rest of the day (it doesn't keep
spending). The admin sees a notice with today's spend/limit and a
**"Resume assistant now"** button to resume it manually ahead of time
(resets the counter). If not clicked, it resumes on its own at
**midnight, site time**.

### "Out of credits" detection

If Anthropic reports that the account ran out of balance, the plugin
distinguishes this from a temporary network error: it stops trying
calls for the rest of the day (no wasted requests against an empty
account) and shows the visitor the same human contact fallback as
with the daily limit.

### Not dependent on WP-Cron

The counter keeps its own date and resets itself when the day
changes — it works the same whether the site's cron is disabled or
broken, unlike other plugins that rely on a cron job to reset daily
counters.
