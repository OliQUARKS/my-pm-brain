# Daily - PERC — 2026-07-20 (verbatim source)

> Immutable audit anchor. Never edited after creation.

**Meeting Title:** Daily - PERC
**Date:** Jul 20 (2026-07-20)
**Meeting participants:** Olivier ("Me"), Marcos Perez, Nicolás Paez, Pablo Folgar

---

## Transcript

Nicolás Paez: Buenas.
Me: ¿Aló, aló?
Marcos Perez: Sabía, si
Nicolás Paez: nadie. ¿Cómo va?
Pablo Folgar: Muy bien. ¿Ustedes?
Me: ¿Cómo anda nuestro corresponsal de guerra?
Nicolás Paez: Valencia.
Pablo Folgar: Pasaban a la una de la mañana gritando argentinos putos, así que nada. Tranquilo.
Me: Pero ¿festejan o no festejan?
Nicolás Paez: Bien.
Pablo Folgar: Sí, pero pasa es un yo creo que está relacionado, yo creo que lo que la falta de euforia está relacionada a la falta a la falta de problemas reales. Entonces, el como como no tenés muchos problemas, económicos, de seguridad, Entonces, nada, es, estás contento. Nosotros es un montón. Nosotros es un montón. Es un montón, buéxes de sabor, pasa cuando vas a la a la cancha.
Me: Una una
Pablo Folgar: Ya la necesitas, la estás por otro lado. No, le falta le faltan kilos de de pasión. Nada, buen kilo.
Me: Qué difícil. El el buzo rojo que suelo usar, no lo puedo desde acá a un mes, lo tengo dañado claramente.
Pablo Folgar: Solamente. Claramente. Encima, que es más vos lloras Claramente. Encima, que es
Marcos Perez: vos lloraste dos veces encima.
Me: Sí, las cosas que lo parió. Sí, sí, sí. No,
Nicolás Paez: Claro.
Me: Nada, el partido del sábado,
Nicolás Paez: Te diría igual,
Me: no tiene valor.
Nicolás Paez: más que un mes, capaz que son cuatro años, Así que ahí
Me: Cuatro años.
Nicolás Paez: vos fijate si lo...
Me: O sea, pero no tiene el escudo, no tiene el escudo, pero es
Pablo Folgar: No, no, Escuchame, Alba. A los políticos en mucho menos tiempo, que a a vos por un buzo. Tranquila.
Me: Sí, sí, sí. El tema es que me perdone, que saliendo a la calle, ¿viste?, que no me cae un cascotazo.
Pablo Folgar: Bien. Tengo eso ahí, vas a.
Me: Bueno, bueno, hacemos un un estatus más que nada para para para Pablo, ya Nico, bueno, Nico y Nico y Marcos estamos más que más que al día. Contamos, el jueves nosotros tuvimos ese UAT, lo voy a
Them: Sí.
Me: poner comillas visibles. ¿Por qué UAT? Porque directamente no teníamos el entorno de al cien por cien como para poder realizarlo, entonces lo hicimos en local. Entonces, fue más o menos un una demo punta a punta, con ello, con el TL, con el CTO, con el de con los los del lado de ellos, y la verdad es que salió espectacularmente bien, así que aplausos ahí al equipo. Muy bien salió, muy bien.
Pablo Folgar: Felicitaciones, equipo.
Me: Pero bueno, obviamente, nos surgen varias incógnitas o varias varias dudas,
Them: That's
Me: o varios cambios que ellos fueron pidiendo. El mismo día de la demo, te pongo en contexto, nos pidieron una rearquitecta de el manejo de los Llandas. Hay porque el consumo era bastante, bastante alto. Acá corrí chicos, si si es, si me equivoco, pero entiendo que era a mayor cantidad de lambda, más caro era, básicamente. Entonces, lo que pidieron era como juntar, para para ese manejo, entonces eso nos conlleva un un un un retrabajo ahí.
Pablo Folgar: ¿Esas bandas son nuestras que propusimos nosotros o eran de ellos
Me: Eso por
Pablo Folgar: que las tomamos nosotros
Marcos Perez: No.
Pablo Folgar: Digamos?
Marcos Perez: ¿Fue la arquitectura que se propuso desde un principio o la aceptaron? Sí.
Them: Viajando, fue viajando, fue viajando hasta que dé la
Marcos Perez: Viajando, fue viajando, fue viajando, hasta que de la nada no les gustó y, bueno.
Me: Fue
Pablo Folgar: Eso es. Ok.
Nicolás Paez: No es que no les gustó, sino que se dieron cuenta que eran Claro, sí. Muchas lambdas a deployar, entonces el CI tardaba cuarenta y cinco minutos en en y los costos se le iban a la mierda. Por el tiempo ese y no,
Pablo Folgar: Ah, ok. Porque lo siento Solo recibo. Infra propia. Pues lo siento Es la razón.
Nicolás Paez: No, en AWS, sí, con serverless, no.
Me: Entonces, ese quizás es uno de los temas más grandes, después, pero bueno, la reunión, igual Pablo fue salió espectacular. No hicimos el UAT caso por caso, sino que hicimos una una demo improvisada bastante larga, pero pero al fin,
Marcos Perez: Que al final se probó
Me: prácticamente todo, no
Marcos Perez: prácticamente todo, ¿no? Fue empezó a salir todo y
Me: no cada escenario así pequeñito, pero, básicamente, lo hicimos todo.
Marcos Perez: Sí.
Me: ¿El tema cuál es? O sea, ¿en tempos oficiales del proyecto, o sea, nosotros teníamos hasta mañana. Pero faltan varias cosas. ¿Qué cosas faltan? Primero, yo no puedo hacer un UAT si no tengo el entorno al cien por cien. Antes de avanzar con el próximo punto. Ahora, ya con lo que subió Gonza, ¿el el entorno está bien faltan todavía cosas?
Marcos Perez: Relativo, porque está bien hasta ahí, porque después cuando hagamos todo el refactor, va a ver que
Me: Eso eso está clarísimo, pero al día de hoy es como
Marcos Perez: todo, digamos, pero sí.
Me: yo ahora me meto en el me meto en dev y está
Marcos Perez: Sí.
Me: al al al día de la demo.
Marcos Perez: Sí, eso sí.
Me: Bien, ok.
Marcos Perez: El tema es, no, no el día de la demo, sino un poquitito antes, porque había un perre abierto el día de la demo, que era el que yo tenía en local,
Me: Ah, okay. Okay. Okay.
Marcos Perez: Entonces, no está el día de la demo, pero así un poquito antes. El problema igual es, bueno, quién va a probar eso ¿no?, porque yo, digamos, tengo bastante para hacer, como no no no lo voy a poder probar. El entorno. No sé.
Me: Ok. Bueno, lo lo proyo.
Nicolás Paez: ¿En el Tony Wally? Sí, pero una vez que deployen la web, no sé si eso lo Sí, pero una vez que deployen la web, no sé si eso lo Claro, eso también estaría bueno, sí. Claro, eso también estaría bueno, sí.
Marcos Perez: Si de Ploj en la web. Creo que
Nicolás Paez: subir el Claro. Sí.
Marcos Perez: Tendría que subir el front y pedirle a Gonza que deploye la web apuntando stage, y va a estar mejor.
Me: Sí,
Nicolás Paez: Sí, por common, perdón, insomnia no tiene sentido, bolí, ponérselo.
Me: Perfecto. Perfecto. Si yo los puedo ayudar con esa parte del testing, la, no tengo ningún problema. Entonces, apuntamos a que suba
Marcos Perez: Sí, yo todavía tengo que subirlo a su repo, y ahí le aviso a Gonza y vemos. Onda, de traccionar el deploy del front. Una vez con eso, ya podríamos empezar a probar lo que hay hasta un PR Después yo tengo toda la parte de cash out, la estoy haciendo, me arrepentí a la mitad, pero bueno, ya ahora que le metí, le tengo que fuerte al medio, Hubiese estado bueno meter antes el refactor de los lambdas, porque ahora voy a agregar cuatro lambdas más, pero bueno, no pasa nada. Son cuatro y ya tenemos sesenta, así que no es mucho. Tengo toda la parte de cash out acá, Eso, bueno, va a ser un tema porque va a viajar, Por ahí, Nico, después te robo un tiempito para que lo veamos juntos, es bastante grande y hay muchas cosas, Dale. Como para por lo menos destrabar el pull request rápido y poder meterle a la parte de los lambdas, porque el refactor no lo voy a poder meter hasta que pase esto. poder meterle a la parte de los Lambdas, porque el refactor no lo voy a poder meter hasta que Son, de modificados son los sesenta archivos, muchos de test igual, porque son treinta de test, muchos de texto igual, porque son treinta pero bueno. Toda la parte de cash out es un cambio grande, y y meticuloso, digamos. Hay que ser ahí.
Me: Bien. Dentro de esa reunión de la de la demo, surgió lo del threshold de los
Marcos Perez: Sí, eso
Me: de los decimales.
Marcos Perez: Sí, eso le dejaría como una tercera etapa, o sea, yo encararía cash out ahora, y por ahí sí lo podemos meter por ahí entre se aprueba el PR de cash out, tarda mucho, lo metemos, y después el refactor de las lambdas, que va a ser otro cambio grande.
Me: Ahí les querés.
Marcos Perez: O sea, ahora dos cambios grandes.
Me: Ahí le querés dar un un poco de de comentario ahí a a Pablo para que lo tenga?
Marcos Perez: Sí, básicamente, quieren que tengamos un threshold para el tema de comparativas de números, para que no tengan que mandar exactamente el mismo número.
Pablo Folgar: ¿Cómo? Ahí me perdí.
Marcos Perez: Quieren que nosotros, digamos, pedimos el número exacto para dar por paga de un crédito, ellos quieren que haya un porcentaje de error ahí por si las dudas más por si las dudas Nada más, Margen de error, así que, bueno, abre de cambiar. Quiero decir,
Pablo Folgar: ¿qué porcentaje? ¿Cuántos...? Porque en definitiva, en realidad, es cuántos dígitos.
Me: Configurable, dijo, por, ¿no? Sin
Marcos Perez: Sí, dijo confirm pero como dijo, creo que tres, tres números después de la coma, y después como que ya está. Lo otro.
Me: Sí.
Marcos Perez: Que que, bueno, en parte por eso había hecho la la función esta de dar por pagada, que a mí me parece que no la supe explicar bien, porque básicamente lo que hace la función de dar por pagada es que no tengas que enviarme el monto, sino que lo consideres como pagado, pero bueno.
Me: Claro. Y la la respuesta fue, no quiero ni tener que hacer
Marcos Perez: Claro, claro, el clic, nada, Claro, está bien, el clic
Me: ese clic porque tengo que tener a alguien operativo, ¿viste?, ahí.
Marcos Perez: Sí, eso sí.
Me: Pero pero sí, bien. Último, eso. Último, último recontraúltimo. Eso, en prioridades. Bien, Entonces, lo del desembolso ya tenemos todo, lo
Marcos Perez: En proceso, pero sí, sí, tenemos lo necesario.
Me: Perfecto. Listo, eso me quería quedar tranquilo.
Marcos Perez: Está en proceso porque también tengo, ¿viste?, lo puedo arrancar a las nueve, que es cuando se deploya todo y hasta las seis, nomás seis tengo para hacerlo. hasta las seis, no a seis tengo
Me: Bien. Bueno, pasando a la reunión que tuvimos el viernes, el viernes, nos juntamos con los de la Mantoana, Y Los De Amphize, estos son nuevos para nosotros.
Pablo Folgar: Okay.
Me: Resumen, resumen, la Mantovana La Mantovana no es quien provee el servicio de préstamos
Marcos Perez: Es una locura.
Me: sino que quien lo provee es
Pablo Folgar: Me terceriza,
Me: una, lo tercerizan, básicamente.
Marcos Perez: Es un organismo del estado.
Me: Sociedade del este es un organismo del estado, de del ejército,
Marcos Perez: Son
Me: que, bueno, que es una ayuda económica y no sé qué. Entonces, como le como lo terceriza, bueno, cuando nos nos mandaron el formato del del documento que tiene que firmar en el en paso del pedido del préstamo, nos empezamos a ver el formatista, era cualquier cosa. Y te pedían datos de si vos eras propietario de un inmueble, si eras propietario de un auto, si vos te tenías que anotar en esta tabla quiénes son tus quiénes son tus familiares, cuáles tu cb u de la empresa, cuál es... Un montón de datos que nosotros no estábamos no estábamos capturando, o no tenemos disponibles y los y y hay que capturarlos de alguna manera, o Perc los tiene que capturar de alguna manera. Cuestión, entonces, ¿le le mostramos el listado o fuimos punto por listado de lo que ellos están pidiendo el documento, fuimos punto por punto viendo cuál es el dato obligatorio. Entonces, obviamente, nos abrió una incógnita de quizás hay datos que tienen que ser cargados manualmente, quizás hay datos que son de selección de opción, o y quizás hay
Pablo Folgar: Con el tema de
Me: Sí.
Pablo Folgar: porque ahora sí ya ya te están metiendo con eso, quizá más privados. La el tema de la de la protección de datos, ¿qué onda?,
Me: No, no, me
Pablo Folgar: eso?
Me: No nos metimos ahí en ese tema.
Pablo Folgar: Este mapper.
Marcos Perez: Este mapa, pero, pues nosotros hacemos un
Pablo Folgar: hacemos un bien, te digo,
Marcos Perez: y que que venga toda la info, después cómo ellos manejan los datos,
Nicolás Paez: No se guarda información relacionada
Marcos Perez: ¿no? Nosotros nosotros no guardamos nada, o sea, lo único que vamos a hacer es guardar la referencia del documento que está almacenado en el de
Pablo Folgar: De ellos, ah, ok, ok. Es decir, no viaja a DNI, no viaja a importe, no viaja a cuota, no viaja a No se loguea por en en logs, nada de eso.
Marcos Perez: Eso, eso sí puede ser porque está la cuenta de la persona que viaja en un Eso sí.
Nicolás Paez: Eso se podría hacer un check al final y buscarlo,
Pablo Folgar: ¿no? No, más que nada, porque supone que si que si es un request viaja por HTTPS, eso está segurizado, Si después algo le hace también tiene su seguridad, el tema es que no quede eso en en en en el docs, ¿no?, revisar eso capaz que
Marcos Perez: capaz que van a tener que hacer ellos el documento, ¿no? Entonces, para que no viaje todo eso,
Nicolás Paez: Sí, igual,
Pablo Folgar: levantarlo, es decir, ¿qué pasó con esto? Y que y que ellos te digan, nosotros después nos encargamos de pasarle al código, una herramienta de revisión de dejarlo levantado como para que ellos vean que nosotros nos preocupamos por eso, que quede en en algún documento para que Oli pueda el día de mañana llegar otra federal defenderse, decir, no, mirá, el de hoy que veinte julio, en el veinte de julio de veinte veintiséis nosotros dijimos esto y ustedes tienen el ejemplo de cosas. Y que después se peguen ellos, pero nosotros tenemos que que cuidarnos el
Marcos Perez: Sí, es así. Cien por ciento.
Me: En contexto de esto, porque no fue una conversación de ojo, porque quizás me estás corriendo el alcance, porque absolutamente sí, Ah, y una cosa que nombraron ahí Marcos Corrigime si me equivoco. Porque los de Amphi, básicamente, pidieron que haya KYC, que análisis biométrico, que la la firma sea la... Sí.
Nicolás Paez: Chicos, ¿Tú? Un segundo, me tengo que pasar una mente de gallo que me había olvidado, que era la
Me: Dale, traguito.
Nicolás Paez: once.
Marcos Perez: Un abrazo
Me: Abrazo.
Marcos Perez: Che. Chau chau. En realidad, ellos van a auditar el proceso, de validación de identidad de
Me: De Perc.
Marcos Perez: Perk. Si, por ejemplo, claro, si Perc pide TOTP, yo entiendo que ya es yo entiendo que ya es válido, Capaz que ellos le van a pedir algo más, pidieron, por ejemplo, una foto. Esa foto va a viajar. va a viajar.
Me: Ya la ya lo hacen, ya lo hacen en el onboarding. No es que lo yo en el proceso de armado del documento tengo que traerme eso y che, pero mirá que también le pedí.
Marcos Perez: Y entiendo que ya con el con el TTP ya es válido, porque ya tenés verificación en dos pasos. Y después la imagen de la persona la pedirán ellos antes, porque no creo que la pidan al momento.
Me: No, no, no, no, la pían en el onboarding, yo me me me la
Marcos Perez: La pidan en el onboarding una verificación de vida y después con el TTP ya estás bien.
Me: Y después, si es Pepifag, si es es sujeto obligado, eso ya lo ya lo responde el el onboarding. Question, ahora a las doce, obviamente, salimos de la reunión y es como, esto nos va a la mierda el alcance, Ahora a las doce nos juntamos, Nico, Seba y yo, a revisar esto en particular. Obviamente, Seba está a las internamente, porque, de repente, descubrió que un montón de cosas que que hacer, así que. Si querés la tabla de datos, Pablo, te la te la paso.
Marcos Perez: Igual, entiendo que entiendo que ellos nos subcontrataron para que nosotros les hagamos el producto y se los entreguemos, ¿verdad? Ellos tienen equipo de sistemas.
Me: Sí, claro, está Jo, está Gonza, es la... Sí, sí, sí, sí, sí.
Marcos Perez: Por eso, yo creo que yo creo que no lo van a implementar ahora, pero capaz que nosotros lo dejamos hasta ahí, tipo la parte
Me: Bueno.
Marcos Perez: que que tenemos, y porque esto del documento tiene pinta de que va a durar meses
Me: La
Marcos Perez: meses y meses.
Me: La verdad es que sí, lo que lo que improvisó, la respuesta que improvisó... No no te lo mandé, Marcos. Hablando entre Fefe y y Seba, entre mandó la captura de WhatsApp, medio que dijo, bueno, más o menos, por así, Así así le entendí, es bueno, dejemos que en el documento acá va este campo, acá va este campo, y después nosotros más adelante
Marcos Perez: Que le dejemos
Me: reapuntamos, ¿sí? Es como, bueno, captura
Marcos Perez: Que le dejemos cableada la función para que
Me: Básicamente, sí, sí, sí.
Marcos Perez: lo haga.
Me: Puede ser una puede ser una una solución. Pero bueno,
Marcos Perez: Sí, nosotros levantamos un HTML con variable
Me: Sí.
Marcos Perez: que ni siquiera levantemos el que tienen ellos, porque eso va a cambiar el Levantamos un HTML pelado, digamos, con un texto, le pegamos un texto plano. Le pegamos variables, todo, hacemos que la firma lo tenga toda la lógica, le damos y le decimos, ok, esta es la función, este este coso, ya Después ellos adaptan el documento
Me: Sí.
Marcos Perez: y listo.
Me: En fin, el único tema que, bueno, que ahí sí vamos a necesitar tu ayuda, es el tema de lo de las pruebas, lo de los casos. Hay
Pablo Folgar: Lo de demo
Me: lo del Snowtest,
Pablo Folgar: Ok,
Me: con lo de los lambdas, con lo de la rearquitectura, los endpoint los los PR pendientes, Ahí marco cómo
Marcos Perez: No, no, no importa, vale la pena igual,
Me: cómo la ves? Bien.
Marcos Perez: No sé si, tipo, la idea sería armar en base al documento que vos tenés,
Me: Sí.
Marcos Perez: casos de testeo, que la IA pueda testear como si fuese un humano, digamos, o sea, testear un endpoint, esperar un resultado que y ver qué se generó en la base de datos, en la base de datos que tenga tipo acceso de lectura, que se fije, que se cree creó. Y que pruebes y los casos que vos pasaste en el Excel se pueden cumplir mediante el insomnia, o sea, mediante el digamos. en el Excel se pueden cumplir mediante el insomnia, o sea, mediante el cool
Me: Para eso es necesario que yo ponga el input y el output,
Marcos Perez: No,
Me: para mejorar la calidad de la IA o
Marcos Perez: No, no, No. No, yo creo que no. O sea, los esperados está sé, Pablo, que opinás?
Pablo Folgar: ¿Cómo te estoy que si vos la respuesta es, es como cuando haces un un ¿no?, que vos le decís, Sí. Voy a inserta estos cuatro campos, chequea que nada más sea estos tenis, ¿no? Sería algo así. Sí. Porque si si tenemos el input y el y el resultado es derivado del input, pasa nada. A ver No
Marcos Perez: sería algo como lo que dijiste, el tema es que tengamos que tenemos que tener en cuenta la lógicas propias del proyecto, ¿no? Por ejemplo, si creas un crédito, que no tiene documento asociado, después no te va dejar Habría que tener un un documento asociado para que te deje firmarlo. Después, no sé, tendrías que firmar el documento y, o sea, como los casos específicos, ¿no? O que no te deje pedir un préstamo en caso de que ya tengas uno,
Pablo Folgar: No, pero eso viene dado por el por el Airbnb está preparando o por los casos que está en air king Ah, Oli.
Marcos Perez: ¿Va?
Pablo Folgar: Que todo que toda esa característica viene dado por los casos de otra que está Olly.
Marcos Perez: Sí.
Me: O sea, ya ya están ahí los casos, pero
Marcos Perez: Por eso. Están, hay cosas puntuales que por ahí no están detalladas, pero no no
Pablo Folgar: hagamos un un una cosa, porque por ahí, no sé si tiene sentido llegar a a tal nivel de detalle en este punto. Ori, pasame, creo que me que me da pasado un link, ¿no?, al Excel. ¿Están ahí lo...? Ahí los los
Me: Sí, sí.
Pablo Folgar: ok, hacer es, empiezo modifico el que tenía basado en en los casos de uso insomnia para usar esto casos. Y después corro una prueba y nos juntamos y y vemos si nos falta algo, si lo podemos mejorar, porque allá pone el sabor la a a definir. Hasta el último caso de uso me parece que Sí, con ellos,
Marcos Perez: con ir acotando el panorama está bien, o sea
Pablo Folgar: Eso es. Poquito.
Marcos Perez: Importate el insomnio, que ahora está bastante más grande, y y, por ejemplo, va a ser algo así como como operador poder crear un credit template. Ok, lo creé, me, que se vaya a chequear a la base de datos si lo creó bien, después que diga, como operador, poder ver quién creó credit templates. Bueno, vas a ver la tabla logs,
Them: te fijás que te haya creado un log correctamente,
Marcos Perez: te fijás que te haya creado un log correctamente, el filtrado, el ordenamiento, todas esas bolas, digamos. Con ir cubriendo de a poquito de una tabla, está bien. Y en todo caso, Oli, por ahí sí,
Me: Bien.
Marcos Perez: más a la larga va a ver que crecer los casos y poner algo bastante bien exacto, digamos, por ahí. La larga. Si quiere
Me: A la larga, no me ha quedado mucho más tiempo.
Marcos Perez: No, pero bueno. Por ahora está bien, como dice, arranquemos y veamos después.
Me: ¿Qué qué
Pablo Folgar: Claro, paso a paso.
Me: qué te imaginas? O sea, ¿cuál es tu expectativa?
Marcos Perez: No, no, hay que ver qué qué podés sacar con eso. Pero en todo caso, después va a haber que poner los casos de horror, los casos de, como dijiste, ¿viste?, de que por ahí ahora no valía la pena ser tan finos, si si queremos testearlo bien después con la IA, por ahí
Me: Ok, bien.
Marcos Perez: sería lo ideal. Pero serían Pero serían diez millones de casos de uso, por eso primero tenga los que están, y después vemos de
Me: Bien. Bien.
Marcos Perez: Igual habría que iterarlos con ella, obviamente, ¿no?, los los hacemos sencillos, que saque varios, y listo. los hacemos sencillos, que saque varios.
Me: Sí, sí, sí, sí, sí, sí.
Marcos Perez: Pero bueno. Pero no, no, no, ahora no vale la pena. Pero bueno. Pero no, no, no. Ahora
Me: Bien. Bueno, muy bien. Bueno, ahora tengo a las doce en la reunión y termino y les cuento que
Marcos Perez: Vale.
Me: onda. Dale. Bien, y... Ah, y y rompamos la pelota con el tema del entorno. Ok, listo. Ah, tengo que mandarlos, voy a voy a mandarte todos los días los pendientes. De del al
Marcos Perez: Lo de pronto, ¿todavía no lo agregues?
Me: al canal de ellos. Pero bueno, entonces el entorno ya está al cien por cien.
Marcos Perez: Lo de pronto, todavía no lo agregues. Que todavía no agregué
Me: Listo, dale, perfecto. Vale, buenísimo.
Marcos Perez: el ¿Sale?
Me: Bueno, chicos, nos vemos.
Pablo Folgar: Hasta luego, gracias.
