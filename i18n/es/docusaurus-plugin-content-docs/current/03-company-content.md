---
title: Empresa y contenido
sidebar_position: 4
---

Todo lo que aquí se configura se inyecta automáticamente en el prompt de
sistema del asistente — no hace falta escribir ni editar ningún prompt a
mano, solo rellenar estos campos.

## Perfil

![Empresa y contenido — Perfil](/img/screenshots/company-content-profile.png)

- **Nombre de la empresa** — nombre de la empresa.
- **Descripción de la empresa** — a qué se dedica, en un par de frases.
- **Tono de voz** — selector con cuatro estilos:
  - Friendly and professional (por defecto)
  - Formal and precise
  - Casual and conversational
  - Warm and empathetic
- **Primary language** (idioma principal) — un selector con buscador que
  cubre idiomas comunes y sus variantes regionales (ej. español de
  Colombia frente a español de España). Por defecto toma el idioma de
  WordPress de tu sitio. Se usa para el resumen de traspaso a WhatsApp
  (siempre redactado en este idioma, sin importar en qué idioma haya
  sido la conversación) y como respaldo para el ajuste de abajo.
- **Which language should the assistant reply in?** (en qué idioma debe
  responder el asistente) — tres opciones:
  - **Match the visitor** (por defecto) — responde en el idioma en el
    que escriba el visitante; solo recurre al idioma principal de
    arriba cuando un mensaje es demasiado corto o ambiguo para
    determinarlo (ej. un chip de pregunta sugerida de una sola
    palabra).
  - **Match the visitor, guess from their browser** — igual, pero ante
    un mensaje ambiguo recurre al idioma del navegador del visitante
    en vez del idioma principal.
  - **Always use the primary language** — ignora por completo el
    idioma del visitante y responde siempre en el idioma principal de
    arriba, incluso ante un mensaje claro escrito en otro idioma. Útil
    si tu equipo de soporte solo atiende en un idioma.

## Servicios

![Empresa y contenido — Servicios](/img/screenshots/company-content-services.png)

Repetidor: nombre + descripción de cada servicio que el asistente puede
explicar a los visitantes.

## Planes de precios

![Empresa y contenido — Planes de precios](/img/screenshots/company-content-pricing-plans.png)

Repetidor pensado para negocios que venden **planes/paquetes con precio
fijo** (no una cotización a medida por servicio) — nombre del plan +
precio/detalle.

## Horario de atención

![Empresa y contenido — Horario](/img/screenshots/company-content-hours.png)

Repetidor de días + horario, por ejemplo: Días "Lunes–Viernes", Horario
"9:00–18:00". Añade una fila extra para fines de semana o un día
"Cerrado".

## Preguntas frecuentes

![Empresa y contenido — FAQ](/img/screenshots/company-content-faq.png)

Repetidor pregunta + respuesta, usado para que el asistente responda con
la redacción exacta que definas en vez de improvisar.

## Contactos

![Empresa y contenido — Contactos](/img/screenshots/company-content-contacts.png)

Repetidor genérico etiqueta + valor (ej. "Correo de soporte" →
`soporte@ejemplo.com`, "Teléfono" → un número). Estos contactos se
**añaden automáticamente** al final de varios mensajes del plugin (mensaje
de bloqueo, mensaje de tope de gasto alcanzado) — no hace falta repetirlos
a mano en esos textos.

## Páginas

![Empresa y contenido — Páginas](/img/screenshots/company-content-pages.png)

Escanea contenido existente de tu sitio para añadir información al
contexto del asistente. El contenido se organiza en una card
colapsable por cada tipo de contenido — Pages, Posts, y cada custom
post type que registre tu tema o tus plugins (solo la primera card
empieza abierta) — para que un sitio con muchos tipos de contenido
siga siendo fácil de recorrer. Cada card es independiente:

- Su propio selector, con todos los elementos publicados de ese tipo
  (con buscador si tiene más de 8).
- Su propio botón **Scan selected _(tipo)_** — la IA lee el contenido
  de lo seleccionado y condensa la información más relevante en el
  cuadro de esa misma card, debajo. Se escanean hasta 10 elementos a
  la vez por card. Si el cuadro ya tiene contenido, escanear pide
  confirmación antes de reemplazarlo.
- Su propio cuadro **Extracted info** con el resultado — separado por
  tipo, para que escanear un tipo nunca sobrescriba lo ya extraído de
  otro.

Escanear usa tus propios créditos de la API de Anthropic y solo
funciona con una clave de API activa (configurada en la pestaña AI
Provider) — el botón **Scan** de cada card muestra el coste exacto de
esa llamada al terminar (ej. "Scanned — cost: $0.0042").

## Custom Info

![Empresa y contenido — Custom Info](/img/screenshots/company-content-custom-info.png)

Un cuadro de texto enriquecido para escribir o pegar tu propia
información a mano — para todo lo que no cubran los campos de arriba
ni el escaneo de las páginas de tu sitio. Si pegas una gran cantidad
de texto, haz clic en **Summarize** para que la IA lo condense a lo
esencial, manteniendo pequeña (y barata) la información que se envía
en cada conversación sin perder lo importante. Igual que al escanear,
esto usa tus propios créditos de la API de Anthropic y solo funciona
con una clave de API activa — el botón **Summarize** muestra el coste
exacto al terminar.

Tanto este campo como cada cuadro "Extracted info" de la pestaña
Pages se envían al asistente como texto plano junto con los demás
campos de Empresa y contenido — el formato (negrita, listas, enlaces)
de Custom Info es solo para tu comodidad al editar y la IA no lo ve.
