---
title: Widget Text
---

All the fixed text the widget shows on its own (buttons, field labels,
error messages) — not the dynamic content the AI generates. Translate
these fields if your visitors speak a language other than the one the
defaults are in (English). Leaving a field empty restores its default
value.

Four sub-tabs: Pre-chat Form (split into Form fields / Buttons &
messages), Chat Window, Accessibility, WhatsApp.

## Pre-chat Form — Form fields

![Widget Text — Pre-chat Form](/img/screenshots/widget-text-prechat.png)

Labels for the name/email/phone fields of the form shown before the
chat (see [Privacy & Data](08-privacy-data/index.md) for when this
form is shown).

## Pre-chat Form — Buttons & messages

- Continue button, Skip button (when applicable).
- Error message when required fields are missing.
- Error message for consent not accepted.
- Text of the link to the Privacy Policy (when the consent checkbox
  is enabled and a privacy page is configured).

## Chat Window

![Widget Text — Chat Window](/img/screenshots/widget-text-chat-window.png)

- Message field placeholder, field label, send button.
- Generic and connection error messages.

### WhatsApp

![Widget Text — WhatsApp](/img/screenshots/widget-text-whatsapp.png)

Text and aria-label of the WhatsApp button, prefix of the WhatsApp
summary — it's its own sub-tab in the admin (not part of Chat
Window).

## Accessibility

![Widget Text — Accessibility](/img/screenshots/widget-text-accessibility.png)

Text that **isn't visible on screen**, only announced by screen
readers — marked with an "SR only" label next to the field so no time
is wasted polishing its visual appearance (it has none):

- Label for the open/close chat button.
- Label for the message log (`role="log"`).
