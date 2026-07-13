# Ingestion: Daily - PERC (2026-06-08)

**Source:** [2026-06-08-daily-perc.md](../../source/meetings/2026-06-08-daily-perc.md)
**Kind:** meeting (daily standup)
**Participants:** Olivier (PM), Nicolás (TL), Marco (dev), Juampi (dev), Connie; ref: Israel, Stefano Giuliano, Seba, José

## TL;DR

Los **dos bloqueantes top de infra se destrabaron** (entorno + S3): PERC da una cuenta **Sandbox de Amazon**, Quarks arma todo para testear, y después PERC monta el entorno de development con CI/CD. Quedó definido el **formato de documentos**: el BO sube HTML, el sistema devuelve **PDF** al cliente (porque la app es Flutter) → la librería es **HTML→PDF** (no al revés). Las **plantillas finales** siguen pendientes (Giuliano las pasó a compliance, esperando resolución) y la **firma** sigue sin respuesta de Seba. El dev avanza en cuotas (saca hardcode del Sistema Francés, lo hace dinámico).

## Observaciones (tagged)

### Infra — entorno dev + S3 (bloqueantes #1 y #2): DESTRABADOS (con pasos)
- **[observation]** PERC (DevOps) va a dar a Quarks una **cuenta Sandbox de Amazon**. Quarks crea el bucket y todo lo necesario para testear/armar. Después PERC monta el entorno de **development con CI/CD** (autodeploys).
- **[observation]** Acción Quarks: pasar a PERC un **punteo de los servicios de Amazon** que van a necesitar (ej. S3 para Cosso/documentos; algún servicio para los claims/eventos, expuestos vía API Gateway + Lambda) para que les habiliten la cuenta.
- **[observation]** Con la Sandbox van a poder **probar las plantillas de documentos contra S3**.
- **[observation]** PERC creó un **canal de dev en PER-Quarks** para preguntas técnicas de ambos lados.
- **[interpretation]** Pasó de "bloqueante duro esperando a PERC" a "camino acordado, pendiente de ejecución" (habilitar cuenta + pasar lista de servicios). Sigue siendo riesgo si la cuenta tarda, pero ya no está trabado conceptualmente.

### Ambigüedad abierta sobre el entorno (a confirmar con Israel)
- **[observation]** No quedó claro si PERC **replica exacto** el entorno o pide que Quarks configure los entornos a mano. Posible plan: el primer proyecto levantan el YAML con **Terraform** y se lo pasan a Quarks — pero el dev no está seguro.
- **[observation]** La reunión **no fue grabada**. Olivier va a preguntarle a Israel qué entendió.
- **[interpretation]** Riesgo de scope: configurar entornos "a mano" no estaba en el scope del contrato. Conviene clarificar antes de asumir trabajo extra.

### Formato de documentos (bloqueante #5): RESUELTO
- **[decision]** Los documentos **arrancan en HTML** (para la parte dinámica) y se **devuelven al cliente en PDF** (la app es Flutter). La librería necesaria es **HTML→PDF**, no PDF→HTML.
- **[observation]** Flujo operativo del BO: el operador tiene su `.docx`, lo pasa a **`.html`**, y recién ahí lo sube al backoffice.
- **[observation]** Lo dijo un dev / José (no Seba) — a Olivier le da más confianza la definición.
- **[interpretation/risk]** Nico marca duda operativa: **¿quién es el operador del BO y sabe convertir docx→HTML?** Riesgo de que suba un XML pensando que es parecido. Mitigación propuesta por Olivier: cartel de advertencia + aclarar en la review que es HTML puro (lo tienen que integrar operativamente); si quieren auto-conversión como mejora, suma ~1 semana.

### Plantillas de documentos finales: sigue pendiente
- **[observation]** Stefano Giuliano informó que **pasó las plantillas a compliance** y está esperando resolución.
- **[observation]** Olivier recuerda tener **documentos viejos con la estructura básica**; los va a buscar y pasar al equipo hoy (solo se necesita la estructura, no el documento final).

### Firma (bloqueante): sin novedad
- **[observation]** Seba "se había llevado cosas para ver"; aún sin respuesta. El gran pendiente sigue siendo documentos + firma.

### Trabajo en curso esta semana
- **[observation]** Dev (Marco) — **cuotas**: por mandar un PR con el fix sugerido por Nico = sacar el **hardcode del Sistema Francés** que estaba en varios archivos y hacerlo dinámico según lo que venga en el crédito. Luego, la lógica para **crear las cuotas** (hoy es solo la tabla en BD). Los **cálculos ya están subidos y mergeados hasta el front** (todo en development) — Olivier puede testearlos.
- **[observation]** Juampi — corrigiendo las **secciones de documentos** con las definiciones del viernes. Sin tareas asignadas formalmente todavía.
- **[observation]** Olivier va a **agendar reunión** para destrabar las definiciones del **próximo sprint (el último)** antes de que vuelvan a bloquear.

## Routing

- **source/** ✅ · **ingestion/** ✅
- **Promoción / durables propuestos** (propose-and-wait, NO escritos): ver abajo.

## Contradicciones / tensiones

- **Refina, no contradice** la decisión [2026-06-01-documentos-dinamicos-html](../../decisions/2026-06-01-documentos-dinamicos-html.md): confirma explícitamente la dirección **HTML→PDF** (HTML como fuente, PDF como entrega al cliente por Flutter). Vale agregarlo como evidencia/nota a esa decisión.
- **Matiz vs. Daily 3/6:** los bloqueantes de infra que ahí eran "esperando a PERC" hoy tienen camino (Sandbox). Pero aparece un **riesgo de scope nuevo** (¿Quarks configura entornos a mano? no estaba en scope) que antes no estaba.

## Open question (PM judgment)

El riesgo de scope sobre los entornos: si PERC espera que **Quarks** configure los entornos (vs. replicar ellos con Terraform), eso es trabajo fuera del scope del contrato. Antes de pasar el punteo de servicios y avanzar, conviene **confirmar con Israel qué se acordó** y, si efectivamente cae sobre Quarks, decidir si se absorbe o se negocia. Es lo primero a clarificar en el canal de dev nuevo.
