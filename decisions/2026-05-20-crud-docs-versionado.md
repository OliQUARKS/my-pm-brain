# Decision: CRUD documentos — versionado con activación explícita, sin edición de versiones publicadas

## Status
decided

## Date
2026-05-20

## Context
El BO gestiona una librería de documentos HTML para el flujo de firma del préstamo. Necesita definirse si las versiones pueden editarse, reemplazarse automáticamente o solo activarse/desactivarse manualmente. La decisión afecta trazabilidad de auditoría, integridad de documentos ya firmados y reutilización del mecanismo para cancelación anticipada.

## Options considered
1. Edición directa de versiones existentes (mutable — sin historial)
2. Versionado con reemplazo automático: la nueva versión archiva la anterior
3. Versionado con activación explícita: múltiples versiones coexisten; el BO desactiva manualmente las que ya no aplican

## Decision
Opción 3 — versionado con activación explícita. Las versiones publicadas son inmutables.

## Why
Un documento firmado por un usuario no puede alterarse retroactivamente sin comprometer la auditoría. El BO puede necesitar mantener versiones previas activas para préstamos ya otorgados mientras activa una versión nueva para solicitudes futuras. El mecanismo es reutilizable para el documento de cancelación anticipada (mismo flujo de firma). La inmutabilidad de versiones publicadas es un requisito de trazabilidad.

## Evidence
- Seba + Nico confirmaron en refinement: versiones existentes siguen activas hasta desactivación explícita por el BO  `[ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../ingestion/meetings/2026-05-20-refinement-backlog-perc.md)`
- El flujo de cancelación anticipada reutiliza la misma librería de documentos y mecanismo de firma  `[ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../ingestion/meetings/2026-05-20-refinement-backlog-perc.md)`
- Coherente con la Sábana como render-only — los documentos individuales son la unidad de persistencia y auditoría  `[decisions/2026-05-20-sabana-no-persiste.md](./2026-05-20-sabana-no-persiste.md)`

## Explicitly NOT doing
- No permitir edición de versiones ya publicadas  `(stakeholder-verbal, Seba, 2026-05-20)`
- No archivar automáticamente versiones anteriores al activar una nueva  `(stakeholder-verbal, Nico, 2026-05-20)`

## What would reverse this
(a) Patricio (Compliance PERC) o legal de PERC define por escrito un modelo de versionado diferente (ej. solo 1 versión activa por tipo de documento en simultáneo). (b) Watson BO tiene restricciones técnicas que impidan mantener múltiples versiones activas.

## Remaining ambiguities
- Documentos dinámicos vs. estáticos: si son dinámicos (con variables del usuario), el versionado debe incluir el mapping de variables. Seba responde ~2026-05-27.
- Restricciones de archivos HTML (tamaño, XSS, sanitización): pendiente respuesta de Ari + Tano (cyber PERC).

## Linked
- Strategy: `../knowledge/strategy.md` § Compliance
- Decisions linked: `./2026-05-20-sabana-no-persiste.md`
- Stakeholders: `../stakeholders/sebastian.md`, `../stakeholders/nicolas.md`, `../stakeholders/ariel-gendelman.md`, `../stakeholders/stefano-giuliano.md`
