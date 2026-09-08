# Decision: Los prototipos para RyD Abogados usan datos genéricos/sintéticos, no datos reales de expedientes

## Status
decided

## Date
2026-09-07

## Context
El discovery del 2026-09-03 dejó abierto el tema de protección de datos: RyD ya usa IA de forma informal sin política de qué comparte, y no había marco definido para tocar datos reales de expedientes (CBU, DNI, datos de litigantes) en ningún prototipo de automatización. Bloqueaba la sección "qué hay que definir sí o sí" del build-context.

## Options considered
1. Pedir a RyD un marco legal/NDA formal antes de tocar cualquier dato real.
2. Usar datos genéricos/sintéticos en todos los prototipos, evitando el problema en esta etapa.
3. No definir nada y avanzar caso por caso.

## Decision
Los prototipos que se construyan para RyD Abogados (mapeo de flujo, demo de automatización) usan datos genéricos/sintéticos. No se cargan datos reales de expedientes, CBU, DNI ni información de litigantes en ningún prototipo.

## Why
Cierra el riesgo de protección de datos sin bloquear el avance del deal esperando un marco legal formal que RyD no tiene resuelto. Es la vía más simple y rápida para no comprometer datos sensibles en esta etapa preventa/discovery.

## Evidence
- El equipo de RyD ya usa IA (ChatGPT/Claude) de forma informal sin política de qué comparte, y no hay marco de protección de datos definido; riesgo real y vigente.  [ingestion/meetings/2026-09-03-ryd-abogados-discovery.md](../ingestion/meetings/2026-09-03-ryd-abogados-discovery.md)

## Explicitly NOT doing
- No se pide a RyD un marco legal/NDA formal de tratamiento de datos en esta etapa.  (chat, no artifact)
- No se usan datos reales de expedientes en ningún prototipo de esta pre-propuesta.  (chat, no artifact)

## What would reverse this
Si en el discovery pago posterior RyD exige o provee un marco de datos formal (NDA, entorno controlado) que habilite trabajar con datos reales, se reabre la decisión para permitirlo bajo ese marco.

## Remaining ambiguities
No se definió una política de IA para el equipo de RyD en general (más allá del alcance de los prototipos de Quarks); sigue abierto pero fuera del alcance de esta decisión puntual.

## Linked
- Build-context: `../briefings/2026-09-07-ryd-abogados-build-context.md`
- Stakeholders informados: `../stakeholders/hernan-capolupo.md`, `../stakeholders/juan-francisco-verde.md`
