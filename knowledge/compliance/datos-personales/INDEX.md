# Datos personales

Tratamiento, almacenamiento, perfilamiento y cesión de datos personales en plataformas digitales. Supervisión por la Agencia de Acceso a la Información Pública (AAIP). Régimen sancionatorio con multas + facultad de "obligaciones de hacer" (injunctions paralizando algoritmos, ordenando borrado de bases).

## Normativa indexada

### Ley N° 25.326 — Protección de Datos Personales (LPDP)
**Qué obliga:** Marco general del tratamiento de datos. Cinco deberes operacionales clave:
1. **Inscripción de bases de datos** en el Registro Nacional de la AAIP (Art. 3 LPDP). Trámite por única vez, pero con obligación de mantener datos actualizados. Email institucional exclusivo por trámite (no genérico, no compartido entre marcas/concesionarias).
2. **Calidad y finalidad:** datos ciertos, adecuados, pertinentes, no excesivos. Una vez agotada la finalidad: suprimir o anonimizar.
3. **Consentimiento previo, libre, expreso e informado** (Art. 5). Casillas desmarcadas por defecto. Sin consentimiento tácito por navegación. Revocable en cualquier momento.
4. **Cesión a terceros** (Art. 11): solo con consentimiento previo + información sobre finalidad y cesionario. Aplica a programmatic ads, retargeting, brokers de datos.
5. **Seguridad y confidencialidad:** medidas técnicas, lógicas, organizativas. La conservación sin condiciones de seguridad acordes al estado del arte es infracción punible.
**Aplica a PERC cuando:** se recopilan, almacenan, perfilan o ceden datos de usuarios (siempre, en cualquier app). Cesión a terceros es disparador particular si PERC comparte datos con bureaus crediticios, analytics, o partners.
**Vigente:** sí.
**Sanción típica:** multas + apercibimientos + suspensión del tratamiento + "obligaciones de hacer" (injunctions).
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 2.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://servicios.infoleg.gob.ar/infolegInternet/anexos/60000-64999/64790/texact.htm

### Ley N° 26.951 — Registro Nacional "No Llame"
**Qué obliga:** Establece el registro de personas que no quieren recibir comunicaciones publicitarias telefónicas. Complementa el régimen sancionatorio aplicado por la AAIP.
**Aplica a PERC cuando:** PERC realiza outbound telefónico para originación, cross-sell, o cobranza (la cobranza extrajudicial tiene su propio régimen — ver `cobranza/`).
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 2.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### RESOL-2024-126-APN-AAIP — Régimen sancionatorio AAIP
**Qué obliga:** Tipificación y graduación de sanciones en tres niveles:
- **Leves:** falla administrativa (no inscribir base operativa). Hasta 2 apercibimientos + multa base $1.000.
- **Graves:** vulneración de principios de calidad, no respuesta a requerimientos, cesión no autorizada. Hasta 4 apercibimientos + suspensión tratamiento 1-30 días + multas desde $80.001.
- **Muy graves:** tratamiento ilegítimo, vulneración de datos sensibles sin encriptación. Multas acumulativas.
- **Herramienta disruptiva:** la Dirección Nacional puede emitir "obligaciones de hacer" — paralizar algoritmos de perfilamiento, ordenar borrado de bases, mandar capacitación obligatoria certificada.
**Aplica a PERC cuando:** se evalúa exposición ante AAIP por incumplimientos de la LPDP.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 2.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://servicios.infoleg.gob.ar/infolegInternet/anexos/395000-399999/399750/norma.htm

## Implicancias de infraestructura cloud

Los proveedores hiperescalares (Microsoft Azure, Dynamics 365) han debido certificarse contra la "Argentina Personal Data Protection Act (PDPA)" para garantizar que el alojamiento distribuido no infrinja garantías de jurisdicción.
**Fuente:** https://learn.microsoft.com/en-us/compliance/regulatory/offering-pdpa-argentina

## Cruces relevantes con otras áreas

- **PSP/billeteras y datos transaccionales:** ver [`bcra/INDEX.md`](../bcra/INDEX.md) — Com. "A" 8398 ciberseguridad.
- **KYC y PLA/FT en cripto:** ver [`cripto/INDEX.md`](../cripto/INDEX.md) — UIF Res 49/2024 exige verificación biométrica y monitoreo.

## Diseños aplicados a productos

- [Diseño — Consentimiento y cesión/encargo a Mantovana (Flujo Crédito)](./diseno-consentimiento-mantovana.md) — flow de consentimiento explícito + inscripción AAIP + DPA Mantovana + canal seguro. Triggered by review PRD 2026-06-08.
