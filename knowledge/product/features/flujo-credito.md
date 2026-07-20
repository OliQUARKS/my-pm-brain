# flujo-credito — Flujo Crédito / Préstamos

## Meta
- Owner: Olivier Luce (PM, Quarks Alchemist)
- Status: building
- Priority: 1 (único feature activo en scope del contrato)
- Last updated: 2026-07-20

## Problem
Los empleados del Grupo PERC no tienen forma de autogestionar solicitudes de préstamos. El proceso actual es manual, con carga alta en el Backoffice y sin trazabilidad ni documentación auditable. (source/adhoc/2026-05-21-prd-flujo-credito.md §1)

## Target users
- **Empleados del Grupo PERC** — 8,000 usuarios habilitados en el MVP. Acceden por app. Segmentados (las 3 opciones de crédito se basan en su segmento, no en scoring individualizado).
- **Operadores de Backoffice (PERC)** — gestionan casos especiales, configuran préstamos, habilitan/deshabilitan usuarios, generan archivos de novedades para La Mantovana.

## Success metrics
| Métrica | Definición | Fuente | Estado |
|---|---|---|---|
| Tasa de adopción | Préstamos aceptados / empleados habilitados | Sistema de préstamos | Pre-producción |
| Eficiencia del BO | Reducción de casos manuales | Watson BO | Pre-producción |
| Compliance | 100% de solicitudes con firma unificada + documentos auditables | Sistema de préstamos | Pre-producción |
(source/adhoc/2026-05-21-prd-flujo-credito.md §2)

## Risks
- **Cancelaciones son manuales (scope decision 2026-05-20):** todos los flujos de cancelación (arrepentimiento, cancelación anticipada, precancelación) resuelven vía mail pre-completado — sin firma digital. Operativamente engorroso para el cliente pero fuera de scope digital. (observation, [ingestion/meetings/2026-05-20-diseno-flujo-credito.md](../../../ingestion/meetings/2026-05-20-diseno-flujo-credito.md))
- **Definiciones técnicas bloqueantes:** tech stack pendiente (Lambda / Java / TypeScript); integración con Watson sin validar. Sin esto no hay estimaciones firmes. (source/adhoc/2026-05-21-prd-flujo-credito.md §5)
- **Fricción con el cliente (PERC):** Sebastián Cárdenas tarda en dar definiciones. Bloquea el refinement del equipo. (stakeholder-verbal, Olivier, 2026-05-21)
- **Dependencia de La Mantovana:** el ciclo de cobro depende de un sistema externo de nómina. Coordinación mensual (~día 20) con riesgo de delay.
- **Circuito de cancelaciones = posible scope creep (2026-06-17):** confirmar bien una cancelación desde el BO obligaría a construir un **circuito de reporte de cancelaciones** (extracción + envío a La Mantovana + recepción + conciliación del total descontado) que **no estaba en el contrato** — el alcance original era "Quarks registra cancelaciones, no las efectúa". Por ahora se quitó la validación de fondos de las historias de cancelación; el BO solo marca el cambio de estado. Olivier lo escala primero a Fefe/Juampi, luego a PERC, para definir el nivel de trazabilidad. Ver tensión en [strategy.md](../../strategy.md). (interpretation, equipo Quarks, [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../../../ingestion/meetings/2026-06-17-planning-sprint4-perc.md))
- **Conciliación manual + corrección inmediata por error de débito (2026-06-12):** los errores de descuento caen a un panel manual en Watson. Casos generales (descuento parcial, ausencia) se ajustan el mes siguiente con un concepto "ajuste de préstamo" aparte; pero si se le **debitó a quien no correspondía**, la corrección debe ser **inmediata** del lado de Perk (rollback/TED) — no diferible. (observation, Nico Ortiz, [ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../../../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md))
- **Fondeo insuficiente:** si la cuenta recaudadora de PERc no tiene fondos suficientes, la transacción queda en pendiente — no rechaza silenciosamente. (source/adhoc/2026-05-21-prd-flujo-credito.md §5)
- **TOTP security gap (identificado 2026-05-20):** el TOTP actual solo bloquea la UI — un actor con token de usuario válido puede llamar el endpoint de transferencia directamente sin pasar por TOTP. Pendiente de revisión con Joy (TL del equipo de integración). (ingestion/meetings/2026-05-20-refinement-backlog-perc.md)
- **Documentos dinámicos vs. estáticos (definición pendiente):** No está resuelto si los documentos HTML serán dinámicos (con variables del usuario) o estáticos. Si dinámicos, se necesita un parser + mapeo de variables. Seba da respuesta en ~1 semana. (ingestion/meetings/2026-05-20-refinement-backlog-perc.md)
- **Sprint 3 bloqueado multifrente (Daily 2026-06-03) — parcialmente destrabado al 2026-06-08:** la infra tiene camino acordado (Sandbox Amazon), el formato de documentos se resolvió (HTML→PDF) y PER-42 se desbloqueó (cálculos mergeados). **Siguen bloqueantes:** plantillas finales (Giuliano las pasó a compliance, esperando resolución), firma (Seba sin responder), y la validación de la estructura de cuotas por Nico. Riesgo nuevo: posible scope extra si Quarks debe configurar los entornos. (observation, [ingestion/meetings/2026-06-08-daily-perc.md](../../../ingestion/meetings/2026-06-08-daily-perc.md))
- **Entorno/infra bloqueante — se materializa (2026-07-16):** ~65 lambdas no corren de forma estable en local (Mac M1 Pro 16 GB, Docker+SAM → timeouts / 500 aleatorios; la lambda no llega a levantar antes del timeout de ~30 s). El dev env de PERC **nunca desplegó la versión actual** (último deploy real fue con ~20 lambdas; faltan variables de entorno + PRs sin aprobar). **Casi todos los fallos del UAT son de ambiente, no de código.** Es la confirmación del riesgo de scope-de-entorno abierto desde el Daily 2026-06-08. (observation, [ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../../../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md))
- **Consolidación de lambdas pedida tarde por PERC (2026-07-16):** Gonza (infra PERC) pide mergear get/post/put/delete por recurso (~65 → ~20 lambdas), motivado por explosión del CI/CD + auditorías de Amazon (costos). Es cambio de implementación, no de lógica, pero **mueve código en todo el proyecto + reescribe todos los paths de front e Insomnia → obliga a rehacer el UAT completo = +1 sprint**. Hunde la deadline del martes 2026-07-21. (observation/interpretation, equipo Quarks, [ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../../../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)) — **Matiz 2026-07-20 (Norverto):** re-atribuye la consolidación a la **arquitectura de PERC** (lambda-por-operación) advertida por Nico antes de arrancar; la enmarca como "iteración normal, no un problema". Cifra de origen difiere (50 vs 65) — a cerrar en la review técnica con Nico/Marcos. (stakeholder-verbal, Juan Pablo Norverto, [ingestion/meetings/2026-07-20-sync-producto.md](../../../ingestion/meetings/2026-07-20-sync-producto.md)) — **Confirmación técnica 2026-07-20 (Nico, daily):** la causa concreta fue que **muchas lambdas → el CI tardaba ~45 min + los costos se disparaban** (AWS serverless); "fue evolucionando" hasta volverse inviable. Cifra actual ~60 lambdas. Cierra buena parte del matiz de causación. (observation, Nico Paez, [ingestion/meetings/2026-07-20-daily-perc.md](../../../ingestion/meetings/2026-07-20-daily-perc.md))
- **KYC/biométrico dentro del flujo de préstamo (riesgo de scope + UX, 2026-07-20 C12):** AMFAYS pide KYC/biométrico/prueba de vida/ID facial como parte de la firma electrónica. Ya se captura en el onboarding, pero el "caso de máxima" (lectura conservadora de Seba/Nico) es **re-pedirlo durante la solicitud del préstamo, documentarlo y bajarlo al PDF** → **modifica el front sí o sí** + validación UI/backend + **sube el drop-off** en un flujo que debería ser simple. **Contradice** la lectura optimista de Marcos en el daily ("con TOTP ya es válido"). Sigue como **duda a evacuar con AMFAYS**. Motivado por el modelo de AMFAYS (cartera asegurable/securitizable — ver [org/amfays.md](../../org/amfays.md)). (observation/interpretation, [ingestion/meetings/2026-07-20-sync-perc-c12.md](../../../ingestion/meetings/2026-07-20-sync-perc-c12.md))
- **Gap de velocidad del front + management gap (2026-07-20):** el frontend (Moyanito) no siguió el ritmo del back durante PERC (seniority + stack no manejado); derivaba tareas de front a Marcos. Quarks reconoce falta de acompañamiento (no le pusieron a Nico encima). Mitigado: Olivier prototipó el BO a mitad de proyecto; Moyanito sale del front y pasa a DAEA. Riesgo residual = capacidad/seguimiento del front para cerrar los pendientes. (interpretation, Olivier + Norverto + Fefe, [ingestion/meetings/2026-07-20-sync-producto.md](../../../ingestion/meetings/2026-07-20-sync-producto.md))

## Dependencies
| Dependencia | Tipo | Estado |
|---|---|---|
| Watson (Backoffice) | Plataforma del cliente | Definición de integración pendiente |
| La Mantovana (Finegans) | Sistema externo de nómina | **Definido 2026-06-12 (call):** ida = Excel por mail ~día 20 (solo cuota del mes, por legajo); vuelta = liquidaciones el 4º día hábil; conciliación manual. Modelo del importador recibido. **Refinado 2026-06-16:** solo se reportan desembolsados; el archivo de vuelta NO trae nº de cuota (se imputa a la primera no pagada); el **legajo lo levanta Quarks** (pendiente OK Fefe). Pendiente: campos del reporte de vuelta. |
| Envío de mails (AWS SES, PERC) | Infraestructura del cliente | **Restricción 2026-07-16 (Gonzalo/infra PERC):** SES en estado **sandbox** — identities/destinos se agregan a mano, rate **1/s**, límite **200/día** para broadcast. **No bloqueante:** el reporte va a 1–2 casillas de La Mantovana, 1 mail/mes. (observation, [ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../../../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md)) |
| Segunda cuenta para desembolso/cashout (PERC) | Cuenta de prueba | **Recibida 2026-07-16** (por el canal; sin fondos, se agregan on-demand). Destraba el test del cashout — Marcos implementa y prueba el 2026-07-17. (observation, [ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../../../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md)) |
| Sueldo / antigüedad / presentismo por empleado (PERC) | Dato de elegibilidad | **Necesario (2026-06-12):** el sueldo habilita el cálculo del tope 30%. La selección de elegibles (antigüedad+presentismo, matriz de riesgo manual) y el on/off de tags en Watson quedan **fuera del scope de Quarks**. |
| Cuenta recaudadora PERc | Fuente de fondos | Validación de saldo activa |
| Endpoint de consulta de fondos (recaudadora / CVU) | API de PERC | ✅ **Resuelto 2026-07-20 (Olivier):** la consulta de saldo de la recaudadora/CVU quedó cubierta del lado PERC. Habilita la validación de fondos para desembolso/arrepentimiento/cancelación anticipada. |
| Tech stack: Lambda + Angular | Decisión técnica | ✅ Decidido 2026-04-20 — [decisions/2026-04-20-tech-stack.md](../../../decisions/2026-04-20-tech-stack.md) |
| Pipeline CI/CD | Infraestructura | Pendiente — mes de discovery |
| Sherlock (servicio PERC) | Asociación documentos firmados a cuenta via S3 presigned URL | Disponible — nuevo en sprint 2026-04-20. (stakeholder-verbal, José Salgado, 2026-04-20) |
| Entorno dev/stage + S3 (PERC) | Infraestructura | **Camino acordado (Daily 2026-06-08):** PERC DevOps da cuenta Sandbox de Amazon; Quarks crea bucket y testea; luego PERC monta dev env con CI/CD. Pendiente: Quarks pasa el punteo de servicios Amazon. ⚠️ A clarificar con Israel: ¿quién configura los entornos? (posible scope extra). |
| Arquitectura de datos interna (Quarks) | Definición técnica | **En progreso (Daily 2026-06-08):** PER-42 desbloqueada — dev armando estructura cuotas-vs-payments, cálculos mergeados; PR a Nico para validar. |

## Timeline
- **Nov 2025:** Creación del documento (PRD v1.0)
- **Dic 2025 – Ene 2026:** Iteraciones de scope y definiciones
- **Feb – Abr 2026:** Ajustes de alcance y armado final del PRD (v2.0)
- **May 2026:** Setup del PM Brain. **Kickoff oficial Quarks–PERC: 2026-05-20.** (discovery técnico en curso)
- **27 Apr – 5 May 2026:** Setup de repos (monorepo structure confirmado). Backlog + Excalidraw flow compartido con equipo el 2026-05-06. [source/meetings/2026-05-06-repo-setup-backlog-share.md](../../../source/meetings/2026-05-06-repo-setup-backlog-share.md)
- **2026-06-02:** Sprint 2 Review (demo) + Planning Interna Sprint 3. Plazo de desembolso confirmado en 24h (Marcos). 4 escenarios de cancelación y TOTP obligatorio definidos.
- **2026-06-03:** PR del Sprint 2 aprobado por PERC (pasó los 4 reviewers automáticos) → **Sprint 2 cerrado al 100%**. Daily: Sprint 3 bloqueado multifrente (ver Risks). Próxima review cliente: martes 2026-06-17 (movida desde el 15/6, feriado).
- **2026-06-08:** Daily — infra destrabada (camino Sandbox de Amazon), formato de documentos resuelto (HTML→PDF), PER-42/cuotas desbloqueada (cálculos mergeados). Pendientes top: plantillas finales (en compliance) + firma + validación estructura cuotas.
- **2026-06-09:** Sprint 4 refinement interno (Seba + Eze). Desembolso con/sin fondos (FIFO-by-payable, polling 5 min, timeout 24h), file delivery (mail MVP), batch partial-failure. [ingestion/meetings/2026-06-09-sprint4-refinement-perc.md](../../../ingestion/meetings/2026-06-09-sprint4-refinement-perc.md)
- **2026-06-12:** Call con La Mantovana (Isis + Nico López). Cerrado el ida y vuelta: reporte = solo cuota del mes, día 20 / 4º día hábil, por legajo, tope 30%, arrepentimiento requiere fondos, ajustes mes siguiente con 2 conceptos (error de débito = corrección inmediata). Elegibilidad/tags fuera de scope Quarks. ⚠️ T&C podrían pasar de 5 docs a 1 (legales) — ver tensión en strategy. [ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../../../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md)
- **2026-06-16:** Refinamiento de historias del ciclo La Mantovana (Seba × Olivier). Corte = solo desembolsados; pago a primera cuota no pagada; estados de error de cuota; legajo lo levanta Quarks. [ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../../../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md)
- **2026-06-17:** Review con PERC (muy buena recepción) + Planning Sprint 4 interno. Desembolso = FIFO; tres estados de error de pago (parcial/error/sobrepago); reporte completo + histórico filtrable; tensión de scope en cancelaciones (escala a Fefe); endpoint de consulta de fondos bloqueante. [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../../../ingestion/meetings/2026-06-17-planning-sprint4-perc.md)
- **2026-07-16:** Demo happy-path con el cliente PERC (corrida en local, NO el UAT formal — dev no está listo por lambdas + PRs). Buena recepción colaborativa. Nuevo requerimiento: **threshold/delta configurable** para evaluar pago de cuota (ver decisión pendiente). Reconfirmado: consolidación de lambdas (racional de infra PERC), SES sandbox, config de corte/mails en BD, storage-key en vez de URL. Desbloqueos: 2ª cuenta de cashout recibida (test 17/7), `person_type` J/F. UAT formal punta-a-punta diferido a dev-100%. [ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../../../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md) (dry-run interno de preparación: [ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../../../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md))
- **2026-07-17:** Call Amfays <> PERc — **relevamiento campo-por-campo del documento** de la ayuda económica con la mutual AMFAYS (proveedor del instrumento). Se definió obligatoriedad de campos, cambio de formato (checkboxes→texto), firma electrónica y unificación multi-formulario→1 archivo. **Destraba parcialmente** el "documento AMFAYS" (bloqueante desde 2026-07-08): quedan definiciones de compliance de AMFAYS para el **lunes 2026-07-20**. Ver §Documento / campos AMFAYS. [ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../../../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md)
- **2026-07-20:** SYNC Producto interno (Quarks). **Fefe avala +1 sprint** ("1–2 semanas sobre 12 = ~10%, pasar como está"); la decisión formal la toma **Seba** en la C12 del 20/7. **Moyanito (front) sale de PERC → DAEA** por gap de velocidad; Fefe pide review técnica Nico/Marcos. Debate abierto: **dónde se cargan los ~20 campos AMFAYS** (hoy solo ~5 disponibles, sin front de carga) — onboarding vs. taggeo en BO (postura Norverto) vs. placeholders diferidos (Fefe: taggeo "es un caos"). Olivier: los pendientes son mayormente **bugs**, no features nuevas. [ingestion/meetings/2026-07-20-sync-producto.md](../../../ingestion/meetings/2026-07-20-sync-producto.md)
- **2026-07-20 (daily interno):** Secuencia de trabajo definida: **cash out** (en curso, +4 lambdas → ~64) → **threshold** → **refactor de lambdas** (no entra hasta pasar el PR de cash out). Entorno dev al **estado ~demo** tras la subida de Gonza; próximo paso = deploy del front a **stage**. Nuevo enfoque: **UAT asistido por IA** (lo lidera Pablo Folgar). Approach para el documento AMFAYS: **HTML pelado + variables + lógica de firma** (AMFAYS adapta el documento después; Marcos lo estima en "meses" → desacoplar del MVP). Flag de **protección de datos** del documento (qué viaja/se loguea). [ingestion/meetings/2026-07-20-daily-perc.md](../../../ingestion/meetings/2026-07-20-daily-perc.md)
- **2026-07-20 (C12 con Seba):** **RESUELTO cómo se resuelven los datos del documento AMFAYS** — por origen: existentes vía **accounts/Sherlock**; faltantes **mockeados/cableados** ahora, con la proveeduría real diferida del lado PERC (importador RRHH); documento **desacoplado del MVP**. Decisión: [2026-07-20-captura-datos-amfays](../../../decisions/2026-07-20-captura-datos-amfays.md). Se confirma **arranque del refactor de lambdas** (no depende de esos datos) y **+1 sprint** formal ([2026-07-20-entrega-perc-mas-un-sprint](../../../decisions/2026-07-20-entrega-perc-mas-un-sprint.md)). Nuevo riesgo: **biométrico dentro del flujo de préstamo** (modifica el front + drop-off). [ingestion/meetings/2026-07-20-sync-perc-c12.md](../../../ingestion/meetings/2026-07-20-sync-perc-c12.md)
- **Próximo hito:** Mes de discovery técnico + definición del pipeline CI/CD antes de comprometer estimaciones finales.

## Evidence
- [source/adhoc/2026-05-21-prd-flujo-credito.md](../../../source/adhoc/2026-05-21-prd-flujo-credito.md) — PRD v2.0 completo

## Linked
- Hypotheses: `../../../hypotheses/flujo-credito.md` (crear cuando haya hipótesis activas)
- Decisions: `../../../decisions/` (crear cuando haya decisiones documentadas)
- Stakeholders afectados: [Sebastián](../../../stakeholders/sebastian.md), [Marcos Copello](../../../stakeholders/marcos-copello.md), [Nicolás](../../../stakeholders/nicolas.md)

## Loan states (definidos 2026-05-20)

| Estado | Descripción |
|---|---|
| **En curso** | Desde que se crea la solicitud hasta confirmar la firma con TOTP |
| **Pendiente** | Desde la firma hasta el desembolso de fondos |
| **Otorgado** | Desde el desembolso hasta la cancelación total |
| **Pagado** | Cancelado totalmente en tiempo y forma |
| **Cancelado anticipadamente** | Pagado por completo de forma anticipada |
| **Precancelado** | Cancelación antes del desembolso (nunca se otorgó) |
| **Arrepentido** | Devolución dentro de los 10 días corridos (Ley de Botón de Arrepentimiento) |

(ingestion/meetings/2026-05-20-refinement-backlog-perc.md)

### Estados a nivel cuota (definidos 2026-06-16, revisados 2026-06-17)

| Estado de cuota | Descripción |
|---|---|
| **Pagada** | El descuento importado iguala el monto de la cuota; queda con fecha de retención |
| **Pago parcial** | El descuento es menor a la cuota; se marca el monto faltante y se genera error. Se completa con carga manual. |
| **Pago con error** | Error de imputación (ej. dato sobre préstamo ya pagado, o desvío no clasificable como parcial/sobrepago). |
| **Sobrepago** | Se descontó de más sobre la cuota; habilita registrar una **devolución al cliente** (la cuota queda PAGADA sin el excedente). |

> **Refinado 2026-06-17 (planning):** se separaron en **tres** estados distintos (Nico objetó usar un único `PAGO CON ERROR` para sub-pago, sobre-pago y no-pago). Nombres y mapeo exacto los afinan Olivier + Seba. (ingestion/meetings/2026-06-17-planning-sprint4-perc.md). El pago se imputa siempre a la **primera cuota no pagada** (el archivo de vuelta de Finegans no trae número de cuota).

> **A relajar — threshold/delta (2026-07-16):** hoy `Pagada` exige que el descuento **iguale exactamente** el monto de la cuota. Si el tercero trunca decimales, todo cae a parcial/error. Se acordó (en principio) introducir un **margen de tolerancia configurable** para la evaluación del pago — la precisión de almacenamiento se mantiene absoluta. Valor y forma (absoluto vs. %) a definir por PERC. Decisión pendiente: [decisions/2026-07-16-threshold-tolerancia-pago-cuota.md](../../../decisions/2026-07-16-threshold-tolerancia-pago-cuota.md). (observation, [ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../../../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md))

## Solicitud creation & expiration logic (definido 2026-05-19)

- La solicitud se crea en BD **solo cuando el usuario completa firma + TOTP** — no al navegar las opciones.
- **Expiración:** 1 hora sin completar firma + TOTP → estado `expirado`. Trigger: cron/Lambda (EventBridge Scheduler).
- **Cambio de template:** expira automáticamente todas las solicitudes `en curso` asociadas.
- A nivel BD: tabla `credits` con estados. A nivel API/UI: endpoints separados para solicitudes en proceso vs. préstamos otorgados.
- **Desembolso:** siempre a cuenta sueldo. Confirmado. El usuario puede tener múltiples wallets — la cuenta sueldo debe identificarse dentro de la lista.

(ingestion/meetings/2026-05-19-planning-refinement-perc.md)

## Documento / campos AMFAYS (relevado 2026-07-17)

> El documento que firma el usuario lo provee **AMFAYS** (la mutual, proveedor del instrumento — ver [knowledge/org/amfays.md](../../org/amfays.md)). Olivier + Marcos bajaron todos los campos del template a un Excel y se revisó campo-por-campo con AMFAYS. **El usuario final no carga nada:** PERC autocompleta el documento y el usuario solo acepta. Definiciones de compliance de AMFAYS pendientes para el **2026-07-20**. Fuente: [ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../../../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md).

### Obligatoriedad de campos (acordado en el call; **[C]** = confirma compliance AMFAYS el 20/7)

| Campo | ¿Obligatorio? | Notas |
|---|---|---|
| Nombre y apellido, DNI | Sí | Disponible en PERC |
| Datos fiscales (CUIT/CUIL) | Sí | Figura en el DNI |
| Lugar de nacimiento | **[C]** | Duda de AMFAYS |
| Teléfono particular (celular) | Sí | |
| Redes sociales / referencias | **No** | PERC no las pide por política |
| Edad | Sí | Se deriva de fecha de nacimiento (para seguro) |
| Correo electrónico | Optativo | |
| Empleador + CUIT empleador + condición + antigüedad | Sí | PERC lo tiene / "hardcodea" (conoce la empresa) |
| **Número de legajo** | Sí (condicionado a la empresa) | Seba: **disponible en el endpoint** (= nº de usuario), hay que enviarlo. Depende de qué exige RRHH para el descuento. Ver también [pendientes §14](../pendientes-produccion.md). |
| Cargo / categoría / sección / actividad / profesión | **No** | Dato comercial, no operativo |
| Domicilio laboral (= de la empresa) | Sí | Por instancia legal |
| Teléfono interno laboral | **No** | |
| **Sueldo NETO** | Sí | Riesgo lo necesita para la matriz (relación cuota/ingreso). **Neto, no bruto.** |
| CVU billetera (corta) | Sí | Cuenta PERC |
| Banco pagador de haberes | Sí | |
| **CBU larga (banco pagador)** | A criterio de riesgo | AMFAYS sugiere capturarla **además** + dejar espacio a un 2º CBU: plan B de cobranza (cámara/COELSA) si el empleado renuncia, de cara a securitización |
| **Nº SAEM/SAIN** | Sí | Correlativo de **14 dígitos, autogenerado por PERC** (no suministrado) |
| Datos del préstamo (monto, cuotas, valor cuota, mes inicio, TNA, CFT, total a reintegrar, comisión precancelación, interés compensatorio) | Sí | Los completa el **Back Office**, no el usuario. Disponibles |
| Destino de fondos | Sí | 5 motivos parametrizables; default **"consumo"** |
| Datos familiares / beneficiario / universidad / servicios sociales | **No** | |
| Declaración jurada PEP + **sujeto obligado (sí/no)** | Sí | El campo sí/no es obligatorio |
| País + autoridad de emisión + volumen de ingreso + motivo | **Condicional** | Obligatorios **solo si sujeto obligado = sí** (regla "fila 47"). AMFAYS duda que algún empleado lo sea |

**Método acordado (ida y vuelta):** marcar todo lo dudoso como obligatorio ahora; PERC devuelve "estos no los tengo"; AMFAYS valida con legales cuáles sacar (2ª revisión). Olivier manda mail de cierre entre 2026-07-17 y el martes.

**Correcciones 2026-07-20 (C12 con Seba):** **propietario de vehículo / inmueble (filas 52-53) → NO obligatorios** (Olivier había supuesto que colgaban de "sujeto obligado"; no es así). Lo obligatorio *si sujeto obligado = sí* son los campos **de arriba** (quién emitió la constancia: país/autoridad de emisión, etc.). **Motivo del préstamo / destino de fondos → hardcode "consumo"**. Firma **sin cambios** (un solo documento, firma electrónica). (observation, Seba, [ingestion/meetings/2026-07-20-sync-perc-c12.md](../../../ingestion/meetings/2026-07-20-sync-perc-c12.md))

### Formato y firma
- **(decisión en principio — AMFAYS OK comercial, falta ver modelo final)** Cambiar el **formato** del documento: checkboxes "de lapicera" y campos sí/no → **texto**, para ingreso dinámico y visualización en la app. Restricción: **no alterar el contenido**, solo la forma.
- **Multi-formulario → 1 archivo firmado:** el legajo son 8-9 formularios que el sistema **unifica en un solo archivo**; se firma el conjunto. **Separar/mezclar formularios distintos rompe la validez del legajo.** **Confirmado 2026-07-20: es 1 solo documento** → decisión [2026-07-20-documento-unico-firma](../../../decisions/2026-07-20-documento-unico-firma.md) (supersede [2026-05-20-sabana-no-persiste](../../../decisions/2026-05-20-sabana-no-persiste.md): ya no se persisten 5 docs por separado).
- **Formulario CVU/CBU = anexo separado** (los bancos lo piden aparte); uso a criterio de riesgo/futuro.
- **Approach de implementación (daily 2026-07-20):** para no bloquear el MVP con el documento real de AMFAYS (que "va a durar meses"), Quarks levanta un **HTML pelado con texto plano + variables + toda la lógica de firma**, deja la función **cableada con placeholders**, y **entrega la función**; **AMFAYS/PERC adaptan el documento definitivo después**. Alinea con placeholders diferidos y con documentos dinámicos HTML→PDF ([2026-06-01](../../../decisions/2026-06-01-documentos-dinamicos-html.md)). (interpretation, Marcos, [ingestion/meetings/2026-07-20-daily-perc.md](../../../ingestion/meetings/2026-07-20-daily-perc.md))
- **Protección de datos del documento (flag 2026-07-20):** **Quarks NO guarda datos del documento — solo la referencia** (el documento vive del lado AMFAYS/PERC). Abierto: ¿viajan/se loguean datos sensibles (DNI, importe, cuota) en request/logs? La cuenta de la persona sí viaja. Pendiente: check para que no queden datos sensibles en logs + dejar **registro fechado** de que Quarks planteó el tema (recomendación de Pablo Folgar). AMFAYS entra como **nuevo tercero** en el tratamiento de datos, no cubierto por el diseño de consentimiento de Mantovana → ver [knowledge/compliance/datos-personales/tratamiento-datos-amfays.md](../../compliance/datos-personales/tratamiento-datos-amfays.md). (observation/interpretation, [ingestion/meetings/2026-07-20-daily-perc.md](../../../ingestion/meetings/2026-07-20-daily-perc.md))
- **Firma = electrónica** (conjunto de evidencias: foto, foto del documento, prueba de vida/movimiento, ID facial), **no digital-por-ley ni holográfica**. Si se securitiza, PERC debe incorporar el proceso de firma y **auditar el proveedor de identidad de la billetera** para que la firma sea válida (relevante a PER-54).

## Open questions
- ~~**Metodología de cuotas:**~~ **Resuelta 2026-05-22 — ver §Cuota methodology.** ([source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))
- ~~**Seguro de vida:**~~ **Resuelto 2026-05-22** — capitalizado al inicio en el monto prestado (`Capital × Seguro%`). Columna G = 0 porque no es cargo mensual. (stakeholder-verbal, Seba, [source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md](../../../source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md))
- ~~**Monto prestado vs. capital solicitado:**~~ **Resuelto 2026-05-22** — fórmula confirmada, ver §Cuota methodology. Capital solicitado = INPUT del BO en el template. (stakeholder-verbal, Olivier, 2026-05-22)
- ~~**Cancelación anticipada — ¿precalculada en template o calculada on-demand?**~~ **Resuelto 2026-07-20 (Olivier) — on-demand: Quarks calcula lo que el usuario debe pagar** (no se precalcula en el template). Confirma la dirección anticipada el 2026-05-27 (era decisión de Quarks). (stakeholder-verbal, Olivier, 2026-07-20)
- ~~**Plazo máximo de desembolso:**~~ **Resuelto 2026-06-02 — 24 horas.** Marcos (CEO) lo confirmó en el Sprint 2 Review: si hay fondos en la cuenta recaudadora la transferencia es inmediata; si no, queda en pendiente y se reintenta. Decisión: [decisions/2026-06-02-plazo-desembolso-24h.md](../../../decisions/2026-06-02-plazo-desembolso-24h.md). Abierto menor: ¿comportamiento exacto en fines de semana / feriados? ([source/meetings/2026-06-03-daily-perc.md](../../../source/meetings/2026-06-03-daily-perc.md))
- ¿Cómo se valida la integración con Watson antes de comprometer estimaciones?
- ~~**Reporte de novedades (sistema → La Mantovana/Finegans):**~~ **Resuelto 2026-06-12 (call con La Mantovana).** Lleva **solo la cuota del mes** (no el total) — decisión: [decisions/2026-06-12-reporte-novedades-cuota-mensual.md](../../../decisions/2026-06-12-reporte-novedades-cuota-mensual.md). Archivo **Excel**, enviado **por mail** a Isis c/c Nico López, **~día 20** (configurable). Campos del importador de Finegans: **número de legajo, número de concepto, nombre, importe, fecha (1° → último día del mes)**. Isis envió el modelo del importador por mail. ([source/meetings/2026-06-12-proceso-prestamos-mantovana.md](../../../source/meetings/2026-06-12-proceso-prestamos-mantovana.md))
- ~~**Reporte de confirmación (La Mantovana/Finegans → sistema):**~~ **Resuelto 2026-06-12.** La Mantovana devuelve el archivo de liquidaciones el **4º día hábil del mes** (día del pago de haberes; puede correr 1–2 días), misma casilla/mail. Conciliación **manual** macheando cuota enviada vs. descontada por legajo; errores → panel/front en Watson para corrección manual. Quarks debe definir los campos del reporte de vuelta. ([source/meetings/2026-06-12-proceso-prestamos-mantovana.md](../../../source/meetings/2026-06-12-proceso-prestamos-mantovana.md))
- **Finegans resuelve por número de LEGAJO (no CUIL/DNI):** Quarks necesita el legajo para comunicárselo a Finegans. **Inclinado 2026-06-16 — lo levanta Quarks** (se guarda en el usuario): no hay opción de leerlo contra la base de La Mantovana, y la alternativa de consumirlo de un servicio externo "la va a descartar Fefe". **Pendiente OK formal de Fefe.** (observation, [ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../../../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md))
- ~~**Regla de corte del archivo de novedades**~~ **Resuelta 2026-06-16 — solo se reportan préstamos DESEMBOLSADOS.** Lo no desembolsado al momento del reporte entra al ciclo siguiente; si el desembolso es post-corte la primera cuota cae al mes posterior y la generación de cuotas lo contempla. Dos ciclos configurables (informe 20→20, pago 4º día hábil). Decisión: [decisions/2026-06-16-corte-solo-desembolsados.md](../../../decisions/2026-06-16-corte-solo-desembolsados.md). ([ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../../../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md))
- **Lógica de aplicación de pagos (definido 2026-06-16):** el archivo de vuelta de Finegans NO trae número de cuota → el pago se imputa a la **primera cuota no pagada** (regla 4+1). Se eliminó el escenario "cuota fuera de rango". Pago parcial → estado `PAGO PARCIAL`; sobre/sub-descuento → `PAGO CON ERROR`. Resolución de diferencias = **carga manual** desde el BO (botón cliente+cuota, registra quién/cuándo/cuánto). (observation, [ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../../../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md))
- ~~**Desembolso: FIFO vs "primer monto pagable con el disponible"**~~ **Resuelto 2026-06-17 (planning) — FIFO.** La cola de desembolsos pendientes se procesa FIFO; sin fondos la solicitud queda PENDIENTE (retry automático cada 5 min, parametrizable), desembolsa automático si ingresan fondos antes de 24h **corridas**, y se cancela a las 24h. Siempre a cuenta sueldo. Decisión: [decisions/2026-06-17-desembolso-fifo.md](../../../decisions/2026-06-17-desembolso-fifo.md). **Residual:** falta confirmación explícita de Seba de que se quiere FIFO estricto (esperar fondos) y no saltar al siguiente pagable. (observation, [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../../../ingestion/meetings/2026-06-17-planning-sprint4-perc.md))
- **Día de corte: valor en base de datos, no variable de ambiente (corregido 2026-06-17):** Nico aclara que el día de corte lo controla el BO → debe vivir en BD, no como parámetro de ambiente. (observation, Nico, [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../../../ingestion/meetings/2026-06-17-planning-sprint4-perc.md))
- **Base del costo de cancelación anticipada (3%) (abierto 2026-06-17):** ¿se aplica sobre la deuda restante o sobre el total? ¿incluye el gasto de otorgamiento? El Excel lo tiene pero el PR dejó dudas internas sin resolver. A validar con Seba/Fefe. (observation, Nico, [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../../../ingestion/meetings/2026-06-17-planning-sprint4-perc.md))
- **¿La Mantovana puede regenerar reportes por rango de fechas (abierto 2026-06-17)?** Ej. del 21 al 30 para cuotas que no entraron en el reporte anterior. Olivier lo lleva a Seba; riesgo de feature regalado. El reporte exportado va **completo**; el filtrado vive solo en la vista de histórico (por usuario/mes/fecha + paginación). (observation, Nico + Olivier, [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../../../ingestion/meetings/2026-06-17-planning-sprint4-perc.md))
- **Historia faltante a crear (2026-06-17):** cancelar la SOLICITUD antes del desembolso (cancelación manual del usuario en la ventana de 24h = desistimiento), en vez de la cancelación automática. (observation, Olivier, [ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../../../ingestion/meetings/2026-06-17-planning-sprint4-perc.md))
- **Deuda de capital desagregada por cuota (abierto 2026-06-16):** Seba propone guardar las variables del template desagregadas (no solo el número de cuota) para poder consultar el capital adeudado hasta cada cuota — necesario para calcular el pago anticipado. A validar con Nico/devs. (observation, Seba, [ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../../../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md))
- **Cuadre contable préstamo total vs. cobrado con pagos parciales (fuera de scope Quarks, 2026-06-16):** con parciales, lo prestado nunca cuadra con lo cobrado (la mutual prestó 100, cobró 90, debe remesar 100). La solución está en cómo liquida La Mantovana contra la mutual — Seba lo resuelve con los devs/Fefe; no es desarrollo de Quarks. La mutual es el proveedor del préstamo, no Perk. (interpretation, Seba, [ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md](../../../ingestion/meetings/2026-06-16-refinamiento-historias-mantovana-perc.md))
- **Tope legal de descuento = 30% del sueldo percibido (definido 2026-06-12):** la cuota no puede superar ese %. Quarks necesita el **sueldo de cada empleado** para calcular el máximo prestable (dato que entra con la elegibilidad). (observation, Nico Ortiz, [ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../../../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md))
- **Casuística border — cancelación entre el día 20 (cuota ya reportada) y el pago de haberes (abierto 2026-06-12):** ¿cómo se comunica la baja de una cuota ya informada? Columna/pestaña, segundo archivo, o update de la novedad en Finegans. **Seba lo llevó a refinamiento interno de Perk** (legal + técnico + producto). Probablemente proceso manual en Finegans, fuera del scope de Quarks (sin acceso a APIs de Finegans). (observation, [ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md](../../../ingestion/meetings/2026-06-12-proceso-prestamos-mantovana.md))
- ~~**Penalidad sobre intereses futuros (cancelación anticipada)**~~ **Resuelto — se aplica costo.** En la precancelación anticipada se cobra penalidad sobre intereses futuros; fórmula cerrada con Seba (Compliance) y Fefe (COO). **Fórmula:** Total = Capital restante + (Int. futuros × % penalidad) + (Capital × % comisión) + IVA. Decisión: [decisions/2026-06-02-penalidad-intereses-futuros.md](../../../decisions/2026-06-02-penalidad-intereses-futuros.md). (observation, [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- **IVA en cancelaciones — ¿aplica siempre o solo si usuario no paga antes?** Excel lo marca configurable (flag B8 = 1). Olivier observa: "me suena raro porque si el usuario la paga bien hasta el final, porqué le cobro la cancelación?" Seba está rearmando la tabla del Excel (más simple). (observation, [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- ~~¿Los documentos HTML son dinámicos o estáticos?~~ **Resuelto — dinámicos, HTML→PDF.** Sebastián confirmó (1/6) que los documentos son dinámicos y van en HTML. **Confirmado 2026-06-08:** el BO sube HTML y el sistema lo devuelve al cliente en PDF (la app es Flutter) → la librería es HTML→PDF, no PDF→HTML. Decisión: [decisions/2026-06-01-documentos-dinamicos-html.md](../../../decisions/2026-06-01-documentos-dinamicos-html.md). **Riesgo operativo:** el operador del BO debe convertir su .docx a .html (¿sabe hacerlo?). **Sigue abierto:** cuáles documentos exactos (plantillas en compliance, ver abajo). ([source/meetings/2026-06-08-daily-perc.md](../../../source/meetings/2026-06-08-daily-perc.md))
- ¿Se puede resolver el TOTP security gap sin breaking changes en la implementación existente? (Nico + Joy)
- Restricciones de archivo HTML: tamaño, XSS, sanitización. (Olivier → cyber)
- **Empleados PJ — parcialmente resuelto 2026-07-16.** Hay empleados PJ en Grupo PERC (stakeholder-verbal, Seba, 2026-05-22). Impacto en documentos y posiblemente front/back/BO. 2026-05-27: Olivier preguntó si "están discriminados en los datos" para identificarlos en BO. **Resuelto (dato):** el endpoint de cuenta trae `person_type` = `J` o `F` al pedir la cuenta — Quarks ya tiene el flag para discriminar PJ/PF. (stakeholder-verbal, José Salgado, 2026-07-16, [ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md](../../../ingestion/meetings/2026-07-16-demo-uat-cliente-perc.md)). **Sigue abierto:** si con eso alcanza para todo el impacto en documentos/BO. ([ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- Verificar que el evento Lambda HTTP trae JWT decodificado. (Isra / Nico)
- Identificar cuenta sueldo dentro de la lista de wallets del usuario vía `get account`. (Nico / Isra)
- **Tab bar redesign:** Incorporar préstamos en la navegación requiere rediseño del tab bar (hoy: QR / perfil / home). ¿Cuál es el nuevo esquema de navegación? Pendiente. (observation, [ingestion/meetings/2026-05-20-diseno-flujo-credito.md](../../../ingestion/meetings/2026-05-20-diseno-flujo-credito.md))
- **Compliance: ¿avisar que la operación va por BIND?** ¿Obligatorio informar al usuario que la operación se procesa a través del BIND (o equivalente)? ¿En qué paso/s? Pendiente respuesta de Seba desde 2026-04-08. (observation, [ingestion/adhoc/2026-03-06-whatsapp-grupo-perc.md](../../../ingestion/adhoc/2026-03-06-whatsapp-grupo-perc.md))
- **Arquitectura: estructura cuotas-vs-payments (Sprint 3 — en validación).** Cómo modelar las tablas (cuotas vs. payments) y qué se guarda. **Actualización 2026-06-08:** el dev está armando la estructura y manda un PR para que Nico la valide antes de implementar. (observation, [ingestion/meetings/2026-06-08-daily-perc.md](../../../ingestion/meetings/2026-06-08-daily-perc.md))
- ~~**PER-42 — tabla / integración de cuotas (bloqueante).**~~ **Desbloqueada 2026-06-08.** El dev sacó el hardcode del Sistema Francés (lo hizo dinámico según el crédito); los cálculos ya están subidos y mergeados hasta el front. Falta la lógica para crear las cuotas (hoy es solo la tabla) y el PR a PERC. (observation, [ingestion/meetings/2026-06-08-daily-perc.md](../../../ingestion/meetings/2026-06-08-daily-perc.md))
- **PER-54 — implementación de firmas (Sprint 3 — bloqueante).** Modelo tentativo (Daily 3/6 + 8/6): iniciales tipo DocuSign — el usuario confirma y se insertan las iniciales de nombre/apellido como consentimiento, sin firma a mano alzada. **Open question clave: ¿alcanza legalmente, o compliance exige algo más estricto?** Seba se llevó el tema y aún no respondió. Define el esfuerzo de toda la firma. (observation, [ingestion/meetings/2026-06-08-daily-perc.md](../../../ingestion/meetings/2026-06-08-daily-perc.md))
- ~~**Infra: bucket S3 + entorno dev/stage (bloqueante).**~~ **Camino acordado 2026-06-08:** PERC DevOps da cuenta Sandbox de Amazon; Quarks crea bucket y testea; luego PERC monta dev env con CI/CD. Pendiente: Quarks pasa el punteo de servicios Amazon. **⚠️ Riesgo de scope abierto:** no quedó claro si Quarks debe configurar los entornos a mano (no estaba en el scope del contrato) o si PERC los replica con Terraform — la reunión no se grabó, **confirmar con Israel**. (observation, [ingestion/meetings/2026-06-08-daily-perc.md](../../../ingestion/meetings/2026-06-08-daily-perc.md))
- **Desglose de cuota del lado del usuario (gap abierto 2026-07-16):** el desglose completo (capital / interés / IVA / gasto administrativo) hoy solo aparece en el **template (BO)** y en el **detalle del operador de BO**; del lado usuario no se muestra. Olivier: "esto tiene que estar". Pendiente decidir/implementar qué desglose ve el usuario en el detalle de cada cuota. (observation, [ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../../../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md))
- **¿Cómo se muestra una cuota "pagada con error" en el front del cliente (abierto 2026-07-16)?** ¿Como "pagada con error" o como "pendiente"? Marcos: "no me enfocaría en eso; si ellos lo quieren cambiar, que nos digan." A definir con PERC. (observation, [ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../../../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md))
- **Nº SAEM/SAIN — generación + unicidad (abierto 2026-07-17, refinado 20/7 C12):** correlativo de 14 dígitos, autogenerado por PERC. **Seba duda de la unicidad** si se genera "random"/algorítmico — no garantiza que no exista previamente (colisión). Debe ser **correlativo único garantizado**, no random. Falta definir dónde/cómo se genera y persiste. (observation, [ingestion/meetings/2026-07-20-sync-perc-c12.md](../../../ingestion/meetings/2026-07-20-sync-perc-c12.md))
- **CBU larga del banco pagador — ¿se captura además de la CVU corta? (abierto 2026-07-17):** AMFAYS lo recomienda como plan B de cobranza para securitización; queda a criterio de riesgo de PERC. Requiere el formulario de autorización (anexo). (observation, [ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../../../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md))
- **Campos AMFAYS pendientes de compliance (2026-07-20):** lugar de nacimiento, datos sensibles, alcance de sujeto obligado/PEP. (observation, [ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../../../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md))
- ~~**¿Dónde se capturan los ~20 campos del documento AMFAYS?**~~ **Resuelto 2026-07-20 (C12) — por origen.** Existentes (nombre/CUIT/cuenta) vía **accounts + Sherlock** (abrir ese endpoint); faltantes (antecedentes laborales, sueldo neto, domicilio laboral, legajo; actividad = hardcode "empleado") **mockeados/cableados** ahora, con la **proveeduría real diferida del lado PERC** (importador RRHH); documento **desacoplado del MVP**. Ni onboarding ni taggeo-BO. Decisión: [2026-07-20-captura-datos-amfays](../../../decisions/2026-07-20-captura-datos-amfays.md). (observation, [ingestion/meetings/2026-07-20-sync-perc-c12.md](../../../ingestion/meetings/2026-07-20-sync-perc-c12.md))
- **Biométrico/KYC en el flujo de préstamo — ¿alcanza el onboarding o hay que re-pedirlo? (abierto 2026-07-20 C12):** caso de máxima asumido = re-pedir + documentar + bajar al PDF (modifica front, ver §Risks). A evacuar con AMFAYS. (observation, [ingestion/meetings/2026-07-20-sync-perc-c12.md](../../../ingestion/meetings/2026-07-20-sync-perc-c12.md))

## Cuota methodology (Excel Seba, 2026-05-22)

**Sistema Francés — cuota fija mensual.**

### Componentes de la cuota

| Componente | Fórmula | Comportamiento |
|---|---|---|
| Interés bruto | Saldo inicial × (TNA/12) | Decrece en cada cuota |
| IVA s/intereses | Interés bruto × 21% | Decrece en cada cuota |
| Amortización capital | Cuota pura − Interés − IVA | Crece en cada cuota |
| Seguro de vida | Capital × Seguro% (capitalizado al inicio) | Siempre 0 en cuotas mensuales — incluido en monto prestado |
| Gasto administrativo | Monto fijo mensual | Fijo por template |
| **Cuota total** | **Suma de los anteriores** | **Fija por Sistema Francés** |

### Cálculo de la TEM y la cuota pura

- TEM sin IVA = TNA / 12
- **TEM con IVA = TEM_sin_IVA × (1 + 0.21)** — se usa para el PMT
- Cuota pura = PMT(TEM_con_IVA, n, −Monto_prestado)
- La cuota es verdaderamente fija porque la TEM ya incorpora el IVA.

### Capital y monto prestado

**Fórmula:**
`Monto prestado = Capital + (Capital × Seguro%) + (Capital × Sellos%) + (Capital × Mora%) + Gastos otorgamiento`

Ejemplo ilustrativo: 1,000,000 + 30,000 (seguro) + 12,000 (sellos) + 30,000 (mora) + 3,000 (otorgamiento) = **1,075,000**

- **Capital solicitado:** INPUT del operador de BO al configurar el template. El cliente recibe este monto.
- **Seguro de vida:** capitalizado al inicio como `Capital × Seguro%`. No aparece en cuotas mensuales (columna G = 0). (stakeholder-verbal, Seba, 2026-05-22)
- **Mora:** capitalizada como costo en el capital inicial — **confirmado por Seba, 2026-05-27:** "se cobra como un adicional... es un % extra un chiquitin especial." Es decir, es un % fijo sobre el capital, no una penalidad condicional. "No hay devoluciones de nada" — se cobra siempre, incluso si el usuario paga en término. (stakeholder-verbal, Seba, 2026-05-22 + 2026-05-27)
- **Total crédito** = Monto prestado + Sellos + Gastos otorgamiento

### Cancelación anticipada

`Total = Capital restante + (Int. futuros × % penalidad) + (Capital restante × % comisión) + IVA s/(penalidad + comisión)`

IVA sobre penalidades: **confirmado aplica** (Excel flag B8 = 1; asunción PM 2026-05-22).
Todos los % son configurables por tipo de préstamo.

### Valores ilustrativos

Los parámetros del Excel (TNA 89%, sellos 1.2%, mora 3%, gasto adm $500, otorgamiento $3,000) son **ejemplos, no valores finales del MVP**. Se configurarán por template/tipo de préstamo. (assumption, Olivier, 2026-05-22)

([source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))

## Technical conventions (acordadas con PERC)
- **IDs de BD:** LUID (Lexicographically Unique ID — ordenables, no exponen volumen). Postgres soporta nativamente. Decisión: [decisions/2026-05-18-luid-ids.md](../../../decisions/2026-05-18-luid-ids.md)
- **Tasas porcentuales:** decimal 0–1 en BD (0.105 = 10.5%). Front se encarga de la representación. Convención consistente con el resto del sistema PERC. (stakeholder-verbal, José Salgado, 2026-05-18)
- **Fechas:** ISO 8601 con offset de timezone (ej. `2026-05-18T15:59:00-03:00`). Postgres: `timestamp with time zone`. (stakeholder-verbal, José Salgado + Nicolás, 2026-05-18)

## Future scope / out of MVP
- **FIFO waitlist cuando recaudadora se vacía:** Marcos quiere cola de solicitudes pendientes cuando no hay fondos, procesadas FIFO a medida que ingresan fondos. Juan Pablo: "lleguemos primero a acabar la plata." Explícitamente fuera del MVP. (stakeholder-verbal, Sebastián Cárdenas + Juan Pablo Norverto, 2026-04-20)
- **Multi-tenant / B2B:** El sistema es escalable via tags a otros clientes B2B. Fuera del scope del contrato actual. (stakeholder-verbal, Sebastián Cárdenas, 2026-04-20)

## Follow-up after launch
- Medir tasa de adopción en las primeras 4 semanas post-lanzamiento.
- Medir reducción de carga manual en el Backoffice (casos gestionados vs. baseline).
- Revisar el flujo de conciliación (doble check) con La Mantovana en el primer ciclo de cobro.
- Evaluar si el scope termina aquí o si hay contrato extendido con Quarks para V2/V3.
