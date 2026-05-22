# Ingestion: Excel CALCULO DE PRESTAMOS PERC — 2026-05-22

- Source: [source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md)
- Recibido: 2026-05-22 15:44 (WhatsApp, Sebastián Cárdenas)
- Feature: flujo-credito

---

## Observations

1. **(decision) Sistema Francés — fórmula de cuota confirmada.** Cuota total = Interés bruto + IVA s/interés (21%) + Amortización capital + Seguro de vida + Gasto adm. mensual. La cuota pura (sin gasto adm.) es el PMT calculado con la TEM con IVA embebida, garantizando cuotas verdaderamente fijas. Cierra la open question del PRD sobre metodología de cuotas. (observation, [source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))

2. **(observation) TEM con IVA embebida en el PMT.** TEM = (TNA/12) × (1 + 0.21). En cada cuota: Interés bruto = Saldo × TNA/12; IVA = Interés bruto × 21%; Amortización = Cuota pura − Interés bruto − IVA. La igualdad mensual viene de usar TEM_conIVA en el PMT. (observation, [source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))

3. **(observation) Monto prestado ≠ capital solicitado: ambos son INPUTs separados.** Capital solicitado (lo que recibe el cliente) = 1,000,000; Monto prestado (base de la tabla) = 1,075,000. No hay fórmula que derive uno del otro automáticamente. Sellos y gastos de otorgamiento se calculan sobre el monto prestado. Open question: ¿cómo se determina el monto prestado a partir del capital solicitado en la implementación? (observation, [source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))

4. **(observation) Seguro de vida: parámetro existe (3%) pero = 0 en el ejemplo.** Premisas B14 = 0.03. Columna G de la tabla con fórmula `Saldo × Seguro%` presente en la estructura, pero TOTALES G = 0 — no hay valores calculados en las 24 cuotas. Pendiente con Seba: ¿el seguro de vida aplica en el MVP? ¿A qué tasa definitiva? (observation, [source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))

5. **(decision) IVA sobre penalidades de cancelación: sí aplica.** Excel flag B8 = 1 (Sí). Fórmula: IVA = (Penalidad intereses futuros + Comisión sobre capital restante) × 21%. Consistente con la asunción del PM. (observation, [source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md) + assumption, Olivier, 2026-05-22)

6. **(assumption) Todos los valores configurables en el Excel son ilustrativos, no finales.** TNA 89%, sellos 1.2%, mora 3%, gasto adm $500, otorgamiento $3,000, penalidades 5%/3% — ejemplos coloreados en amarillo. Los parámetros reales del MVP se configurarán por template/tipo de préstamo. (assumption, Olivier, 2026-05-22 — confirmado por PM en sesión)

7. **(observation) Penalidad de cancelación anticipada — fórmula completa.** Total = Capital restante + (Int. futuros × % penalidad) + (Capital restante × % comisión) + IVA s/(penalidad + comisión). Todos los % son configurables por tipo de préstamo. (observation, [source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))

---

## Routing

- `knowledge/product/features/flujo-credito.md` — cerrada open question "Metodología de cuotas"; agregada §Cuota methodology; nuevas OQ: seguro de vida + monto prestado vs capital solicitado
- `stakeholders/sebastian.md` — touchpoint adicional Excel 15:44 + open ask de cuotas cerrado
