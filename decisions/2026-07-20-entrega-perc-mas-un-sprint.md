# Decision: La entrega de PERC toma +1 sprint sobre las 12 semanas; se arranca el refactor de lambdas antes del UAT formal

## Status
decided

## Date
2026-07-20

## Context
El "hard-stop del martes 2026-07-21" que Olivier venía comunicando se volvió inalcanzable por tres frentes convergentes (consolidación de lambdas pedida tarde por PERC + entorno dev que nunca desplegó la versión actual + documento AMFAYS). El fork: ¿forzar la entrega el martes con lo que hay, escalar el atraso, o aceptar formalmente un sprint más?

## Options considered
1. **Extender +1 sprint "por las buenas"** y arrancar el refactor de lambdas ya, en paralelo al trabajo de datos AMFAYS (desacoplado) — elegida.
2. Escalar el atraso con la lista de frentes como argumento (carta de reserva) — no necesaria: Fefe avaló la extensión sin fricción.
3. Entregar happy-path + código el martes y transferir el deploy a PERC — descartada (el UAT no sería verídico sin el refactor + entorno estable).

## Decision
Se acepta **+1 sprint** (1–2 semanas sobre las 12 = ~10%). Se **arranca el refactor de lambdas hoy/mañana** (antes del UAT formal), porque "va a pasar de todos modos" y no depende de los datos AMFAYS. El trabajo de datos AMFAYS queda desacoplado (ver [2026-07-20-captura-datos-amfays](./2026-07-20-captura-datos-amfays.md)). La decisión operativa del alcance/tiempo fino la valida Seba (PO PERC).

## Why
Un desvío de ~10% sobre 12 semanas con un solo dev es razonable y esperable (Fefe: "es lo lógico, está perfecto, dejemos correr"). El refactor de lambdas es condición para un UAT verídico (reescribe paths de front/Insomnia); hacerlo primero evita rehacer el UAT dos veces. Evita una escalación innecesaria manteniendo la relación con PERC.

## Evidence
- Fefe avala +1 sprint: "una, dos semanas más… en doce semanas nos estiramos una o dos semanas, 10% es lo lógico y está perfecto… dejemos correr"  [ingestion/meetings/2026-07-20-sync-producto.md](../ingestion/meetings/2026-07-20-sync-producto.md)
- Nico: conviene arrancar el refactor de lambdas ya, "va a pasar de todos modos, no depende de esos datos [AMFAYS]"  [ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)
- El refactor reescribe paths de front/Insomnia y obliga a rehacer el UAT completo (+1 sprint); el dev env nunca desplegó la versión actual  [ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)
- Secuencia de trabajo: cash out → threshold → refactor de lambdas (no entra hasta pasar el PR de cash out)  [ingestion/meetings/2026-07-20-daily-perc.md](../ingestion/meetings/2026-07-20-daily-perc.md)

## Explicitly NOT doing
- NO se fuerza la entrega el martes 2026-07-21 con lo que hay  (stakeholder-verbal, Federico Fernandez, 2026-07-20)
- NO se escala el atraso como conflicto (la extensión se acordó "por las buenas")  [ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)

## What would reverse this
Si el refactor de lambdas + el entorno + los frentes AMFAYS/biométrico se extienden más allá de 1–2 semanas, el "+1 sprint" deja de alcanzar y habría que renegociar plazo/alcance formalmente con PERC (Marcos Copello). Señal observable: el UAT formal punta-a-punta no puede arrancar en dev estable dentro de la ventana de +1 sprint.

## Remaining ambiguities
- Confirmación explícita de Seba (PO PERC) del alcance/fecha fina del sprint extra — Fefe delegó la decisión operativa en él.
- El frente **biométrico en el flujo de préstamo** (modifica el front) podría agregar trabajo no dimensionado dentro de esta ventana — a evacuar con AMFAYS.

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md` § Timeline / § Risks
- Pendientes: `../knowledge/product/pendientes-produccion.md` § Meta-decisión plazo
- Strategy: `../knowledge/strategy.md` § Tensions (deadline)
- Decisión relacionada: `./2026-07-20-captura-datos-amfays.md`
- Stakeholders informed: `../stakeholders/federico.md`, `../stakeholders/sebastian.md`, `../stakeholders/nicolas.md`
