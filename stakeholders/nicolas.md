# Nicolás Paez — Tech Lead, Quarks Alchemist

## Snapshot
- Role: Tech Lead, Quarks Alchemist
- Reports to / works with: Juan Pablo Norverto (CTO), Olivier (PM)
- Influence on my work: high
- Friction level: low

## What they care about
- Factibilidad técnica y estimaciones realistas
- Definiciones técnicas de PERC (Watson, stack, CI/CD) para poder estimar
(intuition, PM, 2026-05-21)

## Concerns / watch-outs
TODO: confirmar. Las definiciones pendientes de PERC probablemente lo bloqueen tanto como al PM.

## Communication style
TODO: confirmar.

## Open asks
- Definición del tech stack para cerrar estimaciones. (source/adhoc/2026-05-21-prd-flujo-credito.md §5)
- Postgres DB structure validation with PERC — pending response from Juampi Norverto. Affects architecture for loan data persistence.

## Touchpoint log
- 2026-05-06 — Repo setup + tech validation. Nico identifies postgres DB validation needed with PERC (Juampi Norverto). iPerc-Documents-Vault-Lamda repo shared for S3 signed URLs. [ingestion/meetings/2026-05-06-repo-setup-backlog-share.md](../ingestion/meetings/2026-05-06-repo-setup-backlog-share.md)
- 2026-05-19 — Planning + refinement interno Quarks. Decisiones técnicas: creación de solicitud, expiración 1h, separación solicitudes/préstamos, desembolso a cuenta sueldo. [ingestion/meetings/2026-05-19-planning-refinement-perc.md](../ingestion/meetings/2026-05-19-planning-refinement-perc.md)
- 2026-05-20 — Refinement backlog PERC con Seba. Definiciones: estados del préstamo, CRUD de documentos, firma = 5 docs, TOTP gap identificado. [ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../ingestion/meetings/2026-05-20-refinement-backlog-perc.md)
- 2026-06-12 — Call con La Mantovana. Aclaró que los tags se prenden/apagan en Watson (no es desarrollo Quarks); Quarks solo maneja templates de crédito, no manipula info de usuario. [../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md)
- 2026-07-16 — Demo/UAT con cliente. Acotó el alcance (API, no el front); acordó que el front Angular sandbox se puede deployar en infra para usuarios de negocio de PERC, coordinando con Gonzalo (repo `credit web`, rama development). [../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md)
- 2026-07-20 — Daily PERC. Dio la explicación técnica de la re-arquitectura de lambdas: **no fue rechazo de PERC, sino que el CI tardaba ~45 min + costos disparados** (AWS serverless) al crecer la cantidad de lambdas. Marcos le pide tiempo para **revisar y destrabar el PR de cash out**. [../ingestion/meetings/2026-07-20-daily-perc.md](../ingestion/meetings/2026-07-20-daily-perc.md)
- 2026-07-20 — SYNC PERC (C12) con Seba + Fefe. Framing técnico del **MOCK/wrapper** para los datos AMFAYS faltantes; avaló arrancar el refactor de lambdas ya ("no depende de esos datos"); advirtió el **riesgo de front/drop-off** por el biométrico en el flujo. Recibe hoy el mapeo de datos de Seba. [../ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)

## Last touched
2026-07-20

