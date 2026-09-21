# Contexto de proyecto — Norton — 2026-09-16

> **Documento interno.** Nunca se entrega al cliente. La pre-propuesta cara-al-cliente (§ B) es lo único derivable de acá para mostrar afuera.

**Cliente:** Norton — comercializadora/distribuidora (probable rubro vino, no confirmado explícitamente), venta por 3 canales: directa, indirecta/distribución (off-trade), supermercado/mayorista.
**Tamaño:** sin confirmar (headcount de fuerza de ventas no relevado).
**Contactos:** Martín (Norton, fuerza de ventas, cargo sin confirmar), Tomás (Norton, rol sin confirmar), Fede Pinto (Norton, sistemas — mencionado, no presente en la llamada).
**Historial con Quarks:** primera reunión (discovery/briefing) 2026-09-16. Sin `/briefing-context` previo — este documento es la primera síntesis real del cliente.
**Fuentes:** [`ingestion/meetings/2026-09-16-norton-discovery.md`](../ingestion/meetings/2026-09-16-norton-discovery.md), [`source/meetings/2026-09-16-norton-discovery.md`](../source/meetings/2026-09-16-norton-discovery.md), [`briefings/2026-09-16-norton-minuta.md`](../briefings/2026-09-16-norton-minuta.md).

---

# A. Contexto del proyecto (interno)

## 1. Problemática (ampliada)

**Qué entendíamos antes.** Nada — no hubo prep previa; esta llamada es el primer contacto real registrado con Norton.

**Qué sabemos ahora.** El problema es la fuerza de ventas operando sin una capa que convierta datos ya existentes en decisiones de agenda:
1. No hay criterio sistemático de a qué clientes visitar y cuándo; la vieja lógica de "ficha por cliente" que ordenaba la ruta de venta se perdió.
2. Los datos existen (Power BI, armado por sistemas), pero nadie tiene tiempo dedicado a bajarlos a acción — ni jefes de área ni vendedores revisan sus carteras completas.
3. Consecuencia medible: venta concentrada al cierre de mes, oportunidades chicas perdidas (clientes sin compra hace 2 meses, faltantes de cobertura), y Martín haciendo medio día de análisis manual antes de cada reunión de ventas.
4. Intento previo de resolverlo con una herramienta (CRM en la nube, hace ~3 meses) abandonado por falta de gente dedicada a sostenerlo, no por falta de sistema — dato clave para no repetir el error.

## 2. Contexto ampliado

**Sistemas actuales:**
- **Arbalón** — sistema legado en uso hoy.
- **QAD** — ERP/CRM corporativo nuevo, kickoff recién hecho, implementación estimada en ~1 año (hasta julio 2027). Tiene módulos de CRM; app mobile sin confirmar.
- **Power BI** — tableros consistentes armados por el equipo de sistemas (ventas, volúmenes, compradores/no compradores, por marca/zona); descripto por el propio Martín como confiable ("hay info a cagarse acá... bastante consistente").
- **Login** — cuentas Microsoft para todos los vendedores.

**Números clave:**
- Ejemplo dado: "jefe de área con 4 vendedores" — no confirma headcount total.
- Histórico de ventas multi-año disponible en Power BI, pero el uso operativo real solo compara contra plan y año anterior (salvo cuentas estratégicas).
- Caso cuantificado del dolor: Martín armó a mano un reporte de cobertura de precios tras visitar 50 puntos de venta en un mes — sin ese esfuerzo manual, el gap no se hubiera detectado.

**Decisores y urgencia:** Martín parece dueño funcional del proceso comercial (presupuesto, KPIs, reuniones de venta); Tomás corrobora las decisiones de alcance. No hay decisor de mayor jerarquía identificado todavía, ni deadline — la llamada cerró en "Quarks vuelve con un plan de trabajo", sin fecha comprometida.

**Experiencia previa (perfil del cliente):** escéptico de herramientas "instaladas y listo" — referencia explícita a un proyecto road-to-market grande con la consultora PCG que generó rechazo ("me preocupa mucho menos la solución que me des que cómo la vamos a implementar"), más el CRM abandonado por falta de soporte operativo. Esto favorece la metodología de Quarks (capacitación + iteración, no solo instalación) como argumento de venta explícito.

**Usuarios:** internos — vendedores en campo, jefes de área, Martín. Sin indicios de usuarios externos (clientes de Norton) tocando el sistema.

## 3. Usuarios / roles / permisos

- **Vendedores** — ejecutan visitas; hoy sin agenda sistemática; en una capa futura cargarían evidencia de campo (fotos, precios).
- **Jefes de área** (ej. 4 vendedores por jefe) — supervisan performance; hoy sin tiempo para bajar el análisis de Power BI a acción.
- **Martín** — dueño funcional del proceso hoy, hace el análisis manual.
- **Tomás** — par o superior de Martín en decisiones de alcance.
- **Equipo de sistemas / Fede Pinto** — mantiene Power BI y lidera la implementación de QAD.

## Ejes de análisis obligatorios

- **Regulatorio:** sin eje relevado — no es un rubro con compliance pesado como PERC/RyD. N/A por ahora.
- **Legal:** sin restricciones particulares relevadas sobre uso de datos comerciales internos.
- **Tech stack (eje central acá):** Arbalón (legado) → migración a QAD (~1 año). Power BI como fuente de datos. **Ningún acceso técnico (API, export, DB) fue confirmado en la llamada** — es el hueco más grande para dimensionar factibilidad real.

## 6. Stakeholders — quién es cada uno

- **[Martín](../stakeholders/martin-norton.md)** — dueño funcional del dolor; prioriza implementabilidad y adopción por sobre sofisticación técnica. **(interpretación, ancla: `ingestion/meetings/2026-09-16-norton-discovery.md`)**
- **[Tomás](../stakeholders/tomas-norton.md)** — corrobora el foco inicial junto con Martín; cargo exacto sin confirmar.
- **Juan Pablo Norverto** (Quarks, interno) — lideró el encuadre metodológico de la llamada ("antes de pensar cómo resolver, qué queremos resolver"); queda a cargo de armar el plan de trabajo.
- **[Fede Pinto](../stakeholders/fede-pinto.md)** (Norton, sistemas — mencionado, no presente) — dueño del conocimiento sobre cobertura del módulo CRM de QAD. Clave para no duplicar alcance.

## 7. Contexto metodológico — cómo lo trabajaríamos

Usando como base [`briefings/_contexto-metodologico.md`](../briefings/_contexto-metodologico.md):

- **Grado de gestión:** sin definir — no se relevó si Norton tiene equipo de desarrollo propio más allá del área de sistemas que mantiene Power BI/QAD.
- **Dependencia crítica #1 — cobertura de QAD.** Si el módulo CRM de QAD cubre gran parte de lo pedido, construir algo intermedio ahora podría no justificarse. **Responsable:** Norton (Fede Pinto). **Riesgo si no se resuelve:** proponer algo que se descarta en ~1 año sin necesidad.
- **Dependencia crítica #2 — acceso técnico a Power BI/Arbalón.** No relevado (API vs. export manual vs. sin acceso). **Responsable:** Norton. **Riesgo:** sin esto, la capa predictiva no tiene con qué alimentarse.
- **Modelo de comunicación:** a definir — sin herramienta de gestión compartida identificada todavía.
- **Reviews y documentación:** sin precedente con este cliente.
- **Qué hay que cerrar sí o sí:** (1) cargo real de Martín/Tomás, (2) alcance de QAD vía Fede Pinto, (3) headcount de la fuerza de ventas, (4) acceso técnico a Power BI/Arbalón.

---

# B. Pre-propuesta (cara al cliente, liviana)

## 4. Propuesta

**Alcance — qué sí, qué no.**
- **Sí (foco validado por Martín/Tomás en la llamada):** agenda predictiva de visitas (a partir de cartera por vendedor: recencia de compra, stock estimado, comparación contra presupuesto) + reporte de eficiencia por vendedor (cumplimiento de visitas, conversión comprador/no comprador, frecuencia, surtido, margen), reemplazando el análisis manual de Martín.
- **No, en esta primera etapa:** fotos de punto de venta, inteligencia competitiva, captura geolocalizada de oportunidades — capas que el propio cliente pospuso explícitamente.
- **No cubierto todavía:** canal indirecto/distribuidores — Norton no tiene conexión con la red de sus distribuidores ni exclusividad por zona; queda fuera hasta que exista esa conectividad.

**Discovery.** 2-3 semanas — para confirmar acceso técnico a Power BI/Arbalón, cerrar con Fede Pinto qué cubre QAD, y levantar el detalle de KPIs/incentivos actuales para diseñar el scoring de eficiencia. No hay relevamiento previo del que partir, así que no se puede acortar.

**Prototipo — factible como flujo.** Mockup de la agenda semanal sugerida a un vendedor + vista de reporte de eficiencia para un jefe de área, con datos de ejemplo (no reales, hasta tener acceso a Power BI).

**Cómo lo trabajaríamos.** Extracto de § 7: grado de gestión sin definir, con dos dependencias críticas explícitas (cobertura QAD, acceso a Power BI), cada una con responsable y riesgo nombrado.

**¿Podemos ayudar? — factibilidad honesta.**
- **Alta** para la capa de agenda predictiva + reporte de eficiencia en sí — patrón ya resuelto por Quarks en otro proyecto (referencia propia en la llamada: "hemos hecho para visitadores médicos, es algo similar").
- **Media**, condicionada a acceso técnico real a Power BI/Arbalón — no confirmado.
- **Incierta** la integración con QAD — depende de una conversación pendiente con Fede Pinto.
- **Fuera de alcance por ahora:** conectividad con la red de distribuidores — problema estructural de Norton, ajeno al software.

---

# C. Salida operativa

## 5. Minuta y próximos pasos

**Ya corrida:** `/minutero` generó la minuta cara-al-cliente ([briefings/2026-09-16-norton-minuta.md](../briefings/2026-09-16-norton-minuta.md)), pendiente de validación por Martín/Tomás.

**Abiertos:**
- Cargo real de Martín y Tomás.
- Qué cubre el CRM de QAD (Fede Pinto).
- Headcount de la fuerza de ventas.
- Acceso técnico a Power BI/Arbalón.
- Detalle del intento de CRM previo (qué herramienta, qué falló puntualmente).

**Acciones recomendadas:**
- Esperar el material pedido en la minuta antes de correr `/propuestador` a fondo — sin acceso a datos ni confirmación de QAD, cualquier estimado de alcance/tiempo sería especulativo. (Nota: se corrió igual a pedido del PM, con las salvedades de factibilidad trasladadas a "a definir en discovery".)
- Si Fede Pinto confirma solapamiento fuerte con QAD, revisitar si vale la pena una solución intermedia o esperar la implementación de QAD.
