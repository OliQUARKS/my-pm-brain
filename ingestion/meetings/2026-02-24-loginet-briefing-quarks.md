# Ingesta — Quarks - Loginetsa (reunión de briefing, 2026-02-24)

- **Fuente (verbatim):** [../../source/adhoc/2026-08-19-loginet-fuente-historica-completa.md](../../source/adhoc/2026-08-19-loginet-fuente-historica-completa.md) (sección "24 feb 2026 — Quarks - Loginetsa", dentro del bundle histórico aportado por el PM el 2026-08-19).
- **Shape:** meeting — primera reunión de briefing con el cliente (etapa 3 del [ciclo de preventa](../../briefings/_ciclo-preventa.md)).
- **Participantes:** Facundo Ramirez, Vanina Focaraccio, Manuel Vasquez (Loginet); Jony Ayerbe (Quarks). Se menciona a **Pablo** (encargado del sistema K/Kai) como no colaborativo, sin confirmar si asistió.
- **Nota de proceso:** esta reunión ya había ocurrido (24/2/2026) y no fue ingerida en el brain hasta hoy (2026-08-19), reconstruida a partir de un bundle histórico que el PM aportó junto con el resto del material de Loginet. Es la primera pieza de una cadena de al menos 3 reuniones + 1 propuesta formal ya redactada — ver también [2026-04-06-loginet-2do-mapeo.md](./2026-04-06-loginet-2do-mapeo.md) y [2026-05-27-loginet-scoping-interno-jony-jp.md](./2026-05-27-loginet-scoping-interno-jony-jp.md).

---

## 1. Contexto de la empresa y sistemas actuales

**(observation)** Loginet opera transporte multimodal (principalmente camión + marítimo). Sistema central: **K / Kai / CAI** (nomenclatura inconsistente en las fuentes — es el mismo sistema), un ERP/TMS legacy que maneja aspectos administrativos, contables, financieros y comerciales, evolucionado desde sus inicios. Además usan **Extract**, un bot que lee facturas en PDF y BLs y vuelca la información a Kai — con fricciones frecuentes cuando los datos no cargan o arrojan error. También tienen **Cargoes/Carghost**, un servicio de tracking de contenedores en tránsito (desarrollado por "unos árabes de su rubro" según la transcripción) que envía reportes diarios y alertas de demoras, pero cuya actualización a Kai sigue siendo manual.

**(observation)** Solo usan el sistema **INTRA** para presentar shipping instructions a algunas navieras vía integración; el resto se hace manualmente en la web propia de cada naviera. El protocolo estandarizado para que un sistema converse con la naviera es vía API — si la naviera no la tiene, no hay forma automatizada de interactuar con su portal.

## 2. Fricción central — Extract / Kai / "Rock"

**(observation)** El sistema Extract lee las facturas de las navieras "perfectamente", pero la carga automática a Kai requiere que el monto coincida exactamente con un ítem interno llamado **"Rock"** (una orden de compra/prefactura que administración genera a mano a partir de la cotización cerrada). Si el número de contenedor y el importe neto de la factura no coinciden exactamente con el Rock, Kai no la carga y arroja error — lo que fuerza intervención manual constante.

**(interpretación)** El "Rock" nació como un paso de precontrol manual porque la idea original (Extract + Kai cargando sin intervención humana) no funcionaba por inconsistencias en las facturas de las navieras y falta de cotización cargada a tiempo. (chat, no artefacto — inferido de la discusión, 2026-02-24)

## 3. Flujo comercial → operativo → administrativo (tal como se relevó)

**(observation)** Cotización manual en Excel (por la variedad de destinos y estacionalidad) → cliente acepta → se carga la cotización en Kai, lo que abre la operación → equipo operativo genera el booking en el sistema de la naviera → confirmación de booking se carga en el sistema interno para coordinar con el cliente (camiones, órdenes de retiro) → despachante envía la declaración de embarque (Excel) → se usa para presentar la shipping instruction a la naviera → la naviera devuelve el Bill of Lading (BL) → **se chequea manualmente contra la declaración, de forma visual y tedioso, especialmente en temporada alta.**

**(observation)** Una prueba experimental de comparar declaración vs. BL con IA fue exitosa pero tomaba ~10 minutos por BL — inviable en temporada alta al volumen que manejan.

**(stakeholder-verbal, Vanina Focaraccio, 2026-02-24)** La clave es hacer la verificación de diferencias **antes** de presentar la shipping instruction — una vez emitido el BL, la mayoría de las correcciones tienen costo.

## 4. Facturación y liberación de carga

**(observation)** Tras la salida del buque, administración tiene 48hs para facturar al cliente — requiere BL cargado correctamente, salida confirmada (zarpe) y cotización cargada en el sistema. Las navieras facturan a Loginet ~48hs después de la salida; el control de esas facturas de compra es manual (comparación contra la cotización de compra cargada en Kai) y, si coincide, se genera el "Rock".

**(observation)** Liberación de carga: requiere verificar que el flete esté pagado y tener autorización explícita del cliente. Se necesita una alerta ~48hs antes de la llegada para movilizar la documentación.

## 5. Rol de las personas / dinámica interna

**(stakeholder-verbal, Facundo Ramirez, 2026-02-24)** Sugirió que el problema de integración podría residir en **Pablo**, la persona a cargo del sistema K, reacio a reunirse o colaborar en las integraciones necesarias.

**(stakeholder-verbal, Facundo Ramirez, 2026-02-24)** La tendencia del negocio apunta a la automatización de procesos internos (envío de facturas, rastreo de envíos), mientras el valor humano se enfoca en la personalización del servicio.

**(observation)** Vanina Focaraccio se ofreció a compartir un documento detallado del paso a paso de los procesos comercial/operativo/administrativo — **probable origen** del diagrama de flujo preservado en [`source/adhoc/2026-08-19-loginet-flujo-proceso-diagrama.pdf`](../../source/adhoc/2026-08-19-loginet-flujo-proceso-diagrama.pdf), aunque no está confirmado que sea el mismo artefacto.

## 6. Cierre de la reunión — próximo paso acordado

**(observation)** Se decidió encarar un **Discovery** (sesiones/workshop) como primer paso, para mapear el 100% de los procesos, del que resultaría una propuesta de alcance/tiempos/costos priorizando el mayor valor al menor costo (enfoque MVP/iterativo). Jony Ayerbe enviaría preguntas estructuradas de forma asincrónica a Facundo Ramirez, Vanina Focaraccio y Manuel Vasquez antes de proponer el Discovery formalmente.

---

## Ruteo

- **Stakeholders creados:** [`stakeholders/facundo-ramirez.md`](../../stakeholders/facundo-ramirez.md), [`stakeholders/vanina-focaraccio.md`](../../stakeholders/vanina-focaraccio.md), [`stakeholders/manuel-vasquez.md`](../../stakeholders/manuel-vasquez.md), [`stakeholders/pablo-loginet.md`](../../stakeholders/pablo-loginet.md) (este último marcado explícitamente como distinto de `pablo-folgar.md`, que es QA de Quarks en PERC — personas distintas, no confundir).
- **No se generó decisión formal** — en esta reunión no se comprometió alcance/tiempo/costo, solo el acuerdo de avanzar a un Discovery. No corresponde crear un archivo en `decisions/` todavía.
- **Pendiente:** no se encontró en el repo un `briefings/` para esta reunión (sería la etapa 2 del ciclo de preventa, `/briefing-context`, que en este caso nunca se corrió porque el brain no existía aún en esa fecha). No se retrofittea un briefing-context retroactivo — el valor ya está capturado acá y en el build-context que se arme a partir de todo este material.
