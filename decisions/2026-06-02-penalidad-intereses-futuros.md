# Decision: La precancelación anticipada cobra penalidad sobre intereses futuros

## Status
decided

## Date
2026-06-02

## Context
En la cancelación anticipada (el usuario paga el total antes de término) estaba abierto si se cobra un costo por los intereses futuros no devengados. Define la fórmula de cancelación anticipada y el messaging de costo al usuario (Sprint 4).

## Options considered
1. Sin penalidad: el usuario paga solo el capital restante
2. Penalidad sobre intereses futuros: se cobra un % sobre los intereses no devengados + comisión + IVA

## Decision
Opción 2 — se aplica costo. **Fórmula:** Total = Capital restante + (Int. futuros × % penalidad) + (Capital restante × % comisión) + IVA s/(penalidad + comisión). Todos los % son configurables por tipo de préstamo.

## Why
PERC cobra costo por la cancelación anticipada para compensar los intereses futuros no devengados, como es práctica estándar en préstamos. Seba estaba consultando internamente y Olivier pidió validarlo con Fefe (COO Quarks) antes de cerrar; quedó confirmado que se cobra.

## Evidence
- Seba estaba "consultando si se cobra algo de los intereses futuros como penalidad o no"; Olivier sugirió verlo con Fefe (COO) antes de cerrar  [../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md)
- Confirmado tras la consulta: en precancelación anticipada se aplica costo; fórmula cerrada con Seba (Compliance) y Fefe (COO)  `(chat, no artifact)`
- La fórmula de cancelación anticipada (capital restante + penalidad + comisión + IVA) ya estaba documentada en la metodología de cuota del Excel  [../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md)

## Explicitly NOT doing
- No permitir precancelación sin costo (eso es el flujo de "arrepentimiento" a 10 días, que sí es sin costo — escenario distinto)  `(chat, no artifact)`

## What would reverse this
PERC/legal o un cambio regulatorio de defensa al consumidor define que la precancelación no puede cobrar penalidad sobre intereses no devengados, o Compliance reescribe la fórmula.

## Remaining ambiguities
- % exacto de penalidad y comisión (configurables por template; los valores del Excel son ilustrativos, no finales).
- IVA en cancelaciones: ¿aplica siempre o solo si el usuario no paga en término? — open question separada, Seba rearmando el Excel.

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md` § Cuota methodology § Cancelación anticipada
- Stakeholders informed: [../stakeholders/sebastian.md](../stakeholders/sebastian.md), [../stakeholders/federico.md](../stakeholders/federico.md)
