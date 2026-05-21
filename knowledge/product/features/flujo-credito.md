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
| La Mantovana | Sistema externo de nómina | Coordinación operativa mensual |
| Cuenta recaudadora PERc | Fuente de fondos | Validación de saldo activa |
| Tech stack (Lambda / Java / TypeScript) | Decisión técnica | Pendiente — mes de discovery |
| Pipeline CI/CD | Infraestructura | Pendiente — mes de discovery |

## Timeline
- **Nov 2025:** Creación del documento (PRD v1.0)
- **Dic 2025 – Ene 2026:** Iteraciones de scope y definiciones
- **Feb – Abr 2026:** Ajustes de alcance y armado final del PRD (v2.0)
- **May 2026:** Setup del PM Brain. Inicio formal del proyecto (discovery técnico).
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
| **Arrepentido** | Devolución dentro de los 10 días hábiles |

(ingestion/meetings/2026-05-20-refinement-backlog-perc.md)

## Solicitud creation & expiration logic (definido 2026-05-19)

- La solicitud se crea en BD **solo cuando el usuario completa firma + TOTP** — no al navegar las opciones.
- **Expiración:** 1 hora sin completar firma + TOTP → estado `expirado`. Trigger: cron/Lambda (EventBridge Scheduler).
- **Cambio de template:** expira automáticamente todas las solicitudes `en curso` asociadas.
- A nivel BD: tabla `credits` con estados. A nivel API/UI: endpoints separados para solicitudes en proceso vs. préstamos otorgados.
- **Desembolso:** siempre a cuenta sueldo. Confirmado. El usuario puede tener múltiples wallets — la cuenta sueldo debe identificarse dentro de la lista.

(ingestion/meetings/2026-05-19-planning-refinement-perc.md)

## Open questions
- ¿Cuál es el tech stack definitivo? ¿Lambda, Java, TypeScript? (decisión de PERC + Quarks)
- ¿Cómo se valida la integración con Watson antes de comprometer estimaciones?
- ¿Qué define "apto para crédito" a nivel de segmento del usuario? (lógica de las 3 opciones preaprobadas)
- ¿Cuál es el proceso exacto del archivo de novedades para La Mantovana? (formato, canal, validación)
- ¿Los documentos HTML son dinámicos o estáticos? Si dinámicos, ¿cómo se mapean las variables? (Seba responde ~2026-05-27)
- ¿Se puede resolver el TOTP security gap sin breaking changes en la implementación existente? (Nico + Joy)
- Restricciones de archivo HTML: tamaño, XSS, sanitización. (Olivier → cyber)
- ¿Puede haber empleados persona jurídica (PJ)? Impacto en filtros de BO. (Olivier → Seba)
- Verificar que el evento Lambda HTTP trae JWT decodificado. (Isra / Nico)
- Identificar cuenta sueldo dentro de la lista de wallets del usuario vía `get account`. (Nico / Isra)

## Follow-up after launch
- Medir tasa de adopción en las primeras 4 semanas post-lanzamiento.
- Medir reducción de carga manual en el Backoffice (casos gestionados vs. baseline).
- Revisar el flujo de conciliación (doble check) con La Mantovana en el primer ciclo de cobro.
- Evaluar si el scope termina aquí o si hay contrato extendido con Quarks para V2/V3.
