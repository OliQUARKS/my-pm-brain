---
prd_path: /Users/olivierluce/Downloads/PRD - PERC - Flujo Crédito.md
prd_hash: 304d1224e2e0
reviewed_at: 2026-06-08
lentes: [estratega, cliente, datos, riesgo, stakeholder]
---

# Review — PRD Flujo Crédito v2.0 (PERC)

## Resumen ejecutivo

5 lentes corridos en paralelo. **12 gaps bloqueantes** y **9 contradicciones** con el brain. Tres patrones convergen entre lentes:

1. **El PRD trata como cerrado lo que el brain tiene abierto.** Tech stack, firma, segmentación, cancelación anticipada — todas decisiones que el equipo cree resueltas pero que viven como "pendientes" o "esperando PERC" en `decisions/`, fichas de stakeholders e ingestion reciente.

2. **El producto se diseña para 8.000 personas sin research, sin hipótesis tagged, sin métricas pobladas, y con una "medida de éxito" que el changelog del PRD declara haber agregado pero no aparece en ninguna parte.** Producto sin red epistémica.

3. **El "MANUAL" del PRD para arrepentimiento + cancelación + cobranza tras despido es ilegal frente a Disposición 954/2025 (fricción cero), peligroso frente a Art. 8 bis LDC (trato digno), y sin canal definido para el usuario.**

---

## Lentes

### Estratega

**Fortalezas:**
- El PRD reafirma la prioridad #1 de strategy.md: `"Transformar el proceso de solicitud, gestión y administración de crédito/préstamos en un servicio autónomo y digital para el Empleado de Grupo"` — alineado con "Llevar Flujo Crédito a producción (MVP)".
- Honra el compromiso de compliance no negociable (`knowledge/strategy.md` §priorities #3): `"el resultado es un único PDF con los 5 documentos embebidos para descarga"` — coherente con la firma unificada auditable.
- El bloque §6 enumera explícitamente los no-goals declarados en strategy.md (`"Que el usuario calcule su propio préstamo. Notificar por push. Solicitar cancelación parcial... Expansión a Terceros"`), preservando el perímetro.

**Gaps:**
- [bloqueante] `"Tecnología: Pendiente de definición (Lambda, Java, TypeScript)"` está obsoleto. El stack ya está decidido desde 2026-04-20 (Lambda + Angular). El PRD vigente induce a error a cualquier lector externo y debería actualizarse a §5 con cita a la decisión.
- [serio] `"Backoffice de Gestión (Probablemente en Watson)"` deja la integración Watson como incertidumbre — pero strategy.md §priorities #2 la marca como definición bloqueante para estimaciones. El PRD no compromete fecha ni plan de validación.
- [serio] El PRD afirma `"El sistema debe proyectarse como multitenant... separando los usuarios por organización (tenant)"` en §1 y luego en §6 declara `"Expansión a Terceros"` fuera de scope. Tensión interna: ¿se construye estructura multitenant en MVP (costo de diseño) o no?
- [serio] Plazo de desembolso ausente. La decisión `2026-06-02-plazo-desembolso-24h.md` fijó 24h como SLA comprometible al usuario; el PRD no menciona ningún plazo.
- [menor] §4 dice `"Cancelación Anticipada... puede incluir costos asociados o multas. MANUAL"` — pero la decisión `2026-06-02-penalidad-intereses-futuros.md` cerró la fórmula. El PRD sigue tratándolo como abierto.

**Contradicciones:**
- `"dispara la transferencia de fondos al empleado desde la cuenta recaudadora"` (§3.A) no es contradicción de destino — `decisions/2026-05-19-desembolso-cuenta-sueldo.md` fija el destino como cuenta sueldo del empleado; el PRD se refiere al origen. Compatible, pero deja el destino implícito. (Marcado como pregunta.)
- `"Tecnología: Pendiente de definición..."` (§5) contradice [`decisions/2026-04-20-tech-stack.md`](../decisions/2026-04-20-tech-stack.md): stack decidido Lambda + Angular con `(stakeholder-verbal, Nico + Isra + Eze + Euge, 2026-04-20)`.
- `"firma unificada... el resultado es un único PDF con los 5 documentos embebidos para descarga"` (§3.A) crea ambigüedad respecto a [`decisions/2026-05-20-sabana-no-persiste.md`](../decisions/2026-05-20-sabana-no-persiste.md): el PDF agregado (Sábana) es render-only para descarga; los 5 documentos se persisten por separado. El PRD no aclara esta distinción.

**Preguntas para el PM:**
- ¿Vas a actualizar el PRD a v2.1 con las 10 decisiones tomadas entre abril y junio, o el PRD se congela en v2.0?
- Multitenant en MVP: ¿se construye aislamiento por tenant en Sprint 1 aunque "Expansión a Terceros" sea no-goal?
- Integración Watson: ¿deadline para validarla, o se asume que el discovery del mes la cierra?
- ¿Querés registrar decisión separada formalizando "cuenta sueldo como destino, recaudadora como origen"?

---

### Cliente

**Fortalezas:**
- `"el proceso de aceptación utiliza una 'firma unificada' que, legalmente, dispara la firma de 5 documentos distintos. Para el usuario es un solo flujo"` — reduce fricción en un trámite típicamente burocrático.
- `"el empleado podrá autogestionar su solicitud, recibiendo una oferta calculada automáticamente"` — resuelve el pain point declarado de "Proceso actual 100% manual".
- `"Recupero por Nómina: descuento de cuotas vía liquidación de sueldo (Mantovana)"` — elimina acción mensual del usuario.

**Gaps:**
- **[bloqueante]** No hay evidencia de usuario en el brain para evaluar este PRD. `knowledge/users/insights.md` está vacío (solo template). `knowledge/users/segments.md` está vacío. `source/interviews/` no existe. Las personas en `personas.md` están marcadas como `Confidence: baja — derivadas de PRD + meetings, sin entrevistas de usuario directas`. **El producto se diseña para 8.000 empleados sin haber hablado con ninguno.**
- **[bloqueante]** `"3 opciones preaprobadas basadas en el segmento del usuario"` — no hay segmentación definida en el brain. `segments.md` línea 5: "PM-fillable. Populate from analytics + interview Batch A/D." ¿Qué segmentos? ¿Qué define a cada uno?
- **[serio]** Fricción no diseñada en `"firma unificada... 5 documentos distintos... un único PDF"`: el PRD no especifica si el usuario ve qué firma antes de firmar, ni si puede leer los 5 documentos individualmente. Consentimiento informado en riesgo.
- **[serio]** Las 4 casuísticas "MANUALES" (arrepentimiento, cancelación, despidos/mora/bloqueo) no definen el touchpoint del usuario: ¿a quién contacta? ¿WhatsApp, mail, formulario in-app?
- **[serio]** `"3 opciones preaprobadas"` sin que el usuario pueda calcular su propio préstamo (Out of scope §6). No hay evidencia en el brain de que esto sea aceptable. La asunción de comportamiento en `personas.md` ("no configura monto ni plazo libremente") proviene del propio PRD — razonamiento circular.

**Contradicciones:**
- `"3 opciones preaprobadas basadas en el segmento del usuario"` vs. [`source/adhoc/2026-03-06-whatsapp-grupo-perc.md`](../source/adhoc/2026-03-06-whatsapp-grupo-perc.md) línea 65 ("Consultar Segmentación: Hablar con Eugenio sobre la lógica de flagueo") y línea 79 — Sebastián: *"Perc no tiene informacion sobre prestamos, como se hacen, como se ven, cual es el flujo o como interactua con otras partes del sistema"*. El PRD da por resuelto algo que el cliente reconoció como abierto.
- PRD asume cálculo automático pero [`source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md`](../source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md) §1 (*"Cálculo de cuotas... nos faltan los detalles técnicos precisos"*) y [`source/adhoc/2026-05-22-whatsapp-pendientes-perc.md`](../source/adhoc/2026-05-22-whatsapp-pendientes-perc.md) línea 12 (*"Excel de cuotas: falta el cálculo correcto: IVA variable, seguro de vida, criterio de cuotas iguales"*) muestran que la fórmula no estaba cerrada al momento del PRD.

**Preguntas para el PM:**
- ¿Se hizo o se planea research con empleados de Grupo antes del lanzamiento, o el MVP se valida post-launch con datos de adopción?
- ¿Cuál es la segmentación concreta que define las 3 opciones, y dónde está documentada como decisión?
- En el caso MANUAL: ¿cuál es el canal de contacto declarado al usuario dentro de la app, y quién responde con qué SLA?
- ¿El usuario puede leer los 5 documentos *antes* de firmar, o solo *después* de descargar el PDF?

---

### Datos

**Fortalezas:**
- North-star metric candidata clara: "Tasa de adopción — préstamos aceptados / empleados habilitados" (`knowledge/strategy.md §North-star`).
- Universo poblacional concreto: "8,000 usuarios habilitados" — denominador falseable.
- El non-goal "Scoring en tiempo real" está documentado, coherente con "3 opciones preaprobadas".

**Gaps:**
- **[BLOQUEANTE]** No existe la "medida de éxito" que el changelog del PRD ("30/12/25") declara haber agregado. No aparece en el PRD ni en `knowledge/product/metrics.md` (todas las secciones AARRR vacías). Sin esa medida, "Aumentar la Adopción / Mejorar la Eficiencia / Garantizar Compliance" no son falseables.
- **[BLOQUEANTE]** `hypotheses/` contiene únicamente `INDEX.md` y `_SCHEMA.md` — **no hay un solo archivo de hipótesis poblado** para Flujo Crédito. La hipótesis central ("Si lanzamos crédito autogestionado, X% adoptará en Y meses con mora ≤ Z%") no está formalizada.
- **[serio]** `knowledge/product/metrics.md` vacío. La north-star de strategy.md dice "Current value: N/A (pre-producción)" y "Target TBD post-launch" — sin target, "aumentar adopción" no tiene umbral de fracaso.
- **[serio]** Métricas de cobranza/mora ausentes: tasa esperada de mora, % de empleados que se desvinculan durante préstamo activo, eficacia del descuento por nómina. Sin baseline, no se puede decidir si el producto es viable financieramente.
- **[serio]** Asunción de segmentación opaca. `"3 opciones preaprobadas basadas en el segmento"` sin explicar qué dato alimenta el segmento. ¿Antigüedad? ¿Salario? ¿Categoría laboral? Si hay un scoring offline embebido, contradice el non-goal explícito de "Scoring en tiempo real" — y tiene implicancias regulatorias (sesgo, transparencia).

**Contradicciones:**
- `"Garantizar el Compliance"` (objetivo del PRD) vs. strategy.md (P#2): pregunta BIND compliance abierta desde 2026-04-08 dentro de la tensión "Fricción de Seba". Compliance no puede ser un objetivo *garantizado* del MVP con una pregunta de compliance abierta hace 2 meses.
- §5 `"Fondeo desde cuenta recaudadora PERc"` como tech pendiente vs. strategy.md P#2 que lista "integración Watson sin validar, pipeline CI/CD no acordado" como bloqueantes — el fondeo no aparece en la lista de bloqueantes del brain.

**Preguntas para el PM:**
- ¿Dónde está la "medida de éxito" que el changelog declara haber agregado el 30/12/25?
- ¿Cuál es la hipótesis central de adopción y mora que estás dispuesto a refutar? Sin `hypotheses/flujo-credito.md` con H-V1 / H-B1 / H-O1 tagged, el producto se construye sin red epistémica.
- ¿Qué alimenta exactamente la segmentación? ¿Existe regla documentada, o es un cálculo que vive solo en el código de Mantovana/RRHH del Grupo?
- ¿Cuál es el target mensual de volumen de préstamos y la solvencia mínima de la cuenta recaudadora?

---

### Riesgo / Compliance

**Fortalezas:**
- El PRD reconoce la obligatoriedad del derecho de arrepentimiento de 10 días (`§4 "Por ley, el usuario tiene 10 días para arrepentirse sin costo"`) — el deber sustantivo no se discute, solo la implementación.
- La firma unificada genera un único PDF descargable con los 5 documentos embebidos — base mínima de audit trail para Art. 36 LDC si los documentos contienen el contenido legal exigido.
- `"Los cambios de tasa no son retroactivos; solo aplican a nuevos créditos"` — alineado con CCCN Art. 767 (prohibición de modificación unilateral).

**Gaps:**
1. **[BLOQUEANTE] Botón de Arrepentimiento MANUAL viola Disposición 954/2025.** *"Este flujo será MANUAL debido a la complejidad de revertir pagos y descuentos ya informados a la nómina"*. La Disp. 954/2025 exige **fricción cero**, sistema backend que procese solicitudes **no autenticadas**, SLA 24h con código de identificación, prohibición de "trámites adicionales". La "complejidad de revertir" es razón operativa, no excepción legal — Art. 1.116 CCCN enumera taxativamente y el crédito al consumo no figura. Exposición: hasta 2.100 CBT (>$3.168M ARS al valor abril 2026) + daños punitivos Art. 52 bis.
2. **[BLOQUEANTE] Botón de Baja ausente — préstamo es tracto sucesivo.** La Disp. 954/2025 § Botón de Baja aplica a contratos de tracto sucesivo (cuotas mensuales). El PRD no lo menciona. Si PERC comercializa solo por canales digitales, debe mantener atención humana ≥8 horas días hábiles.
3. **[BLOQUEANTE] Régimen legal de PERC no declarado — bloquea evaluación OPNFC + Com. "A" 8203 BCRA.** Con ~8.000 empleados habilitados, cartera casi seguro supera el umbral de $10M del régimen OPNFC. Inscripción BCRA, reporte mensual CENDEU, Responsable Seguridad de Datos, Fórmulas I-IV. Si OPNFC, aplica Com. "A" 8203 (refuerza Gaps 1 y 2).
4. **[serio] Art. 36 LDC — riesgo de nulidad si los 5 documentos no consignan TEA + CFT + amortización detallada.** El PRD enumera "5 documentos" pero no asegura inclusión verbatim de los 6 datos del Art. 36 bajo sanción de nulidad.
5. **[serio] Cobranza post-despido sin garantía Art. 8 bis LDC + Ley CABA 6171.** *"En caso de despido, se puede cobrar el saldo desde la liquidación final. MANUAL"* — no define canal post-desvinculación. Si se llama/escribe al ex-empleado, aplica Art. 8 bis + Ley 6171 (horarios prohibidos, documentación obligatoria, prohibición de contactar al empleador o terceros).
6. **[serio] Cesión de datos a Mantovana sin consentimiento documentado + base AAIP no declarada.** Envío manual mensual de CUIL/DNI + estados de deuda a Mantovana es cesión a tercero bajo Art. 11 Ley 25.326 — requiere consentimiento previo, libre, expreso e informado. PRD no declara: inscripción AAIP, cláusula de consentimiento, Responsable de Seguridad de Datos.

**Contradicciones:**
- PRD §4: *"Este flujo será MANUAL"* ↔ [`knowledge/compliance/consumidor/INDEX.md § Disposición 954/2025`](../knowledge/compliance/consumidor/INDEX.md): fricción cero, no autenticado, SLA 24h.
- PRD §4: ausencia de Botón de Baja ↔ [`knowledge/compliance/consumidor/INDEX.md`](../knowledge/compliance/consumidor/INDEX.md) § Botón de Baja para tracto sucesivo.
- PRD §3.B: PDF no garantiza TEA+CFT ↔ [`knowledge/compliance/credito/INDEX.md § Art. 36 LDC`](../knowledge/compliance/credito/INDEX.md).
- PRD silencio sobre OPNFC ↔ [`knowledge/compliance/credito/INDEX.md § Régimen OPNFC`](../knowledge/compliance/credito/INDEX.md): disparador casi seguro por volumen.
- Decisión [`decisions/2026-06-02-penalidad-intereses-futuros.md`](../decisions/2026-06-02-penalidad-intereses-futuros.md) ↔ [`knowledge/compliance/credito/INDEX.md § CCCN Art. 770 + § Régimen de precancelación BCRA`](../knowledge/compliance/credito/INDEX.md): la fórmula `Capital restante + (Int. futuros × % penalidad) + (Capital restante × % comisión) + IVA` puede leerse como anatocismo si "% sobre intereses futuros" no se justifica como comisión administrativa pura. Además, BCRA exige **gratuidad** tras 180 días o 1/4 del plazo (lo mayor) — la fórmula actual no condiciona a ese umbral.
- PRD §3.B-C (envío mensual a Mantovana con CUIL/DNI + deuda) ↔ [`knowledge/compliance/datos-personales/INDEX.md § Ley 25.326`](../knowledge/compliance/datos-personales/INDEX.md) Art. 11 + Art. 3.

**Preguntas para el PM:**
- ¿Cuál es el régimen legal declarado de PERC (banco, OPNFC inscripta, "anticipo de sueldo")? Definitorio para Com. "A" 8203, OPNFC, y la V multitenant.
- Los 5 documentos del PDF, ¿incluyen verbatim TEA, CFT, total intereses, amortización detallada, gastos/seguros (Art. 36 LDC)?
- ¿Hay cláusula de consentimiento del empleado a la cesión a Mantovana, y la base inscripta en AAIP?
- ¿La fórmula de cancelación (2026-06-02) tiene umbral 180d/1/4 plazo para gratuidad BCRA, y la % sobre intereses futuros está documentada como comisión administrativa (defenderlo del test Oliva + Art. 770)?

---

### Stakeholder

**Fortalezas:**
- Identifica explícitamente al cliente y al sistema BO: *"Watson es el sistema BO"* — alinea con el roster donde Manfredi (CTO PERC) y Valeiras (TL PERC) son owners técnicos del lado cliente.
- Nombra a Mantovana como proveedor de nómina — reconoce la dependencia externa que la Daily 6/8 y 6/3 todavía no tenían validada operativamente.
- Reconoce la frontera Backoffice ↔ usuario final, coherente con el rol operador del BO que Nico cuestionó el 6/8.

**Gaps:**
- **[bloqueante]** Patricio (Compliance PERC) ausente del PRD y **nunca tocado** (`Last touched: —`, [`stakeholders/patricio.md`](../stakeholders/patricio.md)). Es owner activo de dos definiciones críticas que el PRD da por resueltas: documentos HTML + firma. *"Stefano Giuliano informó que pasó las plantillas a compliance y está esperando resolución"* ([`ingestion/meetings/2026-06-08-daily-perc.md`](../ingestion/meetings/2026-06-08-daily-perc.md)).
- **[bloqueante]** Cybersec PERC ausente pese a open ask abierto: *"Definir restricciones de archivos HTML: tamaño máximo, política XSS, sanitización. (Olivier → Tano)"*. Tano stale 49 días, Ari 21 días. Ari además exigió *"el código debe quedar en repos de PERC (no en repos de Quarks)"* — restricción de propiedad no mencionada en el PRD.
- **[bloqueante]** *"Firma unificada de 5 documentos"* presentada como decisión, pero brain: *"Nico cree que 'por un tema legal van a necesitar algo un poco más estricto' que las puras iniciales. Depende de una definición de compliance de PERC"* ([`ingestion/meetings/2026-06-03-estructura-db-firma-entorno.md`](../ingestion/meetings/2026-06-03-estructura-db-firma-entorno.md)).
- **[serio]** Mantovana ausente como stakeholder con ficha. PRD asume formato + cadencia del envío día 20 sin constancia de confirmación.
- **[serio]** Conflicto de owners técnicos no resuelto. *"Tech stack pendiente"* + 2 CTOs (Norverto QA / Manfredi PERC) + 4 TLs. Ficha de Norverto prácticamente vacía. Manfredi cerró Lambda+Angular el 20/4. PRD trata el stack como abierto cuando un lado ya decidió.

**Contradicciones:**
- PRD "firma unificada decidida" vs. [`ingestion/meetings/2026-06-03-daily-perc.md`](../ingestion/meetings/2026-06-03-daily-perc.md): *"PER-54 — firmas: Nico está esperando 'respuesta del otro lado' (PERC)"*.
- PRD "Tech stack pendiente" vs. [`stakeholders/ezequiel-manfredi.md`](../stakeholders/ezequiel-manfredi.md): *"2026-04-20 — Confirmó Lambda + Angular junto con Nico, Isra, Euge, Jo y Tano"*.
- Open asks de Sebastián ignorados en el PRD: plazo desembolso 24h, documentos dinámicos/estáticos, empleados PJ, IVA cancelaciones, validación Watson ([`stakeholders/sebastian.md`](../stakeholders/sebastian.md)).
- PRD "Probablemente en Watson" vs. validación Watson listada en Open asks de Seba.
- Restricción "código en repos PERC, no Quarks" ([`stakeholders/ariel-gendelman.md`](../stakeholders/ariel-gendelman.md)) no mencionada en el PRD — decisión material ya tomada que afecta multitenant.

**Preguntas para el PM:**
- Patricio nunca tocado y bloquea Sprint 3 (plantillas). ¿Lo subimos a recurrente esta semana o seguimos path Seba/Stefano?
- Firma "por iniciales" no validada por compliance PERC y Nico cree que *"necesitan algo más estricto"*. ¿Bajamos firma de "decidida" a "pendiente Compliance PERC"?
- Mantovana: ¿quién es el contacto y existe confirmación escrita del formato/cadencia, o asunción del PM?
- Tech stack: ¿qué pieza concreta dejás como "pendiente" para que Norverto y Manfredi sepan exactamente sobre qué alinear?

---

## Síntesis

### Tensiones entre lentes

1. **Firma unificada** — 4 lentes convergen:
   - Estratega: ambigüedad PDF agregado vs. persistencia separada (decisión 2026-05-20-sabana-no-persiste).
   - Cliente: usuario no puede leer 5 docs antes de firmar (consentimiento informado).
   - Riesgo: los 5 docs deben tener TEA + CFT (Art. 36 LDC) bajo sanción de nulidad.
   - Stakeholder: Patricio (Compliance PERC) **nunca tocado**, owner activo de las plantillas.
   → **La firma es el cuello del problema. No avanzar sin sign-off de Patricio.**

2. **3 opciones preaprobadas por segmento** — doble confirmación de deuda epistémica:
   - Cliente: segmentación no documentada; Sebastián reconoció *"Perc no tiene información sobre préstamos"*.
   - Datos: segmentación opaca puede ocultar scoring offline → contradice non-goal explícito de strategy.md.
   → **La segmentación es decisión de negocio + decisión técnica + decisión regulatoria. No está en `decisions/`.**

3. **Tech stack pendiente** — Estratega + Stakeholder confirman:
   - El PRD §5 contradice `decisions/2026-04-20-tech-stack.md` (Lambda + Angular cerrado).
   - Manfredi (CTO PERC) ya alineó.
   → **Drift del PRD vs. brain. Actualizar PRD a v2.1.**

4. **Cancelación / arrepentimiento MANUAL** — Riesgo + Datos + Cliente:
   - Riesgo: BLOQUEANTE regulatorio (Disp. 954/2025).
   - Cliente: sin canal definido para el usuario.
   - Datos: sin métricas que monitoreen la frecuencia ni el costo operativo.
   → **El "MANUAL" del PRD acumula tres fallas distintas.**

5. **OPNFC + datos a Mantovana** — Riesgo + Stakeholder:
   - Riesgo: bloqueante regulatorio (inscripción + consentimiento + AAIP).
   - Stakeholder: Patricio (Compliance) nunca tocado, Mantovana sin ficha.
   → **Doble fricción: el régimen legal no está declarado Y el stakeholder que podría definirlo no fue consultado.**

6. **Medida de éxito + research** — Datos + Cliente:
   - Datos: la "medida de éxito" del changelog no existe en el brain.
   - Cliente: 8.000 empleados sin entrevistas, sin baseline de demanda.
   → **El MVP se diseña a ciegas.**

### Top-7 bloqueantes (orden por impacto + cantidad de lentes que lo identifican)

1. 🚨 **Botón de Arrepentimiento "MANUAL" viola Disp. 954/2025.** *Riesgo, Cliente, Datos.* Necesita rediseño a flujo digital con SLA 24h.
2. 🚨 **Patricio (Compliance PERC) nunca tocado** + es owner activo de plantillas que bloquean Sprint 3. *Stakeholder.* Agendar esta semana.
3. 🚨 **No hay hipótesis pobladas + no hay métricas + no hay research de usuario + "medida de éxito" declarada en changelog no existe.** *Datos, Cliente.* Crear `hypotheses/flujo-credito.md` + poblar `knowledge/product/metrics.md`.
4. 🚨 **Régimen legal de PERC no declarado** (banco / OPNFC / "anticipo de sueldo"). *Riesgo.* Bloquea evaluación de Com. A 8203 + OPNFC + Art. 36 LDC.
5. 🚨 **Botón de Baja completamente ausente** (préstamo = tracto sucesivo). *Riesgo.*
6. 🚨 **Cesión a Mantovana sin consentimiento Art. 11 LPDP + base AAIP no declarada.** *Riesgo, Stakeholder.*
7. 🚨 **3 decisiones que el PRD trata como cerradas están abiertas en el brain:** firma, tech stack, segmentación. *Estratega, Cliente, Datos, Stakeholder.*

### Qué falta antes de poder decidir

**Acciones de stakeholders:**
- Agendar reunión con **Patricio** (Compliance PERC) esta semana — bloquea firma + plantillas + régimen legal.
- Confirmar contacto y canal con **Mantovana** — formato + cadencia archivo día 20 + consentimiento cesión de datos.
- Tocar a **Tano y Ari** (Cybersec PERC) — open ask XSS/sanitización (Olivier → Tano) + restricción "código en repos PERC".
- Levantar las **Open asks pendientes con Sebastián** (PO): plazo desembolso, documentos dinámicos, empleados PJ, IVA cancelaciones, validación Watson.

**Documentación que crear:**
- `hypotheses/flujo-credito.md` con H-V1 (adopción), H-B1 (mora/viability), H-O1 (compliance BIND) — todas tagged con provenance.
- Poblar `knowledge/product/metrics.md` con la medida de éxito + target + umbral de fracaso.
- Documentar la **segmentación de las 3 opciones** como decisión (qué dato alimenta, qué regla, quién es el owner).
- Crear decisión formalizando **régimen legal de PERC** (banco / OPNFC / otro).
- Actualizar PRD a **v2.1** con las 10 decisiones tomadas entre abril y junio.

**Diseños regulatorios obligatorios:**
- Rediseñar **flujo de arrepentimiento como digital** (no manual), fricción cero, SLA 24h, código de identificación. Reversa de pagos puede ser asíncrona internamente, pero la solicitud no.
- Diseñar e implementar **Botón de Baja** (mismo requerimiento de fricción cero).
- Verificar que los 5 documentos firmados contengan **TEA + CFT + amortización detallada + gastos** (Art. 36 LDC).
- Diseñar flujo de **consentimiento explícito** para cesión a Mantovana.
- Inscribir bases de datos en **AAIP**.
- Definir **canal y SLA de cobranza post-despido** alineado con Art. 8 bis LDC + Ley CABA 6171 si aplica.
- Verificar **fórmula de penalidad** (2026-06-02) contra umbral 180d/1/4 plazo BCRA + test Oliva/Art. 770.
