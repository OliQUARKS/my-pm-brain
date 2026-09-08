# Propuesta, RyD Abogados: automatización del circuito de pedido de pago (Provincia ART)

## 1. Qué entendimos

El equipo a cargo de Juan Verde (7 personas) dedica una parte significativa de su tiempo a un proceso administrativo repetitivo: cada expediente que llega a sentencia firme o a un acuerdo homologado con Provincia ART genera entre 6 y 7 pedidos de pago separados, uno por cada parte involucrada (actor, abogado, perito, tasa de justicia), cada uno con su propio CBU y su propia documentación requerida. Conseguir esa documentación de terceros (hoy por mail, a cuentagotas) y cargarla pedido por pedido en el portal de Provincia ART absorbe un tiempo considerable, con una carga por persona que puede llegar a varios pedidos de pago diarios. Hoy tampoco existe una vista consolidada de qué expedientes están trabados y a qué parte le falta qué; el seguimiento se hace expediente por expediente, de forma manual. Ese tiempo administrativo es tiempo que el estudio preferiría dedicar al trabajo legal de fondo.

## 2. La solución en una frase

Un asistente de gestión que acompaña el circuito de pedido de pago de punta a punta: da visibilidad consolidada de qué expedientes están trabados y por qué, agiliza el pedido de documentación a terceros, y prepara la carga en Provincia ART, sin reemplazar Lex Doctor ni el portal de la aseguradora, sino orquestando alrededor de ambos.

## 3. Qué hace, funcionalidad del MVP

- **Seguimiento consolidado de expedientes.** Una vista única de qué expedientes tienen pedidos de pago pendientes, qué documentación falta por cada sub-pago (actor, abogado, perito, tasa de justicia) y de quién depende conseguirla; reemplaza el seguimiento manual expediente por expediente.
- **Asistencia en el pedido de datos a terceros.** Generación y seguimiento de los mails de pedido de documentación (CBU, DNI, factura) a abogados y peritos, con recordatorios automáticos cuando no hay respuesta.
- **Preparación de la carga.** Organiza y deja lista la información reunida por cada sub-pago, para que la carga en el portal de Provincia ART sea más rápida y con menos errores.
- **Conciliación del pago.** Cuando llega la constancia de pago de Provincia ART, queda vinculada automáticamente al expediente y al sub-pago correspondiente.

**Fuera del MVP (fases posteriores):**
- Carga automática en el portal de Provincia ART sin intervención humana (depende de la vía técnica que se confirme en el discovery).
- Extensión del mismo enfoque a los otros clientes del estudio, más allá de Provincia ART.
- Extensión a otras áreas del estudio (por ejemplo, mediaciones).

## 4. Cómo se apoya en los sistemas del cliente

RyD Abogados no cambia de sistema. Lex Doctor sigue siendo la fuente de verdad de expedientes, estados y documentación del estudio: el asistente se apoya en esa información y no reemplaza ninguna de sus funciones actuales. La carga final en el portal de Provincia ART tampoco se reemplaza de forma automática en esta primera etapa: durante el discovery vamos a confirmar junto a ustedes el circuito exacto de carga y qué nivel de automatización es viable ahí, y avanzamos primero con lo que sea seguro y sostenible.

Todo el trabajo de diseño, prototipado y pruebas se hace con información genérica, no con datos reales de expedientes ni de terceros, así podemos avanzar en paralelo a que se defina cualquier marco de tratamiento de datos que el estudio considere necesario.

## 5. Cómo trabajamos

- **Metodología ágil.** Trabajamos en iteraciones cortas, con revisiones frecuentes junto al equipo de RyD para validar que lo que construimos refleja el proceso real, y no una versión ideal que nadie termina usando.
- **Etapa inicial de alineación (discovery).** Antes de construir, dedicamos un tramo inicial a profundizar el circuito con casos reales, confirmar las vías técnicas disponibles en el portal de Provincia ART y despejar las dudas que quedaron abiertas en la reunión de relevamiento. Esto evita construir sobre supuestos.
- **Implementación por fases.** Arrancamos por el tramo de mayor impacto y menor riesgo (seguimiento consolidado y pedido de datos a terceros) y sumamos automatización de carga y otras áreas del estudio en fases posteriores, a medida que se validan.
- **Gestión transparente.** Reuniones periódicas de seguimiento, visibilidad del avance y documentación de cada decisión de producto, para que el equipo de RyD siempre sepa en qué estado está el proyecto.
- **Calidad y validación con el equipo real.** Cada entrega se prueba con las personas que efectivamente van a usarla en el día a día, no solo internamente, para asegurar adopción real desde el primer momento.
- **Propiedad del cliente, partner de largo plazo.** Lo que se construye queda para RyD Abogados. No es una solución cerrada que dependa de nosotros indefinidamente, y quedamos disponibles para seguir sumando valor a medida que el estudio lo necesite.

## 6. Roadmap a futuro

- Automatización de la carga en el portal de Provincia ART, una vez validada la vía técnica en el discovery.
- Extensión del mismo enfoque a los demás clientes del estudio, si el patrón se confirma similar al de Provincia ART.
- Extensión a otras áreas del estudio (por ejemplo, el circuito de mediaciones).

## 7. Próximos pasos

- Coordinar una reunión para presentar esta propuesta y resolver dudas.
- Acordar el alcance del discovery inicial (2 a 3 semanas), donde profundizamos el circuito con casos reales y confirmamos las vías técnicas disponibles.
- Una vez acordado, arrancar el discovery con el relevamiento de material y la validación técnica del portal de Provincia ART.
