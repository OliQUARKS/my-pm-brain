# AMFAYS — La mutual (proveedor operativo del instrumento de crédito)

> Partner/proveedor operativo, **no competidor**. AMFAYS es la mutual que provee el instrumento financiero que subyace a Flujo Crédito. PERC/Quarks construyen el módulo que arma y autocompleta el documento; AMFAYS es el **proveedor del crédito**. Perfil vivo — se refina con cada interacción.

## Qué es / rol en el proyecto
- **(observation)** AMFAYS es una **mutual**. El "préstamo" de Flujo Crédito es técnicamente una **ayuda económica** contra **retención de haberes** por la empresa (Grupo La Mantovana), bajo un **código de descuento privado aprobado por INAES**. (source: [../../source/meetings/2026-07-17-call-amfays-documento-prestamo.md](../../source/meetings/2026-07-17-call-amfays-documento-prestamo.md))
- **(observation)** Provee el **documento/template** (legajo de formularios) que el empleado firma al tomar el crédito. Ese template es el que Quarks relevó campo por campo el 2026-07-17.
- **(interpretation)** Cadena de valor: **AMFAYS** (instrumento + fondeo) → **PERC** (billetera/PCP, onboarding, cuenta CVU, módulo de préstamos) → **La Mantovana** (empleador, retiene haberes vía RRHH). Quarks desarrolla el módulo del lado PERC.

## Cómo opera (relevante para el diseño)
- **(observation)** Estructura por **banca individuo / banca mayorista / fideicomiso financiero**. Los datos que exige dependen del tipo de préstamo y del organismo al que se envía el descuento.
- **(observation)** Tiene experiencia integrando **comercializadores** que generan préstamos desde su propio sistema y **migran los datos** al de AMFAYS (con asignación de nº SAEM). Modelo análogo al de PERC.
- **(observation) Nº SAEM/SAIN:** identificador **correlativo de 14 dígitos** que referencia la ayuda económica; **lo autogenera el sistema que origina** (PERC), no se suministra manualmente. Requerido por AMFAYS.
- **(observation) Segmentación por grupos (A/B/C):** AMFAYS permite segregar clientes y personalizar propuesta/tasa por grupo — **no scoring individual**. Consistente con el diseño del feature.
- **(observation) Firma:** AMFAYS usa **firma electrónica** (no digital-por-ley, no holográfica): un **conjunto de evidencias** (foto, foto del documento, prueba de vida por detección de movimiento, identificación facial) vía **su propio proveedor de identidad**. Tiene un **depositario de formularios** que unifica 8-9 formularios individuales en **un solo archivo firmado** — separar/mezclar formularios rompe la validez del legajo.
- **(observation) Compliance propio:** define qué campos son obligatorios/sensibles según su reglamento INAES. Resuelve dudas de datos sensibles / sujeto obligado / PEP por su lado.

## Securitización / fondeo (a futuro)
- **(observation)** El **fondeo vía fideicomiso financiero (securitización de carteras)** es una estrategia a futuro — "tenerlo preparado", se analiza después. (Nico Ortiz, 2026-07-17)
- **(interpretation)** Es la razón por la que AMFAYS pide hoy datos que hoy no parecen imprescindibles: **nº de legajo** y **CBU larga del banco pagador** (plan B de cobranza por cámara/COELSA si el empleado renuncia) — en securitización aparece un **riesgo empresa** distinto al riesgo actual.
- **(interpretation, lectura de Seba)** El objetivo de fondo de AMFAYS es **armar una cartera que después puedan asegurar, securitizar y vender como derivados** ("saben mucho de seguros"). Por eso empujan KYC/biométrico y datos pesados: **no les importa el drop-off** con tal de que los créditos que se concretan sean "exprimibles". Es la raíz de la tensión **UX simple vs. exigencia de datos/validación** (ej. re-pedir biométrico en el flujo del préstamo). (stakeholder-verbal, Sebastián Cárdenas, 2026-07-20)

## Cómo se proveen los datos (definido 2026-07-20 C12)
- **(observation)** Datos que PERC ya tiene (nombre/apellido/CUIT/cuenta) → salen del **core**: endpoint **accounts** + **Sherlock** (ex "Heimdal"), que tiene los datos de la persona asociados a cuenta/CUIL/nombre; hay que **abrir ese endpoint** a Quarks. Datos faltantes → **mockeados/cableados**, con la proveeduría real diferida del lado PERC (importador RRHH). Ver decisión [2026-07-20-captura-datos-amfays](../../decisions/2026-07-20-captura-datos-amfays.md).

## Contactos (AMFAYS)
- [Guido Panella](../../stakeholders/guido-panella.md) — dueño del relevamiento del documento; resuelve dudas con compliance AMFAYS.
- [Ignacio (agente comercial)](../../stakeholders/ignacio-amfays.md) — voz comercial de la mutual.

## Interacciones
- **2026-07-17** — Call Amfays <> PERc: relevamiento campo-por-campo del documento de préstamo. Definiciones de obligatoriedad + formato + firma. [ingesta](../../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md) · [source](../../source/meetings/2026-07-17-call-amfays-documento-prestamo.md)
- **2026-07-20** — SYNC PERC (C12, interno Quarks + Seba): se resolvió cómo proveer los datos del documento (accounts/Sherlock + mock/cableado + proveeduría diferida) y se registró la lectura estratégica de AMFAYS (securitización). [ingesta](../../ingestion/meetings/2026-07-20-sync-perc-c12.md)

## Linked
- Feature: [../product/features/flujo-credito.md](../product/features/flujo-credito.md) (§Documento / campos AMFAYS)
- Decisión relacionada: [../../decisions/2026-05-20-sabana-no-persiste.md](../../decisions/2026-05-20-sabana-no-persiste.md) (sábana + N documentos)

## Last updated
2026-07-20
