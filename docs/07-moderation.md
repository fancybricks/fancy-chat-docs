---
title: Moderation
---

Dos sub-pestañas: Blocked Conversations y Manipulation attempt replies.

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

**Las preguntas fuera de tema nunca suman strikes** — solo cuentan los
intentos reales de manipular al asistente. Un visitante curioso
preguntando algo random no se arriesga a que lo bloqueen.

## Blocked Conversations

- **Strikes before blocking** — número de intentos antes de bloquear la
  conversación (por defecto 3, rango 1–20).
- **Blocked message** — lo que ve el visitante una vez bloqueado. Los
  Contacts y el número de WhatsApp se añaden automáticamente al final.
- El bloqueo **expira solo**, pasado el mismo tiempo configurado como
  "Conversation timeout" (Chat Behavior), o antes si se desbloquea a mano.
- **Unblock a single conversation** — para desbloquear/borrar una
  conversación puntual, se hace desde la pantalla **Conversations**
  (ver [Conversations](09-conversations.md)), no desde aquí.
- **Unblock all conversations** — botón de recurso general ante falsos
  positivos masivos (por ejemplo, si el umbral de strikes estaba
  demasiado bajo). Pide confirmación antes de ejecutar.

## Manipulation attempt replies

Un campo de texto **por idioma** (de los cinco que cubre la heurística) —
la respuesta instantánea que ve el visitante cuando su mensaje es
detectado como un intento obvio de manipulación en ese idioma. Editable
para ajustar tono/redacción sin tocar código.

Distinto del mensaje de bloqueo: este se muestra en el momento del
intento (conversación sigue activa), el de bloqueo se muestra solo tras
superar el umbral de strikes.
