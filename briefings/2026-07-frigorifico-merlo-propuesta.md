# Propuesta — Digitalización del circuito de ventas · Frigorífico Merlo

**Preparado por:** Quarks · **Para:** Frigorífico Merlo
**Deriva de:** [build-context](./2026-07-frigorifico-merlo-build-context.md) (interno) · acompaña al [prototipo navegable](https://claude.ai/code/artifact/4bc2ca1a-a1c0-4250-a0a4-51aa3e662dda)

> Documento cara al cliente. El presupuesto (equipo, tiempo, inversión) y los flujos de trabajo se adjuntan como hojas aparte.

---

## 1. Qué entendimos

Hoy el pedido de cortes **nace digital** (llega por WhatsApp o de forma presencial) pero enseguida se vuelca a papel y circula de mano en mano —de la oficina a cámara, de cámara a administración— hasta que finalmente se vuelve a cargar, dato por dato, en el sistema. En ese ida y vuelta entre el papel y la pantalla es donde se cuela el error: un peso anotado distinto al de la etiqueta, una caja Premium sin su marca, una venta cargada en el depósito equivocado.

El costo no está tanto en cada error puntual como en **encontrarlo**: al cierre, cuando el stock no cuadra, hay que revisar venta por venta contra el Diario de Cajas, y eso puede llevar horas de trabajo administrativo cada día. Con un volumen de alrededor de 105 medias reses y más de 30 clientes en una jornada de producción, esa carga manual se vuelve pesada y difícil de sostener.

## 2. La solución, en una frase

Una **plataforma que digitaliza el circuito de ventas de la despostada de punta a punta** —desde que entra el pedido hasta que la venta queda registrada y el día cierra cuadrado—, apoyándose en el sistema que Merlo ya tiene y eliminando la recarga manual de datos.

Tiene dos caras que trabajan juntas: la **gestión en administración** (donde se ordenan, priorizan y registran las ventas) y la **captura en cámara** (donde el peso de la etiqueta alimenta la venta sin volver a anotarse a mano).

## 3. Qué hace — funcionalidad del MVP

**A. Ingreso y priorización de pedidos**
- Los pedidos que llegan (WhatsApp y presencial) se ordenan en una **lista digital única**, separada por línea A (Criadores Pampeanos) y B (Merlo), sin planillas de papel.
- Cada cliente muestra su **estado de cuenta corriente al lado del pedido**, para decidir con criterio a quién se atiende primero cuando la demanda supera el stock.
- El mecanismo exacto de captura del pedido (incluida la lectura asistida de los mensajes de WhatsApp) se define en el discovery, para elegir el camino más sólido y conveniente.

**B. Programa de despostada**
- El programa del día se arma **automáticamente** a partir de los pedidos confirmados: qué corte, cuánto y de qué línea. Es lo que baja a cámara, sin rehacer la planilla a mano.

**C. Romaneo y venta**
- El **peso llega desde la etiqueta de la balanza**, ya asociado a su cliente —tal como hoy ya ocurre con la Palm en las preventas—, y la **venta se arma sola**: depósito según la línea, precio de la lista de la semana e importe calculado. Nadie vuelve a tipear kilos.

**D. Cierre y control**
- Al registrar las ventas, el sistema **cruza automáticamente lo cargado contra el Diario de Cajas** y, si algo no cuadra (una diferencia de peso, una caja sin marca de línea, un depósito equivocado), lo **marca al instante** con la corrección sugerida, en lugar de tener que buscarlo corte por corte.

**Fuera del MVP (fases posteriores):** el circuito de **preventas y facturación**, la venta de **medias reses** y **menudencias**, la gestión integral de **cobranzas**, la **venta online** a gastronómicos/mayoristas y los **tableros de análisis**. Todo esto queda identificado como camino de crecimiento (ver sección 6), no como parte de esta primera etapa.

## 4. Cómo se apoya en el sistema que ya tienen

**No reemplazamos su ERP.** El sistema propio de Merlo sigue siendo el lugar donde vive la información; la plataforma se **acopla** a él.

- La integración se realiza mediante una **API a medida sobre la base de datos del sistema**, que el equipo de sistemas de Merlo puede desarrollar o co-diseñar con nosotros.
- Se **leen** los maestros que ya existen (clientes y sus cuentas, lista de precios, stock y depósitos) y se **registran** las ventas del circuito; el resto sigue funcionando exactamente como hasta hoy.
- Las **balanzas e impresoras de etiquetas** y la operatoria de cámara no cambian: la plataforma se apoya en ese dato que ya se genera, en lugar de pedir que se cargue dos veces.

El objetivo es sumar capacidades sobre lo que ya funciona —y que **la información y el sistema sigan siendo de Merlo**—, no atarlos a una herramienta cerrada.

## 5. Cómo trabajamos

- **Empezamos por el proceso y los datos, no por la herramienta.** Antes de construir, mapeamos el circuito real y acordamos con su equipo de sistemas cómo integrarnos. *Así lo que se automatiza mejora el proceso en vez de replicar sus problemas.*
- **Etapa inicial de alineación.** Una primera fase corta para definir en conjunto el alcance de la integración, los accesos y los datos de prueba. *Evita sorpresas y arranca el desarrollo sobre base firme.*
- **Trabajo ágil, por fases.** Entregas incrementales y navegables desde temprano, empezando por el tramo que más alivia la carga diaria. *Ven valor rápido y ajustamos sobre algo real, no sobre un documento.*
- **Gestión transparente.** Reuniones cortas para desbloquear, visibilidad del avance y documentación del proceso que queda para ustedes. *Siempre saben en qué estamos y por qué.*
- **Calidad y adopción como parte del proyecto.** Probamos en vivo y acompañamos la transición del equipo de administración y de cámara —gente que trabaja así hace muchos años— para que la herramienta se use, no que quede de adorno. *La mejora sólo cuenta si el equipo la adopta.*
- **Propiedad del cliente y relación de largo plazo.** El sistema y los datos quedan de su lado; nosotros acompañamos el crecimiento como socio tecnológico. *Invierten en capacidad propia, no en una dependencia.*

## 6. Roadmap a futuro

Una vez resuelto el circuito de ventas no facturadas, la misma base habilita crecer por pasos:

- **Preventas y facturación** integradas al mismo flujo.
- **Cobranzas y cuenta corriente** con conciliación asistida (hoy manual, semanal).
- **Medias reses y menudencias** dentro de la plataforma.
- **Venta online B2B** para gastronómicos y mayoristas, sobre la misma operatoria.
- **Tableros** de ventas, stock y clientes para decisiones comerciales.

Son un camino de valor, no una promesa incluida en esta etapa.

## 7. Próximos pasos

1. **Reunión técnica con el equipo de sistemas** para definir el alcance de la API de integración.
2. **Demo del prototipo navegable** que ya preparamos, para ver el flujo en pantalla y ajustarlo con ustedes.
3. **Confirmar insumos** (lista de cortes/depósitos, ejemplos de pedidos, identidad de marca).
4. **Arranque del discovery** para bajar a detalle fino el flujo, el alcance y las fases.

---

*Anexos a adjuntar antes de enviar: hoja de presupuesto (equipo, tiempo, inversión) y diagrama de flujos de trabajo.*
