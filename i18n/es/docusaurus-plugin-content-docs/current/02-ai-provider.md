---
title: Proveedor de IA
---

Todo lo relacionado con la conexión a la IA que impulsa el asistente.

![Pestaña Proveedor de IA](/img/screenshots/ai-provider.png)

## Clave API de Anthropic

- Se guarda **cifrada en reposo** y nunca se envía al navegador del
  visitante — todas las llamadas a Anthropic pasan por el propio servidor
  de WordPress.
- Mientras hay una clave guardada, el campo la muestra enmascarada
  (`********`) — para reemplazarla, simplemente pega una nueva y guarda;
  para confirmarla sin cambiarla, usa **Probar conexión** (no hace falta
  volver a pegarla).

### Probar conexión

Botón junto al campo de la clave. Hace una llamada real mínima (`max_tokens
16`) contra Anthropic con el modelo seleccionado, y distingue tres
resultados:

- **Clave inválida** — Anthropic la rechazó (typo, o clave revocada).
- **Sin créditos** — la clave es válida pero la cuenta de Anthropic no
  tiene saldo.
- **No se pudo conectar** — problema de red/servidor (el servidor no
  permite peticiones HTTPS salientes, por ejemplo).

Funciona tanto con una clave recién pegada en el campo (antes de guardar)
como con la clave ya guardada (dejando el campo con la máscara tal cual).

### Eliminar clave

Botón para eliminar la clave guardada (pide confirmación, ya que el
asistente queda desconectado hasta guardar una nueva). Solo aparece si
hay una clave guardada actualmente.

## Modelo

Selector con tres modelos de Claude:

| Modelo | Cuándo usarlo |
|---|---|
| Claude Haiku 4.5 | Más rápido y barato — ideal para volumen alto de chats |
| Claude Sonnet 5 | Equilibrio entre capacidad y coste |
| Claude Opus 4.8 | Más capaz, coste más alto |

## Máximo de tokens por respuesta

Techo de tokens por cada respuesta del asistente (rango 256–8000). Valores
más altos permiten respuestas más largas, pero cuestan más por mensaje.

## Estimador de coste en vivo

Debajo del selector de modelo y del límite de tokens: "$10 de crédito de
API ≈ X–Y mensajes con este modelo y límite." Se recalcula al instante
según lo que elijas, **antes de guardar** — para decidir con el coste
delante, no después de que ya esté configurado.

El rango (X–Y) va del peor caso (cada respuesta agotando el límite de
tokens) al caso típico (respuestas cortas) — por eso es un rango, no un
número único.
