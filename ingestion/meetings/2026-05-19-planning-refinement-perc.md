# Ingestion — Planning and Refinement PERC

- **Date:** 2026-05-19
- **Participants:** Olivier (PM), Marcos Perez (Dev), Nicolás Paez (TL), Juan Ignacio Moyano (Dev), Giuliano Trincavelli (Dev), Israel Fernandez (TL) — equipo interno Quarks, sin Seba
- **Source:** [../../source/meetings/2026-05-19-planning-refinement-perc.md](../../source/meetings/2026-05-19-planning-refinement-perc.md)
- **Feature:** [flujo-credito](../../knowledge/product/features/flujo-credito.md)

---

## Decisiones técnicas

- **La solicitud se crea en BD solo cuando el usuario completa firma + TOTP.** Antes de ese momento el usuario puede navegar, explorar opciones y abandonar sin dejar registro. Evita data sucia en la tabla `credits`. (stakeholder-verbal, Nico + Isra, 2026-05-19)

- **Expiración de solicitud: 1 hora** sin completar firma + TOTP → expira. Mecanismo: cron/Lambda cleaner (EventBridge Scheduler o similar). El trigger es tiempo, no acción del usuario. (stakeholder-verbal, Nico + Isra, 2026-05-19)

- **Cambio de template expira solicitudes en curso.** Si el BO modifica un template, todas las solicitudes en estado `en curso` asociadas a ese template expiran automáticamente. (stakeholder-verbal, equipo, 2026-05-19)

- **Separación solicitudes vs. préstamos:** A nivel BD, todo en la tabla `credits` con estados. A nivel API y UI, dos endpoints separados: uno para solicitudes en proceso (en curso / pendiente), otro para préstamos otorgados. Evita "vómito de información" en el BO mezclando prospectos con préstamos reales. (stakeholder-verbal, Nico + Isra, 2026-05-19)

- **Tag del usuario viene del JWT decodificado** en el evento de Lambda HTTP (AWS API Gateway HTTP API). Isra ~99% seguro. Subtarea pendiente: verificar que el evento trae el JWT plano. (stakeholder-verbal, Isra, 2026-05-19)

- **Desembolso siempre a cuenta sueldo.** Confirmado. El descuento de cuotas lo hace La Mantovana, no el sistema de créditos. El endpoint `get account` (vía client ID) devuelve múltiples wallets — la cuenta sueldo debe identificarse dentro de esa lista. (stakeholder-verbal, Olivier, 2026-05-21; confirmado en reunión de diseño)

- **Herramienta de API testing: Insomnia.** El equipo usa Insomnia para inspeccionar endpoints del sistema existente (e.g. `get account`, `user account`). (observación, 2026-05-19)

## Backoffice — listado de solicitudes

Variables a mostrar en listado:
`monto`, `tasa`, `cuotas_restantes`, `cuotas_totales`, `tag`, `FT`, `capital_adeudado`, `estado`

Filtros requeridos: persona física / persona jurídica, cuotas totales, cliente, estado.

Exportación: XLSX con todas las variables del filtro activo.

Detalle: endpoint separado del listado — permite agregar más variables en el futuro sin romper el listado.

(stakeholder-verbal, Olivier + equipo, 2026-05-19)

## División de trabajo acordada

| Quién | Tarea |
|---|---|
| Marcos Perez | CRUD de solicitudes/créditos + improvements en proceso |
| Juan Pablo Moyano (Juampi/JP) | Vistas del simulador de préstamo (estilo Playground/Stitch, sin fancy design) |
| Nicolás Paez | Revisión de PR grande entrante |
| Israel Fernandez | Se retiró a reunión L2 |

## Retro rápida del sprint

- En general: bien.
- Mejora identificada: más comunicación entre devs — trabajan "por aparte" sin IDs compartidos.
- Acción de Olivier: arrancar dailies a partir del día siguiente (2026-05-20).

(stakeholder-verbal, equipo, 2026-05-19)

## Pendientes abiertos

| Ítem | Owner | Cuándo |
|---|---|---|
| ¿Puede haber empleados persona jurídica (PJ)? Impacto en filtros de BO | Olivier → Seba | Pendiente |
| Verificar que el evento Lambda HTTP trae JWT decodificado | Isra / Nico | Esta semana |
| Excel de cálculo de cuotas (bloqueante para lógica de cuotas) | Seba | Pendiente |
| Identificar cuenta sueldo dentro de la lista de wallets del usuario | Nico / Isra | Pendiente técnico |

## Routing

- → [flujo-credito.md](../../knowledge/product/features/flujo-credito.md) — agregar lógica de creación/expiración de solicitudes, separación solicitudes/préstamos, cuenta sueldo confirmada
- → [knowledge/org/tools.md](../../knowledge/org/tools.md) — agregar Insomnia
