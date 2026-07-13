# Refinamiento PERC — Historias Mantovana (Seba × Olivier) — Jun 16, 2026

**Fecha:** 2026-06-16
**Duración:** ~1h
**Tipo:** Refinamiento de historias de usuario (ciclo La Mantovana + cancelaciones), revisión sobre las historias que Olivier ajustó tras el call del 12/6.

**Participantes:**
- Olivier Luce — PM, Quarks
- Sebastián Cárdenas — Product Owner, PERC

> Transcripción generada por computadora (puede contener errores), ingresada vía `/ingest` el 2026-06-16. Conservada sin editar como audit anchor.

---

## Transcripción (verbatim)

[Transcripción "Refinamiento - PERC - Transcripción" del 16/6/2026, 00:00:01 → 00:59:51, según fue pegada en el comando /ingest. Incluye, además de charla informal: revisión de la historia 1 (desembolso, definición pendiente FIFO vs "primer monto pagable con el disponible" → anotar las dos opciones como definición de negocio); historia 2 (novedades): regla de corte por ciclo — solo se reporta lo DESEMBOLSADO al momento del reporte, lo no desembolsado entra al ciclo siguiente, primera cuota al mes posterior; la generación de cuotas debe contemplarlo; dos ciclos (informe 20→20 y pago/4º día hábil), ambas fechas configurables; gráfico de Sebastián del happy path (pide → firma → chequea fondos → otorga/desembolsa → informa a Manto → pagos → reporte exportable 4º día); caso border préstamo del 19 en pendiente de desembolso; legajo: Quarks tiene que levantarlo, no hay opción de base de Manto (alternativa servicio externo que Fefe descartará); convivencia envío automático/manual → la Manto toma el más nuevo hasta el proceso de liquidación; historia 2-bis (envío automático + log/histórico de exportaciones + usuario que lo pidió); historia 4 (importar liquidaciones + resumen + detalle de errores, campos a definir en desarrollo); discusión sobre qué es "estado" del préstamo (cuántas cuotas pagadas del total) y necesidad de guardar deuda de capital por cuota para calcular pago anticipado (Seba sugiere desagregar variables del template, no solo número de cuota); historia 5 (aplicar pagos): emparejar por legajo; el número de cuota NO viene en el archivo de vuelta → el sistema asigna a la primera cuota no pagada (4+1); se elimina el escenario "cuota fuera de rango"; pago completo → PAGADA con fecha de retención; pago parcial → nuevo estado PAGO PARCIAL con monto faltante marcado, NO se da por pagada; caso desvío no resuelto antes de próxima cuota (la mal pagada figura como no pagada y se reintenta cobrar); discusión contable: el total prestado vs cobrado nunca cuadra con parciales — cómo liquida Manto vs mutual es problema a resolver con los devs/Fefe, fuera de scope Quarks; mutual es el proveedor del préstamo (no Perk presta); solución operativa = backoffice da por pagado manualmente, pone monto y fecha; "cuota ya pagada" → en realidad "préstamo ya pagado", registro no se modifica, devolución operativa; error de débito = error de importación (empleado sin préstamo vigente en concepto), estado anterior; historia 6 (consultar liquidaciones: listado reciente→antiguo, detalle con monto total y fecha de retención —no cuotas pagadas—, filtro por estado, paginación); conciliar lo importado: historia duplicada → eliminar; gestionar diferencias de conciliación desde panel BO (modal, listado de no reconciliadas por tipo: desvío de monto / faltante / sobrante) → la única acción capturada por ahora es la carga manual de pago; historia "cargar pago realizado manualmente": botón para cargar pago de cuota seleccionando cliente + cuota, registra quién/cuándo/cuánto, para parcial registra el monto faltante (ej. faltan 10), queda PAGO PARCIAL; sobrepago → unificar sobre y sub bajo un único estado PAGO CON ERROR, con devolución al cliente; feedback de Nico (dev) pendiente; comentario de proceso de Seba sobre el formato Gherkin "como quiero pararme" (le confunde) — Olivier explica el valor del contexto para el QA.]

---

*Audit anchor. No editar después de creado. La síntesis y el ruteo viven en `ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md`.*
