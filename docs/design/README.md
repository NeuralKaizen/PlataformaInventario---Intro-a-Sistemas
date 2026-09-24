# Diseño de mise

**mise** (de *mise en place*, nombre provisional) es una plataforma web donde un restaurante usa su histórico de ventas para planear la compra de insumos. Corresponde a la propuesta 2 de `docs/Proyecto 1 introducción a la ingeniería de sistemas.pdf`.

Esta carpeta guarda la definición visual y funcional acordada antes de escribir código.

## Prototipo

`prototipo/mise-prototipo.html` se abre directo en el navegador. Es funcional: los datos son de ejemplo, pero todo lo que editas repercute en las demás pestañas.

| Pestaña | Qué muestra | Captura |
|---|---|---|
| Panorama | Conversación con mise: saludo, resumen del día escrito en vivo y tres tarjetas de acción | `capturas/panorama.png` |
| Despensa | Estantería de frascos; el nivel son los días que alcanza cada insumo | `capturas/despensa.png` |
| Planes de compra | Comandas por proveedor sobre los próximos 7 días, editables y arrastrables | `capturas/planes.png` |
| Pronóstico | Platos esperados por día (barras), con eventos que suman o restan | `capturas/pronostico.png` |
| Proveedores | Mapa con rutas, tiempo de entrega editable y cumplimiento | `capturas/proveedores.png` |
| Recetas | Fichas técnicas con gramajes editables, costo y margen | `capturas/recetas.png` |
| Pregúntale a mise | Asistente de IA que difumina el fondo, conoce la pestaña actual y ejecuta acciones | `capturas/mise.png` |

## Decisiones visuales

- **Dirección:** mezcla de "Mercado vivo" (limpieza, barra lateral) y "Comanda riso" (layout, estética de impresión risográfica). Ver `exploraciones/01` y `02`.
- **Barra lateral:** "barra de tinta" (bloque oscuro, sección activa en rosa). La alternativa "tarjeta sticker" queda guardada en `alternativas/`. Ver `exploraciones/03`.
- **Paleta:** flúor original. Papel `#f6f1e7`, tinta `#1d1a2b`, rosa `#ff48b0`, amarillo `#ffe800`, azul `#0078bf`, naranja `#ff6c2f`, verde `#00a878`. Las versiones atenuadas quedan en `exploraciones/04` por si el equipo quiere bajar la intensidad.
- **Tipografía:** Bricolage Grotesque (titulares), Instrument Sans (texto), DM Mono (datos y etiquetas).
- **Pronóstico:** barras por día, hablando en platos y no en porcentajes. Ver `exploraciones/05`.
- **Panorama:** “mise primero”, variante “conversación en curso”: mise saluda, escribe el resumen del día con los datos vivos y deja tres tarjetas de acción, con la barra para responderle. Ver `exploraciones/06` a `08`.

## Modelo que conecta todo

- Consumo diario de un insumo = gramos por plato (Recetas) × platos vendidos (Pronóstico).
- Días de cobertura = stock ÷ consumo diario (Despensa).
- Comanda sugerida por proveedor: se pide el día en que el insumo se acaba menos el tiempo de entrega del proveedor (Planes, Proveedores).
- Cualquier cambio (un evento, un gramaje, un tiempo de entrega, una cantidad) recalcula riesgos, comandas y Panorama.

## Pendiente

- **Spec técnico:** Angular + Bootstrap (grilla y utilidades) + CSS propio, datos en memoria con signals/computed, IA con OpenRouter (Gemini 2.5 Flash) mediante una función en Vercel, deploy en Vercel.
