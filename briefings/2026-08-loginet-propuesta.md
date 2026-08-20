# Propuesta — Loginet — 2026-08-19

## 1. Qué entendimos

Loginet gestiona hoy alrededor de 4.000 Bill of Ladings al año, con picos de hasta 400 contenedores por semana durante la temporada alta. Buena parte del proceso de armado y envío de la documentación de embarque —declaraciones y shipping instructions— se resuelve de forma manual: la declaración llega por email, se lee y se transcribe a mano en el portal de cada naviera, y recién se detectan los errores cuando la naviera devuelve el Bill of Lading, momento en el que corregirlos ya tiene un costo. Ese proceso manual, sumado a que la información de cada operación queda repartida entre distintas herramientas, genera errores costosos justo en el momento de mayor volumen del año.

## 2. La solución en una frase

Una plataforma propia que lee y valida automáticamente las declaraciones de embarque antes de enviarlas, se integra con Maersk para automatizar el envío y la confirmación de la documentación, y guarda toda la operación en una base de datos propia, trazable y consultable.

## 3. Qué hace — funcionalidad del MVP

**A. Ingesta y validación de declaraciones**
- Lee automáticamente las declaraciones de embarque que llegan por email de los exportadores, sin importar si vienen en Excel, PDF o en el cuerpo del mensaje.
- Extrae y normaliza la información a un esquema único, más allá del formato de origen.
- Valida los datos contra las reglas de negocio del rubro (rangos de temperatura por tipo de carga, campos obligatorios, consistencia general) antes de que la información avance.
- Deja todo listo para una revisión humana simple y rápida antes de confirmar el envío — el equipo mantiene el control final en cada operación.

**B. Integración con Maersk**
- Envía automáticamente la Shipping Instruction a Maersk a través de su API, sin necesidad de cargarla a mano en su portal.
- Recibe el Draft Bill of Lading que devuelve Maersk y lo valida automáticamente contra lo enviado, alertando cualquier diferencia antes de la confirmación final.

**C. Base de datos propia y trazabilidad**
- Toda la información de cada operación queda registrada en una base de datos propia de Loginet — sin depender de un tercero para acceder a su propio historial.
- Cada paso queda auditado: quién aprobó, qué se envió, qué respondió la naviera.
- Sienta la base para construir, más adelante, cualquier consulta o tablero de visualización sobre la operación completa.

**Fuera del MVP (fases posteriores)**
- La integración con el resto de las navieras con las que trabaja Loginet — se incorporan de forma incremental una vez validado el funcionamiento con Maersk.
- Cualquier cambio sobre el sistema de gestión que Loginet usa hoy — este MVP no lo reemplaza ni lo modifica (ver sección 4).
- La automatización de la carga de cotizaciones comerciales y de la conciliación de facturas de proveedores — quedan identificadas como oportunidades a evaluar en una etapa posterior (ver Roadmap).

## 4. Cómo se apoya en los sistemas de Loginet

La plataforma se construye como una capa adicional, no como un reemplazo del sistema de gestión que Loginet usa hoy. No se modifica ni se migra nada de lo existente: la nueva plataforma resuelve el tramo específico entre la recepción de la declaración de embarque y la confirmación del Bill of Lading, y mantiene su propio registro de esa parte del proceso. El resto de la operación —facturación, administración, cuentas corrientes— sigue funcionando exactamente igual que hoy. Esto permite ver resultados concretos sin necesidad de una migración de sistemas ni de coordinar cambios sobre herramientas que ya están en uso. Cualquier necesidad puntual de acceso o coordinación con el equipo interno que administra el sistema de gestión se confirma en la etapa inicial de alineación, antes de arrancar el desarrollo.

## 5. Cómo trabajamos

- **Metodología ágil.** Trabajamos en sprints cortos con revisiones periódicas, para que el avance sea visible desde la primera semana y no recién al final del proyecto.
- **Etapa inicial de alineación.** Antes de desarrollar, confirmamos junto al equipo de Loginet el detalle técnico de la integración con Maersk y formalizamos las reglas de negocio a validar. No partimos de cero: ya relevamos buena parte del proceso en las conversaciones previas, así que esta etapa es acotada.
- **Implementación por fases.** Arrancamos por el tramo de mayor impacto —declaraciones y Maersk— y mostramos resultado sprint a sprint, priorizando que haya algo funcionando cuanto antes.
- **Gestión transparente.** Reuniones periódicas de seguimiento, visibilidad continua del progreso, y documentación de cada decisión funcional y técnica a medida que se toma.
- **Validación con operación real.** Cada entrega se prueba contra operaciones reales de Loginet antes de darla por cerrada, para asegurar que funciona con el volumen y la variedad real del negocio, no solo en un ambiente de prueba.
- **Propiedad del cliente.** Todo lo que se construye —código, base de datos, lógica de negocio— es de Loginet. Buscamos ser un partner de largo plazo, no un proveedor puntual.

## 6. Roadmap a futuro

Una vez validado el funcionamiento del MVP, estas son las líneas de valor que quedan abiertas para fases siguientes:

- Incorporación progresiva del resto de las navieras al mismo esquema de validación e integración.
- Automatización de la carga de cotizaciones comerciales, para reducir la fricción entre el área comercial y administrativa.
- Automatización de la conciliación de facturas de proveedores.
- Integración del tracking de contenedores a la base de datos propia, con alertas automáticas de demoras.
- Evaluación, sobre esta base ya consolidada, de qué otras partes de la operación conviene sumar a la plataforma propia.

## 7. Próximos pasos

- Confirmar el detalle técnico de la integración con la API de Maersk (alcance de campos, formato del Draft Bill of Lading).
- Formalizar junto al equipo de Loginet las reglas de negocio a validar (rangos de temperatura y demás condiciones por tipo de carga).
- Coordinar los accesos necesarios del lado de Loginet para arrancar el desarrollo.
- Definir fecha de kickoff.

---

*Equipo, cronograma e inversión se comparten en una hoja de presupuesto aparte.*
