---
title: Widget & WhatsApp
---

Five sub-tabs: Identity, Suggested Questions, WhatsApp, Disclaimer,
Visibility.

## Identity

![Widget & WhatsApp — Identity](/img/screenshots/widget-whatsapp-identity.png)

- **Bot avatar** — image via WordPress's native Media Library (square
  recommended). If none is set, a default avatar is used.
- **Bot name** — "Fanci" by default. Shown in the widget header and in
  the greeting.
- **Primary color** — a single color from which the whole widget
  palette is derived (including automatic text contrast).
- **Greeting message** — message shown before the visitor's first
  message. Supports the `{bot_name}` token, which is automatically
  replaced with the configured name — if you change the bot's name
  later, the greeting updates itself, with no need to edit the text
  again.

## Suggested Questions

![Widget & WhatsApp — Suggested Questions](/img/screenshots/widget-whatsapp-suggested-questions.png)

Clickable chips shown next to the greeting, before the first message.
Deliberately separate from the FAQ (Company & Content) — FAQ answers
tend to be longer and don't fit well as the text of a compact button.

## WhatsApp

![Widget & WhatsApp — WhatsApp](/img/screenshots/widget-whatsapp-whatsapp.png)

- **WhatsApp number** — country code + number, digits only (no `+`,
  spaces, or dashes). Empty = the WhatsApp button isn't shown.
- **Prefilled message** — message preloaded when the visitor taps the
  button. If a conversation already exists, the plugin also generates
  an **AI summary** of what was discussed and prepends it to the
  message, so the human agent doesn't have to start from scratch.

## Disclaimer

![Widget & WhatsApp — Disclaimer](/img/screenshots/widget-whatsapp-disclaimer.png)

Transparency text about the AI's limitations, shown as a discreet note
under the widget's message field. It can be left empty, though that's
not recommended.

## Visibility

![Widget & WhatsApp — Visibility](/img/screenshots/widget-whatsapp-visibility.png)

Controls which pages the widget appears on:

- **Show on all pages** (default).
- **Hide on selected pages** — pick a list and the widget is hidden
  only there.
- **Show only on selected pages** — the reverse: it only appears on
  the pages you pick.

Useful for not interfering with a landing page or a step in a
conversion funnel. The page selector is a native `<select multiple>` —
Ctrl (Cmd on Mac) to pick several.

**The widget is never shown inside a page builder's editor** (Bricks,
Etch) — both the editing panel and the canvas iframe are detected
automatically, regardless of this setting.
