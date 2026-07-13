# Decision: El archivo de novedades reporta solo préstamos DESEMBOLSADOS; si el desembolso es post-corte, la primera cuota cae al ciclo siguiente

## Status
decided

## Date
2026-06-16

## Context
El ciclo mensual con La Mantovana tiene dos fechas: el corte/envío del archivo de novedades (≈ día 20, configurable) y el pago de haberes / archivo de liquidaciones (4º día hábil). Había que definir qué préstamos entran en el archivo de cada ciclo y cuándo cae la primera cuota, especialmente para los casos border alrededor del corte (préstamo pedido/firmado pero aún no desembolsado, o desembolsado después del 20).

## Options considered
1. Reportar todo préstamo **pedido/otorgado** antes del corte (independiente del desembolso).
2. Reportar **solo lo desembolsado** al momento del reporte; lo no desembolsado entra al ciclo siguiente.
3. Reportar lo pedido y dar de baja después lo que no se desembolsó.

## Decision
Opción 2. El archivo de novedades incluye **únicamente préstamos efectivamente desembolsados** al momento del reporte (automático o manual). Lo que no esté desembolsado entra al ciclo siguiente. Si el desembolso es posterior al envío/exportación del archivo, la **primera cuota cae en el mes posterior** (~33 días) y la generación de cuotas debe contemplarlo. Se razona **por ciclo, no por mes**: ciclo de informe (≈ día 20 → día 20) y ciclo de pago (4º día hábil), ambas fechas configurables.

## Why
Reportar solo lo desembolsado evita cobrar una cuota de un préstamo que nunca se erogó (caso del pedido el 19 que queda en pendiente de desembolso) y simplifica la conciliación. El descalce de ~4 días entre informe y pago no es significativo y ya había sido aceptado por La Mantovana. Imputar la primera cuota al mes posterior cuando el desembolso es post-corte mantiene la coherencia entre lo informado y lo cobrado.

## Evidence
- Seba y Olivier acordaron reportar solo lo desembolsado y mandar lo no desembolsado al ciclo siguiente; resuelve el border del préstamo del 19 en pendiente de desembolso  [../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md)
- La generación de cuotas debe contemplar que un desembolso post-corte tiene su primera cuota al mes posterior  `(stakeholder-verbal, Olivier + Seba, 2026-06-16)`
- "Pensarlo por ciclo, no por mes"; el ciclo de informe va del 20 al 20, distinto del ciclo de pago (4º día hábil)  `(stakeholder-verbal, Seba, 2026-06-16)`
- El descalce de ~4 días entre informe y pago no es significativo y ya lo habían aceptado los referentes de La Mantovana  [../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md)

## Explicitly NOT doing
- No reportar préstamos pedidos/otorgados pero no desembolsados al momento del reporte  `(stakeholder-verbal, Seba + Olivier, 2026-06-16)`

## What would reverse this
La Mantovana exige conocer préstamos comprometidos antes del desembolso, o el negocio decide cobrar la primera cuota en el mismo ciclo del desembolso (lo que obligaría a reportar pre-desembolso).

## Remaining ambiguities
- Fechas de corte y de pago son configurables; valores por defecto (día 20 / 4º día hábil) son operativos, no fijados en contrato.
- Casuística border de cancelación entre el día 20 y el pago de haberes sigue abierta (refinamiento interno de Perk) — ver [2026-06-12-reporte-novedades-cuota-mensual.md](2026-06-12-reporte-novedades-cuota-mensual.md).

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md`
- Decisión relacionada: `2026-06-12-reporte-novedades-cuota-mensual.md`
- Stakeholders informed: `../stakeholders/sebastian.md`
