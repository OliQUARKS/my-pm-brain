# PreReview PERC — 2026-06-26

**Source:** [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md)  
**Participants:** Olivier (PM), Marcos Pérez (dev back, Quarks), Juan Ignacio Moyano / Juampi (dev front, Quarks)  
**Context:** Pre-review historia por historia del estado del ciclo 6 (sprint 4), viernes antes de la review con el cliente PERC (lunes 2026-06-29)

---

## Estado por área al 2026-06-26

### Completo (ciclo 6)
- Template de préstamos ✅
- Diseño ✅
- Project management ✅
- Autenticación ✅
- Solicitud / consulta de préstamos ✅
- Ajuste de gestión de préstamos ✅

### En curso / bloqueado

#### Firma de documento (3 steps secuenciales)
- **Step 1 — Document types + files (4 PRs pendientes de aprobación por Jo):** los PRs fueron rechazados con comentarios generados por IA — en su mayoría inválidos. Marcos corrigió y reenvió. Arquitectura: tabla `types` (encapsula versiones, nombre del tipo ej. "acuerdos y condiciones") + tabla `files` (versiones del documento, una activa a la vez). Escalable sin cambios de arquitectura. (observation, Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **Step 2 — Versioning + documentos en sí:** bloqueado hasta que pasen los PRs del step 1.
- **Step 3 — Usuario firma + auditoría:** bloqueado hasta step 2.
- **TOTP / certificado firma:** sin definiciones de Nico (PERC) — Marcos lo hablé pero no obtuvo respuesta. Olivier mandó mensaje al grupo. Bloqueante para arrancar el step 3. (observation, Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **S3 (almacenamiento documentos):** no confirmado disponible. Marcos lo chequeará con Gonza (infra PERC). Sin S3 no hay upload real ni download (hardcodeable temporalmente). (observation, Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **Auditoría de documentos firmados:** bloqueada hasta step 3. Sección aparte en UI confirmado. (observation, Olivier + Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))

#### Descuento de cuotas
- **100% bloqueado por refactor "money precision"** (manejo de decimales / precisión monetaria). PR enviado a Jo, pendiente aprobación. Una vez aprobado, Marcos mete el refactor completo. Desbloquea historias 69, 70, 71 (importar liquidaciones, aplicar pagos a cuotas, carga manual de pagos). (observation, Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))

#### Cancelaciones
- Sin desarrollo — esperando el refactor de precisión (no bloqueante estricto, pero Marcos no quiere meter más código antes del refactor grande para no complicar el merge). (observation, Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))

---

## Definiciones tomadas en la reunión

- **No se crea botón "crear tipo de documento" en UI.** La arquitectura es escalable pero exponerlo ahora generaría scope creep ("nos van a pedir dos documentos"). El tipo se pre-crea. (decision, Olivier, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **UI de documentos:** tabla unificada con tipos + versiones (sortable por versión), sin botón de crear. Alta/baja via botones de activación/desactivación. (decision, Olivier + Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **Auditorías = sección aparte en UI.** (decision, Olivier, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **Reunión del lunes (2026-06-29) se mantiene.** No se usa la opción "branch paralela" para mostrar más. Decisión de Olivier: mejor que el problema explote ahora (cliente ya está atrasado en PRs) y usar las 2 semanas de slack disponibles para resolverlo. La presentación tendrá sección "bloqueos" explícita. (decision, Olivier, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **Qué se muestra el lunes:** parte de documentos (si pasan los PRs hoy/weekend). Si Jo no los aprueba hoy, Marcos mergea todos en una branch aparte y trabajan sobre esa para la demo. (observation, Marcos + Juampi, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))

---

## Bugs / issues técnicos detectados

- **GET documents devuelve 200 vacío desde el front:** el front no enviaba el auth token en el header → 401 seguido de 200 vacío. Juampi resolvió en la reunión: agregar token al header. (observation, Juampi, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **Payroll notice endpoint tira 500:** posiblemente relacionado con S3. Juampi lo pasa a Marcos por privado. (observation, Juampi, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- **Documentos no estaba en `development`** — Juampi estaba usando rama de `documents`, no `development`. Aclarado en reunión. (observation, Juampi, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))

---

## Fricción PR / proceso con PERC

- **Jo (reviewer PERC) rechazó 4 PRs con comentarios IA-generados** — todos con bloqueantes "major" por cosas triviales (ej. nombre de campo). Marcos los corrigió. Olivier preparado para escalar si persiste la mala leche. (observation, Marcos, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))
- Al momento de la reunión: ~20 PRs pendientes de desarrollo + los que dependen de aprobación de PERC. La cadencia de PR-review de PERC es el cuello de botella estructural del sprint.

---

## Postura comunicacional Olivier → PERC

- Política declarada: "el que avisa no traiciona". Preferencia por transparencia aun si duele.
- Olivier enviará resumen a Sebastián (Seda) post-reunión.
- Slide de "bloqueos" en la presentación del lunes = decisión confirmada.

---

## Notas de calidad del equipo

- Olivier confirmó satisfacción: lo implementado hasta ahora coincide exactamente con las historias — sin brecha de comunicación producto-desarrollo. (observation, Olivier, [source/meetings/2026-06-26-prereview-perc.md](../../source/meetings/2026-06-26-prereview-perc.md))

---

## Pendientes de seguimiento (post-reunión)

- [ ] Olivier: revisar PRs de Marcos en repo PERC y liberarlos
- [ ] Marcos: confirmar con Gonza si S3 está disponible
- [ ] Marcos: mandar mensaje a Nico (PERC) sobre definiciones de TOTP/firma (por el grupo)
- [ ] Olivier: enviar resumen a Sebastián
- [ ] Juampi: avanzar front de firma una vez que pasen PRs de documento types
- [ ] Marcos/Juampi: esperar respuesta de Jo a last PR; si no llega hoy, mergear en branch aparte para demo del lunes
