# Ingesta — Demo/UAT Préstamos con cliente PERC (2026-07-16, 16:00)

- **Fuente (transcript):** [../../source/meetings/2026-07-16-demo-uat-cliente-perc.md](../../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- **Shape:** meeting (demo happy-path con cliente + un requerimiento nuevo)
- **Participantes:** Marcos Perez (dev back Quarks, presenta), Olivier (PM Quarks), Jose Salgado ("Jo", dev/reviewer PERC — voz técnica dominante), Sebastian Cárdenas ("Seba", PO PERC), Gonzalo Kuhn ("Gonza", infra/DevOps PERC), Nicolás Paez ("Nico", TL Quarks), Ezequiel Manfredi (CTO PERC), Eugenio Valeiras (TL PERC).
- **Contexto:** es el call de las 16:00 que el dry-run interno de la mañana ([2026-07-16-uat-prestamos-lambdas-perc](2026-07-16-uat-prestamos-lambdas-perc.md)) venía a preparar. Se corrió **como demo en local, NO como UAT formal caso-por-caso** — tal cual la decisión operativa del dry-run. Olivier abrió reconociendo que dev no está listo (lambdas + PRs) y que al mediodía surgió el cambio de arquitectura de lambdas. **El plan explícito: el UAT fino punta-a-punta se hace después, con el entorno dev al 100%.**

---

## 1. Cómo salió la demo (Type A — routing)

- **(observation)** Recorrido happy-path mostrado end-to-end en local vía Insomnia + playground Angular: templates (alta/update-versionado/baja), solicitud → expiración por cron (1h sin firmar / 24h aprobada-sin-fondear), otorgamiento, cuotas del usuario, importación de descuentos Mantovana (pagada / parcial / sobrepago-con-devolución / ID inexistente / reaplicación), pago manual + "dar por pagado" + devolución, auditoría/logs con snapshots antes-después, histórico de exportaciones/envíos, config de cuenta (día de corte + mails). — [source](../../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- **(observation)** Reaparecen los **fallos de entorno** (502, "explotó la máquina", limpiar Docker) durante la demo — consistente con la causa-raíz infra/lambdas ya documentada. No son fallos de lógica. — Marcos.
- **(interpretation)** Recepción del cliente **buena y colaborativa**; el equipo PERC (Jose/Gonza) aporta soluciones, no fricción. El único entregable comprometido es la **API**; el front Angular es "sandbox para mostrar".

## 2. ⭐ NUEVO REQUERIMIENTO — threshold/tolerancia (delta) para evaluar pago de cuota

Es el resultado sustantivo del call.

- **(observation)** **Seba levanta el riesgo de decimales:** hoy la comparación monto-descontado vs. cuota es **igual = igual (exacta)**. Si un tercero (Finegans/Mantovana) sube el archivo **truncando** decimales en vez de redondear, **toda cuota cae a `pago parcial`/`pago con error`** → "se vuelve inviable"; obligaría a un operador a aprobar manualmente miles de préstamos. — Sebastian, [source](../../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- **(observation)** **Precisión de almacenamiento NO está en cuestión:** se guarda con precisión absoluta (Big.js / tipo decimal, no punto flotante). El problema es solo la **evaluación** del pago. — Marcos + Jose.
- **(decision, en principio — falta formalizar)** Agregar un **margen/threshold (delta)** en la evaluación de "cuota pagada": si la diferencia (de más o de menos) cae dentro del margen, la cuota se da por pagada. **Configurable por variable de entorno** (NO por el operador de BO, a diferencia del día de corte/mails), "por lo menos hasta que entendamos que está bien". Orden sugerido por Jose: **~centésimas, 3 lugares decimales, alrededor de 0,00X** (ej. tolerar ±15 centavos); valor por defecto que ponga Quarks, ajustable luego. — Jose + Marcos + Seba.
- **(observation → acción cross-team)** Jose lo marcó explícitamente como **"un pequeño ajuste de requerimiento que ambos lados tienen que acordar"**: Quarks lo implementa/mide, PERC define el "norte" (qué diferencia es aceptable = decisión de negocio). Olivier: "se extiende más allá del alcance… lo vemos aparte con Seba". — Jose + Olivier.

## 3. Conciliación financiera (Seba) — confirmada, no gap

- **(observation)** Seba pidió garantías de que "dar por pagado" y las devoluciones sean **auditables y conciliables contra la caja del banco**: quién lo hizo, la diferencia retenida, historial de transacciones. Marcos confirmó historial completo (refund/monto/usuario/fecha, snapshots antes-después) y que **el crédito solo se finaliza cuando TODAS las cuotas = pagadas y el balance iguala exactamente el total**. — Sebastian + Marcos.
- Conecta con el riesgo ya documentado de **cuadre contable préstamo-total vs. cobrado-con-parciales** (flujo-credito §Open questions, 2026-06-16): sigue siendo problema de cómo liquida La Mantovana contra la mutual, fuera de scope Quarks. El threshold (§2) es justamente lo que reduce el volumen de descuadres.

## 4. Infra / dependencias nuevas o reconfirmadas

- **(observation, NUEVO) SES en estado sandbox (política de seguridad PERC):** identities/destinations se agregan **a mano**, rate **1/segundo**, y **límite de 200/día** para broadcast masivo. **No bloqueante:** el reporte va a **1-2 casillas de la Mantovana, 1 mail por mes** — entra sin problema. — Gonzalo Kuhn.
- **(observation) Consolidación de lambdas — reconfirmada desde el lado PERC:** >60 lambdas → deploy de 45-60 min ("homicida") + costos/auditorías de Amazon por recurso + overhead del escalado horizontal. Gonza está haciendo **fixes manuales** (el `buildspec` supera el límite de caracteres en el CI/CD) y **migraciones manuales** para dejar el entorno al día mientras Quarks mergea y sigue testeando. Es refuerzo del riesgo ya documentado (dry-run §4), ahora con el racional directo de infra PERC. — Jose + Gonzalo.
- **(observation) Config en BD (no env var), reconfirmado:** día de corte (default **20**) + mails destino viven en la config de cuenta, editables. Los **tres crons** (envío + 2 de corte) ya están preparados; falta probarlos en **stage** post-deploy. Consistente con la corrección del 2026-06-17 (día de corte en BD). — Marcos.
- **(observation) Storage key en vez de URL:** para todos los documentos (incl. firma del usuario y el zip de hasta 25 reportes) se guarda la **storage key** y se resuelve contra el vault al momento — no la URL de descarga. Cambio avisado por Jo. — Marcos.

## 5. Definiciones resueltas / desbloqueos

- **(observation) Empleados PJ — parcialmente resuelto:** el endpoint de cuenta trae **`person_type` = `J` o `F`** al pedir la cuenta. Esto da a Quarks el flag para discriminar persona jurídica vs. física (open question abierta desde 2026-05-22/27). — Jose Salgado. *(Queda por confirmar si con esto alcanza para todo el impacto en documentos/BO.)*
- **(observation) Segunda cuenta para desembolso/cashout — recibida:** PERC la pasó por el canal (sin fondos; agregan fondos on-demand). Marcos implementa y testea el **cashout el 2026-07-17**. Destraba el TODO de cashout (hoy la lógica de fondeo corre pero no fondea). — Jose + Marcos.

## 6. Acción nueva — deploy del front Angular (sandbox) en infra

- **(observation/idea)** Jose pidió **levantar el front Angular sandbox en la infra** para que gente de negocio de PERC (Seba) pueda probar sin pelear con Insomnia. Está **fuera del alcance contractual** (el scope es la API), pero **no hay objeción** en deployarlo: es un **repo separado** (`credit web`), ya en rama `development`; Ezequiel confirmó accesos. **Nico Paez coordina con Gonzalo** el pipe/config web. No implica desarrollo nuevo. — Jose + Nico Paez + Ezequiel + Olivier.

## 7. Acciones

- **Marcos** → (1) implementar y testear **cashout** con la 2ª cuenta (**2026-07-17**); (2) mergear los updates que Gonza deja manualmente y seguir testeando en general (habrá retesting completo post-lambdas); (3) mandar más PRs (mandó 2, Jo revisa).
- **Olivier + Seba** → reunión aparte para **acordar el threshold/delta** (valor + que sea decisión de negocio PERC). Fuera del alcance nominal — tratar como ajuste de requerimiento cross-team.
- **Olivier + Nico Ortiz** → reunión de **documentos/firma el 2026-07-17 a las 15:00** (ya agendada).
- **Nico Paez + Gonzalo** → evaluar deploy del front Angular sandbox en infra (repo `credit web`, rama development).
- **Gonzalo** → fixes manuales del buildspec + migraciones para dejar dev al día.
- **Meta declarada (Olivier):** una vez el entorno dev al 100% y sin más cambios, correr el **UAT formal punta-a-punta, escenario por escenario** (reunión larga).

## 8. Ruteo — destinos durables (PROPUESTOS, requieren OK del PM)

- **`decisions/` NUEVA (pending):** `2026-07-16-threshold-tolerancia-pago-cuota.md` — margen/delta configurable por env var para evaluar cuota pagada; default de Quarks, valor de negocio a definir por PERC; ambos lados acuerdan. Refina los estados de cuota (relaja "igual = igual").
- **`knowledge/product/features/flujo-credito.md`:**
  - Timeline: entrada 2026-07-16 (demo happy-path con cliente; buena recepción; UAT formal diferido a dev-100%).
  - §Estados a nivel cuota: nota de que "Pagada = igual exacto" **se relajará con el threshold** (ver decisión nueva).
  - §Dependencias: agregar **SES sandbox** (rate 1/s, 200/día, identities manuales; no bloqueante para 1 mail/mes); nota de segunda cuenta de desembolso **recibida**.
  - §Open questions: **PJ → `person_type` J/F** (marcar parcialmente resuelto); cashout en implementación (test 17/7).
- **`stakeholders/` — NUEVO:** `gonzalo-kuhn.md` — Infra/DevOps PERC. Disparó/justificó la consolidación de lambdas; impone la restricción SES sandbox; hace fixes/migraciones manuales. (Ya venía como candidato desde el dry-run.)
- **`stakeholders/` touchpoints 2026-07-16:** jose-salgado (voz técnica dominante — decimales/threshold, person_type, 2ª cuenta), sebastian (levanta decimales + conciliación), marcos-perez (presenta), nicolas (Paez — coordina front), ezequiel-manfredi, eugenio-valeiras.
- **INDEX:** decisions/INDEX (nueva pending), stakeholders/INDEX (Gonzalo + last-touched de los presentes).

## 9. Contradicciones / tensiones con evidencia previa

- **Relación con la decisión de comparación exacta (2026-06-16/17):** el threshold **no contradice** sino que **refina** la regla "el descuento iguala el monto de la cuota" (flujo-credito §Estados a nivel cuota). Es un ablande deliberado para viabilidad operativa, no un cambio de criterio contable (la precisión de almacenamiento se mantiene absoluta). Preservado como refinamiento, no como conflicto.
- **Scope creep menor:** deploy del front Angular + el threshold son ambos "fuera del alcance" reconocidos en el call. Ninguno escala a tensión estratégica por sí solo (bajo esfuerzo, sin objeción del cliente), pero **suman** al patrón ya tensionado de "trabajo extra no contratado que aparece tarde" (ver strategy §Tensions y dry-run §4/§6). No creo una tensión nueva; lo dejo anotado como watch.
