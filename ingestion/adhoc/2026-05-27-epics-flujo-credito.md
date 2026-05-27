# Ingestion: Épicas Flujo Crédito (2026-05-27)

## Execution

- **Skill:** `/epics flujo-credito` (no flags)
- **Date:** 2026-05-27
- **Feature:** Flujo Crédito / Préstamos
- **Output:** 5 épicas con slicing MVS/Midgame/Endgame

## Épicas generadas

| # | Título | Slice | Tamaño est. | Bloqueantes | KPIs |
|---|---|---|---|---|---|
| 1 | *Solicitud de préstamo — MVS* | MVS | L | Tech stack validado; Watson API integrada | Tasa de adopción; % errores en solicitud |
| 2 | *Firma digital + TOTP — MVS* | MVS | M | Estructura de documentos confirmada | % completación del TOTP |
| 3 | *Desembolso a cuenta sueldo — MVS* | MVS | M | Integración Watson validada; cuenta sueldo identificable | % desembolsos exitosos; plazo desembolso |
| 4 | *Cancelación manual (email) — MVS* | MVS | S | Estados del préstamo definidos | % cancelaciones procesadas |
| 5 | *Backoffice: BO avanzado — Midgame* | Midgame | XL | MVS completado; Watson refinado | Eficiencia BO (reducción carga manual) |

## Open questions affecting épicas

- Postgres DB structure validation — pending PERC (Juampi Norverto)
- Documentos dinámicos vs. estáticos — Seba responds ~2026-05-27
- Plazo máximo desembolso (24h vs. 48h) — pending Marcos
- Empleados PJ — tratamiento idéntico a PF o hay diferencias?

## Notes

- Épicas 1–4 son MVS. Épica 5 es Midgame y requiere MVS completado.
- Historias por épica se generarán con `/stories <épica-nombre>` tras validación de OQs.
- No pushed a Linear aún — validar OQs y refinar con equipo antes de `--push`.

## Routing

- No promotion a `knowledge/` o `hypotheses/` en esta ronda — épicas son working log.
- Pending: `/stories` descomposición y Linear project creation con `--push`.
