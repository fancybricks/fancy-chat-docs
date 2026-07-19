---
title: Textos del widget
sidebar_position: 6
---

Todos los textos fijos que el widget muestra por sí mismo (botones,
etiquetas de campos, mensajes de error) — no el contenido dinámico que
genera la IA. Traduce estos campos si tus visitantes hablan un idioma
distinto al de los valores por defecto (en inglés). Dejar un campo vacío
restaura su valor por defecto.

Cuatro sub-pestañas: Formulario previo al chat (dividida en Campos del
formulario / Botones y mensajes), Ventana de chat, Accesibilidad,
WhatsApp.

## Formulario previo al chat — Campos del formulario

![Textos del widget — Formulario previo al chat](/img/screenshots/widget-text-prechat.png)

Etiquetas de los campos de nombre/email/teléfono del formulario previo al
chat (ver [Privacidad y datos](08-privacy-data/index.md) para cuándo se
muestra este formulario).

## Formulario previo al chat — Botones y mensajes

- Botón Continuar, botón Omitir (cuando corresponde).
- Mensaje de error cuando faltan campos obligatorios.
- Mensaje de error de consentimiento no aceptado.
- Texto del enlace a la Política de Privacidad (cuando el checkbox de
  consentimiento está activo y hay una página de privacidad configurada).

## Ventana de chat

![Textos del widget — Ventana de chat](/img/screenshots/widget-text-chat-window.png)

- Placeholder del campo de mensaje, etiqueta del campo, botón de enviar.
- Mensajes de error genéricos y de conexión.

### WhatsApp

![Textos del widget — WhatsApp](/img/screenshots/widget-text-whatsapp.png)

Texto y aria-label del botón de WhatsApp, prefijo del resumen de
WhatsApp — es su propia sub-pestaña en el admin (no parte de Ventana de
chat).

## Accesibilidad

![Textos del widget — Accesibilidad](/img/screenshots/widget-text-accessibility.png)

Textos que **no se ven en pantalla**, solo los anuncian los lectores de
pantalla — marcados con la etiqueta "Solo lector de pantalla" junto al
campo para no perder tiempo puliendo su aspecto visual (no tienen
ninguno):

- Etiqueta del botón abrir/cerrar chat.
- Etiqueta del registro de mensajes (`role="log"`).
