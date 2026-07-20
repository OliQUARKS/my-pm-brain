# Decision: Los datos del documento AMFAYS se resuelven por origen — existentes vía accounts/Sherlock; faltantes mockeados/cableados con proveeduría real diferida del lado PERC

## Status
decided

## Date
2026-07-20

## Context
El relevamiento del documento AMFAYS (2026-07-17) reveló ~20 campos a completar, de los cuales PERC/Quarks solo tiene ~5 disponibles hoy; el resto requiere integración o generación (nº SAEM, sueldo neto, domicilio laboral, legajo, antecedentes laborales). El fork: ¿se captura en el onboarding, en el taggeo del Back Office, o se difiere? Sin una definición, el documento AMFAYS bloquea la entrega del MVP (Marcos lo estima en "meses").

## Options considered
1. Capturar todos los campos en el **onboarding** de la billetera — descartada (Norverto: "si nos metemos en el onboarding, esto no termina nunca").
2. Cargar los campos en el **taggeo del Back Office** — descartada por ahora (Fefe: "técnicamente es un caos").
3. **Partir por origen + mockear/cablear lo faltante y diferir la proveeduría real al lado PERC** — elegida.

## Decision
Los datos del documento se resuelven según su origen:
- **Datos que PERC ya tiene** (nombre, apellido, CUIT/CUIL, cuenta): se sirven del **core** — endpoint de **accounts** + **abrir el endpoint de Sherlock** (ex "Heimdal"), que tiene los datos de la persona asociados a cuenta/CUIL/nombre. Seba mapea lo existente y se lo pasa a Nico.
- **Datos que PERC NO tiene** (antecedentes laborales, sueldo neto, domicilio laboral, legajo; actividad/profesión = hardcode "empleado"): se **mockean/cablean** ahora (MOCK sobre endpoint existente, o wrapper/cáscara para uno nuevo), y **queda del lado de PERC la responsabilidad de construir la proveeduría real** (importador desde RRHH). El documento se **desacopla del MVP**.

## Why
Permite desbloquear el desarrollo y el UAT sin esperar a que existan datos que hoy nadie tiene, dejando "todo cableado". La responsabilidad de conseguir los datos reales queda donde corresponde (PERC/RRHH), y el MVP no queda rehén de un documento que "va a durar meses". No es apto para producción tal cual (el mock siempre devuelve lo mismo), pero sí para avanzar el flujo end-to-end.

## Evidence
- Seba: los datos existentes salen del core (Sherlock/accounts); los faltantes "yo personalmente los moquearía desde el lado de PERC… queda en nosotros la responsabilidad de armar la carga de estos datos"  [ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)
- Nico Paez: técnicamente se declara un MOCK — se agrega data mockeada a un endpoint existente o se hace un wrapper para uno nuevo; deja todo cableado pero no pasa a producción así  [ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)
- Nico Paez: conviene arrancar el refactor de lambdas ya porque "va a pasar de todos modos, no depende de esos datos [AMFAYS]" — el trabajo de datos queda desacoplado  [ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)
- Marcos (approach técnico, daily): levantar un HTML pelado con variables + lógica de firma y entregar la función; AMFAYS/PERC adaptan el documento después  [ingestion/meetings/2026-07-20-daily-perc.md](../ingestion/meetings/2026-07-20-daily-perc.md)
- Legajo disponible en el endpoint (= nº de usuario), confirmado por Seba  [ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md](../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md)

## Explicitly NOT doing
- NO se captura el set completo de campos AMFAYS en el onboarding de la billetera  (stakeholder-verbal, Juan Pablo Norverto, 2026-07-20)
- NO se construye la carga de datos en el taggeo del Back Office en esta etapa  (stakeholder-verbal, Federico Fernandez, 2026-07-20)
- NO se difiere la entrega del MVP a que exista la proveeduría real de los datos AMFAYS — se cablea con mocks y se sigue  [ingestion/meetings/2026-07-20-sync-perc-c12.md](../ingestion/meetings/2026-07-20-sync-perc-c12.md)

## What would reverse this
Si AMFAYS/compliance exige que los datos reales estén presentes para validar el documento antes del go-live (no acepta el flujo con mocks), o si PERC no logra construir la proveeduría real (importador RRHH) a tiempo → habría que integrar la captura en el flujo productivo antes de entregar, reacoplando el documento al MVP. Señal observable: definición de AMFAYS sobre si acepta el flujo cableado, o fecha de RRHH para el importador.

## Remaining ambiguities
- **Nº SAEM — unicidad:** se generaría por algoritmo/random, pero eso no garantiza que no exista previamente (colisión). Falta definir generación como correlativo único. (Seba)
- **Sueldo neto = actualización mensual de toda la base** de empleados (RRHH), no incremental — costo operativo nuevo del lado PERC, sin dimensionar.
- Qué endpoints exactos expone Sherlock y cuáles datos ya trae (Seba lo mapea el 20/7).
- Alcance del biométrico/KYC en el flujo (ver decisión/riesgo aparte) — no forma parte de esta decisión de datos.

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md` § Documento / campos AMFAYS
- Org: `../knowledge/org/amfays.md`
- Compliance: `../knowledge/compliance/datos-personales/tratamiento-datos-amfays.md`
- Strategy: `../knowledge/strategy.md` § Tensions (deadline)
- Stakeholders informed: `../stakeholders/sebastian.md`, `../stakeholders/nicolas.md`, `../stakeholders/federico.md`
