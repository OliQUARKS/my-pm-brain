# Personas

> Active personas with JTBD. Confidence: baja — derivadas de PRD + meetings, sin entrevistas
> de usuario directas. Revisar post-lanzamiento con datos de adopción reales.

---

## Empleado del Grupo PERC

- **Archetype:** Empleado en relación de dependencia que necesita liquidez puntual
- **Job-to-be-done:** Solicitar un préstamo de empleador sin depender de RRHH ni del
  Backoffice — ver opciones, firmar y recibir el desembolso en cuenta sueldo, todo en la app.
- **Behaviors:**
  - Accede por app mobile (no desktop-first)
  - Elige entre 3 opciones preaprobadas por segmento — no configura monto ni plazo libremente
  - El descuento de cuotas es automático vía nómina (La Mantovana) — no hay acción mensual
- **Pain points:**
  - Proceso actual 100% manual: depende del Backoffice para cada paso (interpretation, [source/adhoc/2026-05-21-prd-flujo-credito.md](../../source/adhoc/2026-05-21-prd-flujo-credito.md) §1)
  - Sin trazabilidad del estado del préstamo (interpretation, [source/adhoc/2026-05-21-prd-flujo-credito.md](../../source/adhoc/2026-05-21-prd-flujo-credito.md) §1)
- **Current alternatives:** Solicitud manual al Backoffice de PERC
- **Scale:** 8,000 usuarios habilitados en MVP (observation, [source/adhoc/2026-05-21-prd-flujo-credito.md](../../source/adhoc/2026-05-21-prd-flujo-credito.md))
- **Last revised:** 2026-05-22

---

## Operador de Backoffice (PERC)

- **Archetype:** Operador de RRHH/finanzas que gestiona préstamos de empleados
- **Job-to-be-done:** Configurar templates de préstamo, gestionar casos especiales y generar
  el archivo de novedades para La Mantovana — con trazabilidad y sin intervención manual en
  el flujo estándar.
- **Behaviors:**
  - Opera desde Watson BO (plataforma existente del cliente)
  - Gestiona estados del préstamo para casos fuera del flujo digital (mora, desvinculación)
  - Genera exportaciones XLSX del listado de solicitudes/préstamos con filtros activos
  - Activa/desactiva versiones de documentos HTML en la librería de templates
- **Pain points:**
  - Alta carga de casos manuales actualmente (interpretation, [source/adhoc/2026-05-21-prd-flujo-credito.md](../../source/adhoc/2026-05-21-prd-flujo-credito.md) §1)
  - Sin visibilidad centralizada del estado de los préstamos del grupo
- **Current alternatives:** Gestión manual via Watson BO sin módulo de préstamos
- **Scale:** No definido — grupo reducido de operadores
- **Last revised:** 2026-05-22
