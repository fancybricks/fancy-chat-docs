---
title: Licencia y actualizaciones
sidebar_position: 13
---

Cada compra de Fancy AI Chatbot incluye una clave de licencia. Esta página
explica qué pasa justo después de comprar, cómo gestionar tu licencia
desde dentro del plugin, y cómo funcionan las actualizaciones automáticas.

## Después de comprar

Tu compra se procesa a través de la tienda de fancychatbot.com. Justo
después del pago:

- Se crea tu cuenta automáticamente en fancychatbot.com — no necesitas
  registrarte por separado.
- Recibirás un correo con un enlace para definir tu propia contraseña
  (el mismo flujo nativo de WordPress que se usa en cualquier otro sitio
  — nadie, ni siquiera nosotros, ve o te envía una contraseña en texto
  plano).
- Una vez definida tu contraseña, inicia sesión en
  [fancychatbot.com/my-account](https://fancychatbot.com/my-account/).

## Tu panel de cuenta (fancychatbot.com)

Desde tu cuenta puedes:

- Ver tu(s) licencia(s) y en qué sitios está activada cada una
  actualmente.
- Gestionar la facturación (un enlace te lleva directo a tu suscripción
  — datos de tarjeta, facturas, cancelar/renovar — sin un paso de
  inicio de sesión aparte).
- Quitar la activación de un sitio, liberando ese cupo para activar la
  licencia en otro lugar.

## Activar tu licencia (dentro del plugin)

![Licencia — antes de activar](/img/screenshots/license-none.png)

Ve a **Settings → License** en el plugin.

- Pega tu clave de licencia y haz clic en **Activate license**.

![Licencia — activa](/img/screenshots/license.png)

- Una vez activa, la tarjeta muestra: estado (Active), tu plan, la fecha
  de renovación (en planes anuales), y cuántos sitios están usando esta
  licencia del total permitido por tu plan — por ejemplo, "2 of 5 sites
  activated".
- **Deactivate** libera el cupo de este sitio en tu licencia, para que
  puedas activarla en otro lugar (por ejemplo, antes de mover el plugin
  a un sitio distinto).

### Si quitas un sitio desde tu panel de cuenta en vez de hacerlo aquí

Si liberas una activación desde tu cuenta en fancychatbot.com (o
directamente desde Lemon Squeezy) en vez de usar el botón Deactivate del
plugin, el plugin lo detecta solo — ya sea la próxima vez que abras la
pestaña License, o automáticamente en las horas siguientes — y vuelve a
mostrar la pantalla de "introduce tu licencia". No necesitas hacer nada
más en el sitio.

## White label (planes Agency y Scale)

![White Label](/img/screenshots/white-label.png)

Si tu licencia es del plan **Agency** o **Scale**, aparece una pestaña
dedicada **White Label** en la barra lateral (dentro de Advanced):

- Marca **Replace "Fancy AI Chatbot" with your own name throughout
  wp-admin** y escribe el nombre que quieras usar en su lugar.
- Ese nombre reemplaza "Fancy AI Chatbot" en el menú de wp-admin, en la
  cabecera de la propia página de ajustes del plugin, en el título de
  la pestaña del navegador, y — a diferencia de un ajuste típico de
  plugin — **también en la pantalla nativa de Plugins de WordPress**
  (el listado de Installed Plugins, incluida la línea del autor, que
  se borra por completo para que nada apunte a fancychatbot.com).
  También se usa como nombre por defecto en los asuntos de los emails
  de límite de gasto diario y de créditos agotados (siguen siendo
  totalmente editables de todas formas, ver
  [Chat behavior](/chat-behavior)).
- En cualquier otro plan, esta pestaña solo explica que el white label
  es una función de Agency/Scale — no hay nada roto que configurar.
- Si tu licencia después vence o baja de nivel por debajo de
  Agency/Scale, la marca vuelve automáticamente a "Fancy AI Chatbot" en
  todos lados (incluida la pantalla de Plugins) — tu nombre guardado y
  la casilla siguen guardados por si la licencia
  vuelve a ser válida, solo dejan de aplicarse mientras tanto.

### Icono personalizado

Un selector **Custom icon** (el mismo control "Select Image" / "Remove"
que el Bot avatar del widget) te permite subir tu propia imagen para
reemplazar el logo del chatbot que se muestra en el menú lateral propio
de esta página de ajustes. Déjalo vacío para conservar el icono por
defecto. El icono real del menú de wp-admin (junto al nombre del plugin
en el menú lateral) no se ve afectado — se mantiene como el dashicon
genérico.

### Descripción personalizada en la pantalla de Plugins

Un campo **Plugins list description** te permite reemplazar la
descripción por defecto que aparece debajo del nombre del plugin en la
pantalla de Plugins ("AI-powered chat widget for WordPress. Bring your
own Anthropic API key.") por tu propio texto. Déjalo vacío para
conservar la descripción por defecto. Es independiente del reemplazo de
nombre de arriba — puedes activar uno sin el otro.

### Ocultar los enlaces de Tutoriales y Registro de cambios

Una casilla dentro de **Resources links**, **Hide the Tutorials and
Changelog links**, elimina esos dos enlaces (que apuntan a
fancychatbot.com) del menú lateral propio del plugin. Antes esto pasaba
automáticamente al reemplazar el nombre — ahora es una casilla
independiente, así que puedes ocultar estos enlaces sin importar si el
nombre está reemplazado, o reemplazar el nombre sin ocultarlos.

### Ocultar la pestaña de Licencia

Una casilla dentro de **License tab**, **Hide the License tab from the
sidebar nav**, elimina la pestaña License del menú lateral propio del
plugin, junto con todos los avisos relacionados en el resto de
wp-admin: los avisos en línea "Activate your license" / "license
expired" en las demás pestañas del plugin, y el aviso sitewide que de
otro modo aparece en cualquier otra pantalla de wp-admin (Dashboard,
Posts, etc.) cuando la licencia necesita atención. Útil si compartes
acceso a wp-admin con un cliente y no quieres que vea los detalles de
licencia/activación (número de sitios, nombre del plan) ni que le
salgan avisos para gestionarla.

La pestaña en sí sigue funcionando — solo deja de estar enlazada desde
el menú. Añade `&tab=license` a la URL de ajustes del plugin cuando tú
(el titular de la licencia) necesites revisarla o hacer cambios.

### Ocultar la propia pestaña de White Label

Una casilla dentro de **This White Label tab**, **Hide this White Label
tab from the sidebar nav**, oculta la entrada de menú de la propia
pestaña White Label. El nombre "White Label" por sí solo delata que el
producto está reetiquetado, así que vale la pena ocultarla por la misma
razón que la pestaña License — quizás más aún.

Mismo patrón que la pestaña License: sigue funcionando, solo hay que
añadir `&tab=white_label` a la URL de ajustes del plugin para llegar a
ella. Como marcar esta casilla oculta justo la pantalla que te
recordaría esa URL, anótala en algún sitio antes de guardar.

### Ocultar el plugin del menú lateral del admin

También dentro de la pestaña White Label, una sección aparte llamada
**Admin sidebar menu** te permite marcar **Hide from the admin sidebar
menu** — útil si gestionas esto para un cliente y no quieres que le
sature el menú lateral de wp-admin:

- Una vez oculto, tanto la entrada de menú de nivel superior del plugin
  como su submenú **Conversations** desaparecen por completo del menú
  lateral.
- La página de ajustes sigue siendo totalmente accesible — aparece un
  enlace **Settings** en la fila de este plugin en la pantalla de
  Plugins (Plugins → Installed Plugins), justo al lado de Deactivate,
  igual que muchos otros plugins de WordPress exponen sus ajustes.
- Los enlaces directos (marcadores, el propio enlace interno "Open
  Conversations" del plugin) siguen funcionando aunque la entrada del
  menú lateral haya desaparecido.
- Igual que el reemplazo de nombre de arriba, esto también revierte
  automáticamente si la licencia vence o baja de nivel por debajo de
  Agency/Scale — la entrada del menú lateral vuelve, así que nunca te
  quedas sin acceso.

## Qué pasa sin una licencia válida

El widget del chat en sí **nunca deja de funcionar** solo porque una
licencia venza o parezca inválida — tus visitantes nunca se ven
afectados por eso. Lo que sí depende de tener una licencia activa:

- **Sin licencia introducida todavía**: aparece un aviso en todo el
  admin (y en la propia pestaña License) invitándote a introducir una.
  Es solo un recordatorio, no una restricción.
- **Licencia vencida o inválida**: un aviso similar lo explica y enlaza
  para renovar. Dos cosas se pausan hasta que renueves: las
  **actualizaciones automáticas**, y el acceso a **soporte premium**.

Hay una excepción deliberada: una licencia **deshabilitada
explícitamente** desde el dashboard de Lemon Squeezy (Store → Licenses
→ "Disable key" — algo que solo harías tú, como titular de la licencia,
o nuestro equipo de soporte, por ejemplo tras un reembolso) sí oculta
por completo el widget de chat de tu sitio, ya que ese nunca es un
estado ambiguo o temporal. Los propios ajustes del plugin muestran un
aviso claro de "Tu licencia ha sido deshabilitada" cuando esto ocurre.
Una licencia simplemente vencida o inválida es distinta — puede ser un
problema de facturación pasajero, así que nunca bloquea el widget.

## Actualizaciones automáticas

Con una licencia activa, el plugin busca actualizaciones igual que
cualquier otro plugin de WordPress — desde Escritorio → Actualizaciones,
o la página de Plugins. Sin pasos extra.

Sin una licencia activa, no se ofrece ninguna actualización (nada más
del plugin se ve afectado). En cuanto renuevas o activas una licencia
válida, las actualizaciones se reanudan automáticamente — no hace falta
reinstalar nada.

## Solución de problemas

- **"No veo ninguna actualización disponible"** — abre Settings →
  License y confirma que muestra "Active". Una licencia vencida o sin
  introducir es la razón más común por la que no aparecen
  actualizaciones.
- **Liberé la activación de mi sitio por accidente** — simplemente
  vuelve a introducir tu clave de licencia en la pestaña License;
  mientras tu plan tenga un cupo disponible, activarla de nuevo toma
  solo unos segundos.
