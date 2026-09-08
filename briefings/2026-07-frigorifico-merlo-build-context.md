# Contexto de proyecto — Frigorífico Merlo · build-context

**Estado:** preventa · post-discovery 23-jul-2026 · **ampliado con documentación del cliente (doc de flujos, jul-2026)**
**Fuentes:** [discovery 23-jul](../source/meetings/2026-07-23-frigorifico-merlo-discovery.md) · [doc de flujos del cliente](../source/adhoc/2026-07-frigorifico-merlo-doc-flujos-ventas.md) · briefing previo de primer contacto (scratchpad, 21-jul) · sitio [frigorificomerlo.com](https://frigorificomerlo.com/)
**Equipo Quarks:** Jonathan "Jony" Ayerbe (fundador/CEO — llevó el discovery), Olivier (PM/vínculo)

> **Nota de capas:** esto es contexto **interno**. La pre-propuesta cara-al-cliente está en la sección B. La propuesta real (equipo/tiempo/costo) recién con el "sí".
>
> **Actualización jul-2026:** Nacho envió un documento detallado de flujos con capturas del ERP y de las planillas. Cierra casi todos los abiertos técnicos y de proceso. Lo nuevo va marcado **[doc]**.

---

## A. Contexto del proyecto (interno)

### 1. Problemática — ampliada

| Antes (briefing 21-jul) | Post-discovery (23-jul) | Post-doc del cliente **[doc]** |
|---|---|---|
| Dolor = "procesamiento de facturas" (AP). | Dolor real = flujo pedido→producción→pesaje→carga de venta (order-to-cash de la despostada), en papel, con re-transcripciones. | **Confirmado y acotado:** el flujo que duele es sólo el de **ventas NO facturadas** (cortes con hueso + cajas). Hay **otros circuitos aparte**: preventas (facturadas), medias reses, menudencias. |
| Stack = incógnita. | ERP propio Windows, legacy, lenguaje desconocido; API/permisos = gate. | **Gate resuelto:** ERP **VB6 (escritorio Windows) + MySQL**; Palm = **Android** (Zebra); integra balanzas/impresoras Zebra. **No hay API pública, pero el programador ofrece construir una API a medida.** |
| Trazabilidad como posible 2ª necesidad. | Romaneo = fuente de verdad del peso, no trazabilidad de exportación. | Igual. La etiqueta/romaneo sigue siendo el ancla del dato. |

**Problema en una línea:** el pedido nace digital (WhatsApp) → se pasa a papel → viaja mano a mano (oficina → cámara → romaneo → administración) → se re-tipea venta por venta al ERP. Cada salto de papel es un punto de error; el cierre diario se reconcilia a mano contra el "Diario de Cajas".

### 2. Contexto ampliado

**El flujo de ventas NO facturadas (el caso central) — [doc], paso a paso:**
1. Pedido por **WhatsApp** / presencial (muchos clientes son operarios propios). Lo reciben **Matías y Andrés**.
2. Se registra a mano en **dos planillas**: "Cortes con hueso" y "Cajas" (en cajas, "C/" = por caja, ~5 unidades c/u). Premium se marca con **"A" en círculo / birome roja**; estándar sin marca (azul/negra).
3. **Priorización** (Matías): prioridad a clientes al día de pago cuando la demanda supera el stock.
4. **Programa de despostada** (se arma el día anterior; define también qué se congela). Producción **3 días/semana: lunes y jueves = línea B (Merlo); miércoles = línea A (Criadores)**.
5. Camaristas: despostada, balanza, **etiqueta**, escaneo **Palm** (carga stock) + anotan kilo **a mano** en la planilla.
6. La planilla con kilos vuelve a **Nacho**: aplica **lista de precios** (se actualiza semanal), suma kilos, calcula importe.
7. Carga en ERP **Ventas → Cortes**, por ítem: cliente, tipo de venta, corte, **depósito**, piezas, kilos, precio, importe (precio/importe los calcula el sistema). Guardar → **descuenta stock**. Resaltador en la hoja para no omitir/duplicar.
8. **Cierre/revisión:** Informes → Venta de cortes → export Excel (filtra "ventas", no factura) → el total kg/importe debe coincidir con la hoja física. Se archiva la hoja en papel.

**Dos líneas / marcas — [doc]:**
- **Línea A = Criadores Pampeanos (Premium)** — novillos/vaquillonas, calidad 8–10. Producción miércoles.
- **Línea B = Frigorífico Merlo (Estándar)** — vacas buenas, 5–7. Producción lunes/jueves.
- En el sistema **NO se diferencian por color sino por depósito**: `{Criadores|Merlo} {Cortes con Hueso | Enfriado | Congelado}` (6 depósitos).
- **"C" tiene dos significados según posición (fuente de error):** junto al **nombre** = cuenta **"Contado"** (cliente ocasional/primera compra, sin cuenta corriente individual); junto al **pedido** = depósito **Congelado**. Ej.: "A" + "C" = Criadores Congelado.

**Tres tipos de venta — [doc]:**
- **No facturadas** — el flujo de arriba (cortes con hueso + cajas). *El foco del proyecto.*
- **Preventas (facturadas)** — módulo Preventas, se arma el día anterior. Acá el romaneo se hace escaneando el **código del cliente** con la Palm → los cortes quedan **auto-asociados al cliente** (a diferencia del no-facturado, donde Nacho vincula a mano). "Importar del colector" trae piezas/kilos; al día siguiente "Cerrar Preventa" con nº de factura → registra venta y descuenta stock. Incluye cajas, enfriados/congelados y menudencias.
- **Medias reses** — otra unidad operativa, fuera de este análisis.

**Cuenta corriente / cobranza — [doc]:**
- Venta → "Debe" **automático**. Pagos → "Haber" **manual** ("Nuevo Recibo", desde una planilla Excel de cobros del día). Negativo = saldo a favor.
- **Todo se carga a mano** (ventas y recibos) → errores → **Andrés concilia semanalmente (lunes)** su Excel contra el sistema.
- Criterio de prioridad (Matías): plazo de pago ≤ 15 días; clientes al día tienen prioridad ante stock limitado.

**Errores típicos y control — [doc]:**
- Descuadre de kg/piezas al cierre → herramienta **"Diario de Cajas"** (Excel de todas las etiquetas del día) → comparar etiqueta por etiqueta. Causas: venta mal cargada, peso mal anotado en romaneo, etiqueta con código de otro corte, o caja Premium sin "A" cargada como Estándar (depósito equivocado).
- **Control de stock físico** ~3 veces/mes sobre Merlo Enfriado y Criadores Enfriado (camaristas cuentan cajas → se compara con el sistema).

**Volumen (semana de referencia) — [doc]:**
- Lunes: 109 medias reses → 29 tipos de corte, **5.140 kg**, 238 piezas, **17 clientes**.
- Miércoles: 105 medias reses → 28 cortes, **5.001 kg**, 229 piezas, **35 clientes**.
- Jueves: 104 medias reses → 24 cortes, **4.450 kg**, 203 piezas, **32 clientes**.
- Catálogo: ~**25 cortes** (cajas/unidades) + **13 cortes con hueso**, cada uno con precio para A y B. (No incluye medias reses ni menudencias.)

### 3. Usuarios / roles / permisos — [doc, aclarado]

- **Nacho D'Agostino (administración)** — carga las ventas no facturadas al ERP y reconcilia descuadres. Nuevo (~2–3 meses), champion del cambio, junior en decisión.
- **Matías** — recibe pedidos; **coordina y administra las ventas en general**; **decide la priorización** por cuenta corriente. Es el "mi jefe" del discovery y el decisor operativo. *(Objetivo de la próxima reunión.)*
- **Andrés** — recibe pedidos; **dueño del seguimiento de cobranzas**; concilia cuenta corriente los lunes.
- **Camaristas** — despostada, balanza, romaneo con Palm; punto de captura y de error.
- **Sector facturación** — emite facturas de noche (preventas).
- **El programador / área de sistemas** — construyó y mantiene el ERP (VB6/MySQL); **gatekeeper y proveedor de la futura API**.
- **Dueños (familia)** — padre, tío, "Mariano" (ciclo 1 / servicio); sponsors últimos.

### 6. Stakeholders

| Quién | Rol en el proyecto | Qué le importa *(interpretación, anclada a [discovery](../source/meetings/2026-07-23-frigorifico-merlo-discovery.md) / [doc](../source/adhoc/2026-07-frigorifico-merlo-doc-flujos-ventas.md))* |
|---|---|---|
| **Ignacio "Nacho" D'Agostino** | Contacto, champion, usuario administrativo. | Sacarse las horas de carga manual y los descuadres. Abierto pero junior; respeta el "así se trabaja hace 40 años". Muy colaborativo (mandó doc detallado con capturas). |
| **Matías** | Coordinador de ventas y **decisor operativo** (prioriza por crédito). | Que no se rompa lo que funciona; control del riesgo de cobranza (pago ≤15 días). **Sumarlo a la próxima es clave.** |
| **Andrés** | Dueño de cobranzas / conciliación cuenta corriente. | Que la cuenta corriente cuadre; hoy conciliación manual semanal — dolor propio automatizable. |
| **El programador / sistemas** | Mantenedor del ERP; proveedor de la API a medida. | Factibilidad de integración. **Ya se mostró dispuesto a construir la API** → aliado, no bloqueante. |
| **Nacho Manes** | Referidor (amigo de Jony). | Warm intro; cuidar el vínculo. |

> Motivaciones = interpretación. Estilo de trato operativo → futuro `communication-context`.

### Factibilidad — **MEDIA-ALTA** *(subió tras el doc)*

- **Gate técnico prácticamente resuelto:** ERP en **VB6 + MySQL**, Palm Android/Zebra. **No hay API pública, pero el propio programador ofrece desarrollar una API a medida** según lo que necesitemos. Con MySQL de por medio, hay camino claro para leer/escribir datos e integrar.
- **A favor:** el cliente **es dueño del sistema y de los datos** (ideal Quarks); proceso ahora mapeado a detalle con capturas; volumen y catálogo cuantificados; área de sistemas colaborativa.
- **Riesgos que quedan:** (a) **adopción** — cultura de papel de +40 años, camaristas en la producción física; el cambio de proceso pesa tanto como el software. (b) **WhatsApp** — automatizar la lectura de pedidos depende de la vía (API oficial vs. no oficial) y costos de Meta → validar viabilidad. (c) alcance real de la API a medida (esfuerzo del programador, tiempos).

### 7. Contexto metodológico — cómo lo trabajaríamos

Base plantilla [`_contexto-metodologico.md`](./_contexto-metodologico.md). Modelo: **gestión con dependencias** (el programador del cliente construye/expone la API; nosotros nos acoplamos).

- **Enfoque Quarks:** procesos y datos primero, herramienta después. No parche aislado: automatizar el order-to-cash de punta a punta.
- **Arquitectura probable (con lo que sabemos):** una **API a medida sobre MySQL** (la construye el programador o se co-diseña) + una **capa/app propia** que: barre el pedido de WhatsApp → arma lista → cruza contra cuenta corriente → lista curada → romaneo digital desde la etiqueta (sin re-tipear) → registra la venta. El **modelo de preventa ya prueba que la Palm puede asociar corte↔cliente automáticamente** → hay precedente interno del cliente para eliminar la carga manual también en el no-facturado.
- **Quick win posible:** automatizar el **chequeo del "Diario de Cajas"** (cruce etiquetas vs. ventas cargadas) — alto valor, bajo riesgo, no depende de WhatsApp.
- **Dependencia crítica → API + accesos:** definir con el programador el alcance de la API, entornos y datos de prueba. Responsable + SLA al inicio (aprendizaje PERC).
- **Comunicación / decisión:** el decisor operativo (Matías) no estuvo en la llamada — sumarlo. Reuniones cortas para desbloquear.
- **Adopción como parte del proyecto:** subir el cambio de a poco, respetar el saber operativo, acompañar a cámara y administración.

---

## B. Pre-propuesta (cara al cliente, liviana)

- **Alcance (sí):** automatizar el **flujo de ventas no facturadas** (order-to-cash de la despostada). Camino de entrada posible: **quick win** = chequeo automático de discrepancias (Diario de Cajas vs. ventas), o **primer flujo end-to-end** (WhatsApp → lista curada por cuenta corriente → romaneo digital por etiqueta → venta sin re-tipeo). **(No / fase posterior):** preventas/facturación, medias reses, menudencias, cobranza integral, ecommerce.
- **Discovery:** 1–4 semanas para mapear a fondo y definir el alcance de la API — se vende como "equipo por X tiempo, con un discovery inicial", no suelto. *(Recordar: el discovery es etapa post-venta; ver [`_ciclo-preventa.md`](./_ciclo-preventa.md).)*
- **Prototipo:** el flujo completo **no es prototipable hoy** por la integración de WhatsApp; a lo sumo una **simulación** con datos de ejemplo partiendo de texto/Excel.
- **Cómo lo trabajamos:** API a medida sobre su MySQL (con su programador) + capa propia; respetamos que el sistema es de ellos. Extracto de la sección 7.
- **Factibilidad honesta:** **media-alta** — el programador puede construir la API; el dato vive en MySQL; el cliente es dueño de todo. Falta acordar alcance de la API y validar la vía de WhatsApp.

---

## C. Salida operativa

**Abiertos (actualizado tras el doc):**
- Alcance/esfuerzo/tiempos de la **API a medida** que ofrece el programador — reunión técnica con él.
- **Vía y viabilidad económica** de leer pedidos de WhatsApp (API Meta vs. alternativas). *(Único gran técnico que sigue abierto.)*
- Confirmar el **peso relativo de cada circuito** (no facturado vs. preventas facturadas) para elegir por dónde empezar.
- Quién es el **decisor de compra** (¿Matías? ¿el dueño?) y su disponibilidad.

> Cerrados por el doc: stack del ERP (VB6/MySQL/Android-Zebra), existencia de API (no pública, pero construible), volumen (kg/piezas/clientes por día), catálogo (~25 cajas + 13 con hueso), líneas A/B y depósitos, cuenta corriente y criterio de priorización, errores y control de stock.

**Acciones:** *(actualizado tras call interna 24-jul + doc)*
- **Minuta al cliente** — [lista](./2026-07-23-frigorifico-merlo-minuta.md); con el doc recibido, varios pedidos de evidencia ya están cubiertos → agradecer y ajustar el pedido a lo que falta (vía WhatsApp, alcance de API).
- **No prometer prototipo** del flujo completo; a lo sumo simulación futura.
- **Coordinar reunión con el dueño + Matías + el programador** — posicionar enfoque punta a punta y bajar el alcance de la API.
- **Armar/actualizar la pre-propuesta** con los números y el stack ya confirmados (base mucho más sólida).
- **Registrar aparte el lead de chocolatería B2B** (proveedor #1, ~500→1500 productos, ~300 tx/día, web-app marketplace) — otra oportunidad, no Merlo. *(En la call 24-jul apareció, para ese otro lead, un competidor SaaS ya armado — volcar a ese contexto.)*

---

*Provenance: lo marcado **[doc]** proviene del [documento de flujos del cliente](../source/adhoc/2026-07-frigorifico-merlo-doc-flujos-ventas.md); el resto, del [discovery 23-jul](../source/meetings/2026-07-23-frigorifico-merlo-discovery.md) y del research de primer contacto (21-jul).*
