# Síntesis — Refinamiento PERC, Historias Mantovana (Seba × Olivier)
**Fecha:** 2026-06-16
**Source:** [source/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../../source/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md)
**Tipo:** refinamiento de historias del ciclo La Mantovana + cancelaciones, sobre el draft que Olivier ajustó tras el call del 12/6 ([ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](2026-06-12-proceso-prestamos-mantovana.md)).

Esta reunión aterriza las historias a nivel de criterios de aceptación y cierra varias casuísticas que el call del 12/6 dejó abiertas. Es el sprint "más complejo de todos" según Olivier.

---

## Definiciones cerradas / refinadas

1. **Regla de corte = se reporta SOLO lo DESEMBOLSADO al momento del reporte.** (decision) No basta con "otorgado" ni "pedido": lo que no esté desembolsado a la hora del reporte (automático o manual) entra al ciclo siguiente. Resuelve el caso border del préstamo pedido el 19 que queda en pendiente de desembolso: si no se desembolsó, no se reporta. (stakeholder-verbal, Seba + Olivier, 2026-06-16)

2. **La generación de cuotas debe contemplar el corte.** (decision) Si el desembolso es posterior al envío/exportación del archivo, la primera cuota cae en el mes posterior (~33 días). No se cobra una primera cuota en el 4º día hábil inmediato. (stakeholder-verbal, Olivier + Seba, 2026-06-16)

3. **Dos ciclos distintos, ambos con fecha configurable.** (observation) Ciclo de informe (≈ día 20 → día 20) y ciclo de pago (4º día hábil). "Pensarlo por ciclo, no por mes." El descalce de ~4 días entre informe y pago no es significativo (ya lo habían dicho los chicos de La Mantovana). (stakeholder-verbal, Seba, 2026-06-16)

4. **El número de cuota NO viene en el archivo de vuelta de Finegans.** (observation) Por lo tanto el sistema NO puede recibir "cuota 15 de 12" → **se elimina el escenario "número de cuota fuera de rango".** La lógica de aplicación es: **el pago se imputa a la primera cuota NO pagada** (regla 4+1 / "la primera no paga que aparezca"). (stakeholder-verbal, Seba + Olivier, 2026-06-16)

5. **Pago parcial = nuevo estado `PAGO PARCIAL`.** (decision) Si el monto descontado es menor a la cuota, la cuota NO queda pagada, se genera error con descripción del desvío y se marca el **monto faltante**. No se imputa como pagada. (stakeholder-verbal, Olivier + Seba, 2026-06-16)

6. **Sobre-descuento y sub-descuento se unifican en un único estado `PAGO CON ERROR`.** (decision) Seba: "no haría un caso para sobre y otro para sub; lo llamaría pago con error" (nombre del estado a confirmar). Si se descontó de más → se puede registrar una **devolución al cliente**. (stakeholder-verbal, Seba, 2026-06-16)

7. **Carga manual de pago (historia nueva consolidada).** (decision) Botón en BO para cargar el pago de una cuota seleccionando **cliente + cuota**; registra **quién cargó, cuándo, cuánto**. Para parcial se registra el **monto faltante** (ej. vinieron 90 de 100 → se registra que faltan 10, no 100). Es la única acción operativa capturada por ahora para resolver diferencias de conciliación. (stakeholder-verbal, Olivier + Seba, 2026-06-16)

8. **"Cuota ya pagada" → en rigor "préstamo ya pagado".** (observation) Como no hay cuotas individualmente identificadas, el caso real es: llega un nuevo descuento sobre un préstamo ya PAGADO → el registro no se modifica, se arroja error, y la devolución se gestiona operativamente. (stakeholder-verbal, Seba + Olivier, 2026-06-16)

9. **Legajo: Quarks lo levanta. No hay opción de leerlo contra la base de La Mantovana.** (observation) La alternativa (consumirlo de un servicio externo) "Fefe la va a descartar". Esto **inclina** la open question del 12/6 hacia: Quarks guarda el legajo en el usuario. Falta confirmación formal de Fefe, pero Seba y Olivier coinciden. (stakeholder-verbal, Seba + Olivier, 2026-06-16)

10. **Convivencia envío automático vs manual.** (observation) Si conviven, La Mantovana toma el **más nuevo** hasta el proceso de liquidación (4º día). Si se manda después de la liquidación, se mete manual ("me meto el Excel por donde ya sabés"). El log de exportaciones debe registrar **cada vez que se crea el archivo + el usuario que lo pidió** y ser consultable. (stakeholder-verbal, Seba + Olivier, 2026-06-16)

---

## Fuera del scope de Quarks (reafirmado)

- **Cuadre contable préstamo total vs. cobrado.** (interpretation) Con pagos parciales, lo prestado nunca cuadra con lo cobrado (prestó 100, cobró 90, debe remesar 100 a la mutual con 90). Seba: "es un problema a resolver con los chicos... la solución va a estar en cómo liquida Manto contra mutual. No creo que sea nada de lo que ustedes hacen." **La mutual es el proveedor del préstamo, no Perk.** (stakeholder-verbal, Seba, 2026-06-16)
- **Deuda de capital por cuota:** Seba quiere poder consultar cuánto capital se adeuda hasta cada cuota (lo necesita para el pago anticipado). Sugiere **desagregar y guardar las variables del template** en vez de solo el número de cuota. Olivier lo lleva a los devs (Nico). No es un cierre, es un input técnico para el sprint. (stakeholder-verbal, Seba, 2026-06-16)

---

## Cambios a las historias (acción de Olivier)

- **Historia "conciliar lo importado contra lo enviado" estaba duplicada → eliminar.**
- **Eliminar** el escenario "número de cuota fuera de rango" de la historia de aplicación de pagos (def. #4).
- **Agregar estado `PAGO PARCIAL`** (def. #5) y **`PAGO CON ERROR`** (def. #6) al modelo de estados.
- **Consolidar la historia de carga manual de pago** (def. #7) con su contracara de devolución por sobrepago.
- **Reescribir** la historia de aplicación de pagos para que impute a la primera cuota no pagada (no por número de cuota).
- Falta sumar feedback de **Nico (dev)** — no estuvo en la reunión.

---

## Open questions que quedan (need PM/Seba/dev judgment)

1. **FIFO vs "primer monto pagable con el disponible" (historia 1, desembolso).** Definición de **negocio**, no técnica. Documentar AMBAS opciones en la historia. Seba no la tiene ahora. (stakeholder-verbal, Seba, 2026-06-16)
2. **¿Se guarda la deuda de capital desagregada en el template?** Input de Seba, a validar con Nico/devs. Define cómo se calcula el pago anticipado.
3. **¿Cómo se salda contablemente el parcial Manto↔mutual?** Fuera de scope Quarks, a resolver Seba con los devs/Fefe.
4. **Nombre definitivo del estado `PAGO CON ERROR`.** A confirmar.
5. **Convivencia automático/manual:** ¿cuánto espera el sistema antes de procesar el primero? Atado al proceso de liquidación de La Mantovana, no controlado por Quarks.
6. **Confirmación formal de Fefe** sobre que el legajo lo levanta Quarks (no servicio externo).

---

## Nota de proceso

Seba comentó que el formato "Como quiero pararme / dado-cuando-entonces" (Gherkin) le confunde más de lo que le ayuda. Olivier defendió el valor del contexto para el QA. Es comentario, no pedido de cambio de formato. (stakeholder-verbal, Seba, 2026-06-16)

---

## Ruteo propuesto (durable — requiere OK del PM, propose-and-wait)

- **`knowledge/product/features/flujo-credito.md`:**
  - Loan states: agregar `PAGO PARCIAL` y `PAGO CON ERROR` (nivel cuota) al modelo.
  - Open questions: cerrar/actualizar la regla de corte (solo desembolsado), inclinar la del legajo hacia "Quarks lo levanta", agregar FIFO vs pagable, deuda de capital desagregada, cuadre Manto↔mutual.
  - Dependencies: matizar "fuente del legajo" → Quarks lo levanta (pendiente OK Fefe).
- **Decisión candidata:** "Corte = solo préstamos desembolsados se reportan; primera cuota al ciclo siguiente si el desembolso es post-corte." (multilateral, confirmado en esta reunión).
- **Stakeholder:** actualizar last-touched de [Sebastián](../../stakeholders/sebastian.md).
- **NO promover** a knowledge ningún ítem nuevo de usuario/mercado — esto es definición de producto, su home es el feature file.
