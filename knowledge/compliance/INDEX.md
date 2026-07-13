# Compliance — Marco regulatorio aplicable

Mapa de qué normativa/práctica obligatoria aplica al producto. Cada área tiene su INDEX con resúmenes citados a las fuentes en `source/adhoc/`.

**Regla:** este índice NO contiene los textos legales completos. Los INDEX por área contienen resúmenes ejecutivos + links a las fuentes oficiales + cita al material de referencia preservado en `source/`. Si necesitás el texto exacto, está linkeado.

## Cómo se usa

- `/review-prd` carga este archivo cuando corre el lente `riesgo`.
- El lente identifica qué áreas aplican al dominio del PRD, carga el INDEX del área, y desde ahí se profundiza solo en las normas con disparador positivo.
- Cada entrada en un INDEX de área tiene un campo **"Aplica a PERC cuando:"** — eso es lo que el lente usa para filtrar; no se asume que toda norma fichada aplica siempre.
- Si una norma aplica pero no está fichada acá, el lente lo dice explícitamente — no inventa.

## Áreas

| Área | Carpeta | Qué cubre |
|---|---|---|
| Defensa del consumidor | [`consumidor/`](./consumidor/) | Ley 24.240 y derivadas, Botón de Arrepentimiento, daños punitivos, derecho a revocar |
| Datos personales | [`datos-personales/`](./datos-personales/) | Ley 25.326, AAIP, régimen sancionatorio, Registro No Llame |
| BCRA — PSP y bancos | [`bcra/`](./bcra/) | Comunicaciones BCRA: PSP como Servicio, interoperabilidad QR, ciberseguridad, encaje, prohibición cripto en PSP |
| Crédito al consumo | [`credito/`](./credito/) | Art. 36 LDC, OPNFC, tasas (CCCN 767-772), fallo Oliva CSJN, precancelación, anatocismo |
| Activos virtuales | [`cripto/`](./cripto/) | Ley 27.739, CNV RG 1058/2025 (PSAV), UIF Res 49/2024, prohibición cripto en PSP |
| Cobranza extrajudicial | [`cobranza/`](./cobranza/) | Art. 8 bis LDC (trato digno), Ley CABA 6171/6271, jurisprudencia hostigamiento |
| Tributario | [`tributario/`](./tributario/) | ARCA régimen informativo (umbrales 2026), ARBA SIRCUPA, Convenio Multilateral, TISH municipal |
| Cambiario | [`cambiario/`](./cambiario/) | Disposición BCRA 19/09/2025 (eliminación tope USD 36.000 exportadores servicios) |
| Prácticas obligatorias | [`practicas-obligatorias.md`](./practicas-obligatorias.md) | (pendiente) Checklist transversal cuando emerja el patrón |

## Estado

Poblado contra dos fuentes documentales (junio 2026):
- [`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md`](../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md) — guía legal negocios digitales (consumidor, datos, BCRA-PSP, cripto, tributario, cambiario)
- [`source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md`](../../source/adhoc/2026-06-08-leyes-regulaciones-financieras-argentinas.md) — leyes y regulaciones financieras (PSP, OPNFC, crédito, tasas, precancelación, cobranza)

`practicas-obligatorias.md` queda vacío hasta que emerja el patrón transversal a través del uso.

## Formato de una entrada (en cada INDEX por área)

```markdown
### <Norma> — <título corto>
**Qué obliga:** <1-2 líneas, datos clave + números/plazos verbatim>
**Aplica a PERC cuando:** <criterio operativo concreto>
**Vigente:** sí | no (reemplazada por X) | dejada sin efecto
**Sanción típica:** <opcional, si la norma tiene régimen sancionatorio relevante>
**Fuente en este brain:** [path al source]
**Fuente oficial:** [URL]
```

## No incluir

- Textos legales completos. Los INDEX linkean al source preservado; el source linkea a la fuente oficial.
- Interpretaciones legales propias sin fuente. Si es interpretación del PM, taggear `(intuition, PM, <fecha>)` per `CLAUDE.md § Knowledge hygiene`.
- Normativa que no aplica al producto. No mapear todo el derecho argentino — solo lo que toca PERC o el holding Quarks Alchemist.
