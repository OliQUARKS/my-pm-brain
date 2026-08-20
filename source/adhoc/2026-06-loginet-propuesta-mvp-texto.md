# Fuente verbatim — Propuesta comercial Loginet MVP (junio 2026)

> **Tipo:** adhoc — documento comercial ya redactado (output de `propuestador` o equivalente, previo al rediseño de Fase 0 documentado en [`ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md`](../../ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md)).
> **Archivo original:** `Copia para presupuestador _ Loginet_MVP.txt` (aportado por el PM el 2026-08-19).
> **Fecha del documento:** junio 2026 (según portada, "LOGINET / Junio 2026").
> **Preservado verbatim — no editar.** La síntesis y el routing viven en `ingestion/`.

---

Propuesta de consultoría y desarrollo
Automatizaciones + Backoffice + Transformación operativa
LOGINET
Junio 2026
1

EL DESAFÍO
El proceso actual genera riesgos operativos, dependencia de terceros y altos costos
mail_outline
Ingreso manual de declaraciones
Excel, PDF, email y Google Docs → portales de navieras. Alto riesgo de errores en temperatura, peso, contenedor y sellos.
warning
BOT de Extract en Khai con fallas
Dependencia de un proveedor externo (Extract) en el ERP/TMS actual (Khai) que presenta cargas fallidas recurrentes de información.
security
Falta de control y propiedad de datos
Fuerte dependencia de sistemas y proveedores de terceros. Sin control total sobre la data ni la lógica de negocio.
2

LA SOLUCIÓN
rocket_launch
Alcance del MVP
Lee automáticamente las declaraciones enviadas por email por los exportadores
Extrae, normaliza y valida la información contra reglas de negocio predefinidas
Guarda todo en una base de datos propia, segura y normalizada
Permite revisión humana fácil antes de enviar a la naviera
Integra con la API de Maersk para enviar la Shipping Instruction
Valida el Draft Bill of Lading contra lo enviado y actualiza la base de datos
MVP de integración a una naviera, validación de BLs y bases de datos propia.
Además, como parte de la propuesta:
search
Discovery sobre las cargas fallidas del BOT de Extract en Khai + consultoría y propuesta de solución.
architecture
Discovery profundo + propuesta de arquitectura escalable y autónoma para comenzar a reemplazar Khai y adquirir capacidades propias, desacoplando datos y lógica de negocio de tercero.
3

ARQUITECTURA
Flujo completo del MVP
Email del Exportador
Ingesta inicial de documentos
Extracción y Normalización
PDF, Excel, Email a Esquema de base de datos único
Validación y Revisión
Reglas de negocio + Humano
Integración Maersk
Envío de Shipping Instruction
Cierre y Auditoría
Validación Draft B/L + Log
El sistema extrae información de cualquier formato (PDF, Excel, email), la normaliza, valida contra reglas de negocio, permite aprobación humana y envía la Shipping Instruction a Maersk. Luego valida el Draft B/L contra lo enviado.
Toda la información queda registrada en una base de datos propia de Loginet, con trazabilidad completa, auditoría y la escalabilidad de construir cualquier consulta automatizada y tableros de visualización.
4

mail
Ingestión & Normalización
Extracción automática desde email + normalización a schema unificado.
Cierre & Auditoría
Validación Draft B/L vs SI y trazabilidad completa de cada envío.
fact_check
Integración Maersk
Conexión API para envío de Shipping Instruction.
api
Interfaz de Revisión
Dashboard para aprobación humana obligatoria previa al envío.
monitor
Base de Datos Segura
Estructura normalizada actuando como única fuente de verdad.
storage
rule
Motor de Validación
Validación de reglas de negocio (temperatura, pesos, campos obligatorios, etc.).
Entregables concretos en 14 semanas
ALCANCE DEL MVP
5

CRONOGRAMA
14 semanas de trabajo estructurado
Sem 1-8
Full Discovery + Arquitectura + Automatización + Dashboard de Revisión
Esquema de base de datos normalizado • Ingestión • Extracción • Validación • Dashboard de revisión humana
Sem 8-11
Integración Maersk - Testing
Integración con API de Maersk • Flujo de aprobación humana • Tracking de status • Actualización de base de datos
Sem 11-14
Validaciones y siguientes pasos
Módulo de validación de Draft B/L • Auditoría y plan de transformación (Extract/Khai) • Documentación •
6

Impacto esperado en la operación de Loginet
BENEFICIOS
task_alt
Reducción drástica de errores
Eliminación del ingreso manual de datos críticos (temperatura, peso, sellos, contenedores).
timer
Ahorro significativo de tiempo
Automatización del proceso que actualmente consume horas de trabajo operativo por envío.
layers
Trazabilidad completa
Auditoría de cada paso: quién aprobó, qué se envió, qué respondió la naviera.
security
Control total de la data
Base de datos propia. Lógica de negocio en sistemas de Loginet (post-discovery de Khai).
trending_up
Base para escalar
Arquitectura lista para agregar más navieras y automatización completa en el futuro.
7

EQUIPO & INVERSIÓN
Equipo propuesto para el MVP
assignment_ind
1 Project Manager
Gestión del proyecto, coordinación con Loginet y control de entregables
Part Time
terminal
1 Tech Lead
Diseño de arquitectura, revisión técnica y supervisión de desarrollo
Part Time
groups
2 Developers
Desarrollo del MVP, integración con APIs y construcción del dashboard
Part Time
INVERSIÓN TOTAL
USD xxxx + iva
25% Adelanto + 3 pagos de xxxx USD
Tipo de cambio vendedor del Banco Nación al día anterior de la emisión de cada factura.
8

PRÓXIMOS PASOS
Para iniciar el proyecto
PASO 1
Confirmación formal para dar inicio al proyecto.
PASO 2
Kick-off de proyecto
Armado de equipo - introducciones - definiciones del roadmap
PASO 3
POC antes de desarrollar
Evaluación de una POC para descubrir definiciones faltantes / erróneas. Refinamiento del roadmap
Pago inicial del 25%
9

cloud_queue
Costos de infraestructura
El presupuesto no incluye costos de servidores, nube, tokens ni servicios que no sean los provistos por Quarks
ads_click
Alcance de la propuesta
Los tiempos son estimaciones en base a la información relevada. Las definiciones de Loginet pueden variar, o el discovery puede identificar desviaciones significativas del tiempo sobre los entregables.
palette
Diseño gráfico
El presupuesto no incluye branding ni diseño gráfico. La UI definida a criterio de Quarks
storage
Calidad de datos
El éxito de la extracción automática depende de que los formatos de los archivos (PDF/Excel) mantengan una estructura consistente. Cambios drásticos en los formatos de terceros pueden requerir ajustes no contemplados en este presupuesto.
CONSIDERACIONES
Para el éxito del proyecto
10

Transformamos tu capacidades para que puedas escalar
11
