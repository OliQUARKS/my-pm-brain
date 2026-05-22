# Decision: La solicitud de préstamo se persiste en BD solo al completar firma + TOTP

## Status
decided

## Date
2026-05-19

## Context
El sistema necesita definir en qué momento se crea un registro en la tabla `credits`.
Las opciones van desde persistir cuando el usuario empieza a navegar hasta solo cuando
confirma con firma + TOTP. La elección afecta data quality, reporting y estado del BO.

## Options considered
1. Persistir al iniciar navegación de opciones (máxima visibilidad, datos sucios)
2. Persistir al seleccionar una opción de préstamo (mitad del funnel)
3. Persistir solo al completar firma + TOTP (solo compromisos reales)

## Decision
Opción 3 — se crea el registro solo al completar firma + TOTP.

## Why
Evita data sucia en la tabla `credits` con solicitudes abandonadas. El BO ve solo
compromisos reales. El usuario puede navegar, explorar y abandonar sin dejar rastro.
El trigger de expiración (1h) aplica desde este momento, no desde antes.

## Evidence
- Nico y Isra confirmaron como decisión técnica en planning interno  `[ingestion/meetings/2026-05-19-planning-refinement-perc.md](../ingestion/meetings/2026-05-19-planning-refinement-perc.md)`
- El PRD describe el flujo como iniciado solo con acción confirmada  `[source/adhoc/2026-05-21-prd-flujo-credito.md](../source/adhoc/2026-05-21-prd-flujo-credito.md)`

## Explicitly NOT doing
- No persistir al inicio de navegación de opciones de préstamo  `(stakeholder-verbal, Nico, 2026-05-19)`
- No persistir al seleccionar parámetros antes de firmar  `(stakeholder-verbal, Nico, 2026-05-19)`

## What would reverse this
PERC solicita analytics de funnel pre-commit (e.g. tasa de abandono entre opciones y
firma) que requieran registros persistidos antes del TOTP — y ese requerimiento llega
por escrito antes del cierre del MVP.

## Remaining ambiguities
- Si en el futuro hay un "borrador guardado" feature, esta decisión necesitaría revisión.

## Linked
- Strategy: `../knowledge/strategy.md` § 1–2 quarter priorities
- Stakeholders: `../stakeholders/nicolas.md`, `../stakeholders/israel-fernandez.md`
