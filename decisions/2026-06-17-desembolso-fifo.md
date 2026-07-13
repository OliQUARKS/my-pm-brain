# Decision: El desembolso procesa la cola de pendientes por fondos en FIFO; retry cada 5 min; cancela a las 24h corridas

## Status
decided

## Date
2026-06-17

## Context
El desembolso valida firma+TOTP, solicitud completa y fondos en la cuenta recaudadora. Cuando no hay fondos para todos los desembolsos en cola, había que decidir el orden de procesamiento: FIFO estricto (esperar fondos para el primero de la cola) vs. desembolsar el primero que sea pagable con el disponible ("primer monto pagable"). El refinamiento del 16/6 lo dejó como fork de negocio abierto.

## Options considered
1. **FIFO estricto** — el primero que entra es el primero que sale; si no alcanza para él, todos esperan.
2. **Primer monto pagable** — desembolsar el primero de la cola que entre en el disponible, salteando al que no entra.

## Decision
Opción 1 — **FIFO estricto**. Sin fondos, la solicitud queda PENDIENTE (no se rechaza) y se **reintenta automáticamente cada 5 min** (intervalo parametrizable por variable de entorno). Si ingresan fondos antes de **24 horas corridas**, desembolsa automático sin intervención. A las 24h corridas sin fondos, la solicitud se cancela. El desembolso va **siempre a cuenta sueldo** (el usuario no elige). Cada intento (exitoso o pendiente) queda en auditoría. El BO ve las solicitudes pendientes de fondos ordenadas por llegada, con "expira en X" por solicitud.

## Why
FIFO es la regla que el equipo y el PM vienen sosteniendo desde el refinement del 9/6; es la más simple de explicar y auditar, y evita la complejidad de reordenar la cola por monto disponible. El retry automático y la ventana de 24h corridas mantienen la experiencia sin intervención manual.

## Evidence
- Olivier definió FIFO como la lógica del sprint en el planning interno, con retry 5 min y cancelación a 24h corridas  [../ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../ingestion/meetings/2026-06-17-planning-sprint4-perc.md)
- FIFO ya figuraba como criterio en el refinement interno del 9/6 (FIFO-by-payable, polling 5 min, timeout 24h)  [../ingestion/meetings/2026-06-09-sprint4-refinement-perc.md](../ingestion/meetings/2026-06-09-sprint4-refinement-perc.md)
- Desembolso siempre a cuenta sueldo, ya decidido  [../decisions/2026-05-19-desembolso-cuenta-sueldo.md](../decisions/2026-05-19-desembolso-cuenta-sueldo.md)

## Explicitly NOT doing
- No implementar "primer monto pagable" (saltar al siguiente desembolso que entre en el disponible)  [../ingestion/meetings/2026-06-17-planning-sprint4-perc.md](../ingestion/meetings/2026-06-17-planning-sprint4-perc.md)

## What would reverse this
Seba/PERC confirma que el negocio prefiere "primer monto pagable" para no frenar la cola cuando el primer préstamo es grande, o el volumen de solicitudes pendientes hace que el FIFO estricto deje desembolsos grandes bloqueando la cola de forma inaceptable.

## Remaining ambiguities
- **Residual de confirmación de negocio:** FIFO se fijó en planning interno de Quarks; falta confirmación explícita de Seba de que el negocio quiere FIFO estricto (esperar fondos) y no el pagable. Mientras tanto se implementa FIFO.
- El endpoint de consulta de fondos de la recaudadora/CVU no existe aún (pedido a Seba el 17/6) — bloquea la validación.

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md`
- Stakeholders informed: `../stakeholders/sebastian.md`
