---
title: Comportamiento del chat
---

Dos sub-pestañas: Comportamiento y Límite de gasto.

## Comportamiento

![Comportamiento del chat — Comportamiento](/img/screenshots/chat-behavior-behavior.png)

- **Caducidad de la conversación (minutos)** — minutos de inactividad
  antes de que el siguiente mensaje empiece una conversación nueva en vez
  de continuar la anterior. Por defecto 60 (1 hora). Ejemplos: 30 = media
  hora, 1440 = 24 horas.
- **Máximo de mensajes por conversación** — techo duro de mensajes en una
  misma conversación (por defecto 40, rango 2–500), independiente del
  límite por tiempo. Protege contra el coste de una conversación
  anormalmente larga.

## Límite de gasto

![Comportamiento del chat — Límite de gasto](/img/screenshots/chat-behavior-spend-limit.png)

El "kill switch" de presupuesto: mide el gasto **real** (tokens de entrada,
salida y caché reportados por Anthropic, cada uno con su tarifa real), no
una estimación.

- **Límite de gasto diario (USD)** — 0 = sin límite. Junto al campo se
  muestra el **gasto estimado de hoy en vivo**.
- **Mensaje de límite de gasto** — lo que ve el visitante cuando se
  alcanza el tope. Los Contactos y el número de WhatsApp (Widget y
  WhatsApp) se añaden automáticamente al final — no hace falta
  repetirlos aquí.
- **Correo de notificaciones** — a quién avisar cuando se alcanza el tope
  o la cuenta se queda sin créditos. Vacío = usa el email de
  administrador del sitio. Máximo un correo al día por causa.
- **Asunto/cuerpo editables** para los dos casos por separado: "Límite
  diario alcanzado" y "Cuenta sin créditos". El gasto de hoy, el límite y
  un enlace a estos ajustes se añaden automáticamente debajo del texto que
  escribas.

### Qué pasa cuando se alcanza el tope

El asistente deja de responder por el resto del día (no sigue gastando).
El admin ve un aviso con el gasto/límite del día y un botón **"Reanudar
el asistente ahora"** para reanudarlo manualmente antes de tiempo
(resetea el contador). Si no se pulsa, se reanuda solo a **medianoche,
hora del sitio**.

### Detección de "sin créditos"

Si Anthropic reporta que la cuenta se quedó sin saldo, el plugin lo
distingue de un error temporal de red: deja de intentar llamadas por el
resto del día (no desperdicia peticiones contra una cuenta vacía) y
muestra al visitante la vía de contacto humana igual que con el tope
diario.

### Sin depender de WP-Cron

El contador guarda su propia fecha y se resetea solo al cambiar el día —
funciona igual con el cron del sitio desactivado o roto, a diferencia de
otros plugins que dependen de un cron para resetear contadores diarios.
