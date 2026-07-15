---
title: Getting Started
slug: /
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
4. Fill in **Company & Content** so the assistant knows about your
   business (see [Company & Content](03-company-content.md)).

## What happens if you activate the plugin without a key yet

The chat widget **doesn't show up on the site** until an API key is
saved — visitors don't see a broken bubble or a visible error, nothing
simply loads at all.

In the meantime, the WordPress admin reminds you in two ways:

- A dismissible notice throughout the rest of the admin (any screen
  other than the plugin's own), with a direct link to AI Provider.
- A persistent notice inside every tab of the plugin (except AI
  Provider, where it would be redundant with the field itself).

Both notices disappear on their own as soon as you save a valid key.

## First-run redirect

This redirect only happens **once**, right after activating the plugin
(not on every admin page load), and is automatically skipped if you
activate several plugins at once from the plugins list (bulk
activation) — in that case you simply stay on the plugins list, as
expected.
