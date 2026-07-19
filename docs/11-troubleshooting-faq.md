---
title: Troubleshooting / FAQ
sidebar_position: 14
---

## "The widget doesn't show up on my site"

Check in this order:

1. **Is there an API key saved?** Without one, the widget doesn't load
   at all (see [Getting Started](01-primeros-pasos.md)). The admin
   itself shows a notice in the meantime.
2. **Are you inside a page builder's editor** (Bricks, Etch)? The
   widget is intentionally hidden there — load the regular page
   (outside the editor) to see it.
3. **Is the current page excluded by Visibility?** Check
   Widget & WhatsApp → Visibility (see
   [Widget & WhatsApp](04-widget-whatsapp.md)).

## "The assistant stopped replying"

Almost always one of these two causes, both visible in Chat Behavior →
Spend Limit:

- The configured **daily spend limit** was reached.
- The Anthropic account **ran out of credits**.

In both cases there's a **"Resume assistant now"** button to resume
before it resets on its own (at midnight, or once the account is
topped up).

## "A visitor got blocked for no reason"

Check Conversations to unblock that specific conversation, or
Moderation → "Unblock all conversations" if the problem is widespread
(strikes threshold set too low, for example — worth raising it before
it happens again).

## "Test connection says the key is invalid but I'm sure it's correct"

Check that there are no extra spaces when pasting it, and that it
hasn't been revoked from the Anthropic console itself. If the error is
"couldn't connect" (not "invalid key"), the problem is the server's
network, not the key — confirm the server allows outbound HTTPS
requests.

## "A notice appears saying automatic cleanup isn't running"

It means WP-Cron is disabled or broken on the site, so the configured
retention (Privacy & Data) isn't being applied. If WP-Cron was
disabled on purpose (common on high-traffic sites), you'll need to set
up a real server cron that runs `wp-cron.php` periodically.

## "The Skip button doesn't show up" / "It shows up but shouldn't"

Depends on two settings in Privacy & Data, not just one — see
[Privacy & Data](08-privacy-data/index.md) for the exact interaction
between "Allow visitors to skip" and "Require consent checkbox".
