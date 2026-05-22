# Decision: La Sábana es render-only — se persisten los 5 documentos por separado

## Status
decided

## Date
2026-05-20

## Context
El usuario firma un documento compuesto ("Sábana") que agrupa 5 documentos legales.
Decisión: ¿persistir el Sábana como unidad, o los 5 documentos individualmente?
Afecta storage, CRUD de documentos, auditoría y reusabilidad (cancelación anticipada
también requiere firma).

## Options considered
1. Persistir el Sábana completo como un único documento firmado
2. Persistir los 5 documentos individualmente; el Sábana es solo render

## Decision
Opción 2 — los 5 documentos se persisten por separado. El Sábana no se guarda.

## Why
Los documentos individuales son reutilizables para otros flujos (cancelación anticipada
usa el mismo mecanismo de firma). El CRUD del BO maneja un único módulo de documentos
tipificados. La auditoría opera sobre documentos individuales. El Sábana se genera
en el momento del render para el usuario y no tiene valor como artefacto persistido.

## Evidence
- Seba y Nico confirmaron en refinement: "el documento Sábana es solo un render para
  el usuario; lo que se firma y almacena son los 5 documentos individualmente"  `[ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../ingestion/meetings/2026-05-20-refinement-backlog-perc.md)`
- El flujo de cancelación anticipada reutiliza la misma lógica de firma  `[ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../ingestion/meetings/2026-05-20-refinement-backlog-perc.md)`

## Explicitly NOT doing
- No almacenar el Sábana como documento compuesto post-firma  `(stakeholder-verbal, Seba, 2026-05-20)`

## What would reverse this
Un requerimiento legal o de compliance que exija el Sábana firmado como unidad
(e.g. regulación argentina que requiera el documento composite como artifact de auditoría)
— verificado por escrito con el área legal de PERC antes del cierre del MVP.

## Remaining ambiguities
- ¿Los documentos dinámicos vs. estáticos afectan el momento de generación del Sábana?
  (Seba responde ~2026-05-27 — si son dinámicos, el render necesita un parser adicional.)

## Linked
- Strategy: `../knowledge/strategy.md` § Compliance
- Stakeholders: `../stakeholders/sebastian.md`, `../stakeholders/nicolas.md`
