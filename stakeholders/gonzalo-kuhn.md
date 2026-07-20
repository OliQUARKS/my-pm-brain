# Gonzalo Kuhn — Infra / DevOps, PERC
<!-- También: Gonza, Gon -->

## Snapshot
- Role: Infra / DevOps, PERC
- Reports to / works with: equipo técnico PERC (Eugenio Valeiras, Jose Salgado); coordina con Quarks (Marcos, Nico Paez)
- Influence on my work: high <!-- controla infra, CI/CD, entorno dev/stage y las políticas de AWS que condicionan el deploy -->
- Friction level: low <!-- colaborativo; aporta soluciones y hace fixes manuales para destrabar -->

## What they care about
- Costos y seguridad de la infra AWS: cada recurso (lambda) dispara auditorías de Amazon → sobrecarga y costo para la compañía. (observation, [../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md))
- Que la arquitectura sea optimizable y el CI/CD no se vuelva "homicida" (deploy de 45–60 min con >60 lambdas). (observation, ídem)

## Concerns / watch-outs
- Disparó/justificó la **consolidación de lambdas** (agrupar por recurso) por costos + auditorías AWS + overhead del escalado horizontal.
- Impone la restricción **SES en estado sandbox**: identities/destinos manuales, rate 1/s, límite 200/día broadcast.
- TODO: confirmar estilo y canal preferido en próximo touchpoint.

## Communication style
TODO: confirmar. En el call: técnico, directo, propositivo ("pienso en voz alta").

## Open asks
- **Gonzalo → Quarks:** mergear los updates que él deja manualmente (fixes de buildspec + migraciones) para no repetir trabajo.
- **Quarks → Gonzalo (Nico Paez):** coordinar el deploy del front Angular sandbox (repo `credit web`, rama development) — qué necesita para web / pipe directo.

## Touchpoint log
- 2026-07-16 — Demo/UAT con cliente PERC. Justificó la consolidación de lambdas; expuso la restricción SES sandbox; está haciendo fixes manuales (buildspec supera el límite de caracteres) y migraciones manuales para dejar dev al día. [../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md)

## Last touched
2026-07-16
