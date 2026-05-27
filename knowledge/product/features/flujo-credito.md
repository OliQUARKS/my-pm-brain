# flujo-credito — Flujo Crédito / Préstamos

## Meta
- Owner: Olivier Luce (PM, Quarks Alchemist)
- Status: building
- Priority: 1 (único feature activo en scope del contrato)
- Last updated: 2026-05-21

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
- **Fondeo insuficiente:** si la cuenta recaudadora de PERc no tiene fondos suficientes, la transacción queda en pendiente — no rechaza silenciosamente. (source/adhoc/2026-05-21-prd-flujo-credito.md §5)
- **TOTP security gap (identificado 2026-05-20):** el TOTP actual solo bloquea la UI — un actor con token de usuario válido puede llamar el endpoint de transferencia directamente sin pasar por TOTP. Pendiente de revisión con Joy (TL del equipo de integración). (ingestion/meetings/2026-05-20-refinement-backlog-perc.md)
- **Documentos dinámicos vs. estáticos (definición pendiente):** No está resuelto si los documentos HTML serán dinámicos (con variables del usuario) o estáticos. Si dinámicos, se necesita un parser + mapeo de variables. Seba da respuesta en ~1 semana. (ingestion/meetings/2026-05-20-refinement-backlog-perc.md)

## Dependencies
| Dependencia | Tipo | Estado |
|---|---|---|
| Watson (Backoffice) | Plataforma del cliente | Definición de integración pendiente |
| La Mantovana (Finnegans) | Sistema externo de nómina | Definición de reportes bidireccionales pendiente — deadline 2026-06-12 |
| Cuenta recaudadora PERc | Fuente de fondos | Validación de saldo activa |
| Tech stack: Lambda + Angular | Decisión técnica | ✅ Decidido 2026-04-20 — [decisions/2026-04-20-tech-stack.md](../../../decisions/2026-04-20-tech-stack.md) |
| Pipeline CI/CD | Infraestructura | Pendiente — mes de discovery |
| Sherlock (servicio PERC) | Asociación documentos firmados a cuenta via S3 presigned URL | Disponible — nuevo en sprint 2026-04-20. (stakeholder-verbal, José Salgado, 2026-04-20) |

## Timeline
- **Nov 2025:** Creación del documento (PRD v1.0)
- **Dic 2025 – Ene 2026:** Iteraciones de scope y definiciones
- **Feb – Abr 2026:** Ajustes de alcance y armado final del PRD (v2.0)
- **May 2026:** Setup del PM Brain. **Kickoff oficial Quarks–PERC: 2026-05-20.** (discovery técnico en curso)
- **27 Apr – 5 May 2026:** Setup de repos (monorepo structure confirmado). Backlog + Excalidraw flow compartido con equipo el 2026-05-06. [source/meetings/2026-05-06-repo-setup-backlog-share.md](../../../source/meetings/2026-05-06-repo-setup-backlog-share.md)
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

## Solicitud creation & expiration logic (definido 2026-05-19)

- La solicitud se crea en BD **solo cuando el usuario completa firma + TOTP** — no al navegar las opciones.
- **Expiración:** 1 hora sin completar firma + TOTP → estado `expirado`. Trigger: cron/Lambda (EventBridge Scheduler).
- **Cambio de template:** expira automáticamente todas las solicitudes `en curso` asociadas.
- A nivel BD: tabla `credits` con estados. A nivel API/UI: endpoints separados para solicitudes en proceso vs. préstamos otorgados.
- **Desembolso:** siempre a cuenta sueldo. Confirmado. El usuario puede tener múltiples wallets — la cuenta sueldo debe identificarse dentro de la lista.

(ingestion/meetings/2026-05-19-planning-refinement-perc.md)

## Open questions
- ~~**Metodología de cuotas:**~~ **Resuelta 2026-05-22 — ver §Cuota methodology.** ([source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md](../../../source/adhoc/2026-05-22-excel-calculo-prestamos-perc.md))
- ~~**Seguro de vida:**~~ **Resuelto 2026-05-22** — capitalizado al inicio en el monto prestado (`Capital × Seguro%`). Columna G = 0 porque no es cargo mensual. (stakeholder-verbal, Seba, [source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md](../../../source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md))
- ~~**Monto prestado vs. capital solicitado:**~~ **Resuelto 2026-05-22** — fórmula confirmada, ver §Cuota methodology. Capital solicitado = INPUT del BO en el template. (stakeholder-verbal, Olivier, 2026-05-22)
- **Cancelación anticipada — ¿precalculada en template o calculada on-demand?** Resuelto 2026-05-27: Seba confirma que **es una decisión de Quarks**. PERC no requiere específicamente una u otra. Olivier marcó como "good" — probablemente irá on-demand (más limpio). Nico (Tech Lead) debe validar en épica BO. (stakeholder-verbal, Seba, [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- **Plazo máximo de desembolso:** Verbal: 24-48h desde aprobación. Sin confirmación escrita. Abierto: ¿aplica igual en fines de semana y feriados? ([source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md](../../../source/adhoc/2026-05-13-email-definiciones-pendientes-perc.md)) — **Seba sugiere 24hs, decisión de Marcos. Pendiente confirmación.** (stakeholder-verbal, Seba, 2026-05-27 — Seba lo manda por mail) [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md)
- ¿Cómo se valida la integración con Watson antes de comprometer estimaciones?
- **Reporte de novedades (sistema → La Mantovana/Finnegans):** formato (CSV / Excel / otro), columnas requeridas, momento del mes. Permite a Finnegans saber a quién descontarle cuánto y cuándo. Deadline: 2026-06-12. (stakeholder-verbal, Olivier, 2026-05-22) — **Seba tenía reunión con Isis (La Mantovana) el 22/5, ella no asistió. Seba persiguiéndola.** (observation, [ingestion/adhoc/2026-05-22-whatsapp-pendientes-perc.md](../../../ingestion/adhoc/2026-05-22-whatsapp-pendientes-perc.md))
- **Reporte de confirmación (La Mantovana/Finnegans → sistema):** formato, campos, timing mensual. Permite al sistema registrar que el descuento fue realizado. Deadline: 2026-06-12. (stakeholder-verbal, Olivier, 2026-05-22) — **Actualización 2026-05-27:** Seba habló con Isis; quedaron en pasarle excels para subir cuotas + informe para descargar. Estructura bidireccional confirmada. [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md)
- **Penalidad sobre intereses futuros (cancelación anticipada)** — Seba está "consultando si se cobra algo de los interese futuros como penalidad o no" (2026-05-27). Esta es la pregunta abierta principal sobre cancelación anticipada: ¿cobrar % sobre intereses no devengados? Olivier sugiere "verlo con Fefe" (COO Quarks) antes de cerrar. **Aplica a la fórmula de cancelación anticipada:** Total = Capital restante + **(Int. futuros × % penalidad)** + (Capital × % comisión) + IVA. (observation, [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- **IVA en cancelaciones — ¿aplica siempre o solo si usuario no paga antes?** Excel lo marca configurable (flag B8 = 1). Olivier observa: "me suena raro porque si el usuario la paga bien hasta el final, porqué le cobro la cancelación?" Seba está rearmando la tabla del Excel (más simple). (observation, [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- ¿Los documentos HTML son dinámicos o estáticos? Si dinámicos, ¿cómo se mapean las variables? (Seba responde ~2026-05-27) — **Bloqueado en reunión tripartita 2026-05-27: Nicolas Ortiz, Patricio Ertola (Compliance PERC), ambos equipos. Seba tiene preocupación.** (stakeholder-verbal, Seba, [source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../source/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- ¿Se puede resolver el TOTP security gap sin breaking changes en la implementación existente? (Nico + Joy)
- Restricciones de archivo HTML: tamaño, XSS, sanitización. (Olivier → cyber)
- **Empleados PJ — confirmados, pero hay confusión.** Hay empleados PJ en Grupo PERC (stakeholder-verbal, Seba, 2026-05-22). Impacto en documentos y posiblemente front/back/BO. 2026-05-27: Olivier preguntó si "están discriminados en los datos" para identificarlos en BO. Seba preguntó si eso es "un dato que ustedes [Quarks] nos den". **Brecha de entendimiento:** ¿PERC proporciona field/flag PJ en data, o Quarks solicita form field BO?** Sin claridad, no se puede implementar BO. ([ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md](../../../ingestion/meetings/2026-05-27-whatsapp-preguntas-pendientes-perc.md))
- Verificar que el evento Lambda HTTP trae JWT decodificado. (Isra / Nico)
- Identificar cuenta sueldo dentro de la lista de wallets del usuario vía `get account`. (Nico / Isra)
- **Tab bar redesign:** Incorporar préstamos en la navegación requiere rediseño del tab bar (hoy: QR / perfil / home). ¿Cuál es el nuevo esquema de navegación? Pendiente. (observation, [ingestion/meetings/2026-05-20-diseno-flujo-credito.md](../../../ingestion/meetings/2026-05-20-diseno-flujo-credito.md))
- **Compliance: ¿avisar que la operación va por BIND?** ¿Obligatorio informar al usuario que la operación se procesa a través del BIND (o equivalente)? ¿En qué paso/s? Pendiente respuesta de Seba desde 2026-04-08. (observation, [ingestion/adhoc/2026-03-06-whatsapp-grupo-perc.md](../../../ingestion/adhoc/2026-03-06-whatsapp-grupo-perc.md))

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
