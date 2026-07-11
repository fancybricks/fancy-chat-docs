# Fancy Chat AI — sitio de documentación (Docusaurus)

Este repo es el sitio público de documentación del plugin de WordPress **Fancy Chat AI**. Es un proyecto Docusaurus independiente, en una carpeta hermana del repo del plugin — no un submódulo ni una subcarpeta de él.

## Dónde está todo

- **Este repo**: `/Users/coudix/Documents/fancy-chat-docs` — el sitio Docusaurus.
- **Repo del plugin** (privado): `/Users/coudix/Documents/fancy-chat` — código PHP del plugin, remoto `github.com/fancybricks/fancy-chat.git`.
- **Material fuente de la doc**: `/Users/coudix/Documents/fancy-chat/documentation/` — carpeta interna del repo del plugin (no se distribuye con él, ver su propio `.distignore`). Contiene el contenido base en 12 archivos (`01-primeros-pasos.md` … `11-troubleshooting-faq.md`, más `GDPR.md`) que se usó como fuente para redactar `docs/` en este repo. Si el plugin gana una función nueva o cambia un ajuste, ese es el sitio donde probablemente se actualice primero la redacción de referencia antes de traerla aquí — pero **el contenido real y ya publicado vive en `docs/` de este repo**, no ahí.
- **Marketing site** (landing del plugin, WordPress): `/Users/coudix/Documents/fancy-chat/marketing-site/` — de aquí se sacó toda la identidad visual (ver más abajo).
- **Sitio web público del plugin**: `fancychatbot.com`.

## Qué es Fancy Chat AI (para entender el contenido que se documenta)

Plugin de WordPress que añade un widget de chat con IA (Anthropic Claude, BYOK — el cliente pone su propia API key, sin margen del plugin). Pestañas del admin, en el mismo orden que la barra lateral del sitio de docs:

1. **AI Provider** — API key, test connection, modelo, límite de tokens, estimador de coste.
2. **Company & Content** — perfil, servicios, precios, horarios, FAQ, contactos (se inyecta en el prompt de sistema).
3. **Widget & WhatsApp** — identidad del bot, preguntas sugeridas, handoff a WhatsApp, disclaimer, visibilidad por página.
4. **Widget Text** — traducción de todos los textos fijos del widget.
5. **Chat Behavior** — timeout de conversación, límite de mensajes, tope de gasto diario (kill switch real, basado en coste real no estimado).
6. **Moderation** — detección de intentos de manipulación (heurística en 5 idiomas + auto-marcado del modelo), strikes, bloqueo.
7. **Privacy & Data** — formulario pre-chat, consentimiento explícito, retención de datos. Tiene su propia sub-página profunda de RGPD.
8. **Conversations** — pantalla (no pestaña de ajustes) con buscar/filtrar/exportar CSV.
9. Transversales: traducciones/idiomas, troubleshooting/FAQ.

El código del admin vive en `fancy-chat/src/Admin/` (ej. `SettingsPage.php`) si hace falta verificar el comportamiento real de un ajuste antes de documentarlo.

## Identidad de marca (de dónde salió cada cosa)

Todo se copió de `fancy-chat/marketing-site/`, no se inventó nada:

- **Color primario**: `#4f46e5` (indigo), rampa completa en `src/css/custom.css` (`--ifm-color-primary-*`), tomada literalmente de `marketing-site/style.css` (`--color-primary` y sus estados hover `#4338ca` / `#3730a3`).
- **Logo**: `marketing-site/media/logo-icon.svg` → copiado a `static/img/logo.svg` (navbar + favicon).
- **Tipografía**: Plus Jakarta Sans (Google Fonts), igual que la landing.
- **Dominio real**: `fancychatbot.com` (confirmado por el usuario, no inventado).

## Decisiones de arquitectura del sitio (y el porqué)

- **Hosting: subcarpeta `fancychatbot.com/docs/`, no subdominio.** Se decidió así por SEO: la landing es simple (pocas páginas indexables), así que la doc (11+ páginas con contenido sustancial) es la pieza que más autoridad de dominio puede aportarle a `fancychatbot.com` — mejor que repartirla en `docs.fancychatbot.com`. Config actual: `url: 'https://fancychatbot.com'`, `baseUrl: '/docs/'`.
- **Deploy**: Docusaurus compila a HTML/CSS/JS estático puro (`npm run build` → carpeta `build/`). No necesita Node en el hosting — solo subir el contenido de `build/` a la subcarpeta `/docs/` del mismo hosting de WordPress (FTP o file manager), sin proxy ni configuración especial de rewrites (cada página ya es un HTML real, a diferencia de una SPA).
- **Repo GitHub**: pensado como repo **público** aparte (`fancybricks/fancy-chat-docs`, aún no creado/pusheado — el usuario lo gestiona con GitHub Desktop, no por CLI). Público porque el contenido de la doc no es sensible (a diferencia del código del plugin, que sí es privado). El campo `editUrl` en `docusaurus.config.js` ya apunta a esa URL asumida.
- **Home = la documentación misma.** No hay landing page separada: `docs/01-primeros-pasos.md` tiene `slug: /` en su frontmatter, así que es lo primero que se ve al entrar. Sin blog (`blog: false`, carpeta `blog/` eliminada), sin footer (se quitó el bloque `footer` completo del theme config). El navbar solo tiene el logo y un link externo a `https://fancychatbot.com`.
- **`docs.routeBasePath: '/'`** en el preset — URLs planas dentro del baseUrl (`/docs/ai-provider`, no `/docs/docs/ai-provider`).
- **i18n en español** (`defaultLocale: 'es'`) — el scaffold por defecto trae inglés, se corrigió porque todo el contenido es en español (afecta también el idioma de la UI del theme: breadcrumbs, "Editar esta página", etc.).
- **Búsqueda**: `@easyops-cn/docusaurus-search-local` (índice local, sin servicio externo tipo Algolia). Dos cosas no obvias:
  - Solo genera el índice en `npm run build`, **no en `npm start`** — en dev mode la caja de búsqueda aparece pero sin resultados, es esperado.
  - El plugin asume por defecto que los docs viven bajo `/docs/` (routeBasePath típico de Docusaurus). Como nuestro `docs.routeBasePath` es `/`, hay que decírselo explícitamente con la opción `docsRouteBasePath: '/'` en la config del theme — si no, el índice sale vacío (0 documentos) sin ningún error visible, solo un 404 silencioso en `search-index.json`.
- **Estructura de `docs/`**: un archivo por pestaña del admin, mismo prefijo numérico que el material fuente (`01-` … `11-`) para mantener el orden del sidebar. `08-privacy-data/` es una carpeta-categoría con `index.md` (ajustes) + `gdpr.md` (RGPD en profundidad, contenido fusionado desde `GDPR.md` del material fuente). Los enlaces cruzados entre docs usan rutas relativas o slugs absolutos (`/privacy-data`, `/privacy-data/gdpr`) — Docusaurus antepone el `baseUrl` solo automáticamente a esos slugs, no hace falta escribir `/docs/privacy-data` a mano.

## Cómo correrlo en local

```bash
npm start              # dev server con hot-reload, sin índice de búsqueda
npm run build           # build de producción
npm run serve            # sirve el build/ real, con búsqueda funcionando
```

Como `baseUrl` es `/docs/`, en local todo cuelga de `localhost:PORT/docs/` (no de la raíz).

## Qué falta (no asumir que ya está hecho)

- El repo `fancybricks/fancy-chat-docs` **no existe todavía en GitHub** — el usuario lo va a crear él mismo desde GitHub Desktop.
- **Nada se ha subido al hosting real** — el `build/` nunca se copió a `fancychatbot.com/docs/`.
- No hay CI/CD; el build es manual por ahora.
- El nombre de la organización de GitHub (`fancybricks`) es una inferencia del remoto del repo del plugin, no una confirmación explícita del usuario — verificar si el `editUrl` sigue siendo correcto antes de asumirlo.
