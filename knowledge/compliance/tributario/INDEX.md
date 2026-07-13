# Tributario

Regímenes informativos y de retención que captan los flujos de billeteras virtuales, cuentas de pago, exchanges de cripto y operaciones de comercio electrónico. Aplican simultáneamente a nivel nacional (ARCA), provincial (ARBA + Comisión Arbitral), y municipal (tasas locales).

## Normativa indexada

### Régimen Informativo ARCA (ex AFIP) — Activos virtuales y no virtuales / billeteras
**Qué obliga:** Reporte mensual detallado de saldos, ingresos y egresos en billeteras virtuales y cuentas comitentes.
- **Datos a reportar:** identificación completa del titular y cotitulares, CVU/CBU, CUIT, entidad financiera/emisora, terceros proveedores en arquitecturas BaaS, monto y tipo de cada ingreso/egreso del mes, saldo final mensual al último día hábil.
- **Umbrales (vigentes desde abril 2026):**
  - **Personas humanas:** ingresos, egresos o saldo final ≥ **$50.000.000 ARS**.
  - **Personas jurídicas:** ingresos, egresos o saldo final ≥ **$30.000.000 ARS**.
- **Conversión de moneda extranjera:** tipo de cambio comprador BNA al cierre del último día hábil del mes.
- **Conversión de criptomonedas/stablecoins:** último valor de cotización tipo comprador establecido internamente por el sujeto obligado al último día del mes. **Las APIs de cotización interna deben ser trazables** para auditorías futuras.

**Aplica a PERC cuando:** PERC custodia o procesa fondos sujetos a este régimen (PSP, billetera, plataforma con CVU).
**Vigente:** sí (desde 04/2026 con los umbrales nuevos). Modificó RG 4614/19 y RG 5512.
**Sanción típica:** régimen sancionatorio AFIP/ARCA general por incumplimiento informativo.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 5.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md), [`§ 1.3 doc financiero`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)
**Fuente oficial:** https://www.afip.gob.ar/economia-digital/activos-virtuales-y-no-virtuales/servicios-administracion-intermediacion/informacion.asp, https://servicioscf.afip.gob.ar/publico/sitio/contenido/novedad/ver.aspx?id=4490

### F.8126 — Formulario de Régimen de Información ARCA
**Qué obliga:** Formulario técnico para el reporte del régimen informativo de ARCA sobre billeteras virtuales y cuentas comitentes.
**Aplica a PERC cuando:** se diseña la integración con el régimen informativo (sistema de export mensual).
**Vigente:** sí.
**Fuente oficial:** https://www.afip.gob.ar/economia-digital/ayuda/documentos/Manual-usuario-F8126V300.pdf

### ARBA Resolución Normativa N° 25/2025 — SIRCUPA (Recaudación Anticipada en Cuentas de Pago)
**Qué obliga:** Régimen de retención anticipada de Ingresos Brutos sobre acreditaciones en cuentas digitales. Aplicado vía integración al sistema SIRCUPA (administrado por Comisión Arbitral del Convenio Multilateral).
- **Sujetos obligados:** PSPOCP inscriptos ante SEFyC-BCRA. Mutación a agente de percepción/recaudación.
- **Padrón de control:** Comisión Arbitral. El PSP debe integrar API para consulta de CUIT.
- **Hecho imponible:** acreditación de importes en la billetera (pesos o moneda extranjera; **excluye USD y análogos**).
- **Alícuota:** entre **0,01% y 5%** según actividad y calificación de riesgo fiscal del contribuyente. Retención en tiempo real, antes de que se consolide el saldo.
- **Créditos excluidos (deben ser identificados y clasificados por la arquitectura del PSP):**
  - Salarios y remuneraciones por trabajo en relación de dependencia
  - Jubilaciones y pensiones
  - Préstamos personales o prendarios
  - Liquidación de plazos fijos del mismo titular
  - Transferencias desde el exterior
  - Transferencias intra-titular (CBU a CVU misma CUIT)
- **Vigencia escalonada:** 1-oct-2025 para PSPOCP en listados históricos; 1-nov-2025 para resto.

**Aplica a PERC cuando:** PERC es PSPOCP y acredita fondos a usuarios contribuyentes en PBA.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 5.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.bodlegal.com/nuevo-regimen-de-arba-sobre-ingresos-brutos-en-cuentas-digitales/

### Comisión Arbitral Resolución General N° 5/2021 — Presencia Digital (Convenio Multilateral)
**Qué obliga:** Reinterpretación del Art. 1 del Convenio Multilateral. **El sustento territorial tributario se configura en la jurisdicción del comprador** (no del vendedor) cuando hay "presencia digital" del vendedor en esa jurisdicción.
- Presunción **iure et de iure** en la práctica: usar plataformas e-commerce sistematizadas + canalizar ventas a residentes de una provincia = presencia digital activa.
- Consecuencia: una tienda virtual única en CABA que despacha a las 23 provincias adquiere sustento territorial en todas. Obligación de inscribirse en Convenio Multilateral, gestionar RUT, presentar CM05 mensual con coeficientes de distribución.
**Aplica a PERC cuando:** PERC vende, comercializa o presta servicios a residentes de múltiples jurisdicciones (casi siempre, en un producto digital).
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 5.3`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.argentina.gob.ar/normativa/nacional/resoluci%C3%B3n-5-2021-348122, texto FACPCE: https://www.facpce.org.ar/wp-content/uploads/2021/04/CONVENIO-MULTILATERAL-MEDIOS-ELECTRONICOS-R.G.-CA-5.2021-FINAL.pdf

### Comisión Arbitral Resolución General N° 14/2017 — Domicilio del adquirente
**Qué obliga:** Complemento de la RG 5/2021. Regula pautas para establecer el domicilio del adquirente y el "destino final de los bienes" — definiciones operativas que aplican al sustento territorial digital.
**Aplica a PERC cuando:** se determina la jurisdicción tributaria de una operación.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 5.3`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### RG AFIP 4614/19 y 5512 (MODIFICADAS por el régimen vigente)
**Qué obligaban:** Regímenes informativos previos sobre billeteras virtuales con umbrales muy inferiores (entre $400.000 y $1.000.000 en 2024-2025).
**Vigente:** modificadas por el régimen actualizado a abril 2026 (ver primera entrada).
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 5.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### Registro Único Tributario (RUT) — ARCA
**Qué obliga:** Inscripción simultánea ante regímenes nacional, provincial y municipal a través de una única plataforma. Necesario para operar bajo Convenio Multilateral.
**Aplica a PERC cuando:** PERC tiene presencia digital multijurisdiccional.
**Vigente:** sí.
**Fuente oficial:** https://www.afip.gob.ar/registro-unico-tributario/

### Tasa por Inspección de Seguridad e Higiene (TISH) — Régimen General municipal
**Qué obliga:** Tasa municipal sobre la facturación devengada en el ejido local. Base híbrida entre canon por servicios e impuesto sobre ingresos. Requiere declaraciones bimestrales o cuotas proporcionales + papeles de trabajo firmados por contadores. Necesita aplicar Coeficientes Intermunicipales (CM05) para asignar facturación nacional a la sede local.
**Caso de ejemplo (San Isidro, junio 2025):** habilitación 100% digital, gratuita en el inicio, plataforma TESI. **Procedimiento Exprés:** habilitación en 48 horas para negocios digitales puros que operan a puertas cerradas, sin atención de público. Pero el sistema bloquea el certificado definitivo si hay deudas (ABL, padrón deudores alimentarios) — debe regularizarse antes.
**Aplica a PERC cuando:** PERC tiene oficina, dark store, centro logístico o sede administrativa en un municipio bonaerense (u otro).
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 5.4`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://arsi.gob.ar/tasa-por-inspeccion-de-seguridad-e-higiene-ressi-y-regimen-general/, https://arsi.gob.ar/tasa-por-inspeccion-de-seguridad-e-higiene/

## Cruces relevantes con otras áreas

- **BCRA / PSP — los obligados primarios del régimen ARCA y SIRCUPA son justamente los PSP:** [`bcra/INDEX.md`](../bcra/INDEX.md).
- **Cripto — régimen informativo ARCA específico sobre activos virtuales:** [`cripto/INDEX.md`](../cripto/INDEX.md).
- **Cambiario — exportación de servicios:** [`cambiario/INDEX.md`](../cambiario/INDEX.md).
