---
title: Getting Started
slug: /
sidebar_position: 1
---

## Requirements

- WordPress 6.0 or higher.
- PHP 8.1 or higher.
- An Anthropic (Claude) API key — billed directly by Anthropic, the
  plugin doesn't resell tokens or add a markup on AI usage.

## Installation

1. Upload the plugin ZIP from Plugins → Add New → Upload Plugin, and
   activate it.
2. On activation, WordPress **automatically** takes you to the
   **AI Provider** tab — no need to go looking for it.
3. Paste your Anthropic API key and click **Test connection** to
   confirm it works before saving (see
   [AI Provider](02-ai-provider.md)).
4. Go to **License** and paste the key from your purchase confirmation
   email to enable automatic updates and support (see
   [License & Updates](12-license-updates.md)) — this is separate from
   the API key above and never affects whether the chat widget works.
5. Fill in **Company & Content** so the assistant knows about your
   business (see [Company & Content](03-company-content.md)).

## First-run redirect

This redirect only happens **once**, right after activating the plugin
(not on every admin page load), and is automatically skipped if you
activate several plugins at once from the plugins list (bulk
activation) — in that case you simply stay on the plugins list, as
expected.
