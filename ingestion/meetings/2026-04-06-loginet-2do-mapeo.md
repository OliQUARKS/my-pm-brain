# Ingesta — Loginet 2do mapeo (2026-04-06)

- **Fuente (verbatim):** [../../source/adhoc/2026-08-19-loginet-fuente-historica-completa.md](../../source/adhoc/2026-08-19-loginet-fuente-historica-completa.md) (secciones "Pestaña 4" y "Pestaña 8" — notas de Gemini duplicadas de la misma reunión, dentro del bundle histórico aportado el 2026-08-19).
- **Shape:** meeting — segunda sesión de mapeo/discovery con el cliente.
- **Participantes:** Vanina Focaraccio, Manuel Vasquez, Anahí Cappi (Loginet); Jony Ayerbe, Juan Pablo Norverto, Danilo Luce (Quarks).
- **Contexto:** continuación directa de [2026-02-24-loginet-briefing-quarks.md](./2026-02-24-loginet-briefing-quarks.md) — profundiza el mapeo comercial/operativo/administrativo con foco fuerte en el proceso de facturación de compra (conciliación de facturas de navieras) y el rol de Extract/Kai.

---

## 1. Cuello de botella crítico — cotización no cargada

**(observation)** Se identificó un problema recurrente: el embarque sale y se completa, pero la cotización no está cargada en Kai, lo que impide facturar. La responsabilidad de cargar el número de cotización en el "file" operativo es del área comercial. La demora suele deberse a que el margen/"on top" que se cobrará al cliente final todavía no está definido (más común al inicio de temporada).

**(stakeholder-verbal, Jony Ayerbe, 2026-04-06)** Propuso, ante la imposibilidad de forzar la carga de la cotización, disparar un recordatorio automático al iniciar la operación en Excel si la cotización sigue faltando en Kai.

## 2. El proceso de "Rock" en detalle (demo de Manuel Vasquez)

**(observation)** Manuel Vasquez demostró el proceso real: selecciona los ítems de costo del archivo de operación que coinciden con el total facturado por la naviera, genera un **"Rock"** (prefactura/precarga sin número ni fecha de factura), lo sube al sistema, y envía el PDF de la factura a Extract. Extract lee el PDF, pasa la info a Kai, y Kai concilia automáticamente si el número de contenedor y el importe coinciden con el Rock.

**(stakeholder-verbal, Anahí Cappi, 2026-04-06)** Resaltó el volumen que justifica automatizar esto: **~500-600 facturas de líneas marítimas por mes en temporada alta.** El control manual de generación de Rocks es rápido (50 Rocks en 20 minutos), pero el cuello de botella es el volumen total, no la velocidad unitaria.

**(stakeholder-verbal, Juan Pablo Norverto, 2026-04-06)** Propuso que Extract pudiera validar la factura contra un archivo de datos (CSV/XLS) de Kai *antes* de generar el Rock, para automatizar el control humano actual.

**(observation)** Limitación confirmada de Kai: no permite descargar reportes que separen costos por proveedor dentro de una misma operación — complica cualquier automatización de validación externa. El equipo acordó evitar pedir nueva funcionalidad a Kai y trabajar con lo que ya es descargable o lo que Extract puede procesar.

## 3. Manejo de errores de facturación (dos tipos distintos)

**(observation)** Tipo 1 — factura de la naviera mal facturada: administración compara contra el contrato comercial; si la naviera facturó de más o de menos, se contacta directamente para pedir nota de crédito o corrección.
**(observation)** Tipo 2 — la factura de la naviera coincide con el contrato, pero el monto cargado en la cotización (COTI) en Kai está mal: se devuelve a comercial para corregir manualmente, y luego vuelve a administración para el pago.

**(observation)** Los contratos (por temporada o por período) se almacenan en una **planilla maestra de operaciones**, en una pestaña de "contratos" — es la referencia que usa administración para validar facturación. Esto es consistente con lo visto en el diagrama de flujo (nota "los contratos están en una solapa del excel master").

## 4. Otro punto crítico — conceptos no cargados en la cotización

**(observation)** Cuando un concepto de servicio (ej. custodia, ingreso a puerto) no se carga en la cotización, el cliente no es facturado por ese costo — a veces no se descubre hasta que llega la factura del proveedor correspondiente. Es una variante adicional de error, distinta a los errores de monto.

## 5. Carghost / actualización de fechas de arribo

**(observation)** Confirmado: la actualización automática de fechas de arribo desde Carghost a Kai no se puede automatizar hoy por discrepancia de nomenclatura de puertos (siglas vs. nombres completos) — requiere una tabla de conversión.

## 6. Postura del cliente sobre reemplazar Kai

**(stakeholder-verbal, Anahí Cappi, 2026-04-06)** Mencionó haber trabajado con otros sistemas que considera más amigables que Kai (cambios más rápidos), pero **por el momento no es una opción considerar un cambio de sistema**, especialmente arrancando la temporada — el objetivo es optimizar el sistema actual con herramientas externas (Extract, Cargoes) en vez de un reemplazo estructural.

**(interpretación)** Esto ya en abril mostraba tensión con lo que luego se refleja en la llamada interna del 27/5 y en la llamada de hoy (19/8): Anahí personalmente favorece reemplazar Kai (viene de una empresa que construyó su propio sistema en 6 años), pero el mensaje oficial del cliente en esta reunión es "no tocar Kai todavía". Ver [2026-05-27-loginet-scoping-interno-jony-jp.md](./2026-05-27-loginet-scoping-interno-jony-jp.md) § dinámica de venta. (chat, no artefacto, 2026-08-19)

## 7. Próximos pasos acordados en la reunión

- [Grupo] Implementar recordatorio de cotizaciones faltantes al iniciar operación en Excel.
- [Juan Pablo Norverto] Evaluar patrón de datos de Carghost + tabla de conversión de siglas de puertos para Kai.
- [Anahí Cappi] Coordinar reunión con el proveedor de Kai para discutir compatibilidad/automatización/nomenclaturas.
- [Anahí Cappi] Preguntar a Extract qué necesita para automatizar la validación de facturas.
- [Anahí Cappi] Pedir a Kai un reporte más detallado de costos pendientes.
- [Jony Ayerbe, Juan Pablo Norverto] Digerir la información, volver con preguntas, avanzar hacia sugerencia/análisis/propuesta.
- [Manuel Vasquez] Coordinar reunión adicional sobre el circuito administrativo si hace falta.

---

## Ruteo

- **Stakeholders actualizados:** [`stakeholders/vanina-focaraccio.md`](../../stakeholders/vanina-focaraccio.md), [`stakeholders/manuel-vasquez.md`](../../stakeholders/manuel-vasquez.md) (touchpoint agregado) — **creado:** [`stakeholders/anahi-cappi.md`](../../stakeholders/anahi-cappi.md) (nueva en esta reunión, no había aparecido el 24/2).
- **Feature/proceso:** no existe todavía un `knowledge/product/features/<slug>.md` para Loginet en este repo (es un prospect, no hay proyecto activo todavía) — no corresponde crear uno hasta que haya un build-context/propuesta cerrada.
- **Sin decisión formal** — siguen siendo pasos de discovery, no compromisos de alcance/costo/tiempo.
