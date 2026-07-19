---
title: Company & Content
sidebar_position: 4
---

Everything configured here is automatically injected into the
assistant's system prompt — no need to write or edit any prompt by
hand, just fill in these fields.

## Profile

![Company & Content — Profile](/img/screenshots/company-content-profile.png)

- **Company name** — your company's name.
- **Company description** — what it does, in a couple of sentences.
- **Tone of voice** — selector with four styles:
  - Friendly and professional (default)
  - Formal and precise
  - Casual and conversational
  - Warm and empathetic
- **Primary language** — a searchable picker covering common languages
  and regional variants (e.g. Spanish (Colombia) vs. Spanish (Spain)).
  Defaults to your site's own WordPress language. Used for the
  WhatsApp handoff summary (always written in this language,
  regardless of what language the conversation itself was in) and as
  a fallback for the setting below.
- **Which language should the assistant reply in?** — three options:
  - **Match the visitor** (default) — replies in whichever language
    the visitor writes in; falls back to the primary language above
    only when a message is too short or ambiguous to tell (e.g. a
    one-word suggested-question chip).
  - **Match the visitor, guess from their browser** — same, but falls
    back to the visitor's own browser language instead of the primary
    language when a message is ambiguous.
  - **Always use the primary language** — ignores the visitor's own
    language entirely, replying in the primary language above even
    for a clear message written in a different language. Useful if
    your support team only handles one language.

## Services

![Company & Content — Services](/img/screenshots/company-content-services.png)

Repeater: name + description for each service the assistant can
explain to visitors.

## Pricing Plans

![Company & Content — Pricing Plans](/img/screenshots/company-content-pricing-plans.png)

Repeater meant for businesses that sell **fixed-price plans/packages**
(rather than a custom quote per service) — plan name + price/detail.

## Business Hours

![Company & Content — Hours](/img/screenshots/company-content-hours.png)

Repeater of days + schedule, for example: Days "Monday–Friday", Hours
"9:00 AM–6:00 PM". Add an extra row for weekends or a "Closed" day.

## Frequently Asked Questions

![Company & Content — FAQ](/img/screenshots/company-content-faq.png)

Question + answer repeater, used so the assistant replies with the
exact wording you define instead of improvising.

## Contacts

![Company & Content — Contacts](/img/screenshots/company-content-contacts.png)

Generic label + value repeater (e.g. "Support email" →
`support@example.com`, "Phone" → a number). These contacts are
**automatically appended** to the end of several plugin messages
(blocked message, spend-limit-reached message) — no need to repeat
them by hand in those texts.

## Pages

![Company & Content — Pages](/img/screenshots/company-content-pages.png)

Scans existing content on your site for information to add to the
assistant's context. Content is organized into one collapsible card
per content type — Pages, Posts, and each custom post type your
theme/plugins register (only the first card starts open) — so a site
with many content types stays easy to scan through. Each card is
independent:

- Its own picker, listing every published item of that type (with a
  search box once it holds more than 8 items).
- Its own **Scan selected _(type)_** button — the AI reads the
  selected items' content and condenses the most relevant information
  into that same card's own box below. Up to 10 items are scanned at
  once per card. If the box already has content, scanning asks for
  confirmation before replacing it.
- Its own **Extracted info** box showing the result — kept separate
  per type, so scanning one type never overwrites what was already
  extracted from another.

Scanning uses your own Anthropic API credits and only works with an
active API key (set on the AI Provider tab) — each card's **Scan**
button reports the exact cost of that call once it completes (e.g.
"Scanned — cost: $0.0042").

## Custom Info

![Company & Content — Custom Info](/img/screenshots/company-content-custom-info.png)

A rich-text box for writing or pasting your own information by hand —
for anything not covered by the fields above or by scanning your
site's pages. If you paste in a large amount of text, click
**Summarize** to have the AI condense it down to the key points,
keeping the information sent with every conversation small (and
cheap) without losing what matters. Like scanning, this uses your own
Anthropic API credits and only works with an active API key — the
**Summarize** button reports the exact cost once it completes.

Both this field and every "Extracted info" box on the Pages tab are
sent to the assistant as plain text alongside the other Company &
Content fields — formatting (bold, lists, links) in Custom Info is
for your own editing convenience and isn't seen by the AI.
