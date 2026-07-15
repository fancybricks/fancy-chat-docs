---
title: Widget y WhatsApp
---

Cinco sub-pestañas: Identidad, Preguntas sugeridas, WhatsApp, Aviso legal,
Visibilidad.

## Identidad

![Widget y WhatsApp — Identidad](/img/screenshots/widget-whatsapp-identity.png)

- **Avatar del bot** — imagen vía la Media Library nativa de WordPress
  (cuadrada recomendada). Si no se configura ninguna, se usa un avatar por
  defecto.
- **Nombre del bot** — por defecto "Fanci". Se muestra en la cabecera del
  widget y en el saludo.
- **Color principal** — un solo color del que se deriva toda la paleta del
  widget (incluido el contraste automático de texto).
- **Mensaje de bienvenida** — mensaje mostrado antes del primer mensaje
  del visitante. Admite el token `{bot_name}`, que se reemplaza
  automáticamente por el nombre configurado — si cambias el nombre del
  bot más adelante, el saludo se actualiza solo, sin tener que editar el
  texto de nuevo.

## Preguntas sugeridas

![Widget y WhatsApp — Preguntas sugeridas](/img/screenshots/widget-whatsapp-suggested-questions.png)

Chips clicables mostrados junto al saludo, antes del primer mensaje.
Deliberadamente separados de las FAQ (Empresa y contenido) — las FAQ
suelen ser más largas y no caben bien como texto de un botón compacto.

## WhatsApp

![Widget y WhatsApp — WhatsApp](/img/screenshots/widget-whatsapp-whatsapp.png)

- **Número de WhatsApp** — código de país + número, solo dígitos (sin
  `+`, espacios ni guiones). Vacío = el botón de WhatsApp no se muestra.
- **Mensaje predefinido** — mensaje precargado cuando el visitante pulsa
  el botón. Si ya existe una conversación, el plugin genera además un
  **resumen por IA** de lo hablado y lo antepone al mensaje, para que el
  agente humano no tenga que empezar de cero.

## Aviso legal

![Widget y WhatsApp — Aviso legal](/img/screenshots/widget-whatsapp-disclaimer.png)

Texto de transparencia sobre las limitaciones de la IA, mostrado como nota
discreta bajo el campo de mensaje del widget. Se puede vaciar, aunque no
es recomendable.

## Visibilidad

![Widget y WhatsApp — Visibilidad](/img/screenshots/widget-whatsapp-visibility.png)

Controla en qué páginas aparece el widget:

- **Mostrar en todas las páginas** (por defecto).
- **Ocultar en las páginas seleccionadas** — se elige una lista y el
  widget se oculta solo ahí.
- **Mostrar solo en las páginas seleccionadas** — inverso: solo aparece
  en las páginas elegidas.

Útil para no interferir con una landing page o un paso de un embudo de
conversión. El selector de páginas es un `<select multiple>` nativo — Ctrl
(Cmd en Mac) para elegir varias.

**El widget nunca se muestra dentro del editor de un page builder**
(Bricks, Etch) — se detecta automáticamente tanto el panel de edición
como el iframe de canvas, independientemente de esta configuración.
