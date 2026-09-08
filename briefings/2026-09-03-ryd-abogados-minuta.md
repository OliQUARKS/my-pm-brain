> **Nota interna (no enviar)**
> **Objetivo del mail:** que RyD valide el flujo de pedido de pago tal como lo entendimos, y que nos habilite el material que falta para poder armar la propuesta técnica. No hay decisor ausente al que convocar (Juan Verde y Hernán Capolupo, ambos socios, ya estuvieron en la reunión), así que el "próximo paso" es agendar la presentación de la propuesta conceptual, no una reunión de escalación.
> **Qué NO prometer:** ni prototipo, ni una solución técnica específica (agente, RPA, integración por API). Ya revisamos los manuales técnicos de Lex-Doctor (ingeridos 2026-09-04): no documentan API ni acceso SQL directo, así que cualquier promesa de integración sigue siendo alcance no confirmado. Tampoco prometer que el mismo enfoque sirve para los otros 9 clientes del estudio: solo relevamos Provincia ART en detalle.
> **No pedir de nuevo:** documentación técnica de Lex Doctor (ya la tenemos y la revisamos internamente).
> **A quién se escala:** nada que escalar; el foco (área de Juan Verde, pedidos de pago) ya lo fijaron Federico y Juan Pablo Norverto en la propia reunión.
> **Quién aumenta el borrador:** Olivier redacta; Juan Pablo Norverto (o Federico) suma si hay matices técnicos antes de enviar.
> **Destinatarios sugeridos:** Juan Francisco Verde y Hernán Capolupo (RyD Abogados). CC interno: Federico Fernandez, Juan Pablo Norverto.

---

Hola Juan, hola Hernán,

Gracias por el tiempo de la reunión de ayer y por mostrarnos el proceso en vivo dentro de Lex Doctor, que nos ayudó mucho a entender el día a día real del equipo. Les dejamos por escrito lo que entendimos, para que lo validen (o corrijan lo que haga falta), y un pedido puntual de material para poder avanzar. Si les sirve, pueden circular este mail con quien consideren.

**Quiénes somos**

A diferencia de una solución puntual (un bot, una mini-app o una integración aislada), en Quarks miramos la operación y el negocio de punta a punta: diagnóstico primero, herramientas después.

Muchas veces los procesos ya están rotos. Sin ese diagnóstico previo, se terminan implementando herramientas que replican los mismos problemas, o se fuerza el flujo de trabajo para que encaje en la herramienta de moda. Nosotros no forzamos nada: combinamos lo que ya existe con lo que hace falta crear a medida, para resolver los dolores reales y destrabar los desafíos particulares de cada cliente, respetando sus recursos y su realidad operativa.

En síntesis, los ayudamos a crecer y escalar a través de la tecnología.

**Lo que entendimos del proceso actual (pedido de pago, Provincia ART)**

Así entendimos el circuito, desde que un expediente llega a sentencia firme o acuerdo homologado hasta que se acredita el pago. Por favor avísennos si algo no es exactamente así:

1. Se actualiza el estado del expediente en Lex Doctor (sentencia firme / acuerdo homologado) y se verifica que la sentencia, homologación o liquidación esté correctamente cargada.
2. Se crea el evento correspondiente ("Solicitud Fondos - Acuerdo" o "Solicitud Fondos - Sentencia"), con fecha y vencimiento del pago.
3. Como cada expediente puede involucrar distintas partes (actor, abogado, perito) con distinto CBU y distinta documentación requerida, se generan varios pedidos de pago separados para un mismo expediente (en algunos casos, 6 o 7).
4. Para armar cada pedido de pago hace falta reunir la documentación de la parte correspondiente: CBU, DNI (para el actor) o CBU + constancia ARCA + factura discriminada (para abogado y perito). Esa información no siempre está disponible de entrada: se pide por mail al abogado interviniente, y a veces llega en partes.
5. Una vez reunida la documentación de una parte, se carga el pedido de pago en el portal de Provincia ART.
6. El seguimiento de qué falta por expediente se hace hoy a través de la agenda de Lex Doctor, un recordatorio por expediente, revisado día a día por cada persona, sin una vista consolidada de "qué expedientes están trabados y por qué falta".
7. Cuando Provincia ART procesa el pago, envía un mail automático con la constancia, que hoy se acredita manualmente en el expediente.

¿Es correcto este flujo? ¿Hay pasos que se nos escaparon o que funcionan distinto según el tipo de proceso (sentencia vs. acuerdo)?

**Dónde identificamos el dolor**

- El cuello de botella no es solo la carga: es la combinación de **pedir la información** (mails a abogados y peritos, que llegan a cuentagotas) **y cargarla**, ambas tareas manuales.
- Con 7 personas dedicadas a esto y expedientes que se ramifican en 6-7 pedidos de pago cada uno, el volumen de carga administrativa es alto; mencionaron que una sola persona puede tener alrededor de 20 pedidos de pago agendados en un día.
- Esta carga hoy le está quitando tiempo al trabajo estrictamente legal (contestaciones de demanda, defensa), que es donde el estudio agrega más valor.

**Qué necesitaríamos para avanzar**

Para poder armar una propuesta concreta, nos serviría contar con:

1. El instructivo completo de carga de pedidos de pago de Provincia ART (nos llegó un extracto por mail; si hay una versión más completa o actualizada, la agradecemos).
2. Dos ejemplos reales (pueden ser anonimizados) de expedientes completos: uno resuelto por **sentencia** y otro por **acuerdo homologado**, con capturas de cada pantalla de Lex Doctor involucrada (evento, carga de documentación, agenda), para poder contrastar si el circuito varía entre ambos casos.
3. Una captura del portal de Provincia ART donde se cargan los pedidos de pago, para entender si existe alguna vía de integración además del ingreso manual por navegador.
4. Un ejemplo real (texto del mail, sin datos sensibles) de una solicitud típica de documentación a un abogado o perito, tal como se envía hoy.
5. Un número aproximado de pedidos de pago que se cargan por semana o por mes solo para Provincia ART, para poder dimensionar el impacto de cualquier mejora.
6. Confirmación de si este mismo patrón (documentación por CBU, 6-7 pedidos por expediente) se repite igual en los otros clientes del estudio, o es específico de Provincia ART.

**Próximos pasos**

Con ese material y la validación del flujo, del lado de Quarks vamos a armar una propuesta conceptual sobre por dónde atacar esta automatización y cómo la encararíamos técnicamente. Nos gustaría coordinar una próxima reunión para presentarla; quedamos atentos a su disponibilidad.

Quedamos a disposición por cualquier duda.

Saludos,
Equipo Quarks
