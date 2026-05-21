# Data rules

> Source-of-truth per metric, naming conventions, what counts as evidence.

## Source of truth per metric
<!-- Pre-producción. Sin métricas activas. Definir al momento del lanzamiento. -->
| Métrica | Source of truth | Estado |
|---|---|---|
| Tasa de adopción (préstamos aceptados / empleados habilitados) | Sistema de préstamos PERC | Pre-producción |
| Cuotas recuperadas / cuotas esperadas | Mantovana (conciliación) | Pre-producción |
| Tiempo medio de solicitud a desembolso | Logs del sistema | Pre-producción |
| Carga del Backoffice (casos manuales) | Watson BO | Pre-producción |
<!-- From interview Batch D Q1 -->

## Naming conventions
TODO: definir con el equipo técnico (Nicolás + Quarks) una vez que el stack esté definido. Tech stack aún pendiente (Lambda / Java / TypeScript). (source/adhoc/2026-05-21-prd-flujo-credito.md §5)

## Evidence quality

What counts as evidence, by tier:

1. **Direct customer evidence** — quotes, interviews, support tickets, recorded behavior.
2. **Product analytics** — instrumented events, cohort behavior, funnel metrics.
3. **Stakeholder opinions** — internal but informed.
4. **Market / competitor signals** — directional, not definitive.
5. **Internal speculation** — lowest weight. Label as assumption.

