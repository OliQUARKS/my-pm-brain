# Ingestion — Email: Definiciones Pendientes Flujo Crédito

- **Fecha:** 2026-05-13
- **Shape:** adhoc (email saliente)
- **De:** Olivier Luce (PM, Quarks)
- **Para:** Marcos Copello (CEO, PERC), Sebastián Cárdenas (PO, PERC), Federico Fernandez (COO, Quarks)
- **Source:** [../../source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md](../../source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md)
- **Feature:** [flujo-credito](../../knowledge/product/features/flujo-credito.md)

---

## Observaciones

### Sistema de cuotas — parcialmente resuelto

- **Sistema francés confirmado** — mención explícita en el email. (observation, source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md)
- **Pendiente técnico:** IVA variable sobre intereses (puede generar diferencias entre cuotas), inclusión del seguro de vida en el cálculo, criterio para igualdad de cuotas mensuales, ítems incluidos vs. excluidos del modelo. (observation, source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md)
- **Bloqueante:** sin el Excel con la fórmula definitiva, el equipo no puede implementar la lógica de cálculo.

### Desembolso — no resuelto en refinements posteriores

- **Plazo 24-48h mencionado como acuerdo verbal**, sin confirmación escrita. (observation, source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md)
- **Abierto:** si aplica igual en fines de semana y feriados, o si hay excepciones operativas.

### Cancelación anticipada y moras — resuelto en refinement 2026-05-20

- Cancelación anticipada: saldo total disponible, sin congelación, no hay documento legal → PDF dummy/placeholder. ✅
- Moras: 100% manual, sin flujo digital. ✅
- Ver: [ingestion/meetings/2026-05-20-refinement-backlog-perc.md](../meetings/2026-05-20-refinement-backlog-perc.md)

## Routing

- → [knowledge/product/features/flujo-credito.md](../../knowledge/product/features/flujo-credito.md) — agregar detalle metodología cuotas (sistema francés, IVA variable, seguro de vida) y plazo desembolso 24-48h verbal
