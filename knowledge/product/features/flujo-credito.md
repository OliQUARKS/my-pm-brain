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
- **Fricción con el cliente (PERC):** Sebastián tarda en dar definiciones. Bloquea el refinement del equipo. (stakeholder-verbal, Olivier, 2026-05-21)
- **Dependencia de La Mantovana:** el ciclo de cobro depende de un sistema externo de nómina. Coordinación mensual (~día 20) con riesgo de delay.
- **Fondeo insuficiente:** si la cuenta recaudadora de PERc no tiene fondos suficientes, la transacción queda en pendiente — no rechaza silenciosamente. (source/adhoc/2026-05-21-prd-flujo-credito.md §5)

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

## Open questions
- ¿Cuál es el tech stack definitivo? ¿Lambda, Java, TypeScript? (decisión de PERC + Quarks)
- ¿Cómo se valida la integración con Watson antes de comprometer estimaciones?
- ¿Qué define "apto para crédito" a nivel de segmento del usuario? (lógica de las 3 opciones preaprobadas)
- ¿Cuál es el proceso exacto del archivo de novedades para La Mantovana? (formato, canal, validación)

## Follow-up after launch
- Medir tasa de adopción en las primeras 4 semanas post-lanzamiento.
- Medir reducción de carga manual en el Backoffice (casos gestionados vs. baseline).
- Revisar el flujo de conciliación (doble check) con La Mantovana en el primer ciclo de cobro.
- Evaluar si el scope termina aquí o si hay contrato extendido con Quarks para V2/V3.
