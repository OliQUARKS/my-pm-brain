# Ingesta — Loginet, scoping interno Jony ↔ Juan Pablo (2026-05-27)

- **Fuente (verbatim):** [../../source/adhoc/2026-08-19-loginet-fuente-historica-completa.md](../../source/adhoc/2026-08-19-loginet-fuente-historica-completa.md) (sección "Pestaña 5 — Loginet - Transcripción", dentro del bundle histórico aportado el 2026-08-19).
- **Shape:** meeting — llamada 100% interna de Quarks (no es reunión con el cliente). Jony Ayerbe y Juan Pablo Norverto (CTO) discuten cómo escopear/cotizar el proyecto de Loginet antes de presentarle una propuesta al cliente.
- **Participantes:** Jony Ayerbe, Juan Pablo Norverto (ambos Quarks).
- **Nota de scope:** transcripción con lenguaje informal/coloquial extenso (preservado verbatim en `source/`). Esta síntesis extrae solo el contenido de negocio relevante — no reproduce el tono.

---

## 1. Diagnóstico técnico compartido antes de cotizar

**(observation)** Jony había hecho pruebas propias extrayendo datos de drafts de Bill of Lading (uno de "Japac", uno de Maersk) con un LLM/skill de PDF, con mejor resultado que el bot de Extract actual ("no hay un dato que no lo lea, que no lo entienda"). Esto valida que la extracción/normalización de declaraciones es técnicamente resoluble.

**(stakeholder-verbal, Juan Pablo Norverto, 2026-05-27)** Distinguió el diagnóstico: el problema no es necesariamente la extracción de Extract, sino la integración/carga posterior en Kai — "capaz lo que no funciona es la integración... extrae bien la información, y cuando manda la API nada."

## 2. Camino técnico propuesto — capa de ingesta propia

**(observation)** Jony propuso una arquitectura en capas: (1) capa de ingesta documental (monitorear inboxes o recibir uploads manuales al inicio — Juan Pablo Norverto recomienda arrancar con carga manual de archivos, no monitoreo automático de mail, para que el cliente valide que el sistema procesa bien y "se sienta en control" antes de sacarle el mail del medio); (2) normalización a un esquema único de datos; (3) aplicar reglas de negocio (ej. rangos de temperatura válidos por tipo de carga); (4) decisor de ruteo (API vs. RPA por naviera, mencionan N8N como orquestador); (5) carga a la naviera — vía API cuando la naviera la tiene (Maersk y "Japac"/Hapag mencionadas como candidatas), vía RPA/browser automation cuando no.

**(stakeholder-verbal, Juan Pablo Norverto, 2026-05-27)** Advirtió explícitamente contra el riesgo de sobre-prometer: *"no me puedo sacar de la cabeza que todos necesitan un backoffice propio"* — pero también cuestionó cuánto se estaría "reinventando la rueda" del rubro (TMS ya existentes) sin conocer a fondo el negocio.

## 3. Encuadre comercial y de pricing (decisión de enfoque, no de precio final)

**(stakeholder-verbal, Jony Ayerbe, 2026-05-27)** Encuadre de venta explícito: **no vender "te rehago todo el backoffice de cero"**, sino vender un equipo que ataque los incendios actuales por un tiempo determinado (mínimo 3 meses, potencialmente 4), ganando confianza operativa antes de proponer una transformación mayor. Cita textual: *"primero ganarse la confianza pagando los incendios... lo que construyamos, si está ideado para después hacer el backoffice propio, bienvenido sea."*

**(observation)** Cifras de referencia discutidas internamente (no comprometidas con el cliente): ~USD 5.000/mes, mínimo 3-4 meses, equipo de PM (part-time) + supervisor técnico + developer part-time. Se contrasta contra lo que el cliente paga hoy por Extract (~USD 200-500/mes) para anticipar la objeción de precio — el argumento de venta es que construir capacidad propia es más caro a la vista pero evita el riesgo de vendor lock-in y limitaciones del bot actual.

**(stakeholder-verbal, Juan Pablo Norverto, 2026-05-27)** Cuestionó la solidez de la estimación de tiempo: *"no puedo estimar algo viendo un documento así... hicimos un discovery hace un mes y medio y no sé qué pretenden que diga."* Quedó explícito que 3 meses es una **estimación**, no un compromiso firme, y que "atacar" los tres problemas no es lo mismo que "resolverlos" — riesgo de expectativas si el discurso comercial promete resolución total.

## 4. Priorización de navieras — MVP acotado

**(stakeholder-verbal, Jony Ayerbe, 2026-05-27)** Propuso arrancar con las 1-2 navieras de mayor volumen (Maersk y "Japac"/Hapag mencionadas, ambas con API) para resolver ~80% del problema de carga manual con alcance acotado, en vez de cubrir las ~10 navieras con las que trabaja Loginet desde el día uno.

## 5. Asignación de equipo interno (Quarks)

**(observation)** Se discutió quién lideraría la cuenta vs. el producto día a día — Jony y Juan Pablo (CTO) acordaron que deben "despegarse" del detalle operativo de las cuentas a medida que Quarks crece; nombraron a Danilo, Oli (Olivier), Lucía y Natalia como el pool disponible para llevar el día a día con los desarrolladores, con Jony/JP en rol de supervisión/relación de cuenta.

---

## Ruteo

- **No hay stakeholder de Loginet nuevo en esta llamada** — es 100% interna. No se actualizan `stakeholders/` de Loginet a partir de este archivo (sí se podría reflejar en las fichas internas de Quarks si el brain las trackeara, pero ese no es el foco de este repo).
- **Insight de proceso interno** (no de producto): esta llamada es un precedente directo del feedback de Jony del 2026-08-14 sobre `propuestador` (ver [`ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md`](./2026-08-14-sync-jony-preventa-feedback.md) § 1.3 y 1.4) — la tensión entre "vender confianza + atacar incendios" vs. "prometer una resolución completa" y la falta de base para estimados de tiempo ya aparecía acá, en mayo, antes de que se formalizara como cambio al skill en agosto. No se abre una nueva tensión en `strategy.md` por esto — ya está capturado y accionado en el feedback de agosto.
- **Sin decisión formal** — sigue siendo scoping interno previo a la propuesta de junio 2026 (ver [`source/adhoc/2026-06-loginet-propuesta-mvp-texto.md`](../../source/adhoc/2026-06-loginet-propuesta-mvp-texto.md), que sí refleja alcance de MVP, cronograma de 14 semanas y equipo, aunque todavía sin cerrar según la llamada del 2026-08-19).
