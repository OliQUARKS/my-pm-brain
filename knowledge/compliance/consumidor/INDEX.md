# Defensa del consumidor

Marco general de relaciones de consumo aplicable a cualquier contratación con cliente final, incluyendo e-commerce y contratación a distancia. Núcleo del régimen sancionatorio que castiga incumplimientos con daños punitivos indexados.

## Normativa indexada

### Ley N° 24.240 — Defensa del Consumidor (LDC)
**Qué obliga:** Regula relaciones de consumo en general. Establece deberes de información, trato digno, garantías, derecho de revocación, y régimen sancionatorio (multas + daños punitivos).
**Aplica a PERC cuando:** existe relación de consumo con cliente final (siempre, en un producto de crédito al consumo). Es el marco base que activa los demás artículos específicos (8 bis trato digno → ver `cobranza/`; 36 crédito → ver `credito/`).
**Vigente:** sí (modificada por Ley 27.701 en cuantificación de sanciones).
**Sanción típica:** multas escalables hasta 2.100 Canastas Básicas Totales (CBT) — al valor CBT abril 2026 ($1.508.740,25), el techo teórico supera los $3.168 millones ARS.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 1.3`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.argentina.gob.ar/economia/industria-y-comercio/defensadelconsumidor/publicacion-de-sanciones-ley-24240

### Ley N° 27.701 — Modificatoria de daños punitivos (Art. 119)
**Qué obliga:** Modifica el Art. 47 de la Ley 24.240 eliminando topes nominales en pesos y atando las multas a la Canasta Básica Total (CBT): rango entre 0,5 y 2.100 CBT. Auto-indexación frente a inflación.
**Aplica a PERC cuando:** se evalúa exposición sancionatoria por incumplimiento de la LDC.
**Vigente:** sí (publicada B.O. fines de 2022).
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 1.3`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://abeledogottheil.com.ar/defensa-del-consumidor-los-nuevos-montos-de-multas-y-de-danos-punitivos-y-el-costo-argentino/

### Código Civil y Comercial — Art. 1.110 (derecho a revocar)
**Qué obliga:** Derecho irrenunciable del consumidor a revocar la aceptación de un contrato celebrado fuera del establecimiento o a distancia, dentro de los 10 días corridos desde la entrega del bien o celebración del contrato de servicio.
**Aplica a PERC cuando:** el producto se contrata digitalmente (siempre, en PERC).
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 1.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)
**Fuente oficial:** https://www.argentina.gob.ar/justicia/derechofacil/leysimple/boton-arrepentimiento

### Código Civil y Comercial — Art. 1.116 (excepciones al derecho a revocar)
**Qué obliga:** Enumera taxativamente categorías exentas del derecho a revocar: bienes personalizados, perecederos, software/medios decodificados, bienes ya consumidos, adquisiciones B2B (reventa o uso industrial).
**Aplica a PERC cuando:** se evalúa si un componente del producto admite exención del Botón de Arrepentimiento.
**Vigente:** sí.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 1.2`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### Disposición N° 954/2025 (SCS, septiembre 2025) — Botón de Arrepentimiento + Botón de Baja
**Qué obliga:** Especificaciones técnicas obligatorias para ambos botones en cualquier proveedor que comercialice bienes/servicios a distancia (webs, apps, plataformas).
- **Visibilidad:** botón rotulado obligatoriamente "BOTÓN DE ARREPENTIMIENTO", ubicación destacada en home/pantalla principal, acceso directo desde primer acceso. No oculto en menús secundarios.
- **Fricción cero:** prohibido requerir registro previo, login compulsivo, encuestas disuasorias o trámites adicionales. El sistema backend debe procesar solicitudes NO autenticadas.
- **SLA 24h:** una vez enviada la solicitud, el proveedor tiene 24 horas para enviar acuse de recibo con código de identificación del trámite.
- **Costos:** todos los gastos de logística inversa (devolución) son del vendedor.
- **Excepciones especiales (tickets/turismo fecha fija):** plazo 10 días sigue corriendo pero el consumidor debe notificar con 24h de antelación al inicio del evento/servicio.
- **Botón de Baja:** equivalente para contratos de tracto sucesivo (suscripciones, tarjetas, seguros, cuentas de pago). Mismo SLA de 24h. Empresas que comercializan solo por canales digitales/telefónicos deben mantener atención humana ≥8 horas días hábiles.
**Aplica a PERC cuando:** cualquier contratación a distancia (siempre). Botón de Baja aplica en todo producto de tracto sucesivo (préstamos con cuotas son tracto sucesivo).
**Vigente:** sí (publicada 4-sep-2025; período de adecuación 60 días). Deroga Res. 316/2018 y 424/2020.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 1.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md), [`§ 6.2`](../../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md)
**Fuente oficial:** https://www.estudio-ofarrell.com/nueva-disposicion-acerca-del-boton-de-arrepentimiento-y-el-boton-de-baja-de-servicio/

### Resolución N° 316/2018 (DEROGADA)
**Qué obligaba:** Botón de Arrepentimiento previo a la Disp. 954/2025.
**Vigente:** no — derogada por Disposición 954/2025.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 1.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

### Resolución N° 424/2020 (DEROGADA)
**Qué obligaba:** Botón de Baja de Servicio previo a la Disp. 954/2025.
**Vigente:** no — derogada por Disposición 954/2025.
**Fuente en este brain:** [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 1.1`](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md)

## Cruces relevantes con otras áreas

- **Trato digno (Art. 8 bis LDC) y daños punitivos (Art. 52 bis):** ver [`cobranza/INDEX.md`](../cobranza/INDEX.md) — directamente vinculado al recupero crediticio.
- **Crédito al consumo (Art. 36 LDC):** ver [`credito/INDEX.md`](../credito/INDEX.md).
- **Botón de arrepentimiento/baja en banca digital:** ver [`bcra/INDEX.md`](../bcra/INDEX.md) (Com. "A" 8203 — el BCRA exige los mismos botones en home banking/app).
