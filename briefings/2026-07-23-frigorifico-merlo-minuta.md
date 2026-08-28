# Minuta — Reunión 23/07 · Frigorífico Merlo

**Tipo:** cara al cliente · **Deriva de:** [build-context](./2026-07-frigorifico-merlo-build-context.md) · [discovery 23-jul](../source/meetings/2026-07-23-frigorifico-merlo-discovery.md)
**Para:** Ignacio (Nacho) D'Agostino (para escalar a Matías / el dueño)
**De:** Quarks — Jonathan Ayerbe / Olivier
**Asunto sugerido:** Minuta reunión 23/07 + qué necesitamos para avanzar — Frigorífico Merlo

> **Nota interna (no enviar):** borrador para que Jony sume lo suyo antes de mandar. Objetivo del mail (acordado en call Oli↔Jony 24-jul): **detallar lo que entendimos + pedir validación + pedir evidencia (fotos/capturas)**, y dejar pedida la **reunión con el dueño**. **No** prometemos prototipo (el flujo completo no es prototipable hoy por la integración de WhatsApp). En la reunión con el dueño se aclara que iríamos por **automatización de punta a punta**, no una curita aislada.

---

Hola Nacho, gracias por el tiempo del miércoles. Les compartimos el resumen de lo que entendimos para que puedan validarlo, junto con el material que necesitaríamos para avanzar. La idea es que puedas hacerlo circular con Matías y con el dueño.

## Quiénes somos

A diferencia de una solución puntual —un bot, una mini-app o una integración aislada—, en Quarks miramos la operación y el negocio de punta a punta: **diagnóstico primero, herramientas después**.

Muchas veces los procesos ya están rotos. Sin ese diagnóstico previo, se terminan implementando herramientas que replican los mismos problemas, o se fuerza el flujo de trabajo para que encaje en la herramienta de moda. Nosotros no forzamos nada: combinamos lo que ya existe con lo que hace falta crear a medida, para resolver los dolores reales y destrabar los desafíos particulares de cada cliente, respetando sus recursos y su realidad operativa.

En síntesis, los ayudamos a crecer y escalar a través de la tecnología.

## Lo que entendimos del proceso actual

El pedido nace digital (WhatsApp) pero se vuelca a papel y circula de mano en mano hasta que se vuelve a cargar en el sistema:

1. Ingresa el pedido por WhatsApp o presencial y se registra en una hoja (una de **cajas** y otra de **cortes con hueso**).
2. Se prioriza según cuenta corriente (quienes están al día en el pago) y se pasa a una segunda hoja formal, con cliente y pedido, **sin kilos**.
3. Pasa a los camaristas: despostada, balanza, etiqueta, escaneo con la Palm (que carga el stock) y registro del kilo **a mano**.
4. La hoja con los kilos vuelve a administración, donde se aplica la lista de precios, se calcula el importe y se **vuelve a cargar la venta** en el ERP.

**Dónde identificamos el dolor:** cada traspaso en papel introduce un punto de error (transcripción, premium/estándar mal marcado, kilo anotado distinto al de la etiqueta). Corregir un solo descuadre puede llevar entre 20 y 40 minutos, y el cierre diario de ventas insume varias horas, aun cuando la etiqueta ya contiene el dato correcto.

Nos interesa que **validen si este flujo es correcto**: es la base sobre la que vamos a construir la propuesta, así que cualquier corrección o detalle que falte nos resulta clave.

## Qué necesitaríamos para avanzar

Cuanto más material podamos revisar, más precisa será la propuesta. Idealmente:

1. **Fotos de las hojas/planillas:** la de pedidos (borrador), la formal que pasa a los camaristas y la que vuelve con los kilos.
2. **Un ejemplo real de un pedido por WhatsApp** (captura de un mensaje típico de un cliente).
3. **Capturas del ERP:** varias pantallas —carga de ventas, control de stock, cuenta corriente, diario de cajas y los depósitos (A / P).
4. **Diferenciación premium / estándar (A/B):** cómo se distinguen hoy en el circuito más allá del color rojo/azul en la hoja, y cómo se refleja en el sistema.
5. **Sobre el ERP:** en qué lenguaje o tecnología está desarrollado y si expone alguna API o acceso a la base de datos. Idealmente, poder coordinar unos minutos con el programador que lo mantiene.
6. **Volumen:** pedidos y clientes por día de producción, y cantidad de cortes/SKUs distintos.
7. **Cuenta corriente:** cómo se define hoy la prioridad de pago y si esa información está disponible en el ERP.

## Próximos pasos

- Ustedes **validan el flujo** descripto y nos hacen llegar el material que puedan reunir.
- Con eso, coordinamos una **reunión con el dueño** (idealmente con el programador presente) para presentar una **propuesta conceptual** de cómo automatizaríamos el proceso.
- En paralelo, continuamos profundizando la investigación del sector que ya iniciamos.

Quedamos a disposición para cualquier consulta.

Saludos,
Equipo Quarks
