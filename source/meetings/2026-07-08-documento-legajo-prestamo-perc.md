# Documento — PERC (transcripción verbatim)

> **Audit anchor — NO editar.** Call del 2026-07-08. Participantes: Olivier (Me), Marcos Perez (Quarks dev, "Marquitos"), Sebastián Cárdenas / Scardenas (Them, PO PERC). Tema: el documento legal del flujo de crédito (legajo de préstamo AMFAYS). Artefacto adjunto: [../adhoc/2026-07-08-legajo-prestamo-amfays-v1.md](../adhoc/2026-07-08-legajo-prestamo-amfays-v1.md).

---

**Meeting Title:** Documento - PERC
**Date:** Jul 8
**Participants:** Olivier, Marcos, Scardenas

Them: Aló.
Me: Bien, bien, Ahí viene ahí viene Sevita, lo matamos de un tiro.
Them: No, es mentira, no sé. No sé si la es.
Me: No, no, no, no, así no. Voy a compartir acá. Desastre. Le bajo. Buenas buenas,
Them: Buenas.
Me: ¿Cómo va? ¿Estás resfriado?
Them: René. Remera rack beer que pegaste.
Me: Me la regalaron, ¿viste? Me la regalaron, ¿viste? No, y acá yo vivo, a tres cuadras del del casi no podría
Them: No?
Me: No podría, señor.
Them: Muy bien. No sé qué...
Me: ¿Qué hace, Seba? ¿Todo bien?
Them: No sé quién es la contra del casi, pero me imagino que sí. Con esos colores no querés
Me: El ZIG, el ZIG, el Es del es del sik, yo soy yo soy del casi igual. Sí.
Them: Vamos. Yo casi que sé de qué hablas. ¿Qué qué andamos haciendo? ¿Qué andamos haciendo?
Me: Boa. Andamos haciendo? Bueno, te paso a mostrar vamos bien, en concreto, acá. Estamos aquí con Marquitos, el amo y señor de el código. Estamos, o sea, prácticamente, ya estamos por terminar, o sea, no falta prácticamente nada, ahí ya le pasamos los los los PRs algunos a Job, y ya los va a revisar, así que estamos flama,
Them: Jo, estos tres días está de licencia, Te aviso hasta el lunes. Ahí va.
Me: ¿Quién va quién puede quién Pero nos contestó, es raro.
Them: Puede ser, porque es un limado.
Me: Ok, bueno. Ojo con los PRs que íbamos a mandar hoy. Y ya nos contestó, y los que puedan llegar a venir mañana o pasado.
Them: Sí.
Me: Si no, tengo que moverla si no, que mover la u a t, ahí lo lo lo que vos consideres.
Them: Mañana y pasado, nosotros no trabajamos.
Me: Perfecto.
Them: Ok. Era eso ya me lo preguntaste, Once, que ya lo contesté. Bueno, nosotros mandamos los PR, los dejamos ahí y cuando vuelvan, los verán.
Me: De
Them: No, no, no hay grama.
Me: Si no, muevo la reunión del lunes al Porque hay Marcos, si los aprueban el lunes, si los aprueban el... Ya estaríamos ok para poder para poder hacer el UAT.
Them: Sí. Sí, nosotros podemos hacer tipo como si fuese a hacer un happy path y los PR que hagamos pasen, vamos avanzando como asumiendo que eso pasa. Después vemos, pero pero sí, sí, se puede hacer.
Me: Bueno, listo, entonces, no modo nada. Bueno, entonces, documento, Marcos,
Them: Bien. Bueno, cuestiones. Por un lado, lo necesitaríamos en formato HTML, que es el formato que va a estar después para, digamos, que que se editen las variables y todo. Después nosotros lo a PDF cuando se lo enviamos al usuario, en todo caso, pero que la carga debería ser siempre en HTML, para, justamente, manejar variables como, por ejemplo, ahí apellido, nombre, fecha de nacimiento, documento. Todo eso lo podemos editar cuando esté en formato HTML. Eso por un lado. Por el otro lado, tema formateo, no sé qué pasó acá, si es que por ahí ustedes lo han formateado con algo. O qué, pero como verás, está todo como medio extraño, Es más, hay algunos textos medio raros, mirá, por ejemplo, bajá, Oli,
Me: Propietario del vehículo,
Them: bajá un Sí.
Me: propietario del inmueble. Es como
Them: Eso no sé, si es lo que van a poner, digamos, sí, pero Sí, yo yo hice las mismas preguntas sobre un montón de datos y habla de fuerzas armadas y qué sé yo, pero me dijeron, así lo usan para cualquier tipo de aplicación, y no no necesita tener todos los campos llenos. Tenemos que completar los campos necesarios para el pedir el préstamo. Bien.
Me: Tenemos que tener bien claro cuáles son los que los necesarios, porque ahí hay un tema Nosotros tenemos, o sea, los datos que que vienen de el de del endpoint del usuario o sea, lo los tenemos que tener todos, después nosotros completamos con aquellos que son referentes al préstamo en particular. Pero si hay campos que sean de opción, como, por ejemplo, sí, no, o los que siguen, por ejemplo, datos familiares, que son de carga manual, esto no, o sea, está está por fuera de la alcance, nunca habíamos hablado de de de de darle el paso al al cliente de cargar estos datos. Por ejemplo, datos familiares,
Them: Todo lo que es tablas
Me: del subsidio,
Them: que aparte de otra cosa, yo sugeriría que estén tipo en formato plano, todo, más como está más abajo, este tipo más como un texto, para que nosotros podamos poner las variables y ir reemplazándolas por los datos del usuario, pero por ahí no, tipo formato tabla y eso, porque supongo que va a quedar un poco raro. Sugeriría eso. Sí. Esta es una empresa que no somos nosotros, entonces, tengo que averiguar bien qué pasa. Los formularios tienen que ser aprobados por una entidad. Que regula la superintendencia de seguros. Los que nos insistieron en usar este mismo documento era porque estos están ya aprobados. Tengo que averiguar si me parece obvio que lo que aprueban no es el formato, sino el De ser el formato de lo que aprueban, sería más complejo, porque si lo ven, claramente este formato es formato de lo imprimo y lo lleno. Sí. O sea, es tiene cuadraditos en un lugar, o sea, es
Me: Sí.
Them: es claramente imprimible. Ahí en c v larga u de abajo tenés cuadraditos. Entonces, me llevo estas dos preguntas. Uno es si se puede cambiar el formato y el otro es son tres, cuáles son los datos mínimos necesarios y tres, cómo vamos a hacer el input de esos datos, ya que dentro del scope no está la posibilidad de que hagan un formulario en donde el usuario hace el hace el data entry y todo esto.
Me: Que, de hecho, ni lo ni lo diseñamos, ni lo tuvimos en
Them: Sería Claro.
Me: cuenta en el en el en el diseño.
Them: Pero pero está correcto la, más allá, eso, o sea,
Me: Sí, sí, sí, sí, sí, sí, sí, sí, sí, sí, sí.
Them: ok. Sería eso, sería el formato, campos, hablando de los campos también, por ejemplo, ustedes nos dieron a nosotros un endpoint que es de mi cuenta, ¿no?, para obtener los datos de la cuenta que está logueada Bueno, esos campos que nos devuelve, por ejemplo, no sé, antigüedad, legajo, localidad, código postal, PJ, todo eso, va, sí viene. Pero todo lo demás no está. Entonces, en todo caso, habría que anexarlos al endpoint de cuenta, para que nosotros lo podamos obtener. Porque en ese caso, si no, no los estaríamos teniendo. O hacer un un front donde lo llenen. El tema es que Por eso yo yo yo les dije lo mismo sobre este formulario. Pero me insistieron mucho. Déjame, entonces, ahora que ya tengo información la cual ir y reclamar para que tomen una decisión. La decisión a es modificarlo para que esté adaptado y eso implica modificaciones del formato, modificaciones del endpoint, modificaciones de los datos que nosotros guardamos, Alternativamente, que el usuario complete un formulario que no está dentro del scope, y la tercera opción es que me den una idea nueva. Sí. Entonces, voy con esto. Bien. Yo necesitaría hablar con alguien antes de poder seguir sobre esto.
Me: Perfecto. El, o sea, los tema de tiempos, estamos bastante jugados, Tenemos la tenemos toda la semana que viene, ¿no? Pero ¿qué es qué es la la la última semana? Yo te paso te paso en limpio el el requerimiento, si querés, más estructurado, para que
Them: Dale, por
Me: que quede más fácil.
Them: Y quiero aprovechar esto también para hacer otra pregunta, que, claro, la hice ahí en el grupo, pero si cuesta de licencia, no creo que me conteste. No sé si tenés idea vos, Seba, de lo que es la documentación, esta de la insomnia que nos pasaron, No la conozco, pero sí sé que les habían pasado. Ok. A nosotros nos dieron un endpoint, por ejemplo, para obtener info sobre un CPU. ¿Verdad? Ajá. A su vez, también nos dieron uno de cash out, que sería para efectuar el desembolso. Ok. Ahora, mi pregunta es, ¿ustedes nos van a proveer el CVV de la cuenta que tiene los fondos yo tengo que consultar con ese si tiene fondos, ¿verdad? Entiendo que sí. Bien, ok, venía por ahí la mano. Porque por ahí habían hecho el cash out de una forma que yo lo pueda consultar y pedirle los fondos mismo tiempo. Pero bien, listo. No, no, no, es chequear Primero chequeá si hay fondos, y si hay fondos, mandás Bien. Estaría bueno, o sea, no no te lo digo que es una tarea tuya ni y de ni de quartz ni nada, que nosotros hubiésemos creado un endpoint donde además de consultar vos podrías reservar, porque, técnicamente, entre entre que vos consultás, y transferís, hay un tiempo. Aunque sea un microsegundo, hay un tiempo, y en ese tiempo puede dejar de dar fondos. Sí. Sí. O pueden estar los fondos, pero pueden estar en un estado no se pueden enviar. No, yo lo que me imaginé, sino también es el mismo endpoint de decirle cuánta plata quiero, que se fije si están, y ya de una lo saque. Sino más que consultar y después pedir los fondos. ¿Entiende? O sea, una de consulta y pedir al mismo tiempo prevendría este en que Con los los endpoint que vos tenés, ¿ya podés hacer eso? Pregunto, porque no sé. No, y yo tengo este que te digo de consultar cbú, Sí. Y el de cash out, que sinceramente todavía no lo he podido probar, faltan tipo algunos datos. Ah, y de consultar fondos no te pasaron. Claro, sería creo que el de obtener CVU. El de obtener CVU te dice si la cuenta tiene dinero. Pero Pero ¿te dice cuánto dinero? A ver, no O es Muliano, tipo, tiene o no tiene. No, te decía cuánto, a ver. CBU
Me: Haciendo un paréntesis,
Them: Sí.
Me: ese FIFO. Primero, que entra es el primero que sale. Bien. Justo ahí Marcos me preguntaba eso. Así que estamos.
Them: Ah, no, mentira, no dice. No dice el dinero que tiene. Claro. No, no dice el dinero. Bueno, ahí le consulto a los chicos. Habría, claro, necesitaría saber cuál sería el endpoint para saber si hay fondos y y el de cash out Sí. Había preguntado, me está pidiendo como muchas variables que no están en el insomnia, así que me dijo que no lo puedo estar usando, básicamente. ¿Y les podés pasar eso por el grupo? Dale. Ahí ahí lo mando por por el demo. Así yo pido que lo conteste.
Me: Bien, entonces, worst case scenario, O sea, el el mejor escenario es el lunes contamos con lo de los documentos y con esto del endpoint. Ya ya sabemos que, bueno, mañana y pasado no no no están, ¿no? Pero mejor escenario, lo tenemos todo, sale el UAT y tenemos tiempo como para hacer correcciones. En el peor escenario, al al lunes a la tarde no contamos con los documentos, con el documento, y hay que modificar o hay que hacer algo con el endpoint de validación de fondos, y tendríamos que mover la reunión. Estamos de acuerdo, ¿no? Eso, sí. Bien. Ok, listo. Bueno. Te, hoy en la tarde, entonces, te pregunto, a ver, si si tuviste alguna respuesta.
Them: Dale, perfecto. Mauricio,
Me: Listo. Ah, ahí te paso, lo de lo del documento, si querés.
Them: Vale. Excelente.
Me: Listo. Te veo estresado,
Them: Me quedó lo del partido de ayer, estoy todavía.
Me: Treme.
Them: Procesando. Estoy procesando, sí.
Me: あれ ？
Them: Bueno, chau, gracias, muchachos.
Me: No,
Them: Chao.

---

**Nota de Olivier (contexto de la tarea, post-call):** hay que saber qué campos necesita el documento, qué campos están disponibles en el endpoint (`mi cuenta`), qué campos se completan con los datos del préstamo, y qué campos necesarios son de carga manual pero quedan fuera por alcance del proyecto. Después del ingest, armar el requerimiento del documento para facilitar la gestión interna en PERC.
