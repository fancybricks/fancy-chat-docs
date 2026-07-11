---
title: Solución de problemas / FAQ
---

## "El widget no aparece en mi sitio"

Comprobar en este orden:

1. **¿Hay una clave API guardada?** Sin ella, el widget no se carga en
   absoluto (ver [Primeros pasos](01-primeros-pasos.md)). El propio
   admin muestra un aviso mientras tanto.
2. **¿Estás dentro del editor de un page builder** (Bricks, Etch)? El
   widget se oculta a propósito ahí — carga la página normal (fuera del
   editor) para verlo.
3. **¿La página actual está excluida por Visibility?** Revisar
   Widget & WhatsApp → Visibility (ver
   [Widget & WhatsApp](04-widget-whatsapp.md)).

## "El asistente dejó de responder"

Casi siempre una de estas dos causas, ambas visibles en Chat Behavior →
Spend Limit:

- Se alcanzó el **tope de gasto diario** configurado.
- La cuenta de Anthropic **se quedó sin créditos**.

En ambos casos hay un botón **"Resume assistant now"** para reanudar antes
de que se resetee solo (a medianoche, o al recargar la cuenta).

## "Un visitante quedó bloqueado sin motivo"

Revisar Conversations para desbloquear esa conversación puntual, o
Moderation → "Unblock all conversations" si el problema es generalizado
(umbral de strikes demasiado bajo, por ejemplo — conviene subirlo antes de
que vuelva a pasar).

## "Test connection dice que la clave es inválida pero estoy seguro que es correcta"

Comprobar que no haya espacios extra al pegarla, y que no esté revocada
desde el propio panel de Anthropic. Si el error es "no se pudo conectar"
(no "clave inválida"), el problema es de red del servidor, no de la
clave — confirmar que el servidor permite peticiones HTTPS salientes.

## "Aparece un aviso de que la limpieza automática no está corriendo"

Significa que WP-Cron está desactivado o roto en el sitio, así que la
retención configurada (Privacy & Data) no se está aplicando. Si se
desactivó WP-Cron a propósito (común en sitios de alto tráfico), hace
falta configurar un cron real del servidor que ejecute `wp-cron.php`
periódicamente.

## "El botón Skip no aparece" / "Aparece pero no debería"

Depende de dos ajustes en Privacy & Data, no solo uno — ver
[Privacy & Data](08-privacy-data/index.md) para la interacción exacta entre
"Allow visitors to skip" y "Require consent checkbox".
