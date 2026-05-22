# Ingestion — Sprint 1 Review PERC

- **Date:** 2026-05-18
- **Participants:** Olivier, Marcos Perez, Juan Pablo Norverto, Juan Ignacio Moyano, Nicolás, Israel, Federico, José Salgado, Sebastián Cárdenas, Ezequiel Manfredi (CTO PERC), Ariel Gendelman (Cyber PERC)
- **Source:** [../../source/meetings/2026-05-18-sprint1-review-perc.md](../../source/meetings/2026-05-18-sprint1-review-perc.md)
- **Feature:** [flujo-credito](../../knowledge/product/features/flujo-credito.md)

---

## Decisión técnica — LUID para IDs de BD

**(decision)** José (PERC) solicitó explícitamente usar LUID (Lexicographically Unique ID) en lugar de integers secuenciales o UUIDs planos. Razón: los enteros exponen el volumen de la BD; los UUIDs estándar no son ordenables y "traen grandísimos problemas en DB". Los LUID son ordenables como Mongo ObjectIDs (timestamp embebido), Postgres los soporta nativamente. Israel (Quarks TL) y Nico confirmaron el punto.

(stakeholder-verbal, José Salgado, 2026-05-18) — [source/meetings/2026-05-18-sprint1-review-perc.md](../../source/meetings/2026-05-18-sprint1-review-perc.md)

→ Decisión → `decisions/2026-05-18-luid-ids.md`

## Convención técnica — tasas como decimal 0–1

**(observation)** PERC usa decimales 0–1 para representar tasas porcentuales en BD (0.105 = 10.5%). Confirmado por José + Ariel + Seba ("sigamos con la misma lógica"). El front es responsable de la representación visual (con o sin %, separadores de miles por i18n). A nivel API, el dato llega como decimal puro.

(stakeholder-verbal, José Salgado, 2026-05-18) — [source/meetings/2026-05-18-sprint1-review-perc.md](../../source/meetings/2026-05-18-sprint1-review-perc.md)

## Convención técnica — fechas ISO 8601 con offset de timezone

**(observation)** PERC usa ISO 8601 con timezone offset (no UTC epoch). Para Argentina: offset -03. Formato: `YYYY-MM-DDTHH:mm:ss-03:00` (o equivalente con zz). Postgres: `timestamp with time zone`. Confirmado por José + Nico.

(stakeholder-verbal, José Salgado, 2026-05-18) — [source/meetings/2026-05-18-sprint1-review-perc.md](../../source/meetings/2026-05-18-sprint1-review-perc.md)

## Audit table con JSON diffs — validado

**(observation)** José cuestionó inicialmente el approach de guardar JSON diffs en la tabla de auditoría ("están guardando todo como si fuese Jason"). Luego lo validó explícitamente: para auditoría, un snapshot en una sola línea es correcto — mantener una estructura relacional con diff de campos sería muy costoso de mantener. Los IDs de la row anterior y nueva están presentes para trazabilidad. JWT en la tabla es provisional (pruebas), se reemplazará por user_id del token.

(stakeholder-verbal, José Salgado, 2026-05-18) — [source/meetings/2026-05-18-sprint1-review-perc.md](../../source/meetings/2026-05-18-sprint1-review-perc.md)

## Nuevo stakeholder — Ariel Gendelman (Ari)

**(observation)** Ariel Gendelman participa como representante de Cybersecurity/Seguridad PERC — "soy el único de mi equipo". Diferente de Stefano Giuliano (Tano), que también es cyber. Ari confirmó:
- El código queda en repos de PERC
- Estrategia de seguridad: scans automáticos (los que configura el Tano) + PR cruzado contra PERC
- Validó la convención de tasas 0–1

→ Nuevo stakeholder → `stakeholders/ariel-gendelman.md`

## Contenido de la demo (Sprint 1 — backend)

**(observation)** Alcance del sprint 1 entregado: CRUD de templates de préstamo (get con filtros/sort/paginado, create, update-as-new-row, delete lógico). Playground frontend para visualización (no adaptado a Watson). Template tiene: nombre, descripción, tag (máx. 3 por tag), tasas calculadas (TEM, TNA, CFT). Update = nueva row en BD para preservar histórico con usuarios que ya tomaron el crédito. PR de back listo para revisión; PR de front pendiente de repo asignado.

(observation, [source/meetings/2026-05-18-sprint1-review-perc.md](../../source/meetings/2026-05-18-sprint1-review-perc.md))

## Próximos pasos acordados

- Enviar PR a PERC para revisión (foco en arquitectura, no solo datos)
- Sprint 2: flujo de solicitud de préstamo (usuario ve templates por tag, crea solicitud; BO ve listado de solicitudes con filtros y exportación)

## Routing

- → `decisions/2026-05-18-luid-ids.md` — nueva decisión
- → `stakeholders/ariel-gendelman.md` — nuevo stakeholder
- → `stakeholders/INDEX.md` — agregar Ari, actualizar last-touched José + Juan Pablo Norverto
- → `knowledge/product/features/flujo-credito.md` — agregar convenciones técnicas (tasas 0-1, ISO 8601)
