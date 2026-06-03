# Ingestion: Estructura DB, firma digital y entorno de desarrollo (2026-06-03)

**Source:** [2026-06-03-estructura-db-firma-entorno.md](../../source/meetings/2026-06-03-estructura-db-firma-entorno.md)
**Kind:** meeting (interna Quarks — refinamiento técnico, mismo día que la Daily)
**Participants:** Olivier (PM), Nicolás (TL), dev Quarks (Marco)

## TL;DR

Refinamiento técnico de los bloqueantes de la Daily 3/6, con detalle accionable. Sale el **detalle exacto de lo que PERC tiene que entregar** (credenciales/bucket/región S3, un "tiro" real del evento de Amazon, entorno dev) y aparece una **definición concreta sobre la firma** (modelo de iniciales tipo DocuSign, pendiente de que compliance confirme si alcanza legalmente). También quedan definidas **acciones de proceso del PM**: agregar a los devs al canal con PERC y agendar una reunión-recurrente forzadora de decisiones.

## Observaciones (tagged)

### Infra S3 — qué necesita Quarks de PERC
- **[observation]** Tanto los documentos que sube el backoffice como los que genera el backend (con los valores de cada usuario) van a parar a S3.
- **[observation]** PERC dio un ejemplo en la collection de Insomnia, pero falta lo operativo para conectarse: **bucket, región, credenciales** (alcanza con credenciales temporales que luego den de baja).
- **[observation]** Nico va a verificar si la región/config ya está predefinida en la Lambda que PERC usa; igual conviene pedirlo. Hacer un mock suma tiempo y "el tiempo corre en este proyecto".

### Evento de Amazon / JWT — el "tiro" que falta
- **[observation]** El evento para crear/cambiar usuario depende del entorno de dev. Con LocalStack se podría simular un evento de Amazon, pero (1) LocalStack habría que **pagarlo**, y (2) estarían simulando **sin conocer la estructura real** del evento de PERC.
- **[observation]** Necesitan que PERC haga un **"tiro" real** (un disparo del evento del handler) para ver cómo viene cargado: si trae user ID, tag, y con qué más. Esto es para reemplazar el JWT por algo más usable.
- **[interpretation]** El bloqueo de infra no es solo "danos acceso a S3": es "danos visibilidad real de cómo se comporta su evento", que un mock no resuelve.

### Entorno dev — urgencia reforzada (Nico)
- **[observation]** Nico insiste: el entorno de dev debe quedar **configurado cuanto antes**, no en el próximo sprint. Si lo dejan para el próximo sprint, recién ahí podrían empezar a ver el deploy y posibles problemas.
- **[observation]** Hoy está **todo en local** con el problema de LocalStack, que Nico considera "bastante bloqueante" y quiere cambiar ya.
- **[observation]** Confirmado: **no se pueden guardar los documentos firmados sin el entorno**. (Olivier lo verbaliza, Nico asiente.)

### Firma digital — definición concreta (pendiente compliance)
- **[observation]** Lo último que dijo Seba: la firma funciona **estilo Panda/DocuSign** ("Simiel") — el usuario da *confirmar* y el sistema inserta las **iniciales de nombre y apellido** como consentimiento. **No** hay firma manuscrita a mano alzada.
- **[observation]** Implementación tentativa: en el template HTML, donde dice "firma", se pone una variable y se inyecta la inicial de nombre/apellido desde el BO/BAC; se arma con eso.
- **[observation]** En la UI el usuario **nunca** tiene un botón explícito de "firmar": ve el documento, toca *continuar* en cada paso y se firma automáticamente.
- **[interpretation]** Nico cree que "por un tema legal van a necesitar algo un poco más estricto" que las puras iniciales. **Depende de una definición de compliance de PERC** — es la pregunta abierta clave de la firma.

### Proceso / acciones del PM (Olivier)
- **[decision]** Olivier va a **agregar a los devs de Quarks al canal con PERC** (mejor que reenviar mensajes manualmente y arriesgar que se pierdan).
- **[decision]** Olivier va a **agendar una reunión recurrente** con PERC para forzar decisiones on-the-fly — "si les mando un mail, no me contestan nunca". Horario propuesto: **10:45–11:00** (después de la daily), franja libre la semana que viene.
- **[decision]** Mandar a PERC un **resumen/agenda previa** de los temas a tratar, así pueden pre-consultar con compliance y no se llevan todo "para verlo después".
- **[observation]** PRs a PERC: mandar la nueva collection de Insomnia ya (PRs más chicos/atómicos). Las anteriores (1ª y 2ª) ya están aprobadas y mergeadas.

### DB structure
- **[observation]** "Cuotas vs. payments": el dev va a armar **la estructura** (un mini, no implementación completa) y mandar un PR para que **Nico la valide** antes de implementar — para no implementar y rehacer.

## Routing

- **source/** ✅ · **ingestion/** ✅ (este archivo)
- **Promoción a knowledge/**: propuesta abajo (propose-and-wait). Refina open questions del feature file (firma por iniciales pendiente compliance; specs de infra S3/JWT). NO escrito aún.
- **Mensaje a Seba/PERC**: el detalle de infra (bucket/región/credenciales + "tiro" del evento) y la definición de firma deberían reflejarse en el mensaje que el PM está por mandar.

## Contradicciones / tensiones

- Ninguna contradicción. **Refuerza** lo de la Daily 3/6: confirma que el entorno dev es bloqueante para persistir firmas y agrega especificidad. **Matiz nuevo sobre la firma:** el modelo "iniciales tipo DocuSign" coexiste con la duda de si compliance exigirá algo legalmente más estricto — no asumir que las iniciales alcanzan hasta que PERC lo confirme.

## Open question (PM judgment)

La firma por iniciales (consentimiento al tocar *continuar*, sin botón explícito de firmar) es la implementación más barata, pero Nico advierte riesgo legal. **¿Forzamos a compliance de PERC a confirmar por escrito que el modelo de iniciales alcanza** (vs. exigir firma electrónica avanzada / biométrica / token), dado que cambia sustancialmente el esfuerzo de Sprint 3? Es la primera pregunta para la reunión recurrente nueva.
