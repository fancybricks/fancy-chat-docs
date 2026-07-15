---
title: Privacidad y datos
sidebar_position: 1
slug: /privacy-data
---

Controla qué datos personales pide el widget y cuánto tiempo se conservan
las conversaciones. Para el trasfondo legal (RGPD, base legal, la cookie
de sesión) ver [RGPD en profundidad](gdpr.md) — aquí solo se documenta **qué
hace cada ajuste**.

![Privacidad y datos](/img/screenshots/privacy-data.png)

## Pedir datos de contacto

Activa un formulario previo al chat: nombre, email y teléfono, con un
mensaje explicativo editable (**Mensaje de solicitud de contacto**).

**Importante**: si este ajuste está desactivado, no hay formulario en
absoluto — los siguientes ajustes de esta sección no tienen ningún efecto.

## Permitir a los visitantes omitirlo

Con el formulario activo, pulsar **Continuar** siempre exige los tres
campos completos — no existe un modo "parcial". Este ajuste añade un
botón **Omitir** aparte, que evita el formulario por completo.

- **Desactivado (por defecto)**: sin Omitir. Dar los datos es la única
  forma de chatear.
- **Activado**: aparece Omitir junto a Continuar. El visitante elige
  entre dar sus datos completos, o no dar ninguno.

Se valida también en el servidor — aunque alguien intente enviar el
formulario incompleto llamando directamente a la API, o saltárselo por
completo, el servidor sigue exigiendo los datos salvo que este ajuste esté
activado.

## Requerir casilla de consentimiento

Añade una casilla de consentimiento explícito al formulario pre-chat (ver
[RGPD en profundidad](gdpr.md#3-base-legal-interés-legítimo-vs-consentimiento-explícito)
para cuándo tiene sentido usarla). A diferencia de "Permitir a los
visitantes omitirlo", **nunca es opcional una vez activada** — si está
encendida, el visitante debe marcarla para poder chatear, sin excepción.

Por eso, al activarla, la card **"Permitir a los visitantes omitirlo" se
atenúa y queda inerte** (no interactiva) en este mismo admin: con
consentimiento obligatorio, "Omitir" ya no puede coexistir como
alternativa (dejaría evadir también el consentimiento), así que ese
ajuste deja de tener efecto mientras tanto — se muestra atenuado en vez
de desaparecer, para que su valor guardado siga siendo visible.

- **Texto de consentimiento** — texto junto a la casilla. Si hay una
  página de Política de Privacidad configurada en WordPress (Ajustes >
  Privacidad), se añade automáticamente un enlace a ella.
- El consentimiento se guarda con **fecha y hora exactas** en la
  conversación — sirve como prueba, y aparece en la exportación CSV
  (ver [Conversaciones](../09-conversations.md)).

## Retención de datos (días)

Conversaciones inactivas más allá de este plazo se borran
**permanentemente** mediante una tarea diaria. 0 = conservar para siempre
(no recomendado para cumplimiento RGPD). Por defecto 90 días, rango
0–3650.

Si WP-Cron está desactivado o roto en el sitio, aparece un aviso en esta
misma pestaña explicando que la limpieza automática no está corriendo.
