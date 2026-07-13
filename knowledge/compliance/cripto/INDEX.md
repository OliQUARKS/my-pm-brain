# Activos virtuales (cripto)

Marco regulatorio de Proveedores de Servicios de Activos Virtuales (PSAV) bajo competencia concurrente CNV + UIF. Incluye prohibición tajante del BCRA para que PSP y bancos ofrezcan cripto en sus interfaces en pesos.

## Normativa indexada

### Ley N° 27.739 — Reforma de la Ley 25.246 (institucionalización cripto)
**Qué obliga:** Reforma la Ley de Prevención del Lavado de Activos y Financiación del Terrorismo (Ley 25.246), institucionaliza la industria criptográfica local y otorga facultades a la CNV para crear el Registro de PSAV.
**Aplica a PERC cuando:** PERC ofrece, intermedia o custodia activos virtuales.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 4`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.argentina.gob.ar/noticias/la-cnv-crea-el-registro-de-proveedores-de-servicios-de-activos-virtuales-psav

### CNV Resolución General N° 1058/2025 (marzo 2025) — Registro PSAV
**Qué obliga:** Marco regulatorio definitivo para PSAV. Prohíbe operar comercialmente sin inscripción previa en AIF + TAD.
- **Categorías PSAV (5):**
  - **Cat. 1:** Fiat-to-Crypto y Crypto-to-Fiat (rampas).
  - **Cat. 2:** Crypto-to-Crypto (swaps).
  - **Cat. 3:** Transferencia entre wallets.
  - **Cat. 4:** Custodia/administración centralizada de claves privadas (excluye wallets self-hosted/no custodiales).
  - **Cat. 5:** Servicios financieros colaterales (ej. ICOs).
- **Patrimonio neto mínimo (USD):**
  - Cat. 1, 2, 4: **USD 150.000**
  - Cat. 3: **USD 75.000**
  - Cat. 5: **USD 35.000**
  - Volumen <USD 2.5M anuales: capital al 50%. PF cat. 1-2 con <35.000 UVAs anuales: exentos de registro.
- **Forma societaria:** Cat. 4 (custodia) exige SA o SRL constituida en Argentina; SAS debe transformarse. Extranjeros con captación activa deben constituir subsidiaria (Art. 123 LGS) o sucursal (Art. 118 LGS). **"Reverse solicitation" (captación pasiva) no detona registro.**
- **Tasa Fiscalización Anual:** ≈USD 10.000 para PJ.
- **Auditoría informática:** ahora puede ser realizada por profesional interno competente; informe transcripto en libro societario.
- **Segregación de fondos:** contable, sistémica, registral. Saldos fiduciarios en bancos locales/internacionales bajo Basilea III o PSP regulados por BCRA.
- **Transparencia wallets:** registro minucioso de direcciones públicas operativas + multifirma tercerizadas.
- **Prohibido:** mixers/tumblers, publicidad engañosa, ofrecimiento público de activos virtuales que califiquen como valores negociables sin autorización separada CNV. Advertencia de volatilidad obligatoria para activos con <90 días de historial.
- **Régimen informativo:** mensual (15 días post cierre) — clientes, volumen, montos USD, ranking top 10. Anual (70 días post cierre) — auditoría sistemas + informe Oficial de Cumplimiento + estados contables auditados.
**Aplica a PERC cuando:** PERC integra funcionalidad cripto en alguna de las 5 categorías.
**Vigente:** sí. Plazos de adecuación PSAV preexistentes: PF jul-2025, sociedades locales ago-2025, extranjeras sep-2025.
**Sanción típica:** cancelación administrativa de oficio del registro; expulsión del mercado legal.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 4.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://beccarvarela.com/novedades/resolucion-general-cnv-n1058-regulacion-de-proveedores-de-servicios-de-activos-virtuales-psav/, registro: https://www.argentina.gob.ar/cnv/registro-de-proveedores-de-servicios-de-activos-virtuales

### RG CNV 994/2024 y 1025/2024 (PROYECTOS PREVIOS — REEMPLAZADAS)
**Vigente:** no — complementadas y modificadas por la RG 1058/2025.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 4.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### UIF Resolución N° 49/2024 (marzo 2024) — PSAV como sujetos obligados
**Qué obliga:** Operativiza a los PSAV como **Sujetos Obligados primarios** bajo Art. 20 inc. 13 de la Ley 25.246 para PLA/FT.
- **Enfoque Basado en Riesgos (EBR):** matrices de riesgo documentadas para exposición a crimen organizado.
- **Reporte de Operaciones (RO):** todas las operaciones >6 SMVM al momento de la transacción se informan a la UIF.
- **Reporte sistemático mensual:** entre días 1-15 de cada mes, el Oficial de Cumplimiento remite altas/bajas de clientes del mes anterior.
- **Tecnología obligatoria:** KYC biométrico, monitoreo y trazabilidad blockchain (Chainalysis, TRM Labs o equivalentes), algoritmos para Reportes de Operaciones Sospechosas (ROS).
**Aplica a PERC cuando:** PERC opera como PSAV en cualquier categoría.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 4.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.adeba.com.ar/resolucion-de-la-uif-49-2024/, https://beccarvarela.com/novedades/unidad-de-informacion-financiera-uif-resolucion-49-2024-proveedores-de-servicios-de-activos-virtuales-como-sujetos-obligados/

### Ley N° 25.246 — Ley de Prevención de Lavado de Activos y Financiación del Terrorismo (base)
**Qué obliga:** Marco general PLA/FT. Modificada por Ley 27.739 para incluir cripto.
**Aplica a PERC cuando:** evaluación de exposición al régimen PLA/FT.
**Vigente:** sí (con modificaciones).
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 4`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### Com. "A" 7759 BCRA (mayo 2023) — Prohibición cripto en PSPCP
**Qué obliga:** PSPCP no pueden realizar por sí ni facilitar a clientes operaciones con activos digitales no autorizados. "Facilitar" incluye **botones de compra automatizados** en la interfaz. Usuarios operan "por cuenta propia" — escisión forzosa.
**Aplica a PERC cuando:** PERC piensa integrar cripto en interfaz de pesos.
**Vigente:** sí.
**Detalle:** ver también [`bcra/INDEX.md`](../bcra/INDEX.md).
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.3`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.estudio-ofarrell.com/el-banco-central-de-la-republica-argentina-prohibe-a-los-pspcp-realizar-y-facilitar-operaciones-con-activos-digitales/

### Com. "A" 7506 BCRA — Prohibición cripto en bancos
**Qué obliga:** Antecedente de 7759. Prohibición equivalente aplicada a entidades financieras tradicionales.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 3.3`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

## Cruces relevantes con otras áreas

- **BCRA — prohibiciones de cripto en PSP/bancos:** [`bcra/INDEX.md`](../bcra/INDEX.md).
- **Datos personales — KYC biométrico:** [`datos-personales/INDEX.md`](../datos-personales/INDEX.md).
- **Régimen informativo ARCA sobre activos virtuales:** [`tributario/INDEX.md`](../tributario/INDEX.md).
