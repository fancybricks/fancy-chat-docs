---
title: RGPD en profundidad
sidebar_position: 2
slug: /privacy-data/gdpr
---

Fancy AI Chatbot te da las **herramientas técnicas** para minimizar,
proteger, exportar, borrar y divulgar los datos que el propio chatbot
recolecta. Lo que no hace — porque ningún software puede hacerlo — es
decidir la base legal de tu sitio, redactar tu política de privacidad
final, o certificarte como "RGPD compliant": esa responsabilidad sigue
siendo del responsable del tratamiento, es decir, del dueño del sitio.

## 1. Lo que este plugin hace y no hace por ti

**Hace:**
- Da las herramientas técnicas para minimizar, proteger, exportar, borrar y
  divulgar los datos que el propio chatbot recolecta.
- Integra esas herramientas con los mecanismos *nativos* de WordPress
  (Herramientas > Exportar/Borrar datos personales, Ajustes > Privacidad),
  en vez de reinventar una interfaz propia — así el flujo de solicitudes de
  un visitante (ejercer sus derechos RGPD) es el mismo que ya usan otros
  plugins bien integrados (WooCommerce, Contact Form 7).

**No hace:**
- No decide la base legal del sitio, no redacta la política de privacidad
  final, no gestiona el banner de cookies del sitio completo, no cubre
  datos que otros plugins/temas recolecten.
- No es una "certificación" — ningún plugin puede serlo. RGPD es una
  responsabilidad del responsable del tratamiento (el dueño del sitio), no
  del proveedor de software.

## 2. Qué datos toca el chatbot (mapa de datos)

| Dato | ¿Cuándo se recolecta? | ¿Cómo se protege? |
|---|---|---|
| Mensajes de la conversación | Siempre que alguien chatea | Se guardan en las tablas propias del plugin; se borran automáticamente según la retención configurada |
| Nombre / email / teléfono | Solo si el formulario pre-chat está activo, y solo si el visitante los da | Asociados a la conversación; exportables/borrables vía las herramientas nativas de RGPD |
| Dirección IP | Siempre (para limitar abuso) | **Nunca en texto plano** — se guarda como hash SHA-256 irreversible junto con un salt del propio WordPress |
| Cookie de sesión (`fcai_session`) | Al enviar el primer mensaje | httpOnly, `Secure` si hay SSL, `SameSite=Lax`, dura 30 días, de un solo uso funcional (ver sección 4) |
| Consentimiento explícito (si está activado) | Al marcar la casilla | Se guarda como fecha/hora exacta en la conversación — sirve como prueba de que se dio |
| Clave API de Anthropic | La configura el dueño del sitio | Cifrada en reposo, nunca se envía al navegador |

## 3. Base legal: interés legítimo vs. consentimiento explícito

- Un chatbot de soporte al cliente normalmente puede operar bajo
  **interés legítimo** (Art. 6.1.f RGPD) sin pedir un consentimiento
  explícito por checkbox — es análogo a un formulario de contacto.
- Sin embargo, como los mensajes se envían a un procesador de IA externo
  (Anthropic, fuera de la UE) para generarlos, algunas agencias/abogados
  prefieren una base más conservadora. Por eso existe la **casilla de
  consentimiento opcional** (ver [Privacidad y datos](index.md#requerir-casilla-de-consentimiento)):
  permite a quien lo necesite pasar a un consentimiento explícito
  (Art. 7), sin forzarlo en quien no lo necesita.
- **Esta decisión de qué base legal usar es del dueño del sitio/su asesor
  legal.** Preséntalo como una opción informada, no como una recomendación
  universal.

## 4. La cookie de sesión y por qué no necesita banner de cookies

Bajo el criterio clásico del antiguo Grupo de Trabajo del Artículo 29 (hoy
EDPB) sobre exenciones de consentimiento de cookies, una cookie **no
necesita** aparecer en un banner de "aceptar cookies" si cumple estos tres
requisitos:

1. **Propósito exclusivamente técnico/funcional** — no analítica, no
   publicidad, no rastreo entre sitios. `fcai_session` solo sirve para
   reconocer la conversación del mismo visitante.
2. **Solo se activa cuando el visitante pide explícitamente el servicio** —
   se crea únicamente al enviar el primer mensaje, nunca solo por cargar la
   página (igual que la cookie de sesión de un carrito de compra).
3. **No se comparte con terceros** — vive enteramente en el propio sitio.

`fcai_session` cumple los tres. Esto es equivalente a cómo se tratan las
cookies de sesión de WooCommerce o de PHP mismo: casi nunca aparecen en un
banner de consentimiento, solo se *divulgan* en la política de cookies/
privacidad.

Esta es la interpretación general más extendida, no una garantía legal
absoluta para cualquier jurisdicción o comité de protección de datos.

**Divulgación, no consentimiento**: aunque no necesite banner, sí debe
**mencionarse** en la política de privacidad — el texto sugerido de
WordPress (sección 5.7) ya la incluye con su nombre real y duración.

## 5. Función por función: cómo cada una ayuda a cumplir

### 5.1 Exportar/Borrar datos personales (nativo de WordPress)

![Herramientas > Exportar datos personales](/img/screenshots/wp-export-personal-data.png)

![Herramientas > Borrar datos personales](/img/screenshots/wp-erase-personal-data.png)

Se registra en los dos filtros nativos de WP
(`wp_privacy_personal_data_exporters` / `..._erasers`), así que cuando
alguien ejerce su derecho de acceso o de supresión desde Herramientas >
Exportar/Borrar datos personales, el chatbot responde automáticamente:
busca conversaciones por email de contacto (formulario pre-chat) o por
cuenta de WordPress vinculada (visitante logueado mientras chateaba).

Un visitante anónimo que **nunca** compartió su email no tiene un
identificador estable por el que buscar — para ese caso, la protección
real es la retención automática (5.2), no el exportador.

### 5.2 Retención automática y borrado programado

Cron diario que borra permanentemente conversaciones inactivas más allá de
los días configurados (por defecto 90; rango 0–3650; 0 = conservar para
siempre, no recomendado). Aplica el principio de minimización de datos
(Art. 5.1.e RGPD — "limitación del plazo de conservación") sin que el dueño
del sitio tenga que acordarse de hacerlo a mano.

Si WP-Cron está desactivado en el sitio, el admin ve un aviso visible en
Privacidad y datos explicando que la limpieza automática no está
corriendo.

### 5.3 Panel de Conversaciones (buscar, filtrar, borrar individual)

Tabla nativa de WordPress ([Conversaciones](../09-conversations.md)) con
búsqueda por nombre/email/teléfono, filtro por estado, y acciones por
fila: desbloquear o **borrar individualmente** una conversación — más
preciso que el botón "desbloquear todas".

### 5.4 Exportación CSV de contactos

Un clic desde el admin exporta todos los contactos capturados por el
formulario pre-chat (nombre, email, teléfono, fecha de consentimiento si
aplica, fecha). Útil para que el dueño del sitio audite qué datos tiene.

### 5.5 Clave API cifrada en reposo

La clave de Anthropic se cifra antes de guardarse en la base de datos y
nunca se envía al navegador — no es un dato personal de un visitante, pero
sí un secreto sensible cuya fuga comprometería la cuenta del cliente.

### 5.6 Sesiones anónimas e IP solo como hash

No requiere cuenta de WordPress para chatear. La IP se usa solo para
limitar abuso (rate limiting) y se guarda como hash SHA-256 con salt —
nunca en una forma reversible al IP original. Ejemplo de "privacidad por
diseño" (Art. 25 RGPD): el dato mínimo necesario, en la forma menos
identificable posible.

### 5.7 Texto sugerido para la Política de Privacidad

![Ajustes > Privacidad](/img/screenshots/wp-privacy-settings.png)

![Ajustes > Privacidad > Policy Guide, con el texto sugerido por Fancy AI Chatbot](/img/screenshots/wp-privacy-policy-guide.png)

Usa el mismo mecanismo nativo que WooCommerce/Akismet
(`wp_add_privacy_policy_content()`): aparece en Ajustes > Privacidad >
Policy Guide, listo para copiar. Se genera **dinámicamente** a partir de la
configuración real del sitio (¿formulario pre-chat activo? ¿número de
WhatsApp configurado? ¿cuántos días de retención?), así que no queda
desactualizado cuando el dueño cambia esos ajustes. Menciona explícitamente
la cookie de sesión y que los mensajes se envían a Anthropic.

WordPress **nunca publica este texto solo** — el dueño del sitio debe
copiarlo a su página real de Política de Privacidad.

### 5.8 Casilla de consentimiento explícito (opcional)

Ver sección 3. Si se activa, es obligatoria (no existe un modo "opcional
una vez activada"). Se guarda con fecha exacta en la conversación como
prueba. Incluye enlace automático a la página de Política de Privacidad de
WordPress si hay una configurada.

### 5.9 Desinstalación limpia

Al eliminar el plugin (no solo desactivar), se borran sus tablas y
opciones — no deja datos huérfanos en la base de datos del cliente.

## 6. Terceros que procesan datos

- **Anthropic** (proveedor de IA): recibe el contenido de los mensajes para
  generar las respuestas. Es una transferencia internacional de datos
  (empresa de EE. UU.) — normalmente cubierta contractualmente por las
  Cláusulas Contractuales Tipo (SCCs) que Anthropic ya ofrece en sus propios
  términos, pero **el dueño del sitio debe mencionar este hecho** en su
  política (ya lo hace el texto sugerido de la sección 5.7).
- **WhatsApp** (si está configurado): al pulsar el botón de handoff, se
  comparte un resumen de la conversación generado por IA a través de un
  enlace `wa.me` — el visitante inicia esa conversación voluntariamente.

## 7. Preguntas frecuentes

- **¿Este plugin me hace RGPD compliant automáticamente?**
  No — ningún software lo hace. Te da las herramientas técnicas; la
  responsabilidad legal de tu sitio sigue siendo tuya.
- **¿Necesito un banner de cookies para este chatbot?**
  Para la cookie de sesión propia del chat, normalmente no (ver sección 4).
  Si usas otras herramientas de analítica/publicidad en tu sitio, esas sí
  pueden requerirlo — independientemente de este plugin.
- **¿Puedo usar el chatbot sin pedir el checkbox de consentimiento?**
  Sí, es opcional. Muchos sitios operan bajo interés legítimo sin él (ver
  sección 3).
- **¿Qué pasa si un visitante pide que se borren sus datos?**
  Si compartió su email, usa Herramientas > Borrar datos personales de
  WordPress — el chatbot responde automáticamente. Si nunca compartió un
  identificador, no hay forma de localizar su conversación específica; la
  retención automática la eliminará de todos modos con el tiempo.
- **¿Los mensajes salen de mi servidor?**
  Sí, se envían a Anthropic para generar la respuesta — es inherente a
  cómo funciona un chatbot de IA con un proveedor externo.

## 8. Checklist de lanzamiento

- [ ] Configura los días de retención según tu política interna.
- [ ] Copia el texto sugerido (Ajustes > Privacidad > Policy Guide) a tu
      página real de Política de Privacidad.
- [ ] Decide si activas el checkbox de consentimiento explícito (consulta
      con tu asesor legal si tienes dudas).
- [ ] Si usas un plugin de gestión de cookies, añade `fcai_session`
      manualmente a su lista (no lo detecta solo).
- [ ] Revisa periódicamente el panel de Conversaciones si recibes
      solicitudes de borrado fuera del flujo automático de WordPress.
