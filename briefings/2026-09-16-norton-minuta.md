# Minuta — Reunión 16/09 · Norton

**Tipo:** cara al cliente · **Deriva de:** [ingestion/meetings/2026-09-16-norton-discovery.md](../ingestion/meetings/2026-09-16-norton-discovery.md) · [source 16-sep](../source/meetings/2026-09-16-norton-discovery.md)
**Para:** Martín (cc Tomás)
**De:** Quarks — Olivier / Juan Pablo Norverto
**Asunto sugerido:** Minuta reunión 16/09 + qué necesitamos para avanzar — Norton

> **Nota interna (no enviar):** no hay build-context ni briefing-context previos (primera reunión con Norton, sin prep armada); esta minuta deriva directo de [source/meetings/2026-09-16-norton-discovery.md](../source/meetings/2026-09-16-norton-discovery.md) + [ingestion/meetings/2026-09-16-norton-discovery.md](../ingestion/meetings/2026-09-16-norton-discovery.md). **Objetivo del mail:** validar lo que entendimos + pedir evidencia concreta + dejar pedido el próximo paso (plan de trabajo de Quarks). **No prometemos:** timeline, alcance ni integración con QAD (falta confirmar con Fede Pinto qué cubre el CRM de QAD); tampoco mencionamos prototipo, no se habló de eso en la reunión. Va sin el bloque "Quiénes somos" (pedido explícito). Cargos de Martín y Tomás sin confirmar todavía, así que el saludo no usa título. Borrador para que sumes antes de mandar.

---

Hola Martín, gracias por el tiempo de ayer y por sumar a Tomás a la charla. Les compartimos un resumen de lo que entendimos para que puedan validarlo, junto con el material que necesitaríamos para avanzar.

## Lo que entendimos del proceso actual

1. Hoy la fuerza de ventas no cuenta con un criterio sistemático de a qué clientes visitar y cuándo; la vieja lógica de "ficha por cliente" que ordenaba la ruta de venta se perdió con la modernización de los sistemas.
2. La información para tomar esas decisiones existe: el equipo de sistemas armó tableros de Power BI con ventas, volúmenes, clientes compradores/no compradores por marca y zona. Pero no hay tiempo dedicado a bajar esa información a acción: ni los jefes de área revisan la nómina completa de sus vendedores, ni cada vendedor su propia cartera.
3. Como consecuencia, la venta se concentra hacia el cierre de mes y las oportunidades chicas (un cliente que dejó de comprar hace dos meses, un producto sin cobertura en un punto de venta) se pierden en el volumen.
4. Antes de cada reunión de ventas, el análisis de performance del equipo lo termina armando Martín a mano (nos comentó el caso del reporte de cobertura de precios de agosto, armado revisando 50 puntos de venta).
5. Hace unos meses probaron un CRM en la nube para la fuerza de ventas, que se dejó de usar por la carga manual que insumía y porque no había alguien dedicado a analizar lo que generaba.
6. En paralelo, la compañía está migrando a un ERP/CRM corporativo nuevo (QAD), con el kickoff ya hecho y una implementación estimada en un año.

¿Es correcto este panorama? Cualquier ajuste o matiz que nos puedan dar es clave, porque es la base sobre la que vamos a pensar la propuesta.

## Dónde identificamos el dolor

El cuello de botella no es la falta de datos, sino la falta de una capa que los convierta en agenda y en decisiones: hoy ese trabajo lo termina haciendo Martín manualmente, y el intento previo de resolverlo con una herramienta se frenó por falta de una persona dedicada a sostenerla, no por falta de sistema.

## Qué necesitaríamos para avanzar

1. **Capturas de los tableros de Power BI** que ya usan hoy (ventas por cliente/SKU, compradores/no compradores, por zona y marca).
2. **El reporte de cobertura de precios** que armaste a mano en agosto, tal cual quedó, para entender el formato real que buscan.
3. **Un ejemplo de cómo se arma hoy la cartera/nómina de un vendedor** (Excel o vista de Power BI, como la usan en el día a día).
4. **Detalle de los 3 canales** (directa, indirecta/distribución, supermercado/mayorista): cómo se diferencian hoy en los sistemas y si cada uno tiene datos disponibles distintos.
5. **Alcance del módulo CRM de QAD**: si pueden compartirnos qué contempla hoy (o coordinar unos minutos con Fede Pinto), para que la propuesta no se superponga con lo que ya viene en camino.
6. **Tamaño de la fuerza de ventas**: cantidad total de vendedores y de zonas/jefes de área.
7. **Qué herramienta probaron hace unos meses** y qué puntualmente no funcionó, para no repetir el mismo camino.

## Próximos pasos

- Validan el panorama de arriba y nos hacen llegar el material que puedan reunir.
- Con eso, volvemos con un primer plan de trabajo enfocado en lo que definieron como foco inicial: agenda predictiva de visitas + reporte de eficiencia del vendedor. El resto (fotos en punto de venta, inteligencia competitiva, oportunidades geolocalizadas) lo dejamos para una etapa posterior, como ya habíamos hablado.

Quedamos a disposición para cualquier consulta.

Saludos,
Equipo Quarks
