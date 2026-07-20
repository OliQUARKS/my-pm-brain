# Decisions Index

> Append-only log. Filename: `YYYY-MM-DD-<slug>.md`. Schema in [_SCHEMA.md](./_SCHEMA.md).

## Pending
<!-- Decisions opened but not yet resolved. Auto-maintained from files with status: pending. Decision debt — older than 14 days, high blocker impact, or approaching deadline → surface in maintenance. -->
- 2026-07-16 — [Evaluar el pago de una cuota con un margen/threshold (delta) configurable, no por igualdad exacta](./2026-07-16-threshold-tolerancia-pago-cuota.md) — owner Olivier; a acordar con PERC (valor de negocio). Blocker: conciliación operativa post-launch.

## Recently decided
<!-- Last 30 days. Each links to the file. -->
- 2026-07-20 — [El documento del préstamo se firma y persiste como UN solo documento (supersede sábana + 5 docs)](./2026-07-20-documento-unico-firma.md)
- 2026-07-20 — [Entrega PERC = +1 sprint sobre las 12 semanas; refactor de lambdas antes del UAT formal](./2026-07-20-entrega-perc-mas-un-sprint.md)
- 2026-07-20 — [Datos del documento AMFAYS por origen: existentes vía accounts/Sherlock; faltantes mockeados/cableados con proveeduría real diferida (PERC)](./2026-07-20-captura-datos-amfays.md)
- 2026-04-20 — [Tech stack: Lambda (backend) + Angular (frontend)](./2026-04-20-tech-stack.md)
- 2026-05-18 — [IDs de BD usan LUID (no integers secuenciales ni UUID v4)](./2026-05-18-luid-ids.md)
- 2026-05-19 — [Solicitud persiste en BD solo post firma+TOTP](./2026-05-19-solicitud-post-firma-totp.md)
- 2026-05-19 — [Desembolso siempre a cuenta sueldo](./2026-05-19-desembolso-cuenta-sueldo.md)
- 2026-05-19 — [Solicitudes en curso expiran a 1h vía EventBridge Scheduler](./2026-05-19-expiracion-solicitud-1h.md)
- 2026-05-20 — [CRUD documentos: versionado con activación explícita, sin edición de versiones publicadas](./2026-05-20-crud-docs-versionado.md)
- 2026-06-01 — [Documentos del flujo de firma: dinámicos y en formato HTML](./2026-06-01-documentos-dinamicos-html.md)
- 2026-06-02 — [Plazo de desembolso = 24 horas](./2026-06-02-plazo-desembolso-24h.md)
- 2026-06-02 — [Precancelación anticipada cobra penalidad sobre intereses futuros](./2026-06-02-penalidad-intereses-futuros.md)
- 2026-06-12 — [Reporte de novedades a La Mantovana = solo la cuota del mes, no el total](./2026-06-12-reporte-novedades-cuota-mensual.md)
- 2026-06-12 — [Arrepentimiento (10 días) solo se ejecuta si el cliente tiene los fondos](./2026-06-12-arrepentimiento-requiere-fondos.md)
- 2026-06-16 — [Solo se reportan préstamos desembolsados; primera cuota al ciclo siguiente si el desembolso es post-corte](./2026-06-16-corte-solo-desembolsados.md)
- 2026-06-17 — [Desembolso procesa la cola en FIFO; retry cada 5 min; cancela a las 24h corridas](./2026-06-17-desembolso-fifo.md)

## Superseded
<!-- Decisions reversed by a later decision. Both stay in the log. -->
- 2026-05-20 — [Sábana es render-only; se persisten 5 documentos por separado](./2026-05-20-sabana-no-persiste.md) → superseded 2026-07-20 por [documento-unico-firma](./2026-07-20-documento-unico-firma.md) (T&C 5→1: es un solo documento).

## TODO
PM-fillable section is per-decision (filled in each `YYYY-MM-DD-<slug>.md` file), not here.
