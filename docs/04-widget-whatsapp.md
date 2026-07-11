---
title: Widget & WhatsApp
---

Cinco sub-pestañas: Identity, Suggested Questions, WhatsApp, Disclaimer,
Visibility.

## Identity

- **Bot avatar** — imagen vía la Media Library nativa de WordPress
  (cuadrada recomendada). Si no se configura ninguna, se usa un avatar por
  defecto.
- **Bot name** — por defecto "Fanci". Se muestra en la cabecera del widget
  y en el saludo.
- **Primary color** — un solo color del que se deriva toda la paleta del
  widget (incluido el contraste automático de texto).
- **Greeting message** — mensaje mostrado antes del primer mensaje del
  visitante. Admite el token `{bot_name}`, que se reemplaza automáticamente
  por el nombre configurado — si cambias el nombre del bot más adelante,
  el saludo se actualiza solo, sin tener que editar el texto de nuevo.

## Suggested Questions

Chips clicables mostrados junto al saludo, antes del primer mensaje.
Deliberadamente separados de las FAQ (Company & Content) — las FAQ suelen
ser más largas y no caben bien como texto de un botón compacto.

## WhatsApp

- **WhatsApp number** — código de país + número, solo dígitos (sin `+`,
  espacios ni guiones). Vacío = el botón de WhatsApp no se muestra.
- **Prefilled message** — mensaje precargado cuando el visitante pulsa el
  botón. Si ya existe una conversación, el plugin genera además un
  **resumen por IA** de lo hablado y lo antepone al mensaje, para que el
  agente humano no tenga que empezar de cero.

## Disclaimer

Texto de transparencia sobre las limitaciones de la IA, mostrado como nota
discreta bajo el campo de mensaje del widget. Se puede vaciar, aunque no
es recomendable.

## Visibility

Controla en qué páginas aparece el widget:

- **Show on all pages** (por defecto).
- **Hide on selected pages** — se elige una lista y el widget se oculta
  solo ahí.
- **Show only on selected pages** — inverso: solo aparece en las páginas
  elegidas.

Útil para no interferir con una landing page o un paso de un embudo de
conversión. El selector de páginas es un `<select multiple>` nativo — Ctrl
(Cmd en Mac) para elegir varias.

**El widget nunca se muestra dentro del editor de un page builder**
(Bricks, Etch) — se detecta automáticamente tanto el panel de edición
como el iframe de canvas, independientemente de esta configuración.
