# Decision: Tech stack — Lambda (backend) + Angular (frontend)

## Status
decided

## Date
2026-04-20

## Context
El proyecto requería definir el stack tecnológico antes de comprometer estimaciones
y configurar el pipeline CI/CD. Decisión conjunta Quarks + PERC, con participación
del CTO, TL y área de Cybersecurity del cliente.

## Options considered
1. Lambda + Angular
2. Java (mencionado como alternativa en etapas previas del PRD)
3. TypeScript puro (mencionado como alternativa)

## Decision
Lambda (AWS Lambda) para backend, Angular para frontend.

## Why
Decisión conjunta entre los TLs de Quarks y el equipo técnico de PERC.
Alineación completa entre ambos lados — CTO, TL, Dev y Cybersecurity de PERC
participaron en la confirmación.

## Evidence
- Nico, Isra, Eze, Jo, Euge y Tano confirmaron en reunión técnica  `(stakeholder-verbal, Nico + Isra + Eze + Euge, 2026-04-20)`
- Stack referenciado como pendiente en PRD v2.0 §5 antes de esta decisión  `[source/adhoc/2026-05-21-prd-flujo-credito.md](../source/adhoc/2026-05-21-prd-flujo-credito.md)`

## Explicitly NOT doing
- No usar Java como stack principal  `(stakeholder-verbal, Nico, 2026-04-20)`
- No usar TypeScript puro como stack principal  `(stakeholder-verbal, Nico, 2026-04-20)`

## What would reverse this
Requerimiento de infraestructura de PERC que haga inviable Lambda
(e.g. restricción de su entorno cloud confirmada por Eze por escrito).

## Remaining ambiguities
- Pipeline CI/CD: pendiente de configuración, pero ya no bloqueado por el stack.

## Linked
- Strategy: `../knowledge/strategy.md` § 1–2 quarter priorities
- Stakeholders: `../stakeholders/nicolas.md`, `../stakeholders/israel-fernandez.md`, `../stakeholders/ezequiel-manfredi.md`
