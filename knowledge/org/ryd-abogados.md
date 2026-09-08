# RyD Abogados, Cliente (discovery, automatización de pedidos de pago)

> Cliente nuevo de Quarks Alchemist, no relacionado con PERC/Flujo Crédito. Perfil vivo; se refina con cada interacción.

## Qué es / rol en el engagement
- (observation) Estudio jurídico que litiga en nombre de compañías de seguros (10 clientes; foco de esta discovery: **Provincia ART**). ~13,000 expedientes en trámite, equipo de 9 personas (7 dedicadas a carga de pedidos de pago). [ingestion/meetings/2026-09-03-ryd-abogados-discovery.md](../../ingestion/meetings/2026-09-03-ryd-abogados-discovery.md)
- (interpretation) El ask es puramente operativo: liberar tiempo de abogados de tareas administrativas repetitivas (pedido de pago post-sentencia/acuerdo), no un producto; es un engagement de automatización de proceso interno del estudio.

## El proceso bajo la lupa
- (observation) Sistema del estudio: **Lex Doctor** (rígido, sin API conocida); placeholders binarios (`@125`, `@64`...) autocompletan campos en documentos. Portal externo del cliente: **Provincia ART** (web, login manual). [ingestion/meetings/2026-09-03-ryd-abogados-discovery.md](../../ingestion/meetings/2026-09-03-ryd-abogados-discovery.md)
- (observation) Un expediente puede generar 6-7 pedidos de pago separados (distinto CBU/documentación por parte: abogado, actor, perito, tasa de justicia). Cuello de botella real = **pedir datos a terceros por mail** + **cargar en el portal**, no solo la carga. [ingestion/meetings/2026-09-03-ryd-abogados-discovery.md](../../ingestion/meetings/2026-09-03-ryd-abogados-discovery.md)

## Lex-Doctor, sistema técnico (capacidades verificadas en manuales 2026-09-04)

**Arquitectura y componentes:**
- (observation) Lex-Doctor 11 (v11.0.0.16, Caddel S.A., 2021) es un LJMS (Legal Justidic Management System) de arquitectura cliente/servidor con:
  - Tabla central "Procesos" (expedientes/casos) con campos customizables
  - Tabla "Personas" (abogados, clientes, peritos, etc.)
  - Tabla "Impulsos" (eventos/movimientos de proceso, candidato natural para "pedidos de pago")
  - Módulo "Caja" (contabilidad) + "Facturas" (facturación AFIP)
  - Modelos/templates de escritos con placeholders binarios (`@125`, `@64`)
  - Portal web para acceso remoto (miembros) y consulta de clientes
  - Email nativo, integraciones a workflows no claras en docs
  [ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md](../../ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md)

**Automatización nativa:**
- (observation) Placeholders binarios permiten rellenar templates pero no automatizar el flujo reverso (sistema → documento). No hay API documentada ni integraciones de terceros mencionadas en los manuales. [ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md](../../ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md)

**Gaps de integración:**
- No API REST/SOAP documentada
- No acceso SQL directo especificado
- Portal web para clientes (readonly) pero no bidireccional
- Email nativo pero integraciones a workflows no claras
- Sin webhooks o triggers nativos documentados
  [ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md](../../ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md)

**Implicaciones para automatización:**
- (interpretation) Opciones: RPA a nivel UI (frágil a cambios), acceso DB directo (requiere validación de arquitectura), email parsing + manual entry (mejora marginal). Provincia ART integration point aún no validado. [ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md](../../ingestion/adhoc/2026-09-04-lexdoctor-manuals-ryd.md)

## Encuadre de scope (definido 2026-09-03)
- (decision, en la llamada) Discovery enfocado en el área de Juan Verde (7 personas, carga de pedidos de pago); explícitamente no expandir a mediaciones/contestaciones de demanda todavía. Federico: "no caer en la macro ahora". [ingestion/meetings/2026-09-03-ryd-abogados-discovery.md](../../ingestion/meetings/2026-09-03-ryd-abogados-discovery.md)

## Contactos (RyD Abogados)
- [Hernán Capolupo](../../stakeholders/hernan-capolupo.md), socio (gestión operativa/facturación), champion de la automatización.
- [Juan Francisco Verde](../../stakeholders/juan-francisco-verde.md), socio, responsable del área legal (equipo de 7).

## Interacciones
- **2026-09-03** (Discovery call). Relevamiento completo del proceso de pedido de pago (Provincia ART). Sin propuesta ni scope formal todavía. [ingesta](../../ingestion/meetings/2026-09-03-ryd-abogados-discovery.md) · [source](../../source/meetings/2026-09-03-ryd-abogados-discovery.md)
- **2026-09-07** (Build-context + decisiones). Se formalizó el contexto interno del proyecto y la pre-propuesta ([briefings/2026-09-07-ryd-abogados-build-context.md](../../briefings/2026-09-07-ryd-abogados-build-context.md)). Se resolvió la protección de datos (prototipos con datos genéricos) y se decidió que la minuta no pide material operativo; eso pasa al discovery pago. [decisión datos](../../decisions/2026-09-07-ryd-prototipos-datos-genericos.md) · [decisión minuta](../../decisions/2026-09-07-ryd-minuta-sin-pedido-material.md)

## Open questions

**Sobre Lex-Doctor:**
- ¿Lex-Doctor tiene API no documentada (dev-only)?
- ¿Hay acceso SQL directo a la BD de Lex-Doctor?
- ¿Intentos previos de integración con Lex-Doctor (custom dev, Caddel SA support)?

**Sobre Provincia ART + automatización:**
- Existe un portal público de proveedores (`proveedores.artprovincia.com.ar`) con secciones de Facturación y Cotización, sin API documentada públicamente; no confirmado si el "pedido de pago a terceros" se carga ahí o en otra sección/sistema. [ingestion/adhoc/2026-09-07-provinciart-portal-recon.md](../../ingestion/adhoc/2026-09-07-provinciart-portal-recon.md)
- Volumen mensual real de pedidos de pago (para dimensionar ROI).
- ¿El patrón se repite igual en los otros 9 clientes del estudio?

**Resuelto:** protección de datos / uso de IA en prototipos → [decisión 2026-09-07](../../decisions/2026-09-07-ryd-prototipos-datos-genericos.md) (datos genéricos, no reales).

## Last updated
2026-09-07
