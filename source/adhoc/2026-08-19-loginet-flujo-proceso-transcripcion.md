# Transcripción — Diagrama de flujo de proceso Loginet

> **Tipo:** adhoc — transcripción de un diagrama (no es un OCR verbatim; es una lectura fiel del contenido visual).
> **Fuente binaria preservada:** [`2026-08-19-loginet-flujo-proceso-diagrama.pdf`](./2026-08-19-loginet-flujo-proceso-diagrama.pdf) (archivo original: `Loginet.pdf`, aportado por el PM el 2026-08-19).
> **Naturaleza:** parece un export de un whiteboard (Miro/FigJam/similar) con post-its organizados por carril ("swimlane"). No tiene fecha propia visible en el documento — es contenido de proceso, probablemente elaborado por Loginet (Vanina Focaraccio se comprometió a compartir el detalle paso a paso en la reunión del 24/2/2026, ver `ingestion/meetings/2026-02-24-loginet-briefing-quarks.md`) o por Quarks en base a esa reunión.
> **Observación, no interpretación** — es una transcripción de lo que se ve en el diagrama, no una síntesis.

## Carril: Comercial (amarillo)

- Facu → llega consulta (marítima / terrestre)
- Se cotiza. Camino se bifurca:
  - **Se cierra** → carga cotización en Khai → booking → confirmación de booking
  - **No se cierra** → (rama con post-its no del todo legibles) → contrato existente con naviera / contrato spot (1 mes)
- Notas laterales en violeta: "nueva ruta" y similares (poco legibles)

## Carril: Operativo (rosa/salmón)

- Actores: **cliente**, **despachante** → confluyen en un nodo ("comunicación previa a...", poco legible)
- Inicio de operación en Excel
- TR manda draft de BL
- Corte de carga (cut off de carga)
- Chequeo de si el draft de BL coincide con la declaración (nodo destacado)
- Se carga info del BL en Khai
- Se factura una vez que opera/zarpa el buque
- Rama lateral: **salidas por Chile** — proceso separado, cortes de carga propios, mencionado como más manual (consistente con lo discutido en la reunión del 24/2 sobre Chile ~50% del volumen y menos automatizado)

## Carril: Administrativo (verde)

- **VENTA** → administración entra al file de Khai y procede a facturar
- Envío de estado de cuenta
- Clientes con cuenta corriente: +30 días de plazo
- Clientes sin cuenta corriente: deben pagar antes de la llegada del buque — chequear contra el excel si hay cambio de arribo

## Carril: Costo (verde, sub-bloque aparte)

- Llega mail de la naviera con la factura (FC)
- El mail se reenvía automáticamente a **Extract**
- Extract carga la factura en Khai
- Se genera **ROC** (= "Rock" mencionado en las reuniones — la prefactura/precarga manual que concilia el ítem interno con la factura del proveedor)
- Si no está OK: reclamo a comercial
- Chequeo contra contrato — si está mal cargado en el sistema, se corrige manualmente en Khai
- Nota: **"los contratos están en una solapa del excel master"** — confirma lo dicho en la reunión del 6/4 sobre el repositorio maestro de contratos

## Carril: Seguimiento (azul, sin desarrollar en el diagrama)

- Carril marcado pero sin post-its visibles — posible gap del diagrama o sección no completada por el cliente.

---

**Nota de consistencia:** este diagrama confirma casi 1:1 los procesos descriptos en las actas de reunión del [24/2/2026](../meetings/2026-02-24-loginet-briefing-quarks.md) y del [6/4/2026](../meetings/2026-04-06-loginet-2do-mapeo.md) — Khai (ERP/TMS), Extract (bot de lectura de facturas/BL), el concepto de "Rock" como prefactura de conciliación, el Excel master de contratos, y la fricción entre comercial/operativo/administrativo. No introduce información nueva que contradiga lo ya relevado; sirve como confirmación visual del mapeo.
