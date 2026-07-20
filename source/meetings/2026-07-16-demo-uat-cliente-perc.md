# Meeting — Demo/UAT Préstamos con cliente PERC (verbatim)

- **Fecha:** 2026-07-16
- **Título (declarado):** UAT - PERC - Transcripción
- **Naturaleza real:** demo happy-path en local (NO el UAT formal caso-por-caso) — ver ingesta hermana del dry-run interno de la mañana ([2026-07-16-uat-prestamos-lambdas-perc](../../ingestion/meetings/2026-07-16-uat-prestamos-lambdas-perc.md)).
- **Participantes (del transcript):** Marcos Perez (dev back Quarks, presenta), Olivier Luce (PM Quarks), Jose Salgado ("Jo", dev/reviewer PERC), Sebastian Cárdenas ("Seba", PO PERC), Gonzalo Kuhn ("Gonza", infra/DevOps PERC), Nicolás Paez ("Nico", TL Quarks), Ezequiel Manfredi ("Eze", CTO PERC), Eugenio Valeiras ("Euge", TL PERC).

> Audit anchor. Never edited after creation. Transcripción generada por computadora, puede contener errores (nota original al pie).

---

00:00:31

Marcos Perez: Buenas, buenas. Todo bien. ¿Cómo
Jose Salgado: Buenas. ¿Cómo anda eso?
Marcos Perez: va?
Jose Salgado: Bien, aquí andamos los dedos trabados,
Marcos Perez: ¿Y cómo lo vieron ayer? ¿Cómo lo vivieron?
Ezequiel Manfredi: Una locura.
Jose Salgado: ¿eh?
Ezequiel Manfredi: Demasiado sufrimiento.
Marcos Perez: Mal, ¿no? ¿Cómo
Jose Salgado: Ah, ¿cómo anda la gente?
Olivier Luce: ¿Cómo
Marcos Perez: va?
Ezequiel Manfredi: Wow.
Olivier Luce: andan
Jose Salgado: Pero muy bien,
Eugenio Valeiras: ¿Cómo andan?
Jose Salgado: expectantes.
Olivier Luce: finalistas?
Eugenio Valeiras: Totalmente expectantes.
Jose Salgado: Ah, yo pensé que era por esto.
Olivier Luce: No, bueno,
Eugenio Valeiras: Es
Olivier Luce: me gusta igual me gusta la actitud. Ah.
Jose Salgado: Ah.
Olivier Luce: Frenteus gobierno dos parallas,
Marcos Perez: Se murió tu micrfono.
Olivier Luce: eh
Jose Salgado: Sí, estás hablando en lengua, estás como
Marcos Perez: Sí.
Olivier Luce: mata la emoción.
Jose Salgado: poseído.
Ezequiel Manfredi: Ha.
Marcos Perez: ¿Qué pasó con el ¿Qué pasó con el
Olivier Luce: Me mata la emoción.
Marcos Perez: Vaperjo? Se volvió
Jose Salgado: Eh, de acá lo tengo.
Marcos Perez: a
Sebastian Cárdenas: Yeah.
Olivier Luce: Fal.
Jose Salgado: Es un vaper.

00:02:04

Eugenio Valeiras: Muy
Jose Salgado: Es un beraper
Eugenio Valeiras: bien.
Jose Salgado: analógico.
Marcos Perez: Mirá.
Olivier Luce: Mira
Ezequiel Manfredi: Mejoraron.
Olivier Luce: qué
Jose Salgado: Clar.
Eugenio Valeiras: Me gustan los chicos.
Jose Salgado: Pero mira qué realista que es, boludo. Hasta hasta se va chicando.
Olivier Luce: lo que es la tecnología, ¿eh?
Jose Salgado: Ya lo tengo.
Olivier Luce: Ay,
Marcos Perez: Ah, está bien, está bien,
Olivier Luce: Dios.
Marcos Perez: está
Eugenio Valeiras: Budo.
Ezequiel Manfredi: Tremendo.
Jose Salgado: Sí, un made in
Olivier Luce: ¿Qué les iba a contar?
Jose Salgado: Mendoza.
Olivier Luce: Eh, ayer fui a verlo ahí a la, ¿cómo se dice?, al enfrente del planetario que pusieron dos pantallas el gobierno de la ciudad.
Marcos Perez: Hope
Ezequiel Manfredi: Sí,
Olivier Luce: Espectacular.
Ezequiel Manfredi: tremendo.
Olivier Luce: Una cantidad de gente tremenda. No, no, no. Ah, estuviste ahí.
Ezequiel Manfredi: No,
Olivier Luce: Ese
Ezequiel Manfredi: pero vivo por ahí cerca y pasaba corriendo y vi toda la mostruosidad que estaban
Olivier Luce: no. Espectacular,
Ezequiel Manfredi: armando
Olivier Luce: espectacular.
Sebastian Cárdenas: ¿A qué hora pasaste corriendo? Sí, sí.

00:02:53

Sebastian Cárdenas: Yeah.
Ezequiel Manfredi: y 5:10 de la mañana más o menos.
Jose Salgado: Claro.
Ezequiel Manfredi: Corro, corro temprano, literal. Yeah.
Eugenio Valeiras: 5 10 de la mañana. Qué hijo de p***,
Jose Salgado: Pasó antes de los chavones que armaban las
Ezequiel Manfredi: Cada uno con su locura.
Eugenio Valeiras: boludo.
Jose Salgado: cosas.
Olivier Luce: Muy bien, viene ahí.
Ezequiel Manfredi: Claro,
Jose Salgado: Ah, ese está ranqueado a nivel mundial.
Olivier Luce: Bueno,
Jose Salgado: Ojo.
Olivier Luce: me está j*******.
Jose Salgado: No, no es posta. Es posta. Es posta.
Eugenio Valeiras: Fue al mundial.
Olivier Luce: En
Jose Salgado: Sí.
Eugenio Valeiras: al mundial de se fue.
Olivier Luce: serio,
Ezequiel Manfredi: y hace poco ahora un mundial de carrera de trail que hago que son las carreras de montañas
Olivier Luce: mira,
Ezequiel Manfredi: du por República Checa el mes pasado.
Olivier Luce: hace poco no hubo una porque tengo unos amigos que también, perdón, me fui por las ramas por completo, eh, completamente antiprofesional lo que estoy diciendo.
Ezequiel Manfredi: Eh,
Olivier Luce: Bueno, tengo unos amigos que y grabaron todo un documental de una carrera que fue de 200 km medio de supervivencia en la montaña.

00:03:44

Olivier Luce: Puede ser.
Ezequiel Manfredi: puede ser.
Olivier Luce: Son como se tiene que hacer tipo en tres días o algo así.
Ezequiel Manfredi: Sí, pero esa fue ahora o enero,
Olivier Luce: Hace hace un sí,
Ezequiel Manfredi: febrero.
Olivier Luce: más o menos por ahí.
Ezequiel Manfredi: Sí,
Olivier Luce: Sí,
Ezequiel Manfredi: la misión.
Olivier Luce: hace un par de meses la esta la
Ezequiel Manfredi: Sí.
Olivier Luce: misión y la hicieron en la hicieron en
Ezequiel Manfredi: misión algún día la tendré que hacer.
Olivier Luce: tr días sin dormir.
Ezequiel Manfredi: Qué locura.
Olivier Luce: Locos están locos. Hicieron todo un documental de eso. Después te lo pasas espectacular,
Ezequiel Manfredi: Pásamelo, pásamelo.
Olivier Luce: pero bueno, no.
Jose Salgado: Qué loco.
Olivier Luce: Buenísimo. Bueno, eh bueno,
Jose Salgado: Mira.
Sebastian Cárdenas: Ah. M.
Olivier Luce: arrancamos e si quieren con con eh con la reunión más o menos antes para antes de arrancar. un poco les les eh le doy contexto de más o menos lo que tenemos pensado para la sesión de
Marcos Perez: H
Olivier Luce: hoy. Eh, la idea principal es que veamos todos los flujos eh eh en total eh para validar el funcionamiento general de la de la solución. Pero bueno, un poco de contexto eh bien concreto.

00:04:48

Olivier Luce: Hoy el entorno de development no está eh no está completamente listo como como quisiéramos. Eh, si quieren con los últimos ajustes que ajustes integrados e y además eh o sea, tenemos un tema de los de los lambdas por un lado y después algunos PRs que que todavía no están integrados. Eh,
Marcos Perez: H
Olivier Luce: eso para tenerlo en cuenta y además hoy justo al mediodía estábamos hablando ahí con con Gonza y surgió un cambio de arquitectura bastante grande de lo que es principalmente el esquema de los lambdas y que nos implica reorganizar una gran parte de de de la implementación para poder bueno, justamente poder acompañar mejor la arquitectura e y la operación. Pero bueno, no queríamos dejar de de perder este espacio para para poder hacer un poco la revisión. Lo que sí, seguramente o lo que vamos a hacer es justamente la la demo en local. Eso para para tenerlo en cuenta por si tenemos si tenemos temas de tiempo de respuesta o tenemos que eh hacer una levantada de servicios. Eso para para tener en cuenta. No queríamos perder justamente este este espacio que ya lo habíamos movido desde el lunes, entonces lo queremos tener hoy. Sí. Jo.
Jose Salgado: No, hay un poquito de contexto para nuestro equipo. De hecho, lo acabo de llamar al señor Gon, pero lo que habíamos visto es que con más de 60 lambdas en el proyecto tardábamos alrededor de 45 60 minutos para el deploy, lo cual es homicida.

00:06:26

Jose Salgado: Por eso es que primero estuvimos charlando un poco con Gonza, eh, desde lo técnico, desde lo funcional, no había quejas. Si obviamente desde el tiempo que y de la fragilidad que con tanto tiempo de deployment eso podía llegar a tener. Eh, esto es para contarle un poquito también de nuestro lado a los chicos por ahí, si eso no lo no lo no lo tiran en el radar. Por eso se pidió este cambio, no es un cambio funcional. el eh en funcionalidad, en estilo de código, todo lo que está metido en Typescript, estamos muy bien. Eh, esto es una cuestión más específica de de cómo finalmente todo esto vive en los eh en en los servicios host, ¿no? O sea, en AMDAS y en todo lo que se vaya armando.
Olivier Luce: H
Jose Salgado: Ahí va esa la
Olivier Luce: Bien.
Jose Salgado: creación.
Olivier Luce: Eh, buenísimo. O sea, obviamente para para agregar contexto, nosotros el justamente el listado de todos los escenarios que hay como 130 escenarios que tenemos que probar y ya fuimos probando, están están, están validados funcionalmente. Obviamente lo que queremos es aprovechar ese espacio, pero después seguramente lo tengamos que repetir o extenderlo un poco tiempo más en realidad para ir caso por caso, porque eh honestamente hacer el UAT en un entorno que no es dev, quizás eh el día que que esté implementado sobre quizás hay algunas correcciones que tengamos que hacer.

00:07:51

Olivier Luce: Eh, así que esa es no es nuestra propuesta.
Jose Salgado: Sí.
Olivier Luce: lo lo hacemos en local y les mostramos más o menos eh los los flujos principales. Eh, y si es que ustedes ven que hay algún caso que no lo vimos, eh lo agregamos al listado y lo lo después lo pasamos en el en el UAT. ¿Están parece bien?
Jose Salgado: Por mi parte está bien, Sebitas.
Olivier Luce: Perfecto.
Eugenio Valeiras: Sí, señor.
Olivier Luce: Buenísimo. Bien.
Eugenio Valeiras: Me gusta tu
Olivier Luce: Eh, bueno, eh, Marcos,
Eugenio Valeiras: camisa.
Olivier Luce: todo tuyo.
Eugenio Valeiras: Rompa todo, Marcos. Amén. Yeah.
Gonzalo Kuhn: Bueno, perdón, ahí me tarde. Eh, solo para complementar, pero entiendo ya hablaron un poco de lo que decía Jo. Eh, también va e que le decía Marcos que nos juntamos un cachito también para para hacer un sing ahí. Eh, va un tema también por llamémosle costos y seguridad, porque meter toda esa cantidad de recursos por detrás eh Amazon audita todo lo que vos metas por cloud y demás. Entonces es una inmensidad de cosas que que requieren también un detrás de cena fuera de lo de lo funcional propio de ese recurso.

00:09:10

Gonzalo Kuhn: Entonces, bueno, nos parecía quizás que era un poco un overhead el el el tenerlo desarrollado o o tener esa arquitectura y después propio por el concepto de lambda que tiene un escalamiento horizontal, por lo cual eh no es que no es que trigerías y y eso queda en una cola y hasta que no finalices el proceso lambda eh invoca hasta tiene creo que hasta 5000 y tiene un ray enorme, por lo cual eh nos parece que quizás es es llevarlo a una a un tema más de optimización que que otra cosa. Perdón que entré tard ahí n más.
Marcos Perez: era más.
Olivier Luce: No hay drama. Perfecto.
Marcos Perez: Excelente. Bueno, ahí estoy compartiendo.
Olivier Luce: Bien.
Marcos Perez: Bueno, acá nosotros tenemos eh lo que sería básicamente el backoffice que fueron viendo.
Olivier Luce: Ahí si queres te te hago un paréntesis.
Marcos Perez: Eh,
Olivier Luce: Hacemos un un pasaje así a modo general de los módulos que tenemos, eh, y después vamos uno por uno,
Marcos Perez: vale.
Olivier Luce: si te parece. Sí, perdón, ahí Marcos la interrupción.
Marcos Perez: de de explicar esto. Así
Olivier Luce: Claro, así no.
Marcos Perez: es.
Olivier Luce: Así en general las áreas eh que fuimos tocando a lo largo del desarrollo. Primero, bueno, tenemos o vamos a ver cosas de lo que son los templates de préstamos, que es eh aquella parte en del backoffice en donde se deciden los eh préstamos a los cuales se pueden solicitar después del del lado del cliente.

00:10:46

Olivier Luce: Entonces, vamos a ver toda esa parte de gestión. Vamos a ver la simulación desde el lado del cliente en donde van a elegir eh el template de préstamo o el préstamo propiamente dicho que quieren solicitar. Todo ese todo ese flujo, obviamente haciendo un paréntesis, los documentos todavía está pendiente, ahí ya lo estamos eh gestionando con con Seba y Nico Ortiz. Eh, bueno, todo lo que es el seguimiento de la gestión de las de de las solicitudes de préstamo. Bien. Eh, después vamos a tener toda una parte de lo que es el descuento de las cuotas, el y vuelta con la mantovana, que se apliquen las cuotas, qué pasa cuando queda parcial, ese tipo de casuísticas. Eh, y después por último, pero no menor, todo lo que es las casuísticas de cancelaciones, arrepentimiento antes los 10 días, cancelación anticipada y después cancelación de la solicitud. Así, eso a modo general vendría a ser el índice de de lo que tenemos.
Marcos Perez: Así es.
Olivier Luce: Bien.
Marcos Perez: Eh, bueno, ya antes de la reunión estuve cargando and algunos templates, pero ahora vamos a crear uno para que para que podamos ver también ese path. Eh, los estuve creando con las variables que tenemos en el Excel.
Olivier Luce: Hai
Marcos Perez: Básicamente, eh, en este caso voy a crear, por ejemplo, un básico eh del tier gold.

00:12:19

Marcos Perez: Eh, vamos a poner algo así. Vamos a ponerle tres cuotas. Ahora les voy a explicar por qué. Vamos a ponernos algunos valores medios al azar de lo que me voy acordando del Excel. La 21 1.2 más o menos lo tenemos igual al Excel. Bueno, podemos crear un template. En este caso tenemos el tag gold. Eh, al hacer un update, como fuimos viendo, eh básicamente lo que va a pasar es que sigue existiendo como desactivado y se crea una nueva versión eh, con ese cambio. Bien, entonces vamos a venir por acá, vamos a ponerle, por ejemplo, que este sea de 1,500 y al actualizar vamos a ver que cambia eh incluso el ID porque va a cambiar. Y ahora es el la nueva nueva versión. Bien, acá tenemos todo lo que es update, eh tenemos el get de los préstamos, todo esto está documentado con el insomnia y tenemos las
Olivier Luce: para más lento,
Marcos Perez: eliminaciones.
Olivier Luce: más lento. Si no, no.
Marcos Perez: Okay.
Olivier Luce: Así se así se ve bien las secciones.
Marcos Perez: Bien, cualquier cosa igual si me van frenando si tienen alguna duda o algún caso que quieran probar. Bien.
Olivier Luce: Esto.
Marcos Perez: E bien, después del template de préstamo eh podemos tener lo que son las solicitudes de crédito.

00:13:59

Marcos Perez: Para eso nosotros eh hicimos, bueno, este input que ya lo habíamos visto, que es básicamente como para hardcodear un poco el tag del usuario. En este caso, tier gold tengo uno solo, tier silver tengo tres, que son los que ya había generado previamente. Bien, acá podemos atacar algunas casuísticas también de esto que es, por ejemplo, ¿no? Vamos a volver al Gold, vamos a solicitarlo. En este momento, cuando yo lo pongo en solicitar ya está creado como en in progress, bien, esperando la firma del del usuario. Bien, antes de seguir avanzando les voy a mostrar eso. y yo vuelvo, voy a ir a mis préstamos y acá lo tengo en progreso. Bien, aún no está firmado el documento. Yo tengo creada la solicitud del crédito, pero todavía no existe el crédito en sí. Bien, en este caso nosotros también documentamos en el insomnia y lo hicimos también para forzarlo a fines prácticos. Eh, el Chrome que va pasando cada una hora y va a ir cerrando todas aquellas eh solicitudes que están sin firmar. Bien, en este caso por eso fines prácticos nosotros hicimos eh la básicamente la misma invocación que va a ser el Chrome, forzándole el now para decir, "Okay, borrame todo lo que lo que no esté firmado." Bien, al hacerlo, en este caso, forzándolo, lo que nos va a pasar es que nos va a poner como expirada, tenemos una expirada, cero fallidas, eh, la solicitud del préstamo de esta persona.

00:15:50

Marcos Perez: Bien, en este caso vamos a mis préstamos y ya la tengo como expirada. Obviamente esto no lo va a ver el usuario. En este caso decidimos dejarlo, digamos, pasar el filtro para mostrar el tema de la expiración. En este caso no se han creado las cuotas porque como hemos visto también las cuotas se crean una vez aprobado el crédito. Bien, así que en este caso no va a estar bien. Eh, excelente. Bueno, vamos a volver a solicitar un préstamo. Eh, yo me lo gué recién. Sí, ya me lo gué. Voy a aceptar los términos. Acá hicimos a modo de de mocap, digamos, lo que va a ser pasar el TOTP. Bien, en este caso tengo que poner el documento. Les voy a voy a aprovechar para mostrarle las partes de documentos. Como habíamos visto, nosotros tenemos lo que es templates de documentos. Bien, esto lo hicimos para que sea escalable y para que el día de mañana se le pueda agregar más documentos. eh y poder eh no tener que hacer, digamos, tantos cambios. Bien, en este caso lo que pasa es nosotros creamos un template de documento que va a ser en este caso, por ejemplo, términos y condiciones y después van a ir estando las versiones de los documentos.

00:17:16

Marcos Perez: ¿Bien? Entonces, cada vez que un operador del backoffice va cargando las versiones, se va a ir viendo acá, versión uno, versión dos, versión 3, se va marcando como activa y cada vez que nosotros creemos un template de crédito, bien como estos que habíamos visto, se le va a asignar por defecto en este caso el el tipo de documento junto con la versión actual que tiene. Bien, cuando nosotros vamos al simulator acá, bueno, vamos a fingir justamente la firma. Esto lo que hace es forzar la firma del documento. Ya tenemos aprobada la solicitud. Bien, ese botón, el de aprobar básicamente es la firma que en este caso no está firmando el documento en sí porque aún eh
Olivier Luce: Ş.
Marcos Perez: como habíamos hablado, estamos a la espera del documento. Bien, cuando la solicitud está aprobada aún no están las cuotas, ya que las cuotas se crean una vez que está granted el el crédito, que sería fondeada la cuenta. Bien, en este caso yo lo que puedo hacer antes de continuar es correr el próximo eh el próximo el próximo Chrome, que es el que pasa cada 24 horas. Bien, el que pasa cada 24 horas va a cerrar todas aquellas eh solicitudes aprobadas, es decir, firmadas, eh porque una vez que está en in progress, se firma, pasa aprobado, pero que no están fondeadas.

00:18:45

Marcos Perez: Bien, entonces ahora vamos a simular el cron de las 24 horas. En este caso, nuevamente, una cancelada, cero fallidas. Bien, si yo vengo y refresco, la tenemos una como expirada, la otra como cancelada. Bien, en este caso vamos a volver a solicitar el préstamo. Sí,
Jose Salgado: Este estadio eh se puede volver hacia atrás.
Marcos Perez: hijo.
Jose Salgado: Una vez que está cancelada o está expirada, yo puedo retomar ese trabajo. Ponerle que lo hice, no sé, el viernes a última hora porque tenía que hacerlo, pero no lo terminé y lo dejé ahí. Cuando llegue el lunes entiendo que estará o expirado o cancelado,
Marcos Perez: Bien, sí. Eh,
Jose Salgado: ¿no?
Marcos Perez: expirado y cancelado son eh lo que denominamos por ahí eh estadios terminales, es decir, cierran por completo la solicitud.
Jose Salgado: Okay.
Marcos Perez: En ese caso habría que generar otra eh, nuevamente, ¿no? O sea,
Jose Salgado: Bien,
Marcos Perez: están los estadios terminales que son los que van cerrando todo lo que lo que hay en este caso. Bueno, eso es es terminal,
Jose Salgado: perfecto.
Marcos Perez: digamos, e al igual que completado o pagado.
Jose Salgado: Claro.
Marcos Perez: Bien,

00:19:57

Jose Salgado: Bien, bien.
Marcos Perez: bien. Bueno, en este caso vamos a otorgarlo una vez otorgado y fondeada la cuenta, obviamente acá está haciendo e toda la parte de lógica del fondeo, pero no lo está fondeando eh como habíamos visto. Eh, bueno, no se dejó, no se acuer ayer, creo que fue ayer o antes de ayer que vimos todavía no tenemos el cashout implementado, pero sí la lógica con el todoo ahí para implementar. Bien, entonces, bueno, acá podemos ver desde la parte del usuario lo que sería la deuda restante, las cuotas, el capital, el interés, el total, los vencimientos. Los vencimientos se generan a partir de la fecha de creación del crédito, un mes en adelante y así sucesivamente. Bien, en estado pendiente tenemos además, bueno, el total de cuotas, el total del crédito y el pagado. Bien. En este caso, yo Como operador del backoffice puedo por un lado ver todas las solicitudes de crédito. Bien, tenemos las expiradas, las canceladas, las aprobadas, todo con filtro, obviamente y con la opción de exportarlo. Bien, nosotros podemos exportar siempre las solicitudes con los mismos filtros que teníamos aplicados. Bien, le pone la fecha del día de hoy y tenemos la tablita. eh con los filtros. Por otro lado, tenemos lo que son los créditos otorgados o los créditos en sí.

00:21:36

Marcos Perez: Esta es la vista de créditos. Eh, tenemos el otorgado y este que es retirado, que sería eh el que fue cancelado por por la falta de tiempo. Bien, tenemos la división porque una tenemos las solicitudes y después tenemos los créditos una vez creados en sí mismos, ¿no? Después, por otro lado, bueno, por ejemplo, si yo entro por acá como operador del back office, puedo buscar por ID, esto nos va a dar el reporte de las cuotas de la persona y la posibilidad de hacer los pagos manuales. Bien, estos pagos manuales e nosotros podemos ir registrando varios y se va registrando la auditoría en todo momento. Sí.
Olivier Luce: Esto ahí te interrumpo, esto es importantísimo porque lo que queríamos eh evitar o tener herramientas para poder eh para poder evitar el mismatch o para poder acceder o accionar, ahí está, ese es el verbo, eh entre lo que nosotros mandamos y lo que nosotros recibimos por parte de la mantovana. Obviamente no debería haber una diferencia, eh, pero creíamos lo suficientemente importante el caso de borde, eh, como para que el operador de backoffice no tenga que ir a pedir eh tocar una tabla y que tengan las herramientas ahí en el backoffice, que entonces pues las casuísticas que pueden llegar a pasar son concretamente son cuatro, que es que se una que se pague bien, otra que directamente ente, bueno, haya alguna ID de cuota que no sea no sea la que la la correspondiente, entonces ahí tienes un error.

00:23:24

Olivier Luce: Pero después puedes tener dos casos de de pago parcial o de o de sobrepago. Entonces, si yo yo le dije a la mantovana, "Che, descontale 100 y después le descuenta 90," yo tengo la posibilidad desde el backoffe decir, "Bueno, voy, le escribo a al cliente, "Che, me estás debiendo 10, veo como lo gestiono operativamente, pero yo lo cargo para que me quede y me quede computado como pagado." Y lo mismo si es sobrepago, obviamente me va a aparecer el el el rotulado. ese caso también ahí en el backofice hay que estar atento, eh, porque también le tenemos que devolver, o sea, yo le pedí 100 y me y me descontó 110. Bueno, ese lo que lo que implementamos ahí en el backoffice que está mostrando ahora Marcos, justamente es eso para atacar ese caso.
Marcos Perez: Acá eh en este caso voy a a hacer el end point de lo que sería la importación justamente de lo que son los descuentos. Bien. Eh, nosotros como no sé si habían visto la estructura, digamos que esperamos, básicamente eh sería lo que es credit installment ID, que es el crédito, el ID de la cuota, eh un nombre que después vamos a mostrar, que sería lo mismo que enviamos y el monto descontado.

00:24:45

Marcos Perez: Bien, en este momento cuando yo haga esta importación, lo que va a pasar es que le puse una cuota eh como pago parcial. Acá se puede ver el código a la derecha, si no, ahora les muestro igual eh en el fronto. De esto. Tenemos el pago parcial, el segundo que teníamos el pago eh digamos over sobre lo que lo que era el que había que descontar. Tenemos el aplicado y en este caso tenemos un código de error de que eh no había cuota eh con ese ID. Bien, entonces cuando nosotros vamos a este lugar eh que era la parte de cuotas, por ejemplo, no no está muy lindos los botoncitos, pero básicamente lo que hicimos fue dar la opción al operador, por un lado de cargar un pago manual. Bien, en este caso el operador puede cargar cualquier monto, por ejemplo, 100, que en este caso va a seguir siendo a un pago con error y va a seguir siendo pago parcial. y va a estar como parcialmente pagada. Bien. Y después implementamos algo así como un dar por pagado o terminar, digamos, completar el monto, que básicamente lo que haría sería completar el monto faltante para que esté la cuota pagada. Bien. Y lo mismo el tema de la devolución. Vamos a poner devolución. Vamos a poner el monto que devolvemos, que ya nos viene como para que lo pongamos, digamos, por defecto, y eh registramos la devolución.

00:26:20

Marcos Perez: De esta forma nosotros tenemos ya el préstamo eh terminado porque están las tres cuotas pagadas, obviamente está todo en auditorías. Se va.
Sebastian Cárdenas: Tengo una duda con respecto a lo que dar por pagado algo. Eh, queda alogiado quién es, tengo un par de preguntas. Queda logiado quién es el usuario que lo da por pagado.
Marcos Perez: Sí,
Sebastian Cárdenas: Queda registrada la diferencia que hubo entre lo que debía pagar.
Marcos Perez: sí,
Sebastian Cárdenas: Eh,
Marcos Perez: así es.
Sebastian Cárdenas: y eso queda contabilizado en algún, o sea, cuando yo vea el préstamo final, voy a a ver asumido que Right. que le retuve esa plata. O cuando yo quiera conciliar la cuenta,
Marcos Perez: Bien.
Sebastian Cárdenas: yo voy a esperar que haya 100 pesos. Habían 100 cuotas de un peso y una pagó 50 centavos y se la di por aprobada. Tiene 99,50. Yo cuando vaya a la caja del banco va a haber 99,50. Si yo le di por aprobado algo, después me va a decir, "Che, la caja te va a dar 99,50.
Marcos Perez: E eso entiendo que estás hablando como una especie de de conteo de fondos, ¿verdad?
Sebastian Cárdenas: como, o sea, que quiero ver el análisis financiero más que solo el económico,

00:27:39

Marcos Perez: Bien.
Sebastian Cárdenas: en el sentido de que yo después tengo que que marchar esto contra un banco, ¿no? Entonces está buenísimo que lo pueda probar, pero en algún punto le tengo que dejar notificada a la persona de che, eran entraron 50, 50, está todo bien, pero ese dato quiero saber si lo puedo encontrar en algún lado.
Marcos Perez: Bien, nosotros tenemos sí eh todo el historial de transacciones. ¿Cuánto fue lo que devolvió? ¿Cuánto fue lo que faltó? ¿Cuánto fue lo que cargó el usuario que lo cargó?
Sebastian Cárdenas: Perdón.
Marcos Perez: En este caso, por ejemplo, tenemos esta operación de refund, que sería del reintegro, eh, y por 200,000 pesos, eh, tenemos el usuario que lo hizo. Acá está el usuario. Eh, tenemos la fecha, tenemos todo el historial. Eh, después justamente
Sebastian Cárdenas: para darlo por pagado,
Marcos Perez: lo
Sebastian Cárdenas: vos volvés a chequear que la sumatoria de las cuotas da el valor y que la sumatoria de los pagos da el mismo valor.
Marcos Perez: Sí, si no están todas las cuotas como marcadas, como pagadas, eh, justamente no se termina,
Sebastian Cárdenas: No.
Marcos Perez: no se finaliza el crédito. Bien, en este caso, por ejemplo, eh yo había completado una de las cuotas, la había completado con un monto inferior a lo que era completar el pago, ¿no?

00:29:00

Marcos Perez: Entonces ahí aún no seguía apareciendo como pago parcial, es decir, recién vamos a poder dar por terminado el crédito una vez que se respete eh todas las cuotas y queden todas las cuotas como pagadas, o sea, el balance con el total exactamente igual.
Sebastian Cárdenas: con el total exactamente igual.
Marcos Perez: Así es.
Sebastian Cárdenas: Después tengo una pregunta sobre decimales. Decime si es en otro momento que las tengo que hacer.
Marcos Perez: Eh, no, si quieres
Olivier Luce: Oh.
Sebastian Cárdenas: El el requerimiento entonces para que ellos suban el documento y que dé
Marcos Perez: Ahora
Sebastian Cárdenas: exactamente la cantidad de decimales del cálculo de la cuota. Eh, hay dos preguntas que me surgen de eso. Las cuotas siempre son exactamente iguales y si son siempre iguales, se truncaron en algún lugar para poder hacerlo y si se truncaron eso que falta, esa plata que falta, ¿dónde fue? Eh, y por el otro lado, yo Si llego a tener un una fuente de información con menos decimales, se rompe todo,
Marcos Perez: Eh, mira, por un lado, eh,
Sebastian Cárdenas: ¿no?
Marcos Perez: yo creo que nosotros que por ahí más o menos lo que habíamos hablado eh con Jose, nosotros estamos guardando con precisión absoluta en todo momento. Creo que es lo importante eh que nosotros lo registremos como precisión absoluta.
Sebastian Cárdenas: No,
Marcos Perez: Es decir,

00:30:25

Sebastian Cárdenas: eso está perfecto 100%.
Marcos Perez: si después eh yo creo que si después la Mantovana quiere, por ejemplo, prescindir de estos últimos cuatro dígitos, cinco, e yo creo que lo puede hacer, pero a nosotros nos debería llegar el monto justo e para esto, para no perder precisión. No sé, Jose. Igual ibas a decir algo.
Jose Salgado: Sí, eso iba a decir que desde el desarrollo se había pedido usar decimals o o indecimals o stream decimal tiene un nombre diferente en como que llama en cada lenguaje, pero que básicamente es eso. Acabo tenés una representación con todos los números, o sea, con toda su colita decimal, pero en realidad a términos operativos lo máximo que se usan para los cálculos y todo son los los primeros
Olivier Luce: M.
Jose Salgado: tres. Acá estás viendo que tenés cerca de cerca de ocho.
Marcos Perez: Sí.
Jose Salgado: Eh, nada, no sería problema. Eh, incluso entiendo que a la hora de percibir, si vos por ejemplo ves acá para que voy a voy a ver percibido, tenés 78 27 49, bien, vos podés eh percibir con 80 y ya está, porque a vos el cálculo te va a dar perfecto. Sí que vas a tener un una pendejésima de plata ahí que te queda, perdón, pero digamos como un poquito de plata que te queda extra, pero pero nunca jamás vas a perder porque de hecho están usando un un digamos una forma de representar números que no es coma de que no es punto flotante, o sea, que opera diferente los los valores, por tanto, nunca vas a perder representación sobre los números.

00:32:01

Marcos Perez: Así
Jose Salgado: Esto se pidió como un
Sebastian Cárdenas: O sea,
Marcos Perez: es.
Sebastian Cárdenas: o sea, para preguntarlo más de nivel funcional es si Finans me entrega algo
Jose Salgado: requerimiento.
Sebastian Cárdenas: con menos decimales y esos decimales no hace un round up, sino que lo corta En vez de decirte con 80 hace 27 y corta ahí y le faltan el 0,004898, va a quedar la cuota como pagada parcial.
Jose Salgado: A ver, está pagando de menos, o sea, que no,
Sebastian Cárdenas: Por eso, por eso me preocupa, ¿no?
Jose Salgado: a ver, que es lo mismo que si vos,
Sebastian Cárdenas: Esa plata.
Jose Salgado: no sé, tenías que pagar 56,000 y pagas 54, o sea, el caso es exactamente el mismo, solo que con valores más pequeñitos. Eh, creo que también hay una decisión por parte del front que integre esto finalmente, que diga, "Che, muestro solo dos decimales porque en pesos estamos acostumbrados a dos o tres como mucho y redondeo para arriba." Va, entonces siempre estoy cubierto, no no sé si realmente tiene va capaz que yo me estoy metiendo y era va por otro lado la pregunta, pero pero entiendo que numéricamente no, o sea, si se paga eh digamos lo que corresponde, numéricamente no tendríamos problemas.

00:33:13

Marcos Perez: Así
Jose Salgado: Por ejemplo,
Marcos Perez: es.
Jose Salgado: si él paga esto eh 79 en este en el primer renglón, ¿no? Viste que es punto 782. Si él paga con 79, automáticamente cuando se hagan los cálculos se van a operar con toda esa cantidad de dígitos, pero pero digamos luego vos podés eh reescalar esa partecita y y nada, es completamente
Sebastian Cárdenas: O sea,
Jose Salgado: visual.
Marcos Perez: Por eso también la implementación del del botón por ahí de dar por pagada para no pedir exactamente eh que me mande los dígitos que que hacen falta. Si no, bueno, te doy el end point y y te digo, "Okay, mándame este este monto y listo.
Sebastian Cárdenas: Me preocupa en eso. Había visto la parte manual. Mi miedo sería que, entiéndame desde lo de la parte más funcional, ¿no? Eh, que si porque cortan y te pagan con 78 y no pagan todo el resto de los decimales, me van a quedar todas pago pendiente y tengo que tener una persona ahí mandándole aprobar todo 1 préstamos. Y por el otro lado me preocupa de que cualquier número superior a ese valor lo dé por pagado y ese valor superior no sé cómo lo estoy
Jose Salgado: Lo de por sobrepagado,
Sebastian Cárdenas: tomando.
Jose Salgado: decís vos.

00:34:33

Jose Salgado: O sea,
Marcos Perez: Es
Jose Salgado: que esto bien,
Sebastian Cárdenas: En algún momento tengo que hacer algo con esaita,
Marcos Perez: sobrepagado.
Jose Salgado: eh,
Sebastian Cárdenas: no es mía y me la diero.
Jose Salgado: te paso un CBU.
Marcos Perez: No,
Sebastian Cárdenas: ¿Cómo andamos?
Marcos Perez: el sobre pagado igual tampoco cierra porque tiene que venir un operador a solucionarlo. Por eso es pago con error. entran los dos en categoría pago con error, justamente porque tienen la misma importancia, creo yo, a nivel operativo si te pasas como si te quedas de corto de dinero, digamos. E y después, bueno, el otro tema, no sé, no sé por ahí
Sebastian Cárdenas: No hay forma de configurarle la sensibilidad de los decimales.
Marcos Perez: Gracias.
Jose Salgado: Sí. Ah, perdón. Eh, a ver,
Sebastian Cárdenas: eso.
Jose Salgado: eh, una cosa es como vos ves el número y otra cosa es como vos lo operas. Para operarlo, yo recomendaría enfáticamente no tocar decimales. Por eso estamos usando esta clase de números y no coma flotante,
Sebastian Cárdenas: Okay.
Jose Salgado: porque los flotantes lo que tienen es que tienen grandes pedazos en los que no hay representación porque es un cálculo. Eh, lo que creo que por ahí si a la hora de integrar esto con la plataforma PERC, lo que va a haber que hacer es un trabajo sobre cómo yo presento los números, ¿no es cierto?

00:35:43

Jose Salgado: Porque vos la colita decimal después la podés reescalar, o sea, decir, "Che, no me traigas ocho, tráeme tres y usa alguno de los modos de redondeo para arriba,
Sebastian Cárdenas: puede
Jose Salgado: para abajo, medio, como a vos te se te ocurra. Sií, quizás.
Olivier Luce: M.
Jose Salgado: Sí, quizás sería interesante que a la hora de evaluar lo correcto que esté pagado cada una de estas cosas, agreguemos un pequeño campo trehold para decir, "Bueno, soporto que pagues el 0,1% de más o de menos, digo, o sea, como como digamos tengo un un digamos una pequeña W que a mí me permita regular estas pequeñas diferencias como para decir, bueno, si me pagó 3 centavos de más, no importa, me lo pagó, no le voy a devolver ver los 3 centavos y de la misma manera si me pagó 2 centavos de menos, estamos okay. Eh, quizás eh habría que que hablarlo desde el lado más de producto de si agregamos esta funcionalidad o no.
Sebastian Cárdenas: Sí,
Jose Salgado: ¿Qué qué opinan?
Sebastian Cárdenas: sí. O sea, estoy Vos me leíste la
Jose Salgado: Y soy pelado. Los pelados, Marco, te lo podrá decir bien. Tenemos poderes.
Marcos Perez: Tal cual.
Sebastian Cárdenas: mo.

00:36:50

Marcos Perez: Tenemos el Bluetooth activado, ¿eh? No, sí, o sea, eh, como dice, hijo,
Jose Salgado: Claro.
Marcos Perez: en caso de que de que se llega a necesitar como una decisión por ahí de producto, un redondeo o algo por el estilo, eh, como poder se puede hacer. Sí, sí,
Sebastian Cárdenas: es que se vuelve,
Marcos Perez: sí.
Olivier Luce: Sí.
Sebastian Cárdenas: para mí se va a volver inviable requerir de los terceros que van a subir los archivos un nivel de exactitud que haga que eso no de pago con error. Entonces, algún en algún momento tengo que después de guardar todos los datos, está buenísimo, guardo todos los decimales, cortarlo y decir, "Págame esto, por más que yo tengo guardado todo el dato del
Jose Salgado: Sí, incluso si me preguntas a mí creo que ni siquiera habría que hacerlo.
Sebastian Cárdenas: número
Jose Salgado: En realidad creo que lo que habría que hacer es a la hora de evaluar cómo se pagó tener un valor de tres hol, o sea, tener un pequeño eh, ¿cómo es que se llama? Ah, me fue la palabra un margen.
Marcos Perez: Delta,
Sebastian Cárdenas: margen.
Marcos Perez: creo que es
Jose Salgado: Un margen.
Marcos Perez: delta.
Jose Salgado: Un margen eh que yo diga, bueno, okay, tanto por cento de o digamos o tal valor puede rondar en vez de que sea una

00:37:58

Sebastian Cárdenas: Estoy haciendo.
Jose Salgado: igualda, quizás una una evaluación ponderada. O sea, decir, bueno, si estás extremadamente cerca, está okay. Por más que sea un pelín por arriba, un pelín por abajo, eso debería ser configurable seguramente, pero pero bueno, quizás hasta puede ser configurable por variable de entorno, ¿eh? Y ya. Ojo, eso sí ahí,
Marcos Perez: Bien.
Jose Salgado: chicos, eso sí, de ambos lados nos tenemos que poner de acuerdo porque esto sería como un pequeño ajuste de requerimiento, eh, tanto de nuestro lado para poder medirlo como, bueno, de ustedes lados para de su lado para poder entender que norte se toma, ¿no?
Marcos Perez: Tal cual. Sí.
Olivier Luce: Bien,
Jose Salgado: Continúa.
Marcos Perez: Bien.
Jose Salgado: Perdón,
Marcos Perez: Eh,
Jose Salgado: algo más.
Marcos Perez: excelente.
Sebastian Cárdenas: Estamos como queremos. M. Yeah.
Marcos Perez: Bien.
Olivier Luce: Yeah.
Marcos Perez: Eh, bueno, tenemos eh retomando un poco lo que sería el tema del logueo y el audit. Bien, eh tenemos básicamente el registro de todo lo que fue pasando eh mientras, bueno, mientras íbamos viendo. Eh tenemos alta de registro. Eh, acá el update de de inrogress ha expirado. Eh, en este caso tenemos el alta de otro registro que después pasó a aprobado, después tenemos otro que pasó a cancelado.

00:39:23

Marcos Perez: Bueno, básicamente eh tenemos un traqueo eh de todo, como se había hablado. Tenemos por un lado solicitudes de crédito, por otro lado tenemos todo lo que fue pasando con los créditos en sí. Bien, en todo momento nosotros estamos guardando el usuario, el user ID, en este caso ya no tenemos más el token como en algún momento. Eh, tenemos todos los cambios, el antes y el después, digamos, se hizo se hace algunas snapshots de la información que cambió. En este caso, por ejemplo, pasó de estatus granted a estatus paid, que esto fue lo último que hicimos. E tenemos, bueno, lo mismo con templates de créditos. Todo esto eh filtrado eh y ordenado como como se desee. En este caso, por ejemplo, tenemos el cambio del template de 1 millón a 1,illón y medio. Eh, después tenemos el tema de las cuotas e todo lo que fue también los pagos, pago con error, pasó a pagado por este usuario. En este caso no lo estamos mostrando en la tabla esta, pero como les comentaba, guardamos los snapshots, así que tenemos cuánto fue devuelto, cuánto fue eh digamos de qué cambió a qué cambió. Tenemos la parte de pagos acá en esta tabla se está mostrando.
Sebastian Cárdenas: Te hago una pregunta. cuotas. Eh,
Marcos Perez: Sí,
Sebastian Cárdenas: ustedes lo toman la palabra cuota vendría a ser el pago que ya está asociado a un usuario y no el valor del template

00:40:57

Marcos Perez: así es. Eh, porque tenemos Sí, perdón, así es.
Sebastian Cárdenas: genérico.
Marcos Perez: Nosotros tenemos por un lado lo que es el valor de las cuotas del template. Bien. Y por el otro lado tenemos las cuotas que va a pagar el usuario. Eh, cuando nosotros generamos un template de crédito y lo cargamos con todos los valores, que ahora se los voy a mostrar esa parte, eh, y nosotros lo cargamos con todos los valores, se van a crear, digamos, algo así como los templates de cuotas que después se van a crear cuando el usuario tenga el préstamo como otorgado. Bien.
Sebastian Cárdenas: Claro.
Marcos Perez: Eh, en este
Sebastian Cárdenas: Perdón, capaz me confundí un poco con el front,
Marcos Perez: caso,
Sebastian Cárdenas: por ejemplo, ahí está la columna de cuotas y es un número de cantidad de cuotas. Madre mía.
Marcos Perez: okay, estabas trabando ahí. No sé si
Sebastian Cárdenas: Acá internet anda. No puedo hacer
Marcos Perez: Eh, claro. Eh, lo que tenemos, a ver, e los montos, las tasas,
Sebastian Cárdenas: chiste.
Marcos Perez: las variables, eh los cálculos, digamos, de la tasa de mora, de el costo de otorgamiento y todo eso se generan cuando nosotros creamos el temple. Después las cuotas van a hacer referencia a cada una de las cuotas precadas al momento del temple.

00:42:28

Marcos Perez: Bien, este es uno de los errores que comentábamos del entorno.
Sebastian Cárdenas: Ok.
Marcos Perez: Acá ya me ha explotado la máquina claramente,
Sebastian Cárdenas: Y ahí el número de cuotas,
Marcos Perez: por eso es que número de cuotas los cargué a mano cuando
Sebastian Cárdenas: ¿cómo lo calculaste? No es que tenés
Marcos Perez: cargué el crédito, el template. Cada template tiene su cantidad de cuotas y después se calcula, digamos, por ejemplo, acá tenemos,
Sebastian Cárdenas: Okay.
Marcos Perez: no sé, este que tiene tres cuotas, pero teníamos un silver. Este es el que más respeta el Excel que ustedes nos dieron. Tenemos cuando cargué esto, cargué que eran 24 cuotas, cargué todos los valores, todas las variables. Después tenemos los costos computados que se calculan también ahí en el momento. Tenemos algunos montos y acá se genera la división de las cuotas y de cuánto te va a quedar cada cuota.
Olivier Luce: y que después si te fijas y con a ver lo que queremos hacer en el en el cuando tengamos
Marcos Perez: Bien.
Olivier Luce: el entorno ya 10 puntos eh y los ajustes que faltan ya ya estén todos, le dedicamos específico tiempo a validar que cada uno de los números y los cálculos estén perfectos, como en el ejemplo,
Sebastian Cárdenas: Olvídate ahora
Olivier Luce: eh, obviamente va a llevar tiempo, pero pero queremos validar eso porque es lo más importante.

00:43:46

Sebastian Cárdenas: no.
Marcos Perez: Así es. E y bueno, estas son las cuotas del crédito y después tenemos por otro el otro lado las cuotas del usuario, eh, que son las que se van a digamos a hacer referencia a esas que acabamos de ver. Bien, son las que van manejando esos montos. Eh, ¿qué más? Eh, bueno, ahora en el simulator si es que me deja entrar, si no voy a tener que limpiar el Docker. Tal vez voy a tener que limpiar el Docker, el querido, hermoso Docker. Bueno,
Jose Salgado: No, Doc,
Marcos Perez: ahí estamos,
Jose Salgado: no. Yeah.
Marcos Perez: ahí estamos. A ver. Vamos a volver acá, vamos a probarlo, vamos a otorgarlo. Y tenemos también eh la parte de arrepentimientos. Bien, en este momento eh yo me estoy arrepintiendo. Tenemos el lapso de 10 días a partir de depositado el crédito para arrepentirnos. Tenemos también el tema de la cancelación, que hasta que se otorgue el crédito eh podemos cancelarlo. Bien, todo esto obviamente gestionado por el operador del backofice. Bien, ahí creo que no sé si se ha disparado bien. Vamos a verlo. Cancelaciones. Si nos generó. Ya me tiró el 502.

00:45:33

Jose Salgado: Marcos, ¿querés que hagamos un parate?
Marcos Perez: Sí.
Jose Salgado: Le pegas una reiniciada a todo y tomamos este caso de cancelaciones como restarte así a poquito. Eh,
Marcos Perez: Sí,
Jose Salgado: sí, esa pobre compud.
Marcos Perez: no está. No, no te cuento como cada tanto tira una chilladita hermosa.
Jose Salgado: Si te le puedes hacer un huevito
Marcos Perez: Sí, sí, sí, sí.
Jose Salgado: arriba.
Marcos Perez: está un
Olivier Luce: Bueno, entonces mientras
Marcos Perez: poquito
Sebastian Cárdenas: No iba a j**** de que le voy a tener que decir a Federico que compre mi
Olivier Luce: Dale.
Sebastian Cárdenas: mejor.
Eugenio Valeiras: Okay.
Jose Salgado: No pasa que estructuralmente incluso está manteniendo más de 60 lambdas que son contenedores, que son b que chorrada de cosas, chorradas, chorrada de cosas.
Olivier Luce: Eh,
Sebastian Cárdenas: ¿Qué vas a decir?
Olivier Luce: no hacemos un un repaso entonces de los tres casos de cancelación.
Jose Salgado: Vamos ver.
Olivier Luce: nos repetimos siempre, no lo sabemos concretamente son tres. Es la solicitud de préstamo se consolida cuando yo firmo el documento. Firmo el documento, está aprobado con el TOOTP, listo, tengo mi solicitud de de préctas para poder desembolsar los fondos. Si yo no los si yo no los tengo disponibles, eso es eso es algo que falta que todavía eh recién ahora justo podemos eh podemos probar con lo de los eh con el segundo usuario que que tenemos disponible, pero bueno, tengo hasta 24 horas para poder yo depositar ese para desembolsar ese fondo.

00:47:14

Olivier Luce: Si pasa las 24 horas no se desembolsa, la solicitud se cae. Ahora, el usuario en ese periodo de 24 horas, por la razón que sea, eh puede cancelar esa solicitud. Entonces, se se cancela. Ese es el primer tipo.
Marcos Perez: Ok.
Olivier Luce: Después del desembolso, ahí tiene esos dos periodos, antes de los 10 días corridos y después de los 10 días corridos. Después de los 10, o sea, antes es sin costo y después es con costo. Eh, así que bueno, vamos a ver esos esos casos ahí. Marcos ya está.
Marcos Perez: ¿Te
Olivier Luce: Okay.
Sebastian Cárdenas: Te pregunto una sola cosa.
Olivier Luce: Sí,
Sebastian Cárdenas: en los tres casos ya eh digamos se hacen distancia del
Olivier Luce: sí.
Sebastian Cárdenas: préstamo del cliente. Más allá de que no haya habidoción, ya el préstamo como comoamos como objeto está existe, va a quedar como cancelado.
Marcos Perez: referís a vos te referís al lob Eh,
Olivier Luce: al traqueados. Aló.
Marcos Perez: sí, tenemos eh tenemos básicamente estadíos, ¿no? Si en cuando se crea la solicitud se firma el documento y está aprobado, eh nosotros tenemos ya creado el crédito que va después quedar como arrepentido, bien, como arrepentido o expirado por el tema del tiempo.

00:48:36

Marcos Perez: Cuando el fondo ya es se le deposita la plata a la
Sebastian Cárdenas: pas
Marcos Perez: persona, tenemos también ya creadas las cuotas que después se van a cerrar y lo va a dejar como como cancelado. Así que sí, tenemos todo el registro de la creación del crédito,
Olivier Luce: Si si el día de mañana vos querés hacer un tablero de seguimiento de cuántos
Marcos Perez: básicamente.
Olivier Luce: se te quedan a lo largo del funnel, lo puedes hacer.
Sebastian Cárdenas: Pero además ya tengo calculadas las cuotas, ya tengo los montos asignados, o sea, a eso voy. todos los datos que están dentro del crédito.
Marcos Perez: Si lo que no tenemos creada nada más son las cuotas de la persona en si, por ejemplo, en caso de que no esté fondeado el crédito,
Sebastian Cárdenas: Ah,
Marcos Perez: pero si tenemos la referencia a qué crédito estaba apuntando y después tenemos la referencia a
Sebastian Cárdenas: okay.
Marcos Perez: qué cuotas estaba apuntando. Entonces,
Sebastian Cárdenas: Okay. Pero no no se crearon las cuotas en ese
Marcos Perez: de la persona, ¿no?
Sebastian Cárdenas: momento.
Marcos Perez: ¿Se entiende un poco la diferencia entre entre las cuotas del template y las cuotas de la persona o querés hacer doble clic ahí?
Sebastian Cárdenas: Sí, sí, sí, sí, sí. No, no.
Marcos Perez: Bien,
Sebastian Cárdenas: Yo quería saber cuándo se
Marcos Perez: bien.

00:49:48

Sebastian Cárdenas: creaban.
Marcos Perez: Las cuotas de la persona se crean después de fondeado el crédito. Es decir, si yo me arrepentí,
Sebastian Cárdenas: No hay ninguna otra condición.
Marcos Perez: claro, después una vez que se fondeó el crédito, se crean las cuotas de la persona. Sí,
Sebastian Cárdenas: Y durante 10 días puedo cancelar esas esas cuotas que ya están creadas sin
Marcos Perez: así es.
Sebastian Cárdenas: costo.
Marcos Perez: Así es.
Olivier Luce: haciendo, sí,
Sebastian Cárdenas: Ahora y
Olivier Luce: hago un comentario ahí. La cancelación concretamente es manual,
Sebastian Cárdenas: vamos.
Olivier Luce: es el operador tiene que ir a buscar esos fondos, tiene que comunicarse con el cliente, pedir los fondos y eh resolver cómo captura justamente esos fondos. Pero no es no es que hay una validación de que los fondos estén disponibles en la cuenta de el cliente para nosotros después tomarlos. Eh, eso
Sebastian Cárdenas: Pero mi pregunta, mi pregunta va hacia este lugar.
Olivier Luce: sí.
Sebastian Cárdenas: En algún momento yo hago un bajo estos datos para dárselos a esa persona que va a retener la plata que sube estos datos. ¿En qué momento desaparece de esa lista el tipo que se dio debajo? que dijo, cancelo el crédito durante los 10 primeros días a partir que que dice cancelo ya deja de existir en etc.
Olivier Luce: Buenísima pregunta.

00:51:12

Olivier Luce: Eh, corregime, Marco, si me equivoco, pero en el backoffice te va a, o sea, vos tenés auditorio, o sea, el log va a estar siempre va a estar.
Sebastian Cárdenas: Sí,
Olivier Luce: Ahora yo ahora les voy a mostrar eh les vamos,
Sebastian Cárdenas: sí.
Olivier Luce: bueno, es en esta justo en esta pantalla. Yo voy a tener el listado de todas las solicitudes de las cancelaciones estén en el estado, o sea, sea arrepentimiento o cancelación, voy a tener justamente este listado y el que tiene que cerrar el ciclo de la cancelación soy yo, operador. Después le puedo poner un comentario incluso y también se registra en el log por qué o qué hice o cómo lo resolví un campo de texto. Eh,
Marcos Perez: Así es.
Olivier Luce: estoy en lo correcto,
Marcos Perez: Acá en este caso,
Olivier Luce: Marcos.
Marcos Perez: sí, en este caso, por ejemplo, tenemos las cuotas creadas porque ya se había fondeado el crédito.
Olivier Luce: No.
Marcos Perez: Pedimos la cancelación al operador del backoffice. El backoffice recién canceló la operación y eh fíjense acá que dice, "Bueno, no queda deuda pendiente y tenemos las tres cuotas como canceladas." Es decir, ya no me aparece más en el reporte a la mantana para descontarle, por ejemplo, eh la cuota. se da como cerrado.

00:52:31

Marcos Perez: Es un estado justamente terminal del crédito, ¿no? Tenemos el estado pagado o cancelado. Ya está, quedó cerrado el crédito en este
Sebastian Cárdenas: O sea, que con con eh todo lo que exporta cuando
Marcos Perez: momento.
Sebastian Cárdenas: exporta las cuotas que van a ser pagadas por eh los empleados son las cuotas que todavía están vivas por el hecho de existir. Van a y ser de ese mes, van a van a viajar. No tiene ningún otro otra forma de identificarse que es estar viva.
Marcos Perez: Así es la la validación de eh el reporte que se envía la Mantovana es la próxima cuota pendiente que entra en el lapso de tiempo del mes vigente. Bien, que el crédito esté otorgado al menos un mes antes, o sea, que que el crédito esté otorgado, digamos, en el lapso anterior, porque no podés otorgar un crédito y cobrar la cuota el mismo mes. O sea,
Sebastian Cárdenas: Ahora
Marcos Perez: yo otorgo el crédito en este mes, la primer cuota se crea el mes que viene, entonces tenemos como siguiente cuota esa y que estén pendientes a pagar, ¿bien? Y que estén, bueno, en ese en ese de tiempo. Eso es lo que se le envía a la mantogana. El estado cancelado justamente no entra en el reporte y en caso de que yo pida un préstamo, por ejemplo, no sé, antes del día de corte, tampoco va a entrar.

00:53:57

Marcos Perez: La siguiente cuota se va a registrar para el mes que viene.
Olivier Luce: Yeah.
Marcos Perez: Esa es la validación que se toma para el envío.
Sebastian Cárdenas: Okay.
Olivier Luce: Bien.
Marcos Perez: Excelente. No sé si contesté tu pregunta, Seba.
Sebastian Cárdenas: Creo que
Marcos Perez: Okay.
Sebastian Cárdenas: sí.
Marcos Perez: Bueno, esto obviamente queda en la auditoría, quién lo canceló, cuándo lo canceló y el cambio de estado. Bien, eh, ¿qué más tenemos? Tenemos esto, tenemos los pagos, tenemos los versionados que también van a ir estando en el historial, el usuario que los hizo, qué documento puso.
Olivier Luce: documento. Estamos hablando de la el paso de la firma.
Marcos Perez: paso
Olivier Luce: Si bien todavía falta cerrar eh lo de lo que tenemos que ver con Nico Ortiz
Marcos Perez: de
Olivier Luce: mañana, eh ahí nosotros de nuestro lado el horario perfecto. E ya hay cierta lógica que nosotros ya tenemos construida. Sí,
Marcos Perez: Así es.
Olivier Luce: Marcos.
Marcos Perez: Eh, de este lado, eh, un cambio ahí que habíamos hecho último que nos había avisado Jo, básicamente, que era el tema de la storage key, que es lo que estamos guardando en este momento. Nosotros no guardamos eh la URL, digamos,
Sebastian Cárdenas: Wow.
Marcos Perez: de descarga directamente, sino la K después lo vamos a ir a buscar al baut.

00:55:29

Marcos Perez: Eh, esto va a ser para todos los documentos. De la misma forma tenemos lo que es la firma del usuario. Una vez que el usuario firma, nosotros guardamos eh la K de ese documento para después obtenerla. Y lo mismo eh para lo que es la descarga, que habíamos dicho que se podían descargar hasta 25 reportes, lo que se hace es se junta, se zipea,
Sebastian Cárdenas: Buenas
Marcos Perez: se manda al ba y nosotros guardamos el storage key justamente de lo que es el sit. Bien,
Sebastian Cárdenas: noches.
Marcos Perez: obviamente eso tema documentos, eh falta darle una vueltita, pero lo que es la lógica ya la fuimos integrando. Bien, después eh por otro lado tenemos las configuraciones de la cuenta. Lo pusimos para que sea algo bastante más configuracional y no ponerlo en una variable de entorno, que es el día de corte del envío eh para el envío de los reportes. Bien, en este caso está como default el día 20. El día 20 va a pasar el Chrome, va a recopilar todo y lo va a enviar. Y lo mismo e a qué mails se va a enviar eh el reporte. Bien, esto se puede configurar. Justamente lo mismo lo hicimos para no ponerlo en una variable de entorno y que quede un poco más personalizable por si el día de mañana cambia.

00:56:54

Marcos Perez: Bien.
Olivier Luce: Ahí, ahí pausa.
Marcos Perez: khul
Olivier Luce: sea eh Put, esto se era lo que habías pedido de sí, definimos el 20, pero si lo quiero correr lo puedo configurar y si tengo que agregar a alguien de en el mail lo puedo agregar, lo puedo modificar y además tengo después más ahora lo vamos a mostrar más adelante voy a tener el registro de cuándo se mandó, si se mandó bien, si se mandó mal, si lo tuve que extraer, cuántas veces lo extraje. Ese seguimiento también lo tenemos de las exportaciones y después vamos a ver las importaciones de los archivos.
Marcos Perez: Así es. Eh, bueno, lo que es importación ya lo habíamos visto en realidad con el con el end point.
Sebastian Cárdenas: Acá está dando
Olivier Luce: Dale, teja.
Marcos Perez: Oi.
Sebastian Cárdenas: todo lo que dijiste, así o se me va internet.
Olivier Luce: Eh,
Sebastian Cárdenas: Esa es la otra opción.
Olivier Luce: te me Ahí se escuchó o no.
Sebastian Cárdenas: Yo escucho. No sé si ustedes me escuchan.
Marcos Perez: dijo, "Así que bien, escuché en algún momento, así que
Olivier Luce: O sea, okay, bien. Ahora sí,
Marcos Perez: bien.
Olivier Luce: igual haciendo una pausa con esto para poder probar esto con el entorno ya eh de dev, si no mal me equivoco, eh que no llegue, tenemos que probar que no llegue el mail.

00:58:21

Marcos Perez: Así es.
Olivier Luce: Eh eh para eso lo vamos a necesitar.
Marcos Perez: Eso, eso lo fui hablando con Gonza, eh, que están básicamente las variables eh para configurar todo lo que es el envío de
Olivier Luce: Entonces,
Marcos Perez: mails. Los crons, digamos, ya están preparados.
Sebastian Cárdenas: Bien.
Marcos Perez: están los tres crons preparados, tanto el envío como el los dos de corte, así que calculo. Obviamente va a haber probarlo cómo se comporta en stage, pero ni bien este el deploy, eh, nada, habría que testearlo y ya sale con fritas eso. E y después, bueno,
Olivier Luce: Bien.
Marcos Perez: eh, eso sería básicamente más o menos eh la pasadita. Eh, después, bueno, tienen el insomnia, eh, si le importan, básicamente están todas las funcionalidades, todo lo que fuimos hablando. Eh, hay varios casos que obviamente van a tener que por ahí si lo van a probar tocarlo un poco, por ejemplo, acá el get que te pide un ID, bueno, ir llenando algunas variables. lo mismo que es, por ejemplo, Credit applications para ir aprobando las cosas. Pero bueno, básicamente tienen todo cargado acá, dividido por carpetas. Lo que es la parte mi es la parte de mobile, eh, que sería la parte que va a acceder el usuario final, que está eh básicamente capado por lo que puede ver y lo que no puede ver, ¿no?

00:59:55

Marcos Perez: Después Payroll Noveltes, que sería esto que Estábamos hablando de la mantovana,
Sebastian Cárdenas: y
Marcos Perez: perro el confi, que es esto del mail y la fecha de corte.
Sebastian Cárdenas: posible
Marcos Perez: Eh, y básicamente eso serían todas las carpetas. No sé si me quedé con alguna. Los templates, document templates, que es esto que vimos básicamente de los tipos de documento para el día de mañana poder escalarlo un poco más. E, bueno, tenemos algunos casos también de error como para que los puedan probar. Eh, y bueno, eso sería más o menos eh la revisión. No sé si ha quedado alguna duda.
Olivier Luce: Bien.
Marcos Perez: E yo he mandado dos PRs. Jo, mandé, no hay uno que ya lo corregiste, mandé otro, eh, así que nada, cuando puedas apuro, está ahí. Eh, y por ahí estaré mandando alguno más mañana seguramente.
Jose Salgado: Perfecto, chicos. ¿Les parece que antes de irnos le pegamos una repasadita a esto del trehol para la evaluación de cuándo el cu está apagado y cuándo no? Cuestión de que nos llevemos ya el accionable listo para trabajarlo. Cevitas
Olivier Luce: Excelente.
Sebastian Cárdenas: Sí, sí,
Jose Salgado: ese
Sebastian Cárdenas: estoy acordo.
Olivier Luce: Bien.
Jose Salgado: consulta, Marquitos.

01:01:17

Jose Salgado: Eh, esto eh digamos esta diferencia de pagado con error, pagado, o sea, sobrepagado o o o pagado de menos, eh es factible agregarle alguna patita de configuración, decir, "Che, si esto es igual o la diferencia queda dentro de estos rangos, eh, es aceptable. Eh, eso, ¿cómo lo ves? como cómo te, o sea, entiendo que tiene que ser una una configuración va a ser bastante generalista al principio, o sea, una variable de entorno, decir, "Che, las igualaciones son iguales, sí son iguales o quedan dentro de este rango.
Marcos Perez: Bien. Eh, mira, sí, en un momento antes de de poner justamente lo de Big JS, esto para para guardar la precisión absoluta, habíamos hecho una especie de redondeo, eh, o sea, poder hacerlo se puede, lo podemos agregar en la capa de negocio por ahí esto de que tenga no un redondeo, sino un dark justamente por completo a un pago que por ahí entra dentro de un margen. Eh, podríamos hacer eso o podríamos hacer eh justamente por ahí algún endp específico, eh, o no sé. Ahora está bien.
Sebastian Cárdenas: No.
Marcos Perez: Sí, sería
Jose Salgado: Y ojo, hay una realidad. Si vos agarrás eh y rescalás la parte decimal en dos big decimal y les resescalás la

01:02:38

Marcos Perez: Eh
Jose Salgado: parte decimal a la misma forma y le decís, "Che, son iguales, esas diferencias se pueden llegar a solventar." Pero para no quedarnos solo con eso, podríamos hacer esto otro que a la hora de decir que esto porque entiendo que en algún un caso vos decís, "Esto es igual, ¿no? Bueno, o voy para allá o voy para acá o voy para acá y y me voy fijando." Bueno, en el momento que decimos esto es igual o bueno, porque aparte estamos hablando de una precisión, o sea, que vamos a hablar de cuestiones de milésimas, o sea, entiendo que milésimas o centésimas eh son valores realmente pequeños.
Sebastian Cárdenas: Vamos.
Marcos Perez: Bien.
Jose Salgado: Sí.
Marcos Perez: Y y ¿cuál sería el threshold? Decimos, por ejemplo, a partir del cuarto, o sea, sería milésimas, ¿no? el
Jose Salgado: Sí, yo iría al al orden de la centésimas, ponerle que me queden 50 centésimas de diferencia,
Marcos Perez: cuarto.
Jose Salgado: o sea, que son tres lugares decimales, dado que por lo general eh perdón,
Sebastian Cárdenas: Hay dos
Jose Salgado: Cevitas, te voy a mutear. Gracias. Eh, dado que por lo general eh vamos a usar o pesos de de dos dígitos, o sea, dos posiciones decimales, o en el mejorísimo de los casos de tres.

01:03:57

Jose Salgado: Más de eso no vamos a utilizar. Si está bueno la hora de hacer cálculos con todos los decimales para no perder plata en el camino, es mucho más cuando las cuotas son largas y hay procesos iterativos, ahí se puede perder mucha más plata. Eh, pero bueno, eh, entiendo que con tener un un valor, o sea, inicialmente creo que este valor lo vamos a ir ajustando, por eso digo que está bueno que sea una variable de entorno y no esté pegado directamente en el código, eh, pero yo creería que tiene que andar alrededor del 0,00 algo,
Marcos Perez: Bien,
Jose Salgado: que es lo que llegar a ser la diferencia entre eh los valores,
Olivier Luce: Bien.
Jose Salgado: o sea, digamos, si pago con 15 centavos de más o 15 centavos de menos.
Marcos Perez: Bien.
Jose Salgado: Bueno, o sea, porque también creo que hay ahí una decisión de negocio, por eso estaría bueno que sea configurable. De última nosotros dejamos un valor que se nos ocurra por omisión y que después la compañía tenga la posibilidad de decir, "Che, me parece que 25 centavos darle mal pagado está bien o está mal." y nada y que eso lo pueda lo pueda seguir cursando
Marcos Perez: Bien,
Jose Salgado: la
Marcos Perez: ¿crees que sea configurable con como el tema del día de corte y el email o preferís enviarlo en el endo?

01:05:12

Jose Salgado: no. Eh, yo creo que eso en realidad debería ser eh configurable internamente, o sea,
Marcos Perez: más variable entorno,
Jose Salgado: que Sí,
Marcos Perez: ¿no? No, operador de backoffice.
Jose Salgado: sí, sí, sí, sí. mucho más sólido,
Marcos Perez: Bien.
Jose Salgado: por lo menos hasta que entendamos que eso está bien y que y digamos y que no hay posibilidades de que por alguna cuestión se altere. variable de entorno. Creo que está superb porque entiendo que esto además va a tener una integración sobre nuestras plataformas, va a tener una prueba propia nuestra. Eh, nada, con una variable de entorno, de ser necesario, luego se agregará, pero me parece que una variable de entorno está correcto. ¿Estás Ok.
Sebastian Cárdenas: Super.
Olivier Luce: Bien,
Sebastian Cárdenas: Okay.
Olivier Luce: ahí eh bueno, Sebas, después nos juntamos aparte, obviamente esto entiendo que se se extiende más allá He. del del alcance, pero bueno,
Jose Salgado: No me robes,
Olivier Luce: obviamente lo podemos podemos ayer.
Jose Salgado: no me robes,
Olivier Luce: No,
Jose Salgado: no me robes.
Olivier Luce: jamás jamás jamás no jamás jamás. No, pero hagamos un hagamos o ¿Por qué lo por qué lo expreso?
Jose Salgado: Amen.
Olivier Luce: Porque hagamos un un listado un poco de de del estado de situación de qué cosas de qué cosas nos faltan para estar al 100% perfectos.

01:06:23

Olivier Luce: Eh, bueno, sin duda tenemos que tener, o sea, para poder estar perfectos, tenemos que tener el entorno de dev al 100% eh integrado. Eh, tenemos que hacer el ajuste que nos solicitaron de los eh de de los lambdas. eh no lo obviamente no lo teníamos capturado, eh, así que eso también nos conlleva un un esfuerzo. Eh,
Jose Salgado: Un segundo.
Olivier Luce: Cona,
Gonzalo Kuhn: Sí,
Olivier Luce: sí.
Gonzalo Kuhn: ahí eh pienso digo en voz alta en el mientras eh lo que podemos hacer es yo ahí estoy haciendo los fix porque ahí me encontré con con otro quirombito más que como el a la hora de hacer el 6CD hay un hay un archivito que es el billsp que básicamente es un archivito que le dice cómo tiene que que meter. Bueno, es es tanta la cantidad de data que hasta que me explota el bspect porque supera la cantidad de caracteres que tiene que meter. Así que yo estoy haciendo los ajustes y lo voy a hacer manual como para por lo menos ya tener los últimos updates que que pasaron los chicos. Eh,
Olivier Luce: Bien.
Gonzalo Kuhn: tengo que agregar también que eso es un pendiente mío, el tema de las migraciones que justo le decía Marcos, pero bueno, eso también lo ejecuto manual, así por lo menos tenemos el update, estamos al día y pueden continuar con eso en el mientras sí, si ustedes pueden eh hacer ese ese merci estaría bárbaro por todo lo que hablamos antes para no repetir.

01:07:51

Gonzalo Kuhn: Así que si si les parece, vamos por ese camino para quizás agilizar esa parte y y poder algunas
Marcos Perez: Dale, me parece bien.
Olivier Luce: Tam.
Marcos Perez: Sí, sí, porque mientras tanto podemos ir testeando un poco el general.
Gonzalo Kuhn: cos.
Marcos Perez: Después va a haber que volver a testear, eh, pero pero por lo menos Sí,
Gonzalo Kuhn: Sí, pero por lo menos ya ya te sacas encima eh algunas cosas que hacer un retesting de todo,
Marcos Perez: sí, sí,
Gonzalo Kuhn: pero por lo menos sabes que eso va a encaminar. E hay otra consulta que es eh para el tema de los envíos.
Marcos Perez: sí.
Olivier Luce: H
Gonzalo Kuhn: Nosotros por por política de seguridad y zaraza zaraza, el tema de CES lo tenemos limitado en un estado sambo. Eso quiere decir que los identities, digamos, los estination los tenemos que ir agregando a mano y tiene un un rate que es uno por segundo. Esto es porque si tienen que hacer algún envío masivo,
Marcos Perez: Bien.
Gonzalo Kuhn: por lo cual eh yo no sé si ahí ustedes tienen que hacer un envío a casillas particulares o si ya tenemos
Olivier Luce: Okej,
Gonzalo Kuhn: definido eso. Y después esto mismo, si tienen que hacer un broadcast masivo, hay un límite de 200 por día. con lo cual y para que lo tengan en cuenta.

01:08:55

Marcos Perez: Bien, no, ahí te pasé mi mail, eh, que por Right. y es con el que podemos probar.
Gonzalo Kuhn: No
Marcos Perez: Eh, el envío de los reportes va a ser hacia la Mantobana,
Gonzalo Kuhn: sé.
Marcos Perez: o sea, va a ser hacia uno o dos mails específicos eh destinados por ustedes, digamos, y no va a ser masivo, va a ser un mail por mes, así que eh tranqui,
Gonzalo Kuhn: Ah, perfecto. Listo. Vamos.
Marcos Perez: entra.
Olivier Luce: Bien, continúo con las tareas pendientes, quizás más allá del del o además del del entorno. Eh, lo de los documentos. Eh, sin eso no podemos completar. Hay cosas que tenemos que terminar de de desarrollar y dependemos justamente de de esa definición.
Sebastian Cárdenas: Mañana nos juntamos.
Olivier Luce: Eh,
Sebastian Cárdenas: Ya mandaron el Sí,
Olivier Luce: ya lo mandaron. Espectacular.
Sebastian Cárdenas: 3 de la tarde.
Marcos Perez: Sí.
Olivier Luce: Ah, espectacular. Listo. Genial. Buenísimo. Eh,
Sebastian Cárdenas: Sí.
Olivier Luce: bueno, tenemos que implementarlo del cashout. Ahí ya tenemos la cuenta. No sé si de ese tema en particular, Marcos, nos falta algo
Marcos Perez: Eh, no,
Olivier Luce: más

01:10:02

Marcos Perez: la otra cuenta para testear. No sé si vos dijiste ya tenemos la cuenta, la han enviado.
Jose Salgado: Se las pasamos por eh
Olivier Luce: por el canal, creo, si no me recuerdo,
Jose Salgado: por si les falta otra,
Marcos Perez: Ah,
Olivier Luce: ¿no?
Marcos Perez: bien, bien. No lo había visto. Listo.
Olivier Luce: Listo.
Marcos Perez: Genial.
Jose Salgado: pidan. No tiene fondos.
Olivier Luce: Perfecto.
Jose Salgado: Si necesitan que le agreguemos fondos,
Marcos Perez: En todo caso,
Jose Salgado: avisen.
Marcos Perez: no, porque hacemos del otro lado para acá. Eh, bien.
Olivier Luce: Bien,
Marcos Perez: Ya con eso podemos implementar bien lo del cashout y testearlo mañana. Así que
Olivier Luce: bien. Eh,
Marcos Perez: José.
Olivier Luce: tenemos que validar después eh se alcance, bueno, lo del tre. ¿Y qué es lo último que falta? Bueno, me gustaría que ya en el entorno al 100%, ya sin más cambios que meter, eh hacer el UAT. Ese va a ser eh una reunión larga, pero bueno,
Jose Salgado: con
Olivier Luce: eh yo creo que es la la manera más prolija de de hacer la entrega eh escenario
Jose Salgado: café.
Olivier Luce: por escenario, eh, y validamos todo de punta a punta. Em, bien.

01:11:10

Olivier Luce: Eh, bueno, ahí no sé, Marcos, Nico, ¿tienen alguna algo algo que necesiten más?
Marcos Perez: No, eh había una cosa que bueno, eso no pude ver si está, eh, pero bueno, viene de la mano del documento después de los campos que queden. Habían algunos datos que que faltaban por ahí en el en el end point de mi cuenta de la insomnia. Eh, por ejemplo, había uno que decía eh persona jurídica, una cuestión por el
Jose Salgado: lo tiene.
Marcos Perez: estilo.
Jose Salgado: Cuando pedís la cuenta, eso se llama person type y va a ser J o F.
Marcos Perez: Ah, bien. Okay, listo. Listo. Eso estamos.
Jose Salgado: Viste que los pelados tenemos Bluetooth.
Marcos Perez: Sí, sí, sí. Yeah.
Jose Salgado: Bien,
Olivier Luce: Buenísimo.
Jose Salgado: chicos, una consulta. Este este frontend que que nos muestran tipo Sandbox,
Marcos Perez: Excelente.
Jose Salgado: ¿lo piensan levantar también en la infra?
Olivier Luce: No.
Jose Salgado: como para que los chicos de nuestro lado también puedan jugar un poquito y y quizás a veces cuando te lo muestran todo parece tener como superlógica y cuando vos lo probas más simulando tu idea de trabajo, eh eso puede abrir diferencias o que no que no significa que vayan a a a hacer nuevos desarrollos, pero pero que por ahí les puede llegar a a a mejorar un poco la evaluación de esto, dado que en algún momento ustedes tienen que salir y nosotros tenemos que decir también de nuestro lado de todo.

01:12:38

Jose Salgado: todos los lados, no solamente del técnico. Estamos okay con esto. Fin del juego. Eh, eso lo tienen pensado deployar, eh,
Olivier Luce: Ahí la por las dudas el alcance acá. Nico, corregime,
Jose Salgado: no.
Olivier Luce: si me equivoco, hasta donde tengo el eh entiendo que el entorno está hecho en Angular, si no mal me equivoco. E el alcance era principalmente la API, eso sin duda.
Jose Salgado: Ok.
Olivier Luce: Eh, ahí no sé, Nico, si queres algo más, si quieres agregar algo más, pero entiendo que era ahí.
Nicolás Paez: Sí, en sí, si bien estás fuera de del alcance eso porque era un player para mostrar, eh, tranquilamente se podría porque sí entiendo que Las pruebas por insomnia van a ser un dolor de cabeza hablando bien dentro de todo. El lo único tendríamos que ver con con Gonzalo capaz eso,
Marcos Perez: Gracias.
Nicolás Paez: eh, ¿qué tiene para web? El más que nada para configurarlo en ese entorno y que entre por el pipe directo,
Eugenio Valeiras: No.
Nicolás Paez: pero no habría ningún inconveniente más que nada para que cualquier usuario lo pueda probar y no te vaya hacer uno técnico por insomnia.
Jose Salgado: Claro, eso es lo que por me preocupaba, que a la hora de que Sebastian o o chicos mucho más de negocio que técnicos, le presentas un insomnia y se les explota la cabeza, lo cual es sumamente lógico.

01:14:01

Nicolás Paez: Sí. Y ojo, el comentario de Oli va más por el lado de no podrían que
Eugenio Valeiras: Hav
Jose Salgado: No.
Nicolás Paez: sea sí, pero probablemente no puedan copiar y pegar y llevar los backfies, pero si pueden úsenlo, o sea, no no es que es nuestro y no lo compartimos, no ustedes también, así que usenlo
Jose Salgado: Perfecto.
Nicolás Paez: más
Jose Salgado: ¿Esto es parte del repositorio o es otro repositorio? Necesitan un repositorio
Marcos Perez: Eh, creo que está en otro que ya nos lo dieron,
Nicolás Paez: es otro,
Marcos Perez: ¿no?
Nicolás Paez: ¿no?
Ezequiel Manfredi: Ya no creado,
Nicolás Paez: que yo sepa. No,
Jose Salgado: nuevo.
Marcos Perez: H.
Ezequiel Manfredi: parece
Nicolás Paez: yo no recuerdo haber visto uno de web,
Marcos Perez: Bien,
Nicolás Paez: pero puede ser que se me esté pasando.
Marcos Perez: bien. No, yo creí recordar que había uno, pero eso,
Nicolás Paez: No.
Ezequiel Manfredi: hay un par credit web.
Eugenio Valeiras: Hola,
Marcos Perez: pero creo que nunca pusemos ahí y no sé si tengo accesos
Ezequiel Manfredi: No, nunca lo puedo llegar.
Marcos Perez: a eso tampoco.
Jose Salgado: Bien, chequeemos y de última lo seguimos por por el canal que está el Tano que rápidamente lo puede solucionar.

01:14:59

Marcos Perez: Bien,
Olivier Luce: Bien,
Nicolás Paez: Dale,
Marcos Perez: genial.
Nicolás Paez: perfecto.
Marcos Perez: Lo apoyamos por ahí y ya
Nicolás Paez: Lo lo dejamos en la rama development y después ahí ver
Marcos Perez: está.
Olivier Luce: buenísimo.
Nicolás Paez: con si Gon hace los push directo de C o
Ezequiel Manfredi: Y ahí les confirmo que tienen acceso,
Marcos Perez: Ah,
Nicolás Paez: sí.
Ezequiel Manfredi: eh.
Nicolás Paez: Yo ahí entré y lo pude
Marcos Perez: listo, listo.
Nicolás Paez: ver.
Marcos Perez: Entonces, lo pusamos ahí.
Eugenio Valeiras: Espectacular.
Olivier Luce: Bien, buenísimo. Bueno,
Marcos Perez: Excelente.
Olivier Luce: bueno, estamos en contacto. Vamos que terminamos, no falta nada,
Ezequiel Manfredi: calculat.
Olivier Luce: ¿eh? A darle n más.
Jose Salgado: Bien, bien. Trabajo,
Olivier Luce: Bueno,
Jose Salgado: chicos.
Eugenio Valeiras: Chicos,
Gonzalo Kuhn: Ahora Tom
Olivier Luce: bueno,
Eugenio Valeiras: gracias por todo.
Olivier Luce: gracias.
Ezequiel Manfredi: Bueno,
Nicolás Paez: Un abrazo.
Sebastian Cárdenas: Adiós.
Ezequiel Manfredi: ahora sí de trabajo.
Marcos Perez: Nos vemos.
Eugenio Valeiras: Brazo.
Marcos Perez: Ciao.
Nicolás Paez: Co?
Marcos Perez: Ciao.

La transcripción finalizó después de 01:15:44

Esta transcripción editable se generó por computadora y puede contener errores. Los usuarios también pueden cambiar el texto después de que se cree.
