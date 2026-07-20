# Marcos Perez — Developer, Quarks Alchemist

## Snapshot
- Role: Developer, Quarks Alchemist
- Reports to / works with: Nicolás (TL)
- Influence on my work: low
- Friction level: low

## What they care about
- Claridad en los requerimientos para poder implementar
(intuition, PM, 2026-05-21)

## Concerns / watch-outs
TODO: confirmar en daily/refinement.

## Communication style
TODO: confirmar.

## Open asks
- Nada documentado aún.

## Touchpoint log
- 2026-05-19 — Planning + refinement interno Quarks. Owner: CRUD de solicitudes/créditos + improvements. [ingestion/meetings/2026-05-19-planning-refinement-perc.md](../ingestion/meetings/2026-05-19-planning-refinement-perc.md)
- 2026-07-16 (dry-run interno, mañana) — Caminó la planilla del UAT de Préstamos en local. Surgió: bug de `application` no completada tras pago total (bloquea pedir 2º préstamo), gaps de front (desglose de cuota user-side, signo de `deviation`, botón copiar/strings cortados), y fallos aleatorios de infra (65 lambdas en local). Propuso el happy-path con el cliente. [../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)
- 2026-07-16 — Presentó la demo/UAT al cliente (recorrido completo por Insomnia + playground). Confirmó auditoría/conciliación; acordó implementar el threshold/delta en capa de negocio; recibió la 2ª cuenta para cashout (test 17/7). [../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md)

## Touchpoint log (cont.)
- 2026-07-17 — Call Amfays <> PERc. Armó (con Olivier) el Excel que baja todos los campos del documento AMFAYS y presentó la propuesta de cambiar el formato (checkboxes → texto) para el ingreso dinámico. [../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md)
- 2026-07-20 — SYNC Producto (mencionado; de vacaciones en Saint Tropez). Diferencia de velocidad tremenda con el front (JP le derivaba tareas de front). **Candidato a soporte de PERC post-entrega** (Olivier: "le tengo que enseñar") + posible KT de iFlow (fuera de scope PERC). Fefe pide review técnica Nico/Marcos por el tema JP + lambdas. [../ingestion/meetings/2026-07-20-sync-producto.md](../ingestion/meetings/2026-07-20-sync-producto.md)
- 2026-07-20 — Daily PERC. Definió la secuencia de trabajo: **cash out** (en curso, +4 lambdas → ~64, ventana 9–18) → **threshold** → **refactor de lambdas** (~60 archivos; no entra hasta pasar el PR de cash out). Pide a Nico destrabar el PR de cash out. Approach para el documento AMFAYS: **HTML pelado + variables + lógica de firma**, AMFAYS adapta después ("va a durar meses"). Aporta el enfoque de UAT asistido por IA. [../ingestion/meetings/2026-07-20-daily-perc.md](../ingestion/meetings/2026-07-20-daily-perc.md)

## Last touched
2026-07-20

