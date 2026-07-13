# Decision: El arrepentimiento (10 días) solo se puede ejecutar si el cliente tiene los fondos para devolver

## Status
decided

## Date
2026-06-12

## Context
El botón de arrepentimiento (Ley) permite al cliente devolver el préstamo dentro de los 10 días sin absorber costo. Faltaba definir la condición operativa: ¿se puede arrepentir siempre, o solo si tiene los fondos disponibles para devolver el capital? Esto condiciona el criterio de aceptación del flujo de arrepentimiento (Sprint 4) y su implementación técnica (TED de devolución).

## Options considered
1. Permitir el arrepentimiento siempre, generando una deuda a cobrar si no hay fondos.
2. Requerir que el cliente tenga los fondos disponibles para devolver el capital total al momento de arrepentirse.

## Decision
Opción 2 — para efectivizar el arrepentimiento, el sistema primero consulta el saldo; si el cliente tiene los fondos, se ejecuta una **TED que retira el monto del CBU del empleado de vuelta al CBU recaudador**. Si no tiene los fondos, no puede arrepentirse (debería ir por cancelación anticipada, que sí tiene costo).

## Why
Arrepentirse equivale a devolver el producto; en una compra el producto se devuelve físicamente, y acá el producto es monetario. Sin fondos no hay devolución posible, por lo que el arrepentimiento sin costo no aplica. Mantiene el beneficio de protección al consumidor (sin costo) acotado a quien efectivamente puede revertir la operación.

## Evidence
- Seba confirmó que el criterio fue acordado con Marcos: el arrepentimiento implica devolver el monto y, de no tener los fondos, no se puede arrepentir  [../source/meetings/2026-06-12-proceso-prestamos-mantovana.md](../source/meetings/2026-06-12-proceso-prestamos-mantovana.md)
- En un arrepentimiento de compra el cliente debe devolver el producto; acá el producto es monetario, por lo que la devolución del capital es condición  `(industry-knowledge)`

## Explicitly NOT doing
- No habilitar el arrepentimiento generando una deuda cuando el cliente no tiene fondos para devolver — ese caso va por cancelación anticipada (con costo)  `(stakeholder-verbal, Sebastián, 2026-06-12)`

## What would reverse this
Compliance/legal dictamina que el derecho de arrepentimiento debe garantizarse aunque el cliente no tenga fondos (protección al consumidor), obligando a un esquema de devolución diferida sin costo.

## Remaining ambiguities
- Si la primera cuota ya se cobró dentro de la ventana de 10 días, cómo se maneja la devolución de esa cuota — depende de la ventana de toma (ej. habilitar préstamos solo hasta el día 10 para que el arrepentimiento caiga en un mes sin descuento ejecutado). Seba lo lleva a refinamiento interno.
- Canal y UX exactos de la solicitud de arrepentimiento (condicional legal mostrado en el front).
