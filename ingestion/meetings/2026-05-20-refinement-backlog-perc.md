# Ingestion — Refinement Backlog PERC

- **Date:** 2026-05-20
- **Participants:** Olivier (PM, Quarks), Nicolás (TL, Quarks), Sebastián Cárdenas (PO, PERC)
- **Source:** [../../source/meetings/2026-05-20-refinement-backlog-perc.md](../../source/meetings/2026-05-20-refinement-backlog-perc.md)
- **Feature:** [flujo-credito](../../knowledge/product/features/flujo-credito.md)

---

## Definiciones resueltas

- **Cálculo de cuotas:** Seba tiene el Excel. Pendiente de prolijarlo y enviarlo. (stakeholder-verbal, Seba, 2026-05-20)
- **Cancelación anticipada — sin congelación de fondos:** Para cancelar anticipadamente, el usuario debe tener el saldo total disponible. No se congela nada. (stakeholder-verbal, Seba, 2026-05-20)
- **Documento de cancelación anticipada:** No existe el documento legal todavía. Decisión: usar un PDF dummy/placeholder. La lógica de firma es idéntica a la del préstamo original. El CRUD de documentos puede manejar ambos tipos (préstamo + cancelación) en un solo módulo con tipificación. (stakeholder-verbal, Seba, 2026-05-20)
- **Mora vs. desvinculación:** La mora es 100% manual, sin flujo digital ni requerimientos de sistema adicionales. Lo relevante es la **desvinculación**: el sistema debe exponer la tabla de cuotas por persona (cuotas restantes + monto) para que el BO calcule el cobro del saldo desde la liquidación final. (stakeholder-verbal, Seba, 2026-05-20)
- **Firma = 5 documentos por separado:** El "documento Sábana" es solo un render para el usuario. Lo que se firma y almacena son los 5 documentos individualmente. El Sábana no persiste. (stakeholder-verbal, Seba + Nico, 2026-05-20)
- **Guardado de documentos firmados:** Si los documentos son dinámicos, se guardan **después** de validar el TOTP, no antes. Template → documento firmado, sin estado intermedio. (stakeholder-verbal, Nico, 2026-05-20)

## Estados del préstamo — definición final

| Estado | Descripción |
|---|---|
| **En curso** | Desde que se crea la solicitud hasta que se confirma la firma con TOTP |
| **Pendiente** | Desde la firma hasta el desembolso de fondos |
| **Otorgado** | Desde el desembolso hasta la cancelación total del préstamo |
| **Pagado** | Préstamo cancelado totalmente en tiempo y forma |
| **Cancelado anticipadamente** | Préstamo pagado por completo de forma anticipada |
| **Precancelado** | Cancelación antes del desembolso (nunca se otorgó) |
| **Arrepentido** | Devolución dentro de los 10 días hábiles |

(stakeholder-verbal, Seba + Nico, 2026-05-20)

## CRUD de documentos (sprint siguiente)

Contexto: Watson BO necesita una sección de gestión de documentos HTML que conforman el Sábana que firma el usuario.

**Decisiones:**
- Los documentos se cargan como HTML (no PDF) para ser dinámicos y combinables en el Sábana.
- El CRUD no modifica archivos existentes: se agrega una nueva versión y se selecciona cuál está **activa**.
- Es una **librería de documentos reutilizables** — compliance puede activar versiones anteriores sin re-subir.
- El orden de visualización de los 5 documentos en el Sábana se define a nivel template (no en el CRUD).
- Descarga masiva: patrón de background job + notificación por mail con link temporal (como Gmail). No descargar en bloque desde el navegador.
- Auditoría completa de cada acción (alta, baja, cambio de activo).

(stakeholder-verbal, Seba + Nico, 2026-05-20)

## Definiciones pendientes (open items)

| Ítem | Owner | Deadline |
|---|---|---|
| Casuística de desembolso de fondos | Seba | Pendiente de confirmación de su lado |
| Cálculo de cuotas — Excel prolijo | Seba | Lo antes posible |
| ¿Documentos dinámicos o estáticos? Si dinámicos, ¿cómo se mapean las variables a completar? | Seba | 1 semana (acordado en reunión) |
| Restricciones de archivo HTML con cyber (tamaño, XSS, sanitización) | Olivier → cyber (Ari / Tano) | Pendiente |
| TOTP security gap — revisar con Joy si se puede arreglar sin breaking changes | Nico | Pendiente |
| Repo del front — acceso para PRs | Seba → Job | Pendiente (Seba lo gestiona) |
| PRs pendientes de aprobación (2 ya hechos + potencialmente más) | Seba | Pendiente |

## Riesgo de seguridad identificado — TOTP bypass

**Observación:** El TOTP actual solo bloquea la UI (no se puede llegar a la pantalla sin pasarlo), pero el endpoint subyacente puede ser llamado directamente con un token de usuario válido, sin pasar por TOTP. Un actor con el token de usuario puede completar la transferencia sin autenticar. (stakeholder-verbal, Nico, 2026-05-20)

**Estado:** Pendiente de revisión con Joy. Si no se puede arreglar sin tocar la implementación existente, se usará el mecanismo actual como está.

## Routing

- → [flujo-credito.md § Risks](../../knowledge/product/features/flujo-credito.md) — agregar TOTP security gap y estados del préstamo
- → [stakeholders/sebastian.md](../../stakeholders/sebastian.md) — touchpoint, apellido Cárdenas, open asks actualizadas
