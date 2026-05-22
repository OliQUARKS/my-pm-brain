# Decision: El desembolso de préstamos se realiza siempre a la cuenta sueldo

## Status
decided

## Date
2026-05-19

## Context
El sistema necesita definir a qué cuenta se deposita el monto del préstamo. El usuario PERC puede tener múltiples wallets (cuenta sueldo, cuenta de ahorro, etc.). La elección afecta el flujo de desembolso, la integración con `get account` y la coherencia con el ciclo de cobro vía nómina.

## Options considered
1. El usuario elige la cuenta destino entre sus wallets disponibles
2. Siempre a la cuenta sueldo (identificada dentro de la lista de wallets del usuario)

## Decision
Opción 2 — el desembolso se realiza siempre a la cuenta sueldo.

## Why
El ciclo de cobro opera vía nómina (La Mantovana descuenta de sueldo cada mes). Tiene coherencia sistémica que el desembolso vaya a la misma cuenta. Simplifica el flujo: no hay decisión del usuario sobre el destino. El sistema identifica la cuenta sueldo dentro de la lista de wallets vía `get account`.

## Evidence
- Decisión confirmada en planning + refinement interno Quarks con Nico e Isra  `[ingestion/meetings/2026-05-19-planning-refinement-perc.md](../ingestion/meetings/2026-05-19-planning-refinement-perc.md)`
- El PRD describe el desembolso como operación a cuenta sueldo del empleado  `[source/adhoc/2026-05-21-prd-flujo-credito.md](../source/adhoc/2026-05-21-prd-flujo-credito.md)`

## Explicitly NOT doing
- No permitir al usuario elegir una cuenta destino alternativa para el desembolso  `(stakeholder-verbal, Nico, 2026-05-19)`

## What would reverse this
PERC solicita por escrito la posibilidad de desembolsar a una cuenta distinta a la de nómina (ej. cuenta de ahorro o inversión), y ese requerimiento llega antes del cierre del MVP.

## Remaining ambiguities
- La identificación de la cuenta sueldo dentro de la lista de wallets vía `get account` está pendiente de validación técnica (Nico / Isra).

## Linked
- Strategy: `../knowledge/strategy.md` § 1–2 quarter priorities
- Stakeholders: `../stakeholders/nicolas.md`, `../stakeholders/israel-fernandez.md`, `../stakeholders/sebastian.md`
