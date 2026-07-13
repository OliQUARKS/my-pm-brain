# Source: Estructura de base de datos, firma digital y entorno de desarrollo — pendientes con equipo (2026-06-03)

**Kind:** meeting (interna Quarks — refinamiento técnico)
**Date:** 2026-06-03
**Participants:** Olivier (PM), Nicolás (TL), dev Quarks (probable: Marco)
**Captured:** transcript verbatim (audio → texto, sin editar)

> Audit anchor. Nunca se edita. La síntesis vive en `ingestion/meetings/2026-06-03-estructura-db-firma-entorno.md`.

---

## Transcript

Them: Después, ¿cuál es, digamos, y cuál no es agregar la variable?
Me: Okay. Bye.
Them: El el tema es qué esperan ellos, si saben que lo tienen que subir, en HTML o o no, y quieren subirlo en PDF, ver cómo se parcea eso, En tal caso, habría que ir probando, chicos, alguna algún paquete tipo PDF2 o HTML, y ver si lo convierte, respeta diseño y demás, Ok. Entiendo que todo esto va a estar subido a un s tres, ¿verdad? Los documentos que se arman, sí. Sea ellos nos dieron como en el insomnia un ejemplo, pero nos tienen que pasar el bucket y toda la bola para poder conectarlo. ¿O no? Claro. Sí, o sea, tanto en lo que sube el back office como lo que genera después backend con los valores de cada usuario, van a parar ese tres. Bien. Por eso, eso ellos nos tienen que pasar eso. Digamos. Para Sí, la el OACE, la región, Y salvo que ya la tengan predefinida en esa lambda que usan, Que yo haya visto, no. Ok. Me me vuelvo a fijar igual y lo pedimos. Sí, porque hacer un mock y demás es sumar tiempo y
Me: Sí.
Them: como que el tiempo corre en este proyecto, entonces, nos comparta unas credenciales que después las dan de baja y listo. Bien. Después tenemos lo del evento también, que decíamos, de para cambiar al usuario. Ahí dependemos de que nos hagan un ambiente de dev,
Me: Sí.
Them: Bien. También quedamos a la espera de eso. Y después, la otra cosa que yo que por ahí lo teníamos que ver con vos, era el tema este de las cuotas que habíamos hablado el otro día. ¿Te acordás, Nico? Cuotas versus payments. Claro, de cómo planteamos la estructura de la base de datos. Si quieren que la ancare y mande un pull request y me dicen qué les parece, espero alguna definición, y después lo encaramos, como quieren hacer. Ya le iré encarando, si querés, capaz que no tanto a nivel de implementación, sino un mini y ahí podemos contemplar a ver si se escapa algo. Y después se implementa, para no no implementar y después Lo único, volviendo al punto anterior, decías el evento para mandar los los los usuarios en, o sea, que dependía de un de un deploy, no es lo que ayer de que creen un nuevo usuario por eso que querían otro caso. No, no, el tema de el tema del del deploy es, nosotros, con local stack, podríamos simular un evento de Amazon, ¿verdad? El tema es que para que nosotros nos envíe lo que es el evento con el user ID, el tag y todo eso, el, primero, el local stack habría que pagarlo, segundo, que estaríamos simulando, pero no sabemos en sí cómo está estructurado su su evento, digamos, de Amazon. Necesitamos que de plugin para hacer un tiro y ver cómo viene el evento si viene cargado con el user ID, con qué viene cargado, digamos. Bien, es el el evento del handler. Ok, ahora sí. Para cambiar lo del JWT ya por algo más más usable, digamos, ¿no? Ok. ¿Es OLE no sé si ellos lo tienen en cuenta, la la celeridad que el deploy, porque ayer fue un sí, sí, vemos pero pero
Me: A ver, en base a lo que levanta, lo que estamos levantando, yo creo que, o sea, por un lado, voy a apoyar eso, por otro lado, creo que ahí una conversación, más que nada, pendiente. No sé si puedo mandarle su mail, lo defina y me lo devuelve.
Them: No, no, no,
Me: En el México.
Them: no decía o sea, el el environment de dev, para ellos es transparente, por la idea es que respete lo mismo, por eso
Me: Sí.
Them: fuimos intercambiando ya a priori.
Me: Sí.
Them: El lo que digo, la seriedad que necesita es que ese entorno de dev quede configurado,
Me: Para el
Them: Si lo dejan para el próximo sprint,
Me: Sí.
Them: nos complica un poco, ¿sí?, porque recién el próximo sprint podríamos podríamos empezar a ver eso, ver que no haya ningún tema en el deploy, etcétera. Entonces, cuanto antes se configure el entorno,
Me: Sí.
Them: ya te quedas tranquilo con el
Me: Además, entiendo que no podemos ni guardar ni los documentos firmados, si no tenemos el entorno, ¿no? Bien.
Them: ¿Y qué adónde local? Todo en local, y tenemos este problema del local stack, que, sinceramente, a mí me gustaría ya cambiarlo, ¿no? Porque es algo que creo que es bastante bloqueante.
Me: Bien. Y después, entiendo que quedaba cómo encargamos, técnicamente, el tema de la firma, cómo, qué se guarda, cómo, dónde,
Them: Claro, Sí. Sí, tema firma, no sé, Nico, cómo cómo sería eso, si No, es que firma, bueno, ahí yo tengo una mezcla de versiones en la cabeza, pero lo último que dijo Seba era como hace Panda o Simiel, que vos le das confirmar, y eso te te mete el inicial de cada nombre y apellido, como que lo firmaste, o sea, ahí está el consentimiento, no hay una firma literal a mano alzada, por así decirlo. ¿Y eso cómo lo implementaríamos? ¿Alguna librería, alguna cosa de Python que pegue las iniciales? Es que, por eso, hay que ver qué les demanda compliance de su lado, porque, si no, nosotros en el en el template del HTML, donde diga firma, le pones una variable arriba, y le mandas la inicial de de nombre, apellido, en...? Desde BAC, y ya se arma con eso. El tema es que no sé si necesitan algo más legal, O sea, que ahí dependemos de una definición de ellos. Ya, es only por lo que dijo, va alcanzaba con las iniciales, pero bueno, hay que ver si entiende que es nosotros metemos las iniciales, no es que el usuario O sea, porque en la UI el usuario nunca tiene una opción de firmar, ver el documento, y en cada import donde tiene que firmar, toca. Si no, es un continuar y se le firma automáticamente. Yo creo que por un tema legal, igual van en necesitar algo un poco más estricto, me Sí, la verdad que ahí no sé. Porque, básicamente, ellos después ven el el documento firmado, entonces, si te querés quejar, te quejás en en el momento o no seguís continuando. Aludas, te interrumpí.
Me: Bien. No, no, es que le, ahí le mandé a Seba, que o sea, yo ahora voy a voy a poner en el en el grupo lo del lo del entorno. Eso para para bastante, que es el canal con con ellos. Yo los los agrego a ustedes al canal ese, porque ya me me a esta altura ya me parece lo lo mejor. Igual. ¿Qué les iba a decir? Me parece que tengo que agendar un un espacio en donde tenemos que hacer todas estas estas consultas. Si yo les mando un mail, me lo van a contestar nunca más. Los tengo que los tengo que forzar a tomar decisiones ahí on the fly, porque me demoran siempre.
Them: Ok,
Me: Ese ese era mi mi comentario,
Them: Sí, quieres mandale como una un resumen de qué es lo que se va a ver, así ya lo van planeando, porque si no, vamos mirar la meeting y van a decir, me lo tengo que llevar para ver con compliance y va a ser una meet para que todos se lo lleven. Entonces, que ya sepan y capaz que pueden ir adelantando temas.
Me: Listo, perfecto. Perfecto. Listo. Marco, ¿tenías alguna duda más? Para apuntar a Nico?
Them: Ya con eso, por lo menos, encargo del tema de las cuotas. O sea, por lo menos la estructura para que Nicolas valide,
Me: Bien.
Them: después, bueno, así lo demás quedamos a espera de definiciones, pero no se puede. Eso es solo
Me: Bueno, ahí, si quieren, yo les mando el mensaje, no me quiero mandar cagada. Si ustedes lo lo ven claro, yo lo mando ahí al al al grupo.
Them: Sí, y sí, haría los los chicos, fue, si alguno de nosotros se olvida de reenviar el mensaje, no se enteran, entonces,
Me: Sí, por eso, listo, ahí yo ya los
Them: Ah, y, Nico, otra pregunta. Viste que yo mandé el pool request de la collection de Insomnia? Eso Sí. ¿Se lo mando a ellos o espero juntar algo más? Tipo, ¿qué tan atómico crees que le hagamos los los pull requests a ellos? Es que si ese ya tiene una collection con lo que está hoy, para usar mediante Sí. Ey, ya pasáselo, no no hace falta. No sé si el anterior ya lo revisaron. El anterior ya está aprobado, ya está merceado. El primero, el segundo también, El primero, el segundo, y y el de, digamos, lo mostramos todo lo que hicimos ayer, digamos, en la Buenísimo. Sí, ya mandales otro para empezar a pasarle PR más chicos. Van a ver que es una collection de insomnia, la van a pasar dentro de todo rápido, imagino. Listo, dale. Salvo que pidan más documentación, tipo un m d asociado por por API, pero Ya, ok. Ahí tengo las rules para documentar todo y nada, un poco más eso.
Me: Listo. Bueno, ahí les paso el texto. Y me avisan. Estoy anotando unas cosas.
Them: Calentir,jillo.
Me: Dale, bueno. Y, ah, y después, no sé, Nico, que no sé si, y crees que reagende las leyes así así estás? ¿Cómo cómo lo ves?
Them: Sí, Dame un segundo, que mañana, por ejemplo, puedo estar hoy había AL dos, los viernes no hay, Y la semana que viene podría miércoles jueves nada más. El tema es que no hay un horario
Me: Perfecto. Sí, no, yo la yo muevo, o sea, cuando
Them: específico en el que
Me: veo bien tu calendario, muevo las las las a los espacios que los tengan libre.
Them: Mira, el ¿cuánto dura la daily? ¿Diez o quince? Quince. De de diez cuarenta y cinco a once, estás siempre libre. Si lo puedes meter ahí, salvo casos aislados, ¿no?, como hoy, que no hubiese podido, pero diez cuarenta y cinco, once, la semana que viene, por ejemplo, está toda libre.
Me: Listo. Lo pongo en esa hora, entonces. Bueno, ahí les paso, entonces,
Them: Buenísimo. Dirigí, yo ahí entré al channel. Un lujo. Bueno, listo, entonces, se encargo con
Me: Listo, bueno. Dale, abra su.
Them: Estamos hablando. Un abrazo. Dale, abrazo. Chau, chau.
Me: Chau, chau.
