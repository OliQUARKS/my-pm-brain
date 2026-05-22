# Ingestion — Kickoff Flujo Crédito PERC

- **Date:** 2026-04-20
- **Participants:** Olivier, Fefe, Israel, Nicolás, Juan Pablo Norverto, Juampi, José Salgado, Eugenio Valeiras, Stefano Giuliano (Tano), Ezequiel Manfredi, Sebastián Cárdenas
- **Source:** [../../source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)
- **Feature:** [flujo-credito](../../knowledge/product/features/flujo-credito.md)
- **Context:** Kickoff técnico real (pre-kickoff formal Quarks–PERC del 2026-05-20). Primera reunión conjunta de integración.

---

## Arquitectura de autenticación — Heimdal

**(observation)** Stack de autenticación y autorización de PERC:
- **Heimdal**: servicio central de auth. Verificación asimétrica via JWKS. Tokens JWT con permisos (no roles, están migrando).
- **SHQuelist**: Redis/similar para tokens quemados (logout forzado, etc.). Todos los servicios validan firma + SHQuelist.
- **OPA (Open Policy Agent)**: en migración para autorización. Bundle Rego. Primero para servicios Java y Watson (via proxy Envoy). Lambdas: todavía sin definición de cómo aplica OPA — posiblemente API Gateway filter.
- Para las lambdas de Quarks: se espera que no tengan que ocuparse de seguridad a nivel servicio — la gateway lo resuelve.

(stakeholder-verbal, José Salgado, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## TOTP = requerimiento regulatorio BCRA

**(observation)** Stefano Giuliano (Tano, Cybersecurity PERC) confirma explícitamente que el TOTP para operaciones sensibles es un requerimiento de compliance del BCRA, no solo una decisión de UX. "Para operaciones sensibles, como regla general también por cumplimiento regulatorio lo tenemos también para como requerimiento." El préstamo califica como operación sensible. → Refuerza la decisión de TOTP en la solicitud.

(stakeholder-verbal, Stefano Giuliano, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## Sherlock service + S3 para documentos firmados

**(observation)** PERC tiene un servicio llamado **Sherlock** (gestión de datos del cliente) que en este sprint está sacando feature para asociar documentos a cuentas via S3 presigned URL. Disponible para usar en flujo crédito para asociar los 5 PDFs firmados a la cuenta del empleado. José: "Sí, eso está disponible, lo pueden usar."

Nueva dependencia técnica para el flujo crédito.

(stakeholder-verbal, José Salgado, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## FIFO waitlist — scope futuro, no MVP

**(observation)** Marcos quiere una cola FIFO de solicitudes cuando la cuenta recaudadora se vacía: "dar préstamos hasta que se me acabe la plata, luego lista de espera". Juan Pablo: "lleguemos primero a acabar la plata [...] vamos al paso uno primero." Feature de waitlist explícitamente out of scope del MVP — se define cuando sea necesario.

(stakeholder-verbal, Sebastián Cárdenas + Juan Pablo Norverto, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## Tag mechanism — comenzar permisivo

**(observation)** Múltiples tags posibles por usuario (Mantovana + tier de crédito). No se impone validación técnica de colisión al inicio — se maneja operativamente. José: "yo no creo que necesitemos ser super restrictivos [...] podríamos hacer un camino inicial más eh iterativo, adaptativo". Juan Pablo: "lo dejaría como algo operativo y después lo complejizaría llegado al caso."

(stakeholder-verbal, José Salgado, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## Multi-tenant — MVP = solo PERC

**(assumption)** Seba preguntó si el sistema es escalable a B2B. Respuesta de Juan Pablo: escalable via tags, pero el MVP es para PERC únicamente. "Estamos haciendo un sistema de créditos preaprobados." Complejidad de multi-tenant está en la gestión de usuarios/empresas, no en el crédito en sí — fuera de scope actual.

(stakeholder-verbal, Sebastián Cárdenas + Juan Pablo Norverto, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## Watson es Angular — confirmado

**(observation)** Eugenio Valeiras confirma: "Angular." Stack frontend de Watson = Angular. Opciones para entrega del módulo de crédito: (a) compartir acceso a Watson + PR en el repo, (b) Quarks entrega como módulo/package instalable en Watson. Eze + Euge inclinados por compartir Watson; José propone librería instalable como alternativa si hay restricciones de seguridad. Resultado: pendiente de definición más detallada en reunión técnica.

(stakeholder-verbal, Eugenio Valeiras, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## Insomnia collection acordada

**(observation)** José propone preparar una colección Insomnia con todos los endpoints que Quarks va a usar (tag de cuenta, consulta de cuenta por CUIT/clientId, TED desde cuenta recaudadora). Juan Pablo: "Buenísimo." → Pendiente de entrega por PERC.

(stakeholder-verbal, José Salgado + Juan Pablo Norverto, 2026-04-20) — [source/meetings/2026-04-20-kickoff-flujo-credito.md](../../source/meetings/2026-04-20-kickoff-flujo-credito.md)

## Omitido (ya capturado en brain)

- Lambda + Angular stack → `decisions/2026-04-20-tech-stack.md`
- TOTP en solicitud → `flujo-credito.md § Risks`
- Mantovana bidirectional files → `flujo-credito.md § Open questions`
- Firma electrónica (no digital) → `flujo-credito.md`
- 5 documentos / Sábana = render-only → `decisions/2026-05-20-sabana-no-persiste.md`
- Cuenta recaudadora como fuente de fondos → `flujo-credito.md § Dependencies`

## Routing

- → `knowledge/product/features/flujo-credito.md` — agregar: Sherlock dependency, FIFO waitlist (future scope note), Insomnia pending
- → `stakeholders/stefano-giuliano.md` — touchpoint 2026-04-20 (last-touched ya coincide)
- → `stakeholders/eugenio-valeiras.md` — touchpoint 2026-04-20 (last-touched ya coincide)
