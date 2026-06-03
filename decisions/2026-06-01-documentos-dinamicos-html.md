# Decision: Los documentos del flujo de firma son dinámicos y en formato HTML (no PDF como fuente)

## Status
decided

## Date
2026-06-01

## Context
El flujo de firma requiere ~5 documentos por préstamo. Estaba abierto si serían estáticos o dinámicos (con variables del usuario/préstamo) y en qué formato fuente se gestionarían en el backoffice. La decisión afecta el ABM de documentos, el motor de inyección de variables y la firma embebida (Sprint 3).

## Options considered
1. Documentos estáticos en PDF (sin variables; un PDF fijo por tipo)
2. Documentos en Word + parser para inyectar variables y firma
3. Documentos dinámicos en HTML: el HTML recibe las variables, se renderiza y se arma el PDF final con la firma embebida

## Decision
Opción 3 — documentos dinámicos en HTML. El HTML es la fuente; recibe las variables del usuario/préstamo, se pisa y de ahí se arma el PDF firmado.

## Why
Los documentos necesitan datos del usuario y del préstamo (nombre, CUIL, montos, cuotas), por lo que no pueden ser estáticos. El HTML permite inyectar variables de forma limpia y embeber la firma sin un parser intermedio; Word obligaría a mantener un parser frágil. Es coherente con el versionado de documentos ya decidido (misma librería y flujo de firma).

## Evidence
- Sebastián confirmó en el design review (1/6) que los documentos incluyen variables del usuario/préstamo (dinámicos)  `(stakeholder-verbal, Sebastián, 2026-06-01)`
- Nico (planning 2/6): los documentos van en HTML — el HTML recibe las variables, se pisa y se arma el PDF; en Word "sí o sí necesitaría un parser"  `(stakeholder-verbal, Nico, 2026-06-02)`

## Explicitly NOT doing
- No usar PDF/Word como formato fuente de los documentos — no permite inyección limpia de variables ni firma embebida sin parser  `(stakeholder-verbal, Nico, 2026-06-02)`

## What would reverse this
PERC entrega los documentos finales únicamente en Word/PDF sin equivalente HTML mantenible, o Compliance (Patricio) exige por escrito un formato fuente distinto.

## Remaining ambiguities
- Cuáles documentos exactos son dinámicos vs. estáticos — pendiente, parte de las plantillas finales escaladas al CEO.
- Tamaño/peso de los archivos (asunción <1MB por PDF, sin validar) y restricciones HTML (XSS, sanitización) pendientes de cyber PERC (Ari + Tano).

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md`
- Decisions linked: [./2026-05-20-crud-docs-versionado.md](./2026-05-20-crud-docs-versionado.md), [./2026-05-20-sabana-no-persiste.md](./2026-05-20-sabana-no-persiste.md)
- Stakeholders informed: [../stakeholders/sebastian.md](../stakeholders/sebastian.md), [../stakeholders/nicolas.md](../stakeholders/nicolas.md)
