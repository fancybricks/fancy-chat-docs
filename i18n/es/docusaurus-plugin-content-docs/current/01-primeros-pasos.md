---
title: Primeros pasos
slug: /
sidebar_position: 1
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
4. Ve a **Licencia** y pega la clave de tu correo de confirmación de
   compra para activar las actualizaciones automáticas y el soporte
   (ver [Licencia y actualizaciones](12-license-updates.md)) — es
   independiente de la clave API de arriba y nunca afecta si el widget
   de chat funciona.
5. Rellena **Empresa y contenido** para que el asistente conozca tu
   negocio (ver [Empresa y contenido](03-company-content.md)).

## Redirección de primer uso

Este redirect solo ocurre **una vez**, justo después de activar el plugin
(no en cada carga del admin), y se salta automáticamente si activas varios
plugins a la vez desde la lista de plugins (activación en bloque) — en ese
caso simplemente te quedas en la lista de plugins, como es de esperar.
