---
title: Widget Text
---

Todos los textos fijos que el widget muestra por sí mismo (botones,
etiquetas de campos, mensajes de error) — no el contenido dinámico que
genera la IA. Traduce estos campos si tus visitantes hablan un idioma
distinto al de los valores por defecto (en inglés). Dejar un campo vacío
restaura su valor por defecto.

Tres sub-pestañas: Pre-chat Form (dividida en Form fields / Buttons &
messages), Chat Window, Accessibility.

## Pre-chat Form — Form fields

Etiquetas de los campos de nombre/email/teléfono del formulario previo al
chat (ver [Privacy & Data](08-privacy-data/index.md) para cuándo se muestra
este formulario).

## Pre-chat Form — Buttons & messages

- Botón Continue, botón Skip (cuando corresponde).
- Mensaje de error cuando faltan campos obligatorios.
- Mensaje de error de consentimiento no aceptado.
- Texto del enlace a la Política de Privacidad (cuando el checkbox de
  consentimiento está activo y hay una página de privacidad configurada).

## Chat Window

- Placeholder del campo de mensaje, etiqueta del campo, botón de enviar.
- Mensajes de error genéricos y de conexión.
- Texto y aria-label del botón de WhatsApp, prefijo del resumen de
  WhatsApp.

## Accessibility

Textos que **no se ven en pantalla**, solo los anuncian los lectores de
pantalla — marcados con la etiqueta "SR only" junto al campo para no
perder tiempo puliendo su aspecto visual (no tienen ninguno):

- Etiqueta del botón abrir/cerrar chat.
- Etiqueta del registro de mensajes (`role="log"`).
