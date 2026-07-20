# Decision: El documento del préstamo se firma y persiste como UN solo documento (supersede la sábana + 5 docs)

## Status
decided

## Date
2026-07-20

## Context
La decisión [2026-05-20-sabana-no-persiste](./2026-05-20-sabana-no-persiste.md) definió que la "sábana" era render-only y que se **persistían 5 documentos por separado**. El relevamiento con AMFAYS (2026-07-17) estableció que el legajo se **unifica en un solo archivo firmado** (separar/mezclar formularios rompe la validez), y en el C12 (2026-07-20) Seba confirmó que **la estructura es un solo documento con firma electrónica**. Olivier confirma el cierre de la tensión "T&C 5→1": **es un solo documento**. Esto reversa la parte de "5 documentos por separado" de la decisión previa.

## Options considered
1. Persistir los 5 documentos individualmente; la sábana es solo render (decisión previa, 2026-05-20).
2. **Un solo documento unificado** (firma electrónica) que se firma y persiste como unidad — elegida.

## Decision
El flujo de firma opera sobre **un solo documento** (firma electrónica, conjunto de evidencias). Se firma y persiste como **una unidad**, no como 5 documentos separados. **Supersede** [2026-05-20-sabana-no-persiste](./2026-05-20-sabana-no-persiste.md).

## Why
El instrumento de AMFAYS es un legajo que se unifica en un único archivo firmado; separar los formularios rompe la validez del legajo. Alinear la persistencia con "un documento" evita divergencia entre lo que exige la mutual y lo que Quarks almacena, y simplifica el CRUD/auditoría (un artefacto firmado por solicitud). La reutilización de la lógica de firma para cancelaciones ya no es un driver: las cancelaciones quedaron **registro-only con trazabilidad en el BO** (ver tensión resuelta en strategy).

## Evidence
- AMFAYS: el legajo (8-9 formularios) se unifica en **un solo archivo firmado**; separar/mezclar formularios rompe la validez  [ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md)
- Seba (C12): "la estructura del documento sigue siendo la misma, en tanto es **un solo documento**; tiene una firma electrónica, no tiene más magia que eso"  [ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)
- Olivier confirma el cierre de la tensión T&C 5→1: es un solo documento  (chat, no artifact)

## Explicitly NOT doing
- NO se persisten los 5 documentos por separado (revierte la decisión 2026-05-20)  (chat, no artifact)
- NO se construye un circuito de reporte de cancelaciones a Mantovana — las cancelaciones son **registro-only con trazabilidad de usuario en el BO**  (stakeholder-verbal, Olivier, 2026-07-20)

## What would reverse this
Un requerimiento legal/compliance (AMFAYS o legales PERC) que exija persistir los formularios/documentos subyacentes por separado como artefactos de auditoría independientes. Señal observable: definición escrita de compliance que pida N documentos separados.

## Remaining ambiguities
- El documento único debe seguir siendo **auditable** (los contenidos de los formularios embebidos, trazables) — confirmar que la auditoría opera bien sobre el archivo unificado.
- Modelo final del documento reformateado (texto en vez de checkboxes) pendiente de ver con AMFAYS.

## Linked
- Supersedes: `./2026-05-20-sabana-no-persiste.md`
- Feature: `../knowledge/product/features/flujo-credito.md` § Documento / campos AMFAYS
- Org: `../knowledge/org/amfays.md`
- Strategy: `../knowledge/strategy.md` § Tensions (T&C 5→1)
- Stakeholders informed: `../stakeholders/sebastian.md`, `../stakeholders/nicolas.md`
