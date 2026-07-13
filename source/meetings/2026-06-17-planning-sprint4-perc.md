# Planning Sprint 4 — PERC (equipo interno Quarks) — Jun 17, 2026

**Fecha:** 2026-06-17
**Tipo:** Sprint Planning interno Quarks, posterior a la review con PERC del 17/6. Repaso historia por historia del sprint (desembolso, ciclo La Mantovana, conciliación, cancelaciones) + reparto de subtareas front/back.

**Participantes:**
- Olivier Luce — PM, Quarks ("Me")
- Juan Ignacio Moyano (Juaní) — Quarks
- Juampi (Juan Ignacio Moyano / Juampi Moyano) — front, Quarks
- Marcos — Quarks
- Nicolás Paez — Tech Lead, Quarks
- Giuliano — Quarks
- Israel — Quarks

> Transcripción generada por computadora (puede contener errores), ingresada vía `/ingest` el 2026-06-17. Conservada sin editar como audit anchor.

---

## Transcripción (verbatim)

[Transcripción "Planning - PERC" del 17/6/2026 según fue pegada en el comando /ingest. Tras ~15 min de charla informal (fútbol, una pava eléctrica 110V comprada en Amazon y el costo del transformador), el cuerpo de trabajo cubre, historia por historia:

**Desembolso (historia 65):** validar firma+TOTP, solicitud completa y fondos en cuenta recaudadora; lógica **FIFO**; si no hay fondos la solicitud queda PENDIENTE (no se rechaza) y se reintenta automáticamente cada 5 min (parametrizable por variable de entorno); si ingresan fondos antes de 24h corridas → desembolsa automático; a las 24h corridas sin fondos → se cancela; desembolso siempre a cuenta sueldo (no elige); trazabilidad/auditoría de cada intento (exitoso o pendiente); FIFO para procesar la cola. Nico pide vista en BO de **solicitudes pendientes de fondos** ordenadas por orden de llegada, con "expira en X tiempo" por solicitud (24h corridas, no hábiles).

**Generar archivo de novedades (66) y envío automático (67) e histórico (68):** solo cuotas del ciclo vigente de préstamos otorgados (excluye pendientes por firma/fondos); se reportan solo cuotas a descontar este mes, no el préstamo entero; corte default día 20, período 20→20, configurable (valor en base de datos controlado por BO, no env var según Nico); pueden coexistir reporte automático y manual y generar múltiples reportes (la fila es idéntica); el archivo lleva legajo + concepto + nombre + importe + período; legajo pendiente de que PERC lo disponibilice; envío automático por mail a Isis + Nico López, con auditoría (fecha/hora/destinatarios/archivo/resultado) y registro de fallo; el automático informa en BO si se generó pero no permite descargar el adjunto enviado (se descarga de nuevo). Discusión sobre filtrado del reporte: el **reporte va completo** (riesgo si se pasa un reporte parcial a La Mantovana como si fuera total); la **vista de histórico** sí debe filtrarse por usuario/mes/fecha + paginar. Nico marca que falta mapear servicios AWS adicionales (SES para mail, cron tipo EventBridge). Quedó pendiente preguntar a Seba si quieren regenerar reportes por rango de fechas (ej. del 21 al 30) para las que no entraron en el reporte anterior — Olivier teme que sea scope/feature regalado.

**Importar liquidaciones (69):** lo carga un admin (no API), el día de carga es indistinto; formato incorrecto → se rechaza el reporte entero, no actualiza nada; resumen con total/ok/error; el detalle de error es a nivel fila/registro, NO a nivel cuota (ni ida ni vuelta referencian número de cuota); campos exactos del archivo de vuelta los define Quarks y se los pasa a La Mantovana para configurar en Finegans.

**Aplicar pagos:** pago sin préstamo coincidente (legajo inexistente) → error, continúa; pago = cuota → se imputa a la **primera cuota no pagada** (Sistema Francés, todas iguales) y queda PAGADA con fecha de retención; pago < cuota → no queda pagada (estado de error, monto faltante marcado); caso de desvío no resuelto antes de la próxima cuota → resolución operativa, pendiente; todas las cuotas pagadas → préstamo PAGADO; préstamo ya PAGADO recibe nuevo dato → error "préstamo ya pagado", no modifica; descuento de más → error. **Nico objeta usar un único estado "pago con error" para tres casos distintos (sub-pago, sobre-pago, no-pago)** → se acuerda usar **tres estados distintos: pago parcial / pago con error / sobrepago** (nombres a afinar). Discusión de alerta por mail/WhatsApp en errores → deseable pero suma complejidad, se difiere.

**Carga manual de pago:** botón en detalle del préstamo / panel de diferencias; selecciona cliente + cuota, registra monto + fecha, crea una línea en los pagos; completar el faltante → cuota PAGADA; pago manual aún insuficiente → sigue parcial; "dar por pagada sin completar" → Olivier no está convencido, lo deja en suspenso para validar con Seba (Nico: el operador igual puede hacer cualquier cosa); auditoría quién/cuándo/cuánto; devolución sobre sobrepago → cuota PAGADA sin el excedente + auditoría. Juaní pregunta cómo se recibe la hora del pago del cliente → Olivier aclara que el cliente no paga, La Mantovana descuenta del haber (recibe neto en billetera Perk).

**Consultar liquidaciones importadas (71/72):** listado reciente→antiguo, detalle, filtro, paginación (simétrico al de exportaciones).

**Arrepentimiento (10 días corridos, sin costo):** botón en sección Préstamos; dentro del plazo → acepta; devuelve solo capital sin intereses/comisiones/penalidades; código de trámite; queda PENDIENTE y la cancelación la confirma el BO (manual) → préstamo ARREPENTIDO, cancela cuotas futuras, frena descuento por nómina; fuera de plazo → botón no disponible, se ofrece cancelación anticipada; **validación de fondos en el CVU** (sin fondos no puede arrepentirse, se le informa).

**Cancelación anticipada:** igual al arrepentimiento pero después de los 10 días; muestra monto total a pagar desglosado antes de confirmar; aplica costos de cancelación del producto. Nico/Juaní preguntan sobre la base del costo (3%): ¿sobre deuda restante o total?, ¿aplica gasto de otorgamiento? Está en el Excel pero con dudas no resueltas del PR.

**Tensión de scope — cancelaciones:** Olivier recuerda que el alcance original era que Quarks **registra** cancelaciones pero **no las efectúa** (flujo manual). El equipo razona que confirmar la cancelación desde BO requiere que La Mantovana **reporte el total descontado** para esa cancelación → eso abre un **circuito nuevo de cancelaciones** (extracción + envío + recepción/conciliación de un reporte de cancelación) que **nunca se conversó en el contrato**. Juaní plantea trazabilidad/evidencia (riesgo de que un BO marque "cancelado" sin que haya pasado) y la sensibilidad de los datos. Decisión: Olivier **quitó la validación de fondos de las historias de cancelación** para no abrir scope, lo lleva primero a Fefe/Juampi y después a PERC para definir el nivel de trazabilidad. Por ahora: solo se registra intención + BO marca como confirmada (cambio de estado), sin validación ni cancelación automática.

**Historia faltante (Olivier la debe crear):** cancelar la SOLICITUD antes del desembolso (cancelación manual dentro de la ventana de 24h, en vez de la cancelación automática) → desistimiento. Gestión BO de cancelaciones lista los 3 tipos: arrepentimiento, anticipada, desistimiento.

**Bloqueos / endpoints:** falta el **endpoint de consulta de fondos** de la cuenta recaudadora / CVU — no existe, Olivier ya se lo pidió a Seba esa mañana. Todos los endpoints de "fondos" faltan. Israel mandó el PR del entorno y tagueó a Jody/Gong; se espera respuesta. Reparto: back toma validación de fondos + endpoints; se piden subtareas prolijas front/back por la complejidad del sprint.]

---

*Audit anchor. No editar después de creado. La síntesis y el ruteo viven en `ingestion/meetings/2026-06-17-planning-sprint4-perc.md`.*
