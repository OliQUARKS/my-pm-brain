# BCRA — Comunicaciones para PSP, billeteras y bancos

Marco regulatorio del Banco Central aplicable a Proveedores de Servicios de Pago (PSP), entidades financieras y arquitectura del sistema de pagos electrónicos.

## Texto Ordenado de referencia

**Proveedores de servicios de pago que ofrecen cuentas de pago (T.O.):** https://www.bcra.gob.ar/archivos/Pdfs/Texord/t-snp-psp.pdf
**Protección de los usuarios de servicios financieros (T.O.):** https://www.bcra.gob.ar/archivos/Pdfs/texord/t-pusf.pdf

## Normativa indexada

### Com. "A" 8432 (mayo 2026) — PSP como Servicio (PSP as a Service / BaaS)
**Qué obliga:** Formaliza la figura de "PSPCP-as-a-Service": el PSPCP regulado provee infraestructura backend a un tercero "tomador" que opera el frontend. Restricciones:
- Prohibido prestar a personas jurídicas no constituidas en Argentina (excluye offshore).
- Prohibido prestar a mercados, cámaras compensadoras, agentes de bolsa.
- El tomador debe informar de manera clara la denominación comercial del PSPCP que provee la cuenta.
- PSPCP que ya operaban "as a Service" tienen 10 días hábiles para reportar al BCRA la nómina de tomadores.
- Inscripción endurecida: divulgación de personas humanas con ≥10% del capital, certificados de antecedentes penales de directivos, identificación de Oficial de Cumplimiento UIF, banco patrocinante declarado.
- Plazo para iniciar operaciones tras inscripción: extendido de 6 a 12 meses, pero el BCRA puede dar de baja por inactividad ≥180 días.
- PSP previamente inscriptos: 90 días corridos para adecuación.
**Aplica a PERC cuando:** PERC opera como tomador de servicios PSP (front blanco sobre un PSPCP regulado), o cuando PERC actúa como PSPCP. Identificar arquitectura BaaS es disparador.
**Vigente:** sí (vigencia plena desde 26-may-2026).
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md), [`§ 1.1 del doc financiero`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)
**Fuente oficial:** https://www.marval.com/publicacion/nueva-regulacion-sobre-proveedores-de-servicios-de-pago-17601

### Com. "A" 8398 (febrero 2026) — Ciberseguridad y riesgos tecnológicos PSP
**Qué obliga:** Categoriza a los PSP como sujetos obligados plenos bajo "Requisitos mínimos para gestión y control de riesgos de tecnología y seguridad de la información":
- Taxonomía de servicios tercerizados (IaaS, PaaS, SaaS, SOC, redes) con métricas de riesgo aprobadas por máxima autoridad del PSP.
- **Notificación al BCRA con 60 días de antelación** antes del inicio operacional de cualquier servicio tecnológico crítico tercerizado.
- Tercerización intra-grupo en el extranjero: certificación escrita del supervisor del país de origen (adherencia a Basilea + GAFI).
- Subcontratistas aceptan contractualmente auditorías directas del BCRA.
- Contratos cloud deben incluir borrado seguro de datos post-terminación + plan de salida con recuperación de código fuente.
**Aplica a PERC cuando:** PERC es PSP o terceriza servicios tech críticos (siempre que toque cuentas de pago).
**Vigente:** sí. Plazo de adecuación: 180 días — **vencimiento 4 de agosto de 2026**.
**Fuente en este brain:** [`source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md § 1.2`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)
**Fuente oficial:** https://jfcattorneys.com/es/news/bcra-com-a-8398-ciberseguridad-psp

### Com. "A" 8411 y "A" 8415 (2026) — Régimen disciplinario, PSP en "Grupo A"
**Qué obliga:** Iguala el tratamiento sancionatorio de los PSP a los bancos comerciales y a infraestructuras críticas del mercado (COELSA, Interbanking, Red Link, Newpay). PSP pasan al "Grupo A" del régimen disciplinario.
**Aplica a PERC cuando:** se evalúa exposición sancionatoria del BCRA.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md § 1.1`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)

### Com. "A" 8203 (2025) — Protección de Usuarios de Servicios Financieros
**Qué obliga:** Texto Ordenado consolidado. Exige que entidades financieras y emisoras de tarjetas incorporen "botón de arrepentimiento" y "botón de baja" en home banking y app móvil, en lugar jerarquizado, permitiendo rescisión/revocación sin demoras. Incluye estándares de trato equitativo (resúmenes en Braille, etc.).
**Aplica a PERC cuando:** PERC ofrece tarjeta o producto financiero con interfaz digital propia.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md § 6.2`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)
**Fuente oficial:** https://www.bcra.gob.ar/archivos/Pdfs/comytexord/A8203.pdf

### Com. "A" 7429 (diciembre 2021) — Encaje 100% saldos PSP
**Qué obliga:** Saldos inmovilizados de billeteras virtuales (dinero transaccional no invertido) deben estar en cuentas a la vista en entidades financieras comerciales que constituyan encaje legal del 100% en el BCRA. Garantiza disponibilidad inmediata frente a insolvencia del PSP.
**Aplica a PERC cuando:** PERC custodia saldos de usuarios.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://bomchil.com/noticia-y-publicacio/el-bcra-modifica-el-regimen-de-administracion-de-fondos-de-clientes-aplicable-a-los-proveedores-de-servicios-de-pago-que-ofrecen-cuentas-de-pago/

### Com. "A" 7611 (septiembre 2022) — 45% Bonos del Tesoro
**Qué obliga:** Flexibiliza el encaje permitiendo que los bancos destinen hasta 45% de los fondos encajados de clientes PSP a la suscripción de Bonos del Tesoro Nacional en pesos (vencimiento mayo 2027).
**Aplica a PERC cuando:** PERC custodia saldos transaccionales que entran al encaje BCRA.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### Com. "A" 7825 (agosto 2023) — Traslado obligatorio de rentabilidad (DEJADA SIN EFECTO)
**Qué obligaba:** Forzaba a los PSPCP a trasladar automáticamente a clientes la rentabilidad originada por inversiones en títulos públicos en pesos sobre los fondos encajados.
**Vigente:** no — dejada sin efecto en **junio 2024**. Hoy el usuario debe hacer opt-in explícito (suscribir cuotapartes de FCI) para percibir rendimientos.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.marval.com/publicacion/el-bcra-obliga-a-los-proveedores-de-servicios-de-pagos-a-trasladar-a-sus-clientes-el-rendimiento-que-producen-los-fondos-acreditados-en-las-cuentas-de-pago-15587

### Com. "A" 7769 (mayo 2023) — Interoperabilidad QR con tarjeta de crédito
**Qué obliga:** Toda billetera digital interoperable debe procesar y leer pagos con tarjeta de crédito sobre cualquier código QR, sin importar quién lo proveyó. Comisión cruzada máxima entre PSP iniciador y emisor de la tarjeta: **0,07% del importe de la transacción**.
**Aplica a PERC cuando:** PERC ofrece QR de cobro o procesa pagos con QR de terceros.
**Vigente:** sí (prorrogada por Com. "A" 7831).
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md), [`§ 1.4 del doc financiero`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)
**Fuente oficial:** https://www.palabrasdelderecho.com.ar/articulo/5111/El-Banco-Central-dispuso-la-interoperabilidad-QR

### Com. "A" 8032 (mayo 2024) — Interoperabilidad QR extendida a tarjetas prepagas
**Qué obliga:** Extiende las reglas de interoperabilidad QR a pagos con tarjetas prepagas. Plazo de adecuación técnica: 60-270 días según componente del sistema. Implementación técnica plena: **25 de febrero de 2025**.
**Aplica a PERC cuando:** PERC procesa pagos con tarjetas prepagas vía QR.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.bcra.gob.ar/archivos/Pdfs/comytexord/A8032.pdf

### Com. "A" 7795 (junio 2023) — Topes tasa MiPyMEs y descubiertos
**Qué obliga:** Topes nominales fijos históricos (ej. 40% / 35% según coyuntura) para asistencia crediticia a MiPyMEs, descubiertos en cuenta corriente y refinanciaciones de saldos de tarjetas de crédito.
**Aplica a PERC cuando:** PERC ofrece crédito a MiPyMEs o equivalentes.
**Vigente:** sí (sujeto a actualizaciones por el BCRA).
**Fuente en este brain:** [`source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md § 4`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)
**Fuente oficial:** https://www.bcra.gob.ar/archivos/Pdfs/comytexord/A7795.pdf

### Com. "A" 7759 (mayo 2023) — Prohibición cripto en PSPCP
**Qué obliga:** Prohibido a PSPCP realizar por sí o facilitar a clientes operaciones con activos digitales no autorizados por autoridad nacional o BCRA. "Facilitar" incluye la simple disponibilidad de **botones de compra automatizados** dentro de la plataforma. Usuarios que quieren cripto deben operar "por cuenta propia" (escisión forzosa de la arquitectura).
**Aplica a PERC cuando:** PERC integra o piensa integrar funcionalidad cripto en la interfaz en pesos.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.3`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md). Ver también [`cripto/INDEX.md`](../cripto/INDEX.md).
**Fuente oficial:** https://www.estudio-ofarrell.com/el-banco-central-de-la-republica-argentina-prohibe-a-los-pspcp-realizar-y-facilitar-operaciones-con-activos-digitales/

### Com. "A" 7506 — Prohibición cripto en bancos (antecedente de 7759)
**Qué obliga:** Restricción equivalente a 7759 pero aplicada a entidades financieras tradicionales antes de extenderse a PSP.
**Vigente:** sí. Ver detalles en [`cripto/INDEX.md`](../cripto/INDEX.md).

## Cruces relevantes con otras áreas

- **Crédito al consumo (OPNFC, Art. 36 LDC, precancelación):** ver [`credito/INDEX.md`](../credito/INDEX.md).
- **Activos virtuales (cripto):** ver [`cripto/INDEX.md`](../cripto/INDEX.md) — Com. "A" 7759 y 7506 también figuran allí por afinidad temática.
- **Régimen informativo ARCA / SIRCUPA ARBA:** ver [`tributario/INDEX.md`](../tributario/INDEX.md) — los PSP son agentes de retención.
- **Botón de arrepentimiento/baja en banca digital:** ver Com. "A" 8203 arriba + [`consumidor/INDEX.md`](../consumidor/INDEX.md).
