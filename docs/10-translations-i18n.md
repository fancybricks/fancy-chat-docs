---
title: Translations & Languages
sidebar_position: 12
---

Two **separate and complementary** translation systems — easy to
confuse in support, so it's worth explaining them separately.

## 1. Translation of the admin itself (automatic)

The plugin's interface (tabs, labels, tooltips, error messages) ships
with complete translations included:

- **Spanish** — with automatic fallback to **any regional variant**
  (Mexico, Colombia, Argentina, Venezuela, Chile, Peru, generic Latin
  American Spanish...): if the site is set to "Mexican Spanish" and
  there's no file specific to that variant, it automatically falls
  back to the general Spanish translation.
- **German** — with the same fallback to Austria, Switzerland, and the
  formal "Sie".

This language is decided by WordPress itself (Settings > General >
Site Language, or each user's profile language) — there's nothing to
configure in the plugin for this.

## 2. Translation of what visitors see (manual, Widget Text tab)

The **AI-generated content** always replies in the language the
visitor writes in, automatically — this requires no configuration at
all.

But the widget also has its own **fixed text** that the AI doesn't
generate: the message field placeholder, the pre-chat form labels,
error messages, the WhatsApp button text, etc. Those DO need to be
translated manually, field by field, in the **Widget Text** tab (see
[Widget Text](05-widget-text.md)) — they're in English by default.

## Adding a new language to the admin

1. Generate an updated `.pot` file (`wp i18n make-pot`).
2. Translate each string into a new `.po` file
   (`languages/fancy-chat-ai-{locale}.po`).
3. Compile it into a `.mo` file (`wp i18n make-mo`).
4. If the language has regional variants (like Spanish/German), add an
   entry to the fallback map (`Plugin::CANONICAL_LOCALE_BY_LANGUAGE`)
   pointing to the canonical locale — so any regional variant without
   its own file automatically falls back to the main translation.
