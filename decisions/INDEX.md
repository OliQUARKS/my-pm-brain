# Decisions Index

> Append-only log. Filename: `YYYY-MM-DD-<slug>.md`. Schema in [_SCHEMA.md](./_SCHEMA.md).

## Pending
<!-- Decisions opened but not yet resolved. Auto-maintained from files with status: pending. Decision debt — older than 14 days, high blocker impact, or approaching deadline → surface in maintenance. -->

## Recently decided
<!-- Last 30 days. Each links to the file. -->
- 2026-04-20 — [Tech stack: Lambda (backend) + Angular (frontend)](./2026-04-20-tech-stack.md)
- 2026-05-18 — [IDs de BD usan LUID (no integers secuenciales ni UUID v4)](./2026-05-18-luid-ids.md)
- 2026-05-19 — [Solicitud persiste en BD solo post firma+TOTP](./2026-05-19-solicitud-post-firma-totp.md)
- 2026-05-19 — [Desembolso siempre a cuenta sueldo](./2026-05-19-desembolso-cuenta-sueldo.md)
- 2026-05-19 — [Solicitudes en curso expiran a 1h vía EventBridge Scheduler](./2026-05-19-expiracion-solicitud-1h.md)
- 2026-05-20 — [Sábana es render-only; se persisten 5 documentos por separado](./2026-05-20-sabana-no-persiste.md)
- 2026-05-20 — [CRUD documentos: versionado con activación explícita, sin edición de versiones publicadas](./2026-05-20-crud-docs-versionado.md)
- 2026-06-01 — [Documentos del flujo de firma: dinámicos y en formato HTML](./2026-06-01-documentos-dinamicos-html.md)
- 2026-06-02 — [Plazo de desembolso = 24 horas](./2026-06-02-plazo-desembolso-24h.md)
- 2026-06-02 — [Precancelación anticipada cobra penalidad sobre intereses futuros](./2026-06-02-penalidad-intereses-futuros.md)

## Superseded
<!-- Decisions reversed by a later decision. Both stay in the log. -->

## TODO
PM-fillable section is per-decision (filled in each `YYYY-MM-DD-<slug>.md` file), not here.
