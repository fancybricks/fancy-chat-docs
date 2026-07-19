---
title: Moderación
sidebar_position: 8
---

Tres sub-pestañas: Bloqueo, Respuestas a intentos de manipulación y
Conversaciones bloqueadas.

## Cómo funciona la detección (antes de llegar aquí)

Dos capas, ambas gratuitas (sin coste extra de IA):

1. **Heurística de patrones** — detecta intentos obvios de manipulación
   ("ignora tus instrucciones", "ahora eres...", "revela tu prompt de
   sistema", "modo jailbreak", etc.) en **inglés, español, portugués,
   francés y alemán**, antes de llamar siquiera a la IA.
2. **Auto-marcado del propio modelo** — cuando el visitante escribe en
   cualquier otro idioma que la heurística no cubre, el modelo mismo
   señala el intento (invisible para el visitante) en la misma respuesta
   que ya se está generando, sin coste extra.

**Las preguntas fuera de tema nunca suman avisos** — solo cuentan los
intentos reales de manipular al asistente. Un visitante curioso
preguntando algo random no se arriesga a que lo bloqueen.

## Conversaciones bloqueadas

![Moderación — Bloqueo](/img/screenshots/moderation-blocking.png)

- **Avisos antes de bloquear** — número de intentos antes de bloquear la
  conversación (por defecto 3, rango 1–20).
- **Mensaje de bloqueo** — lo que ve el visitante una vez bloqueado. Los
  Contactos y el número de WhatsApp se añaden automáticamente al final.
- El bloqueo **expira solo**, pasado el mismo tiempo configurado como
  "Caducidad de la conversación" (Comportamiento del chat), o antes si se
  desbloquea a mano.
- **Desbloquear una sola conversación** — para desbloquear/borrar una
  conversación puntual, se hace desde la pantalla **Conversaciones**
  (ver [Conversaciones](09-conversations.md)), no desde aquí.
- **Desbloquear todas las conversaciones** — botón de recurso general
  ante falsos positivos masivos (por ejemplo, si el umbral de avisos
  estaba demasiado bajo). Pide confirmación antes de ejecutar.

![Moderación — Conversaciones bloqueadas](/img/screenshots/moderation-blocked-conversations.png)

## Respuestas a intentos de manipulación

![Moderación — Respuestas a intentos de manipulación](/img/screenshots/moderation-replies.png)

Un campo de texto **por idioma** (de los cinco que cubre la heurística) —
la respuesta instantánea que ve el visitante cuando su mensaje es
detectado como un intento obvio de manipulación en ese idioma. Editable
para ajustar tono/redacción sin tocar código.

Distinto del mensaje de bloqueo: este se muestra en el momento del
intento (conversación sigue activa), el de bloqueo se muestra solo tras
superar el umbral de avisos.
