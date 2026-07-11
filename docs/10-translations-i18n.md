---
title: Traducciones e idiomas
---

Dos sistemas de traducción **distintos y complementarios** — es fácil
confundirlos en soporte, así que conviene explicarlos por separado.

## 1. Traducción del propio admin (automática)

La interfaz del plugin (pestañas, etiquetas, tooltips, mensajes de error)
viene con traducciones completas incluidas:

- **Español** — con fallback automático a **cualquier variante regional**
  (México, Colombia, Argentina, Venezuela, Chile, Perú, Latinoamérica
  genérico...): si el sitio está en "Español de México" y no hay un
  archivo específico para esa variante, usa automáticamente la traducción
  de español general.
- **Alemán** — con el mismo fallback a Austria, Suiza, y el "Sie" formal.

Este idioma lo decide el propio WordPress (Ajustes > General > Idioma del
sitio, o el idioma del perfil de cada usuario) — no hay nada que
configurar en el plugin para esto.

## 2. Traducción de lo que ven los visitantes (manual, pestaña Widget Text)

El **contenido generado por la IA** siempre responde en el idioma en que
escribe el visitante, automáticamente — esto no requiere ninguna
configuración.

Pero el widget también tiene **textos fijos propios** que no genera la
IA: el placeholder del campo de mensaje, las etiquetas del formulario
pre-chat, los mensajes de error, el texto del botón de WhatsApp, etc. Esos
SÍ hay que traducirlos manualmente, campo por campo, en la pestaña
**Widget Text** (ver [Widget Text](05-widget-text.md)) — están en
inglés por defecto.

## Añadir un idioma nuevo al admin

1. Generar el `.pot` actualizado (`wp i18n make-pot`).
2. Traducir cada cadena a un `.po` nuevo (`languages/fancy-chat-ai-{locale}.po`).
3. Compilarlo a `.mo` (`wp i18n make-mo`).
4. Si el idioma tiene variantes regionales (como español/alemán), añadir
   una entrada en el mapa de fallback (`Plugin::CANONICAL_LOCALE_BY_LANGUAGE`)
   apuntando al locale canónico — así cualquier variante regional sin
   archivo propio cae automáticamente en la traducción principal.
