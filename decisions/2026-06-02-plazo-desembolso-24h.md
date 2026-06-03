# Decision: Plazo de desembolso del préstamo = 24 horas

## Status
decided

## Date
2026-06-02

## Context
El plazo máximo de desembolso desde la aprobación estaba en discusión (verbal 24–48h, sin confirmación escrita). Es un parámetro que define la promesa al usuario, el messaging de la pantalla "tu solicitud está siendo procesada" y la lógica de fondeo/expiración del Sprint 4.

## Options considered
1. 48 horas desde aprobación
2. 24 horas desde aprobación
3. Sin SLA fijo (best-effort)

## Decision
Opción 2 — 24 horas. Si hay fondos en la cuenta recaudadora la transferencia es inmediata (estado `fondeado`); si no hay fondos, la solicitud queda en pendiente y se reintenta dentro de la ventana.

## Why
Es el plazo más corto comprometible dado el modelo de fondeo, y mejora la experiencia frente a 48h. Marcos (CEO PERC), como decisor final, lo confirmó; Seba ya lo había sugerido. El comportamiento sin fondos (queda pendiente, no rechaza silenciosamente) es consistente con la regla de fondeo del PRD.

## Evidence
- Marcos (CEO) confirmó 24h en el Sprint 2 Review  `(stakeholder-verbal, Marcos, 2026-06-02)`
- Seba ya había sugerido 24h, marcándolo como decisión de Marcos  [../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md)
- Si la cuenta recaudadora no tiene fondos, la transacción queda en pendiente — no rechaza silenciosamente  [../source/adhoc/2026-05-21-prd-flujo-credito.md](../source/adhoc/2026-05-21-prd-flujo-credito.md)

## Explicitly NOT doing
- No comprometer 48h ni dejar el desembolso sin SLA fijo  `(stakeholder-verbal, Marcos, 2026-06-02)`

## What would reverse this
PERC define por escrito un SLA distinto, o una restricción operativa de la cuenta recaudadora / del rail de pago (BIND) impide cumplir 24h de forma consistente.

## Remaining ambiguities
- Comportamiento exacto en fines de semana y feriados (¿el reloj de 24h corre igual?).
- Relación con la auto-cancelación a 24h sin fondos y con quién/cómo se notifica al usuario (open question separada del feature file).

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md`
- Decisions linked: [./2026-05-19-desembolso-cuenta-sueldo.md](./2026-05-19-desembolso-cuenta-sueldo.md)
- Stakeholders informed: [../stakeholders/marcos-copello.md](../stakeholders/marcos-copello.md), [../stakeholders/sebastian.md](../stakeholders/sebastian.md)
