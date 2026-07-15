---
title: Primeros pasos
slug: /
---

## Requisitos

- WordPress 6.0 o superior.
- PHP 8.1 o superior.
- Una clave API de Anthropic (Claude) — se paga directamente a Anthropic,
  el plugin no revende tokens ni añade margen sobre el consumo de IA.

## Instalación

1. Sube el ZIP del plugin desde Plugins → Añadir nuevo → Subir plugin, y
   actívalo.
2. Al activarlo, WordPress te lleva **automáticamente** a la pestaña
   **Proveedor de IA** — no hace falta ir a buscarla.
3. Pega tu clave API de Anthropic y pulsa **Probar conexión** para
   confirmar que funciona antes de guardar (ver
   [Proveedor de IA](02-ai-provider.md)).
4. Rellena **Empresa y contenido** para que el asistente conozca tu
   negocio (ver [Empresa y contenido](03-company-content.md)).

## Qué pasa si activas el plugin sin configurar la clave todavía

El widget de chat **no aparece en el sitio** hasta que hay una clave API
guardada — no se muestra una burbuja rota ni un error visible para los
visitantes, simplemente no se carga nada.

Mientras tanto, el propio admin de WordPress te lo recuerda de dos formas:

- Un aviso descartable en el resto del admin (cualquier pantalla que no
  sea la del propio plugin), con un enlace directo a Proveedor de IA.
- Un aviso permanente dentro de cualquier pestaña del plugin (salvo
  Proveedor de IA, donde sería redundante con el propio campo).

Ambos avisos desaparecen solos en cuanto guardas una clave válida.

## Redirección de primer uso

Este redirect solo ocurre **una vez**, justo después de activar el plugin
(no en cada carga del admin), y se salta automáticamente si activas varios
plugins a la vez desde la lista de plugins (activación en bloque) — en ese
caso simplemente te quedas en la lista de plugins, como es de esperar.
