# Fancy AI Chatbot — sitio de documentación (Docusaurus)

Este repo es el sitio público de documentación del plugin de WordPress **Fancy AI Chatbot**. Es un proyecto Docusaurus independiente, en una carpeta hermana del repo del plugin — no un submódulo ni una subcarpeta de él.

**Nota de nombres**: el sitio se llamó inicialmente "Fancy Chat AI" en el scaffold de Docusaurus (título, navbar, logo alt) — corregido el 2026-07-12 a **"Fancy AI Chatbot"**, el nombre real y público del plugin (confirmado por el usuario, y coincide con el `Plugin Name` del propio `.po`/`fancy-chat-ai.php` y con lo que muestra el admin real). Si aparece "Fancy Chat AI" en algún sitio del repo, es un resto de esa confusión inicial y debe corregirse.

## Dónde está todo

- **Este repo**: `/Users/coudix/Documents/fancy-chat-docs` — el sitio Docusaurus.
- **Repo del plugin** (privado): `/Users/coudix/Documents/fancy-chat` — código PHP del plugin, remoto `github.com/fancybricks/fancy-chat.git`.
- **Material fuente de la doc**: `/Users/coudix/Documents/fancy-chat/documentation/` — carpeta interna del repo del plugin (no se distribuye con él, ver su propio `.distignore`). Contiene el contenido base en 12 archivos (`01-primeros-pasos.md` … `11-troubleshooting-faq.md`, más `GDPR.md`) que se usó como fuente para redactar `docs/` en este repo. Si el plugin gana una función nueva o cambia un ajuste, ese es el sitio donde probablemente se actualice primero la redacción de referencia antes de traerla aquí — pero **el contenido real y ya publicado vive en `docs/` de este repo**, no ahí.
- **Marketing site** (landing del plugin, WordPress): `/Users/coudix/Documents/fancy-chat/marketing-site/` — de aquí se sacó toda la identidad visual (ver más abajo).
- **Sitio web público del plugin**: `fancychatbot.com`.

## Qué es Fancy AI Chatbot (para entender el contenido que se documenta)

Plugin de WordPress que añade un widget de chat con IA (Anthropic Claude, BYOK — el cliente pone su propia API key para el consumo de IA, sin margen del plugin sobre eso). **Desde julio 2026 hay además una capa de licencia paga (vía Lemon Squeezy)**, pero es independiente del BYOK: gatea únicamente actualizaciones automáticas/soporte y la función White Label — nunca el widget de chat en sí (ver `docs/12-license-updates.md`). Pestañas del admin, en el mismo orden que la barra lateral del sitio de docs:

1. **AI Provider** — API key, test connection, modelo, límite de tokens, estimador de coste.
2. **License** — activar/desactivar clave de licencia, estado, tier, sitios activados. *(añadido julio 2026, ver más abajo)*
3. **Company & Content** — perfil, servicios, precios, horarios, FAQ, contactos, idioma principal/de respuesta, escaneo de páginas del sitio, Custom Info (se inyecta en el prompt de sistema).
4. **Widget & WhatsApp** — identidad del bot, preguntas sugeridas, handoff a WhatsApp, disclaimer, visibilidad por página.
5. **Widget Text** — traducción de todos los textos fijos del widget.
6. **Chat Behavior** — timeout de conversación, límite de mensajes por conversación, rate limiter de mensajes por sesión (prevención de abuso), tope de gasto diario (kill switch real, basado en coste real no estimado).
7. **Moderation** — detección de intentos de manipulación (heurística en 5 idiomas + auto-marcado del modelo), strikes, bloqueo.
8. **Privacy & Data** — formulario pre-chat, consentimiento explícito, retención de datos. Tiene su propia sub-página profunda de RGPD.
9. **White Label** — solo planes Agency/Scale: nombre e icono personalizado, descripción en el listado de plugins, ocultar pestañas/menú. *(añadido julio 2026, ver más abajo)*
10. **Conversations** — pantalla (no pestaña de ajustes) con buscar/filtrar/exportar CSV.
11. Transversales: traducciones/idiomas, licencia y actualizaciones, troubleshooting/FAQ.

**Importante**: License y White Label son dos pestañas separadas en el admin real, pero en el sitio de docs se documentan juntas en **una sola página**, `12-license-updates.md` ("License & Updates"/"Licencia y actualizaciones") — esa página ya existía (escrita antes de julio 2026, con detalle de flujo de compra/cuenta/facturación que no vive en el código del plugin sino en fancychatbot.com) y es más completa que documentar cada tab por separado, así que se mantuvo esa estructura en vez de crear dos páginas nuevas 1:1 con las pestañas.

**Funciones añadidas julio 2026 (verificar que sigan reflejadas en los docs si se vuelve a auditar este repo)**: License, White Label, idioma principal/idioma de respuesta del asistente (Company & Content), escaneo de contenido del sitio + Custom Info (Company & Content), rate limiter de mensajes por sesión (Chat Behavior). Todo esto se agregó en `fancy-chat` entre el 2026-07-17 y el 2026-07-19 — si ha pasado tiempo desde esa fecha, es buena señal revisar `git log --oneline -20` en el repo del plugin por si hay funciones más nuevas todavía sin documentar aquí.

El código del admin vive en `fancy-chat/src/Admin/SettingsPage.php` (~4000 líneas, un solo archivo con todos los tabs) si hace falta verificar el comportamiento real de un ajuste antes de documentarlo — el método privado `tabs()` lista todas las pestañas actuales con su grupo (`settings`/`advanced`) y es la forma más rápida de confirmar qué existe antes de auditar los docs.

## Identidad de marca (de dónde salió cada cosa)

Todo se copió de `fancy-chat/marketing-site/`, no se inventó nada:

- **Color primario**: `#4f46e5` (indigo), rampa completa en `src/css/custom.css` (`--ifm-color-primary-*`), tomada literalmente de `marketing-site/style.css` (`--color-primary` y sus estados hover `#4338ca` / `#3730a3`).
- **Logo**: `marketing-site/media/logo-icon.svg` → copiado a `static/img/logo.svg` (navbar + favicon).
- **Tipografía**: Plus Jakarta Sans (Google Fonts), igual que la landing.
- **Dominio real**: `fancychatbot.com` (confirmado por el usuario, no inventado).

## Decisiones de arquitectura del sitio (y el porqué)

- **Hosting: subcarpeta `fancychatbot.com/docs/`, no subdominio.** Se decidió así por SEO: la landing es simple (pocas páginas indexables), así que la doc (11+ páginas con contenido sustancial) es la pieza que más autoridad de dominio puede aportarle a `fancychatbot.com` — mejor que repartirla en `docs.fancychatbot.com`. Config actual: `url: 'https://fancychatbot.com'`, `baseUrl: '/docs/'`.
- **Deploy**: Docusaurus compila a HTML/CSS/JS estático puro (`npm run build` → carpeta `build/`). No necesita Node en el hosting — solo subir el contenido de `build/` a la subcarpeta `/docs/` del mismo hosting de WordPress (FTP o file manager), sin proxy ni configuración especial de rewrites (cada página ya es un HTML real, a diferencia de una SPA).
- **Repo GitHub**: repo **público** aparte (`fancybricks/fancy-chat-docs`, ya creado — el usuario lo gestiona con GitHub Desktop, no por CLI). Público porque el contenido de la doc no es sensible (a diferencia del código del plugin, que sí es privado).
- **Sin botón "Edit this page"**: se quitó `editUrl` de la config de `docs` a propósito (2026-07-12) — es un sitio público de cara al visitante, no tiene sentido invitarlo a "editar" el contenido vía GitHub. Si se reactiva en el futuro, recordar añadir también `editLocalizedFiles: true` para que la versión en español enlace al archivo real en `i18n/es/...` en vez de al inglés.
- **Home = la documentación misma.** No hay landing page separada: `docs/01-primeros-pasos.md` tiene `slug: /` en su frontmatter, así que es lo primero que se ve al entrar. Sin blog (`blog: false`, carpeta `blog/` eliminada), sin footer (se quitó el bloque `footer` completo del theme config). El navbar solo tiene el logo y un link externo a `https://fancychatbot.com`.
- **`docs.routeBasePath: '/'`** en el preset — URLs planas dentro del baseUrl (`/docs/ai-provider`, no `/docs/docs/ai-provider`).
- **i18n: inglés por defecto, español como idioma secundario** (`defaultLocale: 'en'`, `locales: ['en', 'es']`). Decisión revertida el 2026-07-11 — al principio el sitio era solo español (`defaultLocale: 'es'`) porque todo el contenido se redactó primero en ese idioma, pero se decidió que el inglés fuera el idioma principal de la documentación pública, con español como alternativa vía el selector de idioma del navbar (`type: 'localeDropdown'`). Cómo queda estructurado:
  - **`docs/` = inglés** (idioma por defecto, sin prefijo en la URL: `/docs/ai-provider`). Es el contenido "fuente" — cualquier doc nuevo se escribe aquí primero.
  - **`i18n/es/docusaurus-plugin-content-docs/current/` = español** (con prefijo `/docs/es/...`). Espeja exactamente la misma estructura de archivos que `docs/` — mismos nombres de archivo, aunque el nombre no tenga por qué reflejar el idioma del contenido (es solo el id interno que Docusaurus usa para emparejar una traducción con su original; por eso `01-primeros-pasos.md` sigue llamándose así en la carpeta de español aunque el archivo equivalente en inglés sea también `01-primeros-pasos.md` con contenido distinto).
  - Los 13 archivos existentes (12 de nivel raíz + `08-privacy-data/gdpr.md`) ya están traducidos en ambos idiomas (incluido el extenso `gdpr.md`/"GDPR in depth" y `12-license-updates.md`/"Licencia y actualizaciones"). Si se edita contenido, **hay que actualizar los dos** (inglés en `docs/`, español en `i18n/es/...`) o quedan desincronizados — Docusaurus no avisa si una traducción queda desactualizada.
  - Las imágenes (`static/img/screenshots/`) son compartidas entre ambos idiomas — mismas rutas `/img/screenshots/...png` en ambos `docs/` e `i18n/es/...`, no hace falta duplicarlas.
- **Búsqueda**: `@easyops-cn/docusaurus-search-local` (índice local, sin servicio externo tipo Algolia). Cosas no obvias:
  - Solo genera el índice en `npm run build`, **no en `npm start`** — en dev mode la caja de búsqueda aparece pero sin resultados, es esperado.
  - El plugin asume por defecto que los docs viven bajo `/docs/` (routeBasePath típico de Docusaurus). Como nuestro `docs.routeBasePath` es `/`, hay que decírselo explícitamente con la opción `docsRouteBasePath: '/'` en la config del theme — si no, el índice sale vacío (0 documentos) sin ningún error visible, solo un 404 silencioso en `search-index.json`.
  - `language: ['en', 'es']` en la config del theme de búsqueda — indexa ambos idiomas, cada uno con su propio tokenizador.
- **Estructura de `docs/`**: en general un archivo por pestaña del admin, pero no siempre 1:1 (ver nota de License/White Label arriba). Los archivos mantienen su prefijo numérico de archivo (`01-` … `12-`) del material fuente, pero **el orden real del sidebar ya no depende de esos números** — se agregó `sidebar_position` explícito en el frontmatter de los 13 docs de nivel raíz (2026-07-19, al insertar la pestaña License en medio de la secuencia existente) para no tener que renombrar archivos ni arreglar enlaces cruzados cada vez que se inserta una pestaña nueva. **Regla al agregar cualquier doc nuevo de nivel raíz: usar `sidebar_position` explícito, no depender del nombre de archivo ni asumir que Docusaurus lo intercalará bien solo** (mezclar archivos con y sin `sidebar_position` en la misma categoría autogenerada da un orden impredecible). `08-privacy-data/` es una carpeta-categoría con `index.md` (ajustes) + `gdpr.md` (RGPD en profundidad, contenido fusionado desde `GDPR.md` del material fuente); su posición en el sidebar la controla `position` en `_category_.json` (actualmente `9`), independiente del prefijo numérico del nombre de la carpeta. Los enlaces cruzados entre docs usan rutas relativas (con el nombre de archivo real, prefijo incluido cuando lo tiene — ej. `06-chat-behavior.md`) o slugs absolutos (`/privacy-data`, `/privacy-data/gdpr`) — Docusaurus antepone el `baseUrl` solo automáticamente a esos slugs, no hace falta escribir `/docs/privacy-data` a mano. Docusaurus también **quita automáticamente el prefijo numérico del slug/URL** (`06-chat-behavior.md` → `/docs/chat-behavior`), por eso los enlaces absolutos nunca llevan el número.

## Cómo correrlo en local

```bash
npm start              # dev server con hot-reload, sin índice de búsqueda
npm run build           # build de producción
npm run serve            # sirve el build/ real, con búsqueda funcionando
```

Como `baseUrl` es `/docs/`, en local todo cuelga de `localhost:PORT/docs/` (no de la raíz).

## Qué falta (no asumir que ya está hecho)

- El repo `fancybricks/fancy-chat-docs` **ya existe en GitHub** (creado por el usuario desde GitHub Desktop, 2026-07-12), pero el trabajo de traducción/i18n/capturas de esa sesión seguía sin comitear la última vez que se verificó — confirmar el estado real de `git status` antes de asumir qué hay subido.
- **Nada se ha subido al hosting real** — el `build/` nunca se copió a `fancychatbot.com/docs/`.
- No hay CI/CD; el build es manual por ahora.
