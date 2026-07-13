# Síntesis — Planning Sprint 4 PERC (equipo interno Quarks)
**Fecha:** 2026-06-17
**Source:** [source/meetings/2026-06-17-planning-sprint4-perc.md](../../source/meetings/2026-06-17-planning-sprint4-perc.md)
**Tipo:** Sprint Planning interno, posterior a la review con PERC. Cierra implementación del sprint más complejo: desembolso + ciclo La Mantovana + conciliación + cancelaciones.

Continúa y aterriza a tickets lo refinado el 16/6 ([ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](2026-06-16-refinamiento-historias-mantovana-perc.md)). Trae 3 cambios de peso: FIFO confirmado para desembolso, **tres** estados de error de pago (no dos), y una **tensión de scope nueva** en cancelaciones.

---

## Definiciones cerradas / refinadas

1. **Desembolso = FIFO.** (decision) Validar firma+TOTP + solicitud completa + fondos en recaudadora. Sin fondos → solicitud PENDIENTE (no se rechaza), **retry automático cada 5 min** (parametrizable por variable de entorno). Si ingresan fondos antes de **24h corridas** → desembolsa automático; a las 24h corridas sin fondos → se cancela. Desembolso **siempre a cuenta sueldo**. Cola procesada FIFO. (stakeholder-verbal, Olivier + equipo, 2026-06-17) — **resuelve la open question FIFO-vs-pagable del 16/6 hacia FIFO** (ver contradicción abajo).

2. **Vista BO de solicitudes pendientes de fondos.** (decision) Ordenadas por orden de llegada, con "expira en X tiempo" por solicitud. Pedido de Nico, no estaba capturado. (stakeholder-verbal, Nico Paez, 2026-06-17)

3. **Tres estados de error de pago, no dos.** (decision) Nico objetó usar un único `PAGO CON ERROR` para sub-pago, sobre-pago y no-pago. Se acuerdan **tres estados distintos: `PAGO PARCIAL` / `PAGO CON ERROR` / `SOBREPAGO`** (nombres a afinar; Olivier edita las historias). **Esto revisa la definición del 16/6** que unificaba sub+sobre bajo `PAGO CON ERROR`. (stakeholder-verbal, Nico + Olivier, 2026-06-17)

4. **El detalle de error de importación es a nivel fila/registro, NO a nivel cuota.** (observation) Ni la ida ni la vuelta referencian número de cuota; refuerza la imputación a la primera cuota no pagada (Sistema Francés, todas las cuotas iguales). (observation, Olivier, 2026-06-17)

5. **El reporte de novedades va completo; el filtrado vive en la vista de histórico.** (decision) El archivo exportado lleva la data completa (riesgo: un reporte parcial confundido con total ante La Mantovana). La **vista de histórico de exportaciones** sí se filtra por usuario / mes / fecha + paginación. (stakeholder-verbal, Nico + Olivier, 2026-06-17)

6. **Coexisten reporte automático y manual; se pueden generar múltiples.** (observation) Mismo préstamo aparece con fila idéntica en distintos reportes; La Mantovana toma el más nuevo hasta su proceso de liquidación. El día de corte es **valor en base de datos controlado por BO**, no variable de ambiente (corrección de Nico al 16/6). (observation, Nico, 2026-06-17)

7. **El archivo de liquidaciones lo carga un admin (no API); el día de carga es indistinto.** (observation) Formato incorrecto → rechazo íntegro. (observation, Olivier, 2026-06-17)

8. **Cancelaciones: Quarks registra intención + BO confirma (cambio de estado); NO efectúa la cancelación ni valida fondos.** (decision) Se quitó la validación de fondos de las historias de cancelación para no abrir scope. La cancelación real es flujo manual; el BO marca "cancelado" cuando ya se gestionó. (stakeholder-verbal, Olivier, 2026-06-17)

---

## Tensión de scope — cancelaciones (NUEVA, alta relevancia, no resolver acá)

Confirmar una cancelación desde el BO **bien hecha** requeriría que La Mantovana **reporte el total efectivamente descontado** para esa cancelación → eso abre un **circuito de cancelaciones completo** (extracción + envío + recepción + conciliación de un reporte de cancelación) que **nunca se conversó en el contrato**. (interpretation, equipo, 2026-06-17)

- El alcance original (decisión de scope): Quarks **registra** cancelaciones, **no las efectúa** — flujo manual. (ver [flujo-credito.md](../../knowledge/product/features/flujo-credito.md) §Risks, scope 2026-05-20).
- Riesgos planteados por Juaní: un BO podría marcar "cancelado" sin evidencia de que ocurrió; los datos del reporte (quién pidió, cuánto, qué cuota) son **sensibles**.
- Camino acordado: llevarlo **primero a Fefe/Juampi**, luego a PERC, para definir el nivel de trazabilidad deseado y si se vende como step 2 / oportunidad. (stakeholder-verbal, Olivier + equipo, 2026-06-17)
- **No se resuelve en esta ingesta.** Es un fork de scope/negocio que escala a Fefe.

---

## Bloqueos / dependencias

- **Endpoint de consulta de fondos (cuenta recaudadora / CVU) — NO existe.** (observation) Es el habilitador central del sprint (validación de fondos para desembolso, arrepentimiento, cancelación anticipada). Olivier ya se lo pidió a Seba la mañana del 17/6. Todos los endpoints de "fondos" faltan del lado PERC. (stakeholder-verbal, Olivier, 2026-06-17)
- **Servicios AWS adicionales a mapear:** SES (envío de mail) + cron tipo EventBridge (envío automático). Nico lo mapea en la historia. (observation, Nico, 2026-06-17)
- **Entorno:** Israel mandó el PR del entorno y tagueó a Jody/Gong; a la espera. (observation, Israel, 2026-06-17)

---

## Open questions que quedan (need PM/Seba/Fefe judgment)

1. **Circuito de cancelaciones: ¿se construye (scope extra) o se mantiene registro-only?** Escala a Fefe → PERC. (ver tensión arriba)
2. **Base del costo de cancelación (3%):** ¿sobre deuda restante o total? ¿aplica gasto de otorgamiento? El Excel lo tiene pero con dudas no resueltas del PR. A validar con Seba/Fefe. (stakeholder-verbal, Nico, 2026-06-17)
3. **¿La Mantovana puede regenerar reportes por rango de fechas** (ej. 21→30) para las cuotas que no entraron en el reporte anterior? Olivier lo lleva a Seba; teme feature regalado. (observation, Nico + Olivier, 2026-06-17)
4. **Nombres definitivos de los 3 estados de error** (`PAGO PARCIAL` / `PAGO CON ERROR` / `SOBREPAGO`).
5. **"Dar por pagada sin completar el monto":** Olivier no está convencido, en suspenso hasta validar con Seba.
6. **Historia faltante a crear:** cancelar la SOLICITUD antes del desembolso (cancelación manual en la ventana de 24h = desistimiento).

---

## Contradicciones con evidencia previa (preservadas, no resueltas)

1. **Estados de error: 2 → 3.** El 16/6 se definió `PAGO PARCIAL` + `PAGO CON ERROR` (este último unificando sub y sobre-pago). El 17/6 Nico lo separó en **tres** (`PAGO PARCIAL` / `PAGO CON ERROR` / `SOBREPAGO`). La versión del 17/6 es la vigente; el feature file debe actualizarse.
2. **FIFO vs "primer monto pagable".** El 16/6 quedó como **open question de negocio** (decisión de PERC). El 17/6 Olivier lo afirma como **FIFO** para la implementación del sprint. Es una **decisión de PM/equipo en planning**, no una confirmación explícita de Seba sobre el fork de negocio — conviene cerrar formalmente con Seba que FIFO estricto es lo querido (vs. saltar al siguiente pagable cuando el primero no entra). Coherente además con el FIFO ya mencionado el 9/6.
3. **Día de corte: ¿variable de ambiente o valor en BD?** El 16/6 / decisión lo trataba como parámetro de ambiente; Nico corrige que debe ser **valor en base de datos** controlado por el BO. Menor, pero a reflejar.

---

## Ruteo propuesto (durable — requiere OK del PM, propose-and-wait)

- **`flujo-credito.md` §Estados a nivel cuota:** pasar de 2 a **3** estados (`PAGO PARCIAL` / `PAGO CON ERROR` / `SOBREPAGO`), con nota de que los nombres y el mapeo exacto los afina Olivier + Seba.
- **`flujo-credito.md` §Open questions:** cerrar FIFO (working decision), corregir corte = valor en BD, sumar base del costo de cancelación, regeneración por rango de fechas, historia de desistimiento pre-desembolso.
- **`flujo-credito.md` §Risks + §Dependencies:** agregar el **circuito de cancelaciones** como riesgo de scope creep; agregar **endpoint de consulta de fondos** como dependencia bloqueante (PERC, pedido a Seba 17/6).
- **Decisión nueva candidata:** `2026-06-17-desembolso-fifo.md` (FIFO + retry 5min + cancela 24h corridas + cuenta sueldo). Confirmar con el PM si va como `decided` o `pending` (residual de confirmación de negocio con Seba).
- **Tensión de estrategia candidata:** "Circuito de cancelaciones = posible scope creep vs. contrato registro-only." Recurrente (toca la decisión de scope del 20/5), decision-relevant y escala a Fefe → cumple el umbral. **Requiere OK del PM para tocar `strategy.md`.**
- **Stakeholders:** last-touched de Nico, Marcos, Israel, Giuliano, Juampi/Juaní → 2026-06-17 (participaron).
- **NO promover** nada a knowledge de usuarios/mercado — es definición de producto/proceso.
