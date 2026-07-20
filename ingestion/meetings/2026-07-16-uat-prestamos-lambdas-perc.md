# Ingesta — UAT Préstamos + bomba de lambdas (PERC, 2026-07-16)

- **Fuente (transcript):** [../../source/meetings/2026-07-16-uat-prestamos-lambdas-perc.md](../../source/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)
- **Participantes:** Olivier (PM Quarks), Marcos Perez (dev back Quarks), un TL de Quarks (Nico Paez / Isra — voz que plantea el tema de entorno; atribución no 100% cierta), Gonza/Gonzalo (infra PERC, vía mensaje). Menciones: José Salgado (dev PERC), Fefe (COO Quarks), Juampi (dev front Quarks), Seba (PO PERC), Jo (reviewer PRs PERC).
- **Shape:** meeting (dry-run interno de UAT + escalación de bloqueos)
- **Contexto:** ensayo interno del UAT del módulo Préstamos (~92 casos) en local, la mañana previa a una reunión con PERC agendada como "UAT" a las 16:00. A mitad de sesión entra el TL, se dispara la discusión de entorno, y luego Gonza (infra PERC) pide **consolidar las lambdas**, lo que fuerza reescritura y hunde la deadline del martes.

---

## 1. Estado del UAT (Type A — routing)

- **(observation)** UAT corrido **100% a mano** sobre **local**, vía **Insomnia (API)** + un **playground en Angular**. De ~92 casos: **~60 chequeados (66%)**, **~50 aprobados**, **3 rechazados**, resto pendiente; **~30 casos por chequear**. — Olivier, [source](../../source/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)
- **(observation)** El **simulator/playground** muestra solicitudes expiradas y estados que **no se verán en el front real** — es herramienta de prueba, no entregable. Lo comprometido es la **API (Insomnia)**; el playground Angular se ofrece "si les sirve". — Marcos + Olivier, ídem.

### Casos validados / reconfirmados en la corrida
- Template: listado, detalle (costos, tasas, costos computados, cuadro de marcha/cuotas), alta y **baja lógica con trazabilidad en logs/auditoría**. La eliminación de un template **no modifica los créditos ya otorgados**; sí cierra las solicitudes en curso al editar el template. — coherente con lógica de expiración ya definida.
- Solicitud en curso **expira a la hora sin firmar** (cron corrido en la demo). ✅
- Otorgamiento: "aprobar" en la demo = firmar el documento (si se firma, se aprueba automático; no hay paso de aprobación manual — el préstamo es **pre-aprobado**). — Olivier/Marcos.
- Listado de solicitudes BO + **exportación** (solo la aprobada). ✅
- Créditos otorgados: listado, filtrar/ordenar, detalle con próxima cuota y vencimiento. ✅
- Importación de liquidaciones Mantovana: casos **pagada / pago parcial (menos) / sobrepago (más, habilita devolución) / ID inexistente (no matching) / reaplicación (ya procesada)**. ✅ (con las salvedades de front de abajo)
- Carga manual de pago (cliente + cuota + monto + fecha → pago parcial; completar faltante → cuota pagada). ✅
- Histórico de exportaciones/envíos (usuario, origen, cuotas, ciclo, fecha; paginado; log de envíos Mantovana). ✅

## 2. Hallazgos funcionales / gaps abiertos (aprobados-con-comentario o pendientes)

- **(observation → gap de front)** **Desglose de cuota (capital / interés / IVA / gasto administrativo) NO se muestra del lado usuario.** Hoy solo aparece en el **template (BO)**. Olivier: "esto tiene que estar". Se reencuadró: el desglose completo vive en el **detalle del préstamo del operador de BO**; el usuario ve total, cantidad de cuotas, restantes, fecha de acreditación, ID, próxima cuota, deuda restante, estado de cuotas + botones. **Pendiente** decidir/implementar qué desglose ve el usuario. — Olivier + Marcos.
- **(observation → gap de front)** El **`deviation amount`** del resumen de importación **no muestra el signo (+/-)** en el front (sí está en el back). Debe mostrarse si es partial (falta) u over (excedente). Aprobado-con-comentario. — Marcos.
- **(observation → gap de front)** El **resumen de importación** ("N aprobados / N con error", tipo vista de data-analyst que mostró JP) **solo se ve por Insomnia**, no hay pantalla en el front; el detalle por cuota (expected/discounted/deviation/description/outcome) existe pero hay que **mostrar la pantalla** en el UAT. Aprobado-con-comentario. — Olivier + Marcos.
- **(observation → gap de front)** Tablas de BO **cortan el string** de IDs largos y **falta botón de copiar** → agregar copy o estirar el string. Marcos se lo anota. — Marcos.
- **(bug abierto)** Préstamo **pagado no libera al usuario para pedir otro**: el crédito pasa a `paid` pero la **`application` no pasa a `completada`**, y el filtro que bloquea un segundo préstamo no la deja. Marcos lo está chequeando. Caso marcado **rechazado** provisoriamente en la planilla. — Marcos.
- **(observation)** **Aleatoriedad al pagar cuotas/hacer devoluciones**: rompe ~la mitad de las veces sin explicar el error (ver §3, es problema de infra/lambdas, no de lógica). — Marcos.
- **(assumption/decisión pendiente)** Al front del cliente, ¿una cuota "pagada con error" se muestra como tal o como "pendiente"? Marcos: "no me enfocaría en eso; si ellos lo quieren cambiar, que nos digan." **No resuelto.** — Marcos.
- **(observation)** Los **centavos** se comparan **exacto (igual = igual)**: cualquier diferencia de centavos cae a pago parcial/error. — Marcos.
- **(observation)** **Número de legajo** todavía **no lo entregó PERC** → casos que lo requieren quedan pendientes. El archivo de novedades ya arma legajo / ID cuota / nombre / importe. — Olivier.

## 3. Regla de corte del reporte Mantovana — clarificada (refina decisión previa)

- **(observation)** Durante la demo, la generación del archivo **no incluía ninguna cuota**; se depuró la ventana de corte. Ventana del ciclo (ej. **julio**):
  - **`due_date` de la cuota entre el 1 y el 31 del mes del ciclo**, **Y**
  - **crédito otorgado/`granted` antes del día 20 del mes anterior** (ej. antes del 20 de junio para el ciclo de julio), **Y**
  - crédito activo con cuota pendiente activa.
  - Regla de vencimiento: **fecha de vencimiento = fecha de pedido del préstamo + 1 mes**. Si se pide el 16/07, la 1ª cuota vence el 16/08 y entra al ciclo del mes siguiente (corte hasta el día 20). Al usuario se le muestra el **mes siguiente**.
  - Refina/operacionaliza [decisions/2026-06-16-corte-solo-desembolsados.md](../../decisions/2026-06-16-corte-solo-desembolsados.md). — TL Quarks + Marcos + Olivier.
- **(bug conocido, no bloqueante para la lógica)** La **query de corte funciona** (exporta la cuota correcta) pero **falla al subir el archivo al vault** (el documento con ID cuota/legajo/concepto/empleado/importe "no lo está subiendo bien"). Se sabe el workaround (armar el installment y correr el import por Insomnia). Marcos lo sigue. → **La ida-y-vuelta completa de Mantovana se prueba el lunes 2026-07-20** con casos: 1 cuota OK, 1 que sobra, 1 que falta, 1 con ID mal. — Marcos + Olivier.

## 4. LA BOMBA — consolidación de lambdas (Gonza / infra PERC)

- **(observation / cambio de scope tardío)** **Gonza (infra PERC) pide reagrupar todas las lambdas**: hoy hay **~65 lambdas** (antes eran ~20); pide **mercharlas** (agrupar get/post/put/delete por recurso en una sola lambda). Motivo declarado: **explota el flujo de CI/CD** y **auditorías de Amazon** (cada lambda dispara una auditoría → costos de la compañía). "Me pidió perdón porque no lo vio antes." — Marcos.
- **(observation)** El **último deploy real fue con ~20 lambdas** — "nunca más se volvió a deployar". El ambiente de development **nunca corrió la versión actual**. — Marcos.
- **(interpretation, equipo)** Es un cambio de **implementación, no de lógica**, pero **mueve código en todo el proyecto** + **reescribe todos los paths del front y del Insomnia** → **hay que rehacer el UAT completo** (los casos no cambian; los resultados verificados sí). **+1 sprint. La deadline del martes 2026-07-21 es inalcanzable.** — Marcos + TL.
- **(interpretation, Olivier)** "No nos prestaron atención, y ahora que nos prestan atención saltan cosas que deberían haber hecho al arrancar." Es algo que **debió surgir el día 2 del proyecto**. Sirve, además, como **argumento** para justificar la extensión de plazo ante Fefe/PERC. — Olivier + TL.

## 5. Problema de entorno / infra (raíz de casi todos los fallos)

- **(observation)** El UAT corre en la **local de Marcos** (**Mac M1 Pro, 16 GB RAM**) levantando **~65 serverless functions** con **Docker + SAM** → **timeouts / 500 aleatorios** (memoria 512, la lambda no llega a levantar antes del timeout de ~30 s). Se reintenta y anda. **Casi todos los fallos del UAT son de ambiente, no de código.** — Marcos + TL.
- **(observation)** Ambiente de **development de PERC no está listo**: faltan **variables de entorno** y **PRs por aprobar** (Jo, reviewer PERC, corrige PRs en 5 min marcando blockers triviales). El TL: "no haría el UAT por primera vez frente al cliente, y menos en un entorno que nunca desplegó la versión actual." — TL + Marcos.
- **(idea, TL)** Mínimo, darle a Marcos una **instancia AWS con más RAM (paga Quarks) + SSH** para correr el stack, en vez de la local. — TL.
- **(observation)** El `make fresh` (borrar Docker y reempezar) ayuda a descongestionar; conviene **pre-cargar un caso de préstamo de 3 cuotas** al hacerlo (solo hay 1 usuario → 1 solo préstamo a la vez, lo que ralentiza los casos de pago total). — Marcos + Olivier.

## 6. Decisiones operativas tomadas (para confirmar por PM)

- **(decision operativa, equipo Quarks)** **La reunión de las 16:00 NO se corre como UAT caso-por-caso.** Se hace un **happy path end-to-end de los flujos principales**, encuadrado como "el recorrido que **verificamos en nuestros entornos**, ya que **dev no está disponible**". La planilla de UAT (todos los casos probados) se **muestra**, no se re-ejecuta en vivo. El UAT fino caso-por-caso queda **interno** hasta tener el entorno dev estable. Propuesto por Marcos, avalado por el TL y Juampi ("el que avisa no traiciona" es la postura declarada de Olivier). — [source](../../source/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)
- **(decision, Olivier)** Abrir la reunión mencionando explícitamente que **el entorno dev no está listo** (faltan PRs + variables), por eso se muestra en local y puede haber comportamiento de **infra** (no de código). Wording afinado con el equipo.
- **(decision de proceso)** La consolidación de lambdas + el documento AMFAYS pendiente + el trabajo de desembolso **empujan la entrega a otro sprint**; se comunica a Fefe/PERC con la lista de atrasos como argumento. Vía primero "por las buenas" (pedir un sprint más), la escalación completa como carta de reserva. — Olivier + TL.

## 7. Acciones

- **Olivier** → mandar a PERC (¿José?) un **listado estructurado**: (a) ¿está la **segunda cuenta** para el **desembolso**?; (b) ¿ya **capturan el legajo** en el endpoint de datos del usuario? (PR 67 visado). Documentos se hablan aparte.
- **Olivier** → preparar el guion de la reunión de las 16:00 (happy path + paréntesis de entorno) y hablarlo con **Fefe** (y Juampi) antes del martes para reencuadrar expectativas / extensión de plazo.
- **Marcos** → (1) chequear el bug de `application` no completada tras pago total; (2) agregar copy/estirar strings en tablas BO; (3) resolver la subida al vault del archivo Mantovana; (4) con Gonza/Gonzalo, ver qué falta del entorno dev.
- **Marcos + equipo** → evaluar la reescritura de lambdas (merge get/post/put/delete) — posiblemente en branch aparte, a confirmar arriba antes de invertir el tiempo.
- **Lunes 2026-07-20** → probar ida-y-vuelta completa de Mantovana (casos OK/sobra/falta/ID mal).

## 8. Ruteo — destinos durables (PROPUESTOS, requieren OK del PM)

- `knowledge/product/features/flujo-credito.md`:
  - **Timeline:** entrada 2026-07-16 (dry-run UAT; consolidación de lambdas hunde deadline; happy-path con cliente).
  - **Risks:** nuevo riesgo "**Entorno/infra: 65 lambdas no corren en local + dev nunca desplegó versión actual**" y "**Consolidación de lambdas pedida tarde por PERC = reescritura + rehacer UAT = +1 sprint**".
  - **Open questions:** desglose de cuota del lado usuario (qué se muestra); estado de cuota "pagada con error" en front del cliente; legajo aún no entregado; segunda cuenta de desembolso.
  - **Cuota/corte:** anotar la ventana de corte clarificada (due_date en el mes ∧ granted antes del día 20 del mes anterior).
- `knowledge/strategy.md § Tensions`: nueva tensión **"deadline martes 2026-07-21 vs. scope tardío + entorno no entregado"** (tensiona prioridad #1). Cambio en strategy → requiere OK del PM.
- `stakeholders/marcos-perez.md`: touchpoint 2026-07-16 (dueño del UAT/back; propone happy path; lleva bug de application + reescritura de lambdas).
- `stakeholders/` (Quarks TL: Nico Paez o Isra): touchpoint 2026-07-16 (atribución a confirmar).
- **Nuevo stakeholder (candidato):** **Gonzalo ("Gonza") — Infra/DevOps, PERC.** Disparó el pedido de consolidación de lambdas. No tiene ficha aún.
- **Posible decisión futura:** registrar formalmente "UAT con cliente = happy path, no caso-por-caso, hasta entorno dev estable" y/o "consolidación de lambdas → +1 sprint" si el PM quiere anclarlas como decisiones.

## 9. Contradicciones / tensiones con evidencia previa

- **Entorno como scope extra** ya estaba señalado como riesgo abierto ("¿quién configura los entornos?", flujo-credito §Risks / Daily 2026-06-08). Hoy **se materializa**: el dev env sigue sin estar operativo un mes después, y ahora agrega la reescritura de lambdas. No es señal nueva — es la **confirmación** de un riesgo ya documentado.
- La **fricción de PRs con PERC (Jo)** ya estaba en [ingestion/meetings/2026-06-26-prereview-perc.md](2026-06-26-prereview-perc.md). Persiste (blockers triviales, 5 min de review).
- El **documento AMFAYS pendiente** ([2026-07-08](2026-07-08-documento-legajo-prestamo-perc.md)) sigue sin entregarse y es co-causa de la extensión de plazo.
