# Ingestion: Daily - PERC (2026-06-03)

**Source:** [2026-06-03-daily-perc.md](../../source/meetings/2026-06-03-daily-perc.md)
**Kind:** meeting (daily standup)
**Participants:** Olivier (PM), dev Quarks (reporta), Nicolas (TL Quarks), Marcos (CEO PERC), Juan Ignacio Moyano, Giuliano, Israel, Pablo

## TL;DR

El Sprint 3 pasó de "bloqueado por definiciones de documentos" a **bloqueado en múltiples frentes**: ahora se suman bloqueantes de **arquitectura interna** (relación de tablas, tabla de cuotas) y de **infraestructura** (entorno dev/stage, bucket S3 + cadena de conexión). El dev está prácticamente parado salvo trabajo de estructura UI (secciones de documentos). El desbloqueo depende de Nico (definiciones internas) y de PERC (respuestas + infra).

## Observaciones (tagged)

- **[observation]** El dev reporta que "básicamente todas las task están medias bloqueadas". En el momento de la daily está "medio bloqueado".
- **[observation]** Bloqueante de arquitectura — **cambio de relación de tablas**: aún no está del todo definido (qué tablas, qué se guarda y qué no). Es una definición interna (Quarks/Nico).
- **[observation]** **PER-42 — integración de cuotas**: el dev la había encarado, Nico le pidió frenarla porque faltan definiciones. Bloqueada.
- **[observation]** La **visualización del préstamo concedido (vista de cuotas)** depende de definir primero la **tabla de cuotas** (PER-42). Olivier propuso adelantarla (la tenía pensada para "el fin que viene") ya que el dev está bloqueado, pero también depende de la misma definición.
- **[observation]** **PER-54 — firmas**: cómo encarar la implementación de las firmas. Nico está esperando "respuesta del otro lado" (PERC).
- **[observation]** **Firma digital — persistencia**: qué se guarda (fecha, IP, etc.), cómo y dónde. Para guardar esos datos se necesita el **entorno de dev**.
- **[observation]** **Infra S3**: les pasaron una collection de Insomnia para conectarse a S3, pero NO tienen bucket, NO tienen documentos, NO tienen cadena de conexión, NI entorno de stage para probar. Necesitan: bucket + cadena de conexión S3 + entorno de stage.
- **[observation]** Pendientes ya conocidos (documentos) siguen abiertos: tamaño de archivos, tipo de archivo, si hay que parsear, cuáles son dinámicos / cómo se completan.
- **[observation]** Lo único que el dev pudo avanzar: terminó y envió la **collection de Insomnia**. Va a seguir con la **estructura UI de las secciones de documentos** (listas, botones) — trabajo de andamiaje que no depende de las definiciones bloqueadas.
- **[observation]** No hay tareas creadas para la estructura de documentos; el dev las va a crear él mismo.
- **[observation]** No necesitan habilitaciones / ramas del otro lado por ahora.
- **[interpretation]** El cuello de botella se desplazó: ya no es solo "PERC nos debe las plantillas". Ahora hay deuda de definición **interna** (Nico) + deuda de **infraestructura** (PERC: S3/stage). El riesgo de slip del Sprint 3 subió.
- **[interpretation]** Olivier asume el rol de desbloqueador: "haré esas definiciones y les devuelvo la respuesta". Compromiso de PM de resolver el set de definiciones para que el dev arranque.

## Bloqueantes nuevos / actualizados (para los HTML de status y definiciones)

| # | Bloqueante | Tipo | Owner | Sprint |
|---|---|---|---|---|
| 1 | Relación de tablas (qué guardar / qué no) | Arquitectura interna | Nico + dev | S3 |
| 2 | PER-42 — Tabla de cuotas / integración de cuotas (frenada) | Arquitectura interna | Nico | S3→S4 |
| 3 | PER-54 — Implementación de firmas (cómo encararlas) | Definición (espera PERC) | Nico ↔ PERC | S3 |
| 4 | Firma digital: qué/cómo/dónde se persiste | Depende de entorno dev | Nico + PERC | S3 |
| 5 | Entorno dev/stage (para persistir firmas y probar) | Infraestructura | PERC | S3 |
| 6 | Infra S3: bucket + cadena de conexión + stage | Infraestructura | PERC | S3 |

## Routing

- **source/** ✅ `source/meetings/2026-06-03-daily-perc.md`
- **ingestion/** ✅ este archivo
- **HTMLs** ✅ `perc-flujo-credito-status.html` + `perc-definiciones-pendientes.html` actualizados (pedido explícito del PM)
- **Promoción a knowledge/**: ver propuesta abajo (propose-and-wait). Candidato: actualizar `knowledge/product/features/flujo-credito.md § dependencies/risks` con los bloqueantes de infra+arquitectura. Aún no escrito — espera confirmación.
- **Stakeholders**: candidatos a `Last touched` 2026-06-03 → Nico, Marcos. No escrito aún (espera confirmación, salvo last-touched que es auto-mantenido).

## Contradicciones / tensiones con evidencia previa

- Ninguna contradicción dura. **Matiz importante**: el relato previo (planning 2/6) enmarcaba el Sprint 3 como bloqueado principalmente por las **plantillas de documentos** (escalado al CEO). Esta daily muestra que, aunque se desbloqueen las plantillas, **el Sprint 3 seguiría bloqueado** por arquitectura interna (tablas/cuotas) e infra (S3/stage). El bloqueo es multifrente, no single-point.

## Open question (PM judgment)

¿La definición de arquitectura (relación de tablas + tabla de cuotas, PER-42/PER-54) la resuelve Nico internamente, o requiere algo de PERC? El dev dijo que PER-54 "está esperando respuesta del otro lado" — conviene confirmar con Nico qué parte es interna (Quarks decide) y qué parte está genuinamente bloqueada esperando a PERC, para no escalar a PERC algo que podemos resolver nosotros.
