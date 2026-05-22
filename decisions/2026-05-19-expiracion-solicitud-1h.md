# Decision: Las solicitudes en curso expiran a 1 hora vía EventBridge Scheduler

## Status
decided

## Date
2026-05-19

## Context
El sistema crea la solicitud en BD solo al completar firma + TOTP. Antes de ese momento el usuario navega opciones sin compromiso. Si abandona el flujo, el sistema necesita definir: (1) si hay un timeout para ese estado intermedio y (2) cuál es el mecanismo técnico de expiración.

## Options considered
1. Sin expiración — el estado `en curso` permanece hasta que el usuario lo abandona o completa
2. Expiración vía polling desde el cliente
3. Expiración vía cron/Lambda con EventBridge Scheduler (serverless, 1h)
4. Expiración vía DB trigger

## Decision
Opción 3 — EventBridge Scheduler, timeout de 1 hora.

## Why
1 hora es suficiente para completar el flujo de firma sin que la sesión del usuario expire antes. EventBridge Scheduler es serverless y se integra de forma nativa con Lambda (tech stack acordado). Los DB triggers acoplan la lógica de expiración al modelo de datos. El polling desde el cliente requiere state management adicional en el front.

## Evidence
- Nico confirmó el mecanismo EventBridge + timeout de 1h en planning interno  `[ingestion/meetings/2026-05-19-planning-refinement-perc.md](../ingestion/meetings/2026-05-19-planning-refinement-perc.md)`
- Consistente con la arquitectura Lambda acordada  `[decisions/2026-04-20-tech-stack.md](./2026-04-20-tech-stack.md)`

## Explicitly NOT doing
- No dejar solicitudes `en curso` sin mecanismo de expiración  `(stakeholder-verbal, Nico, 2026-05-19)`
- No usar polling desde el cliente para gestionar la expiración  `(stakeholder-verbal, Nico, 2026-05-19)`

## What would reverse this
(a) PERC exige por escrito un tiempo de expiración diferente por compliance o UX (ej. 30min o 2h). (b) El pipeline CI/CD confirma que EventBridge Scheduler no es gestionable desde la infraestructura PERC.

## Remaining ambiguities
- Un cambio de template activa la expiración de todas las solicitudes `en curso` del usuario — edge case a validar en implementación.
- El tiempo de 1h es configurable; pendiente confirmar que no hay restricción de compliance que lo limite.

## Linked
- Strategy: `../knowledge/strategy.md` § 1–2 quarter priorities
- Decisions linked: `./2026-05-19-solicitud-post-firma-totp.md`
- Stakeholders: `../stakeholders/nicolas.md`, `../stakeholders/israel-fernandez.md`
