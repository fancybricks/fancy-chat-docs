---
title: AI Provider
---

Everything related to the AI connection that powers the assistant.

![AI Provider tab](/img/screenshots/ai-provider.png)

## Anthropic API key

- Stored **encrypted at rest** and never sent to the visitor's
  browser — every call to Anthropic goes through the WordPress server
  itself.
- While a key is saved, the field shows it masked (`********`) — to
  replace it, just paste a new one and save; to confirm it without
  changing it, use **Test connection** (no need to paste it again).

### Test connection

Button next to the key field. Makes a minimal real call (`max_tokens
16`) to Anthropic with the selected model, and distinguishes three
outcomes:

- **Invalid key** — Anthropic rejected it (typo, or a revoked key).
- **Out of credits** — the key is valid but the Anthropic account has
  no balance.
- **Couldn't connect** — a network/server problem (the server doesn't
  allow outbound HTTPS requests, for example).

Works both with a key freshly pasted into the field (before saving)
and with the key already saved (leaving the field masked as-is).

### Remove key

Button to delete the saved key (asks for confirmation, since the
assistant is disconnected until a new one is saved). Only shows up if
a key is currently saved.

## Model

Selector with three Claude models:

| Model | When to use it |
|---|---|
| Claude Haiku 4.5 | Fastest and cheapest — ideal for high chat volume |
| Claude Sonnet 5 | Balance between capability and cost |
| Claude Opus 4.8 | Most capable, highest cost |

## Max tokens per reply

Token ceiling for each assistant reply (range 256–8000). Higher values
allow longer replies, but cost more per message.

## Live cost estimator

Below the model selector and the token limit: "$10 in API credit ≈
X–Y messages with this model and limit." Recalculated instantly as you
choose, **before saving** — so you decide with the cost in front of
you, not after it's already configured.

The range (X–Y) goes from the worst case (every reply maxing out the
token limit) to the typical case (short replies) — that's why it's a
range, not a single number.
