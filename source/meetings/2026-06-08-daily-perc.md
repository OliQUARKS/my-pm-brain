# Source: Daily - PERC (2026-06-08)

**Kind:** meeting (daily standup)
**Date:** 2026-06-08
**Participants:** Olivier (PM), Nicolás (TL), Marco (dev), Juampi (dev), Connie, (ref: Israel, Stefano Giuliano, Seba, José)
**Captured:** transcript verbatim (audio → texto, sin editar)

> Audit anchor. Nunca se edita. La síntesis vive en `ingestion/meetings/2026-06-08-daily-perc.md`.

---

## Transcript

Me: El El Seath.
Them: Buenas.
Me: Que hace
Them: Está tranquilo.
Me: Así que salió bien esa esa juntada, entonces.
Them: Sí, sí, sí, se salió muy bien.
Me: Bien, bien, bien, sí, sí, me dijo Fefe recién.
Them: Vos, ¿cómo fuiste de cumpleaños?
Me: Recontento. Bien, bien, super Fue todo un fin de semana muy relajado. No quería, Ahora, el fin de que viene, festejo con mis amigos,
Them: Bien.
Me: porque este fin de fue recontrafamiliero,
Them: Bien.
Me: sí, mucha mucha mucha comida, mucha cocina, mucho, y...
Them: Ahí va.
Me: Así que ha sido, bueno, fue poco de eso, y, nada, muy contento. La verdad que bien aprovechado el el fin de cumpleañero. Al final del del viernes estuve, al pedo en mi casa, y es como usted, posteado, me agarraba un terrible, Ay, dios. Connie.
Them: Hola, buenas, ¿todo bien?
Me: Bien.
Them: Vengo escuchando, Mario.
Me: Ah, bien. Bueno. Ahí te quería preguntar, Marcos, más que nada, por lo por, bueno, concretamente, por la reunión, jefe no me no me pudo decir mucho, Pampi, ahí Nico,
Them: Bien. ¿Vienes?
Me: Muy bien. No, bueno, les iba a preguntar, entonces, por la reunión. Ahí como salió, qué de los pendientes, esos cinco pendientes que teníamos y más allá del entorno, pudieron definir algo, cómo cómo es la vuelta.
Them: Sí, a ver, le, lo que son los bloqueantes, el punto uno, el punto dos, básicamente, que eran los dos más.
Me: El el entorno de y el acceso H3,
Them: Sí. Nos van a dar una cuenta sandbox de Amazon,
Me: Sí.
Them: vamos a entrar y lo vamos a hacer, tipo, vamos a hacer nosotros el bucket, tenemos lo único que tenemos que hacer es un punteo de los servicios de Amazon, que vamos a necesitar. Para pasarles y que nos den acceso a esos servicios. Así que, Nico, habría que pasarles eso, No sé. Sí. Consulta, porque yo a esa no me podía sumar Nosotros vamos a creer todo, no su gente de Así es, la gente de DevOps nos va a crear la cuenta Sandbox, nosotros vamos a crear todo para testear y armar lo que queramos, y después ellos van a armar lo que es development con un CICD para para los autodeploys y todo eso, pero primero, lo primero, nos van a dar una cuenta Sandbox. Ok. Entonces, tenemos que pasarles qué servicios de Amazon vamos a necesitar, ejemplo, bueno, en este caso va a ser el s tres de lo de Cosso, y después, no sé, esto para para hacer los claims los los eventos, no sé qué otro servicio sería. Pero bueno, por los Claro, porque eso va a quedar expuesto mediante gateway y una lambda. Eso. El tema ahí, eso, configurarlo a mano, Ok. Porque después, si ellos replican, o sea, replican exacto o nos piden que configuremos nosotros los entornos. A IOLI capaz que conviene hacer un proyecto de de directamente de nuestro lado y después pasarselo, el tema es que no estaba en el scope eso. A ver,
Me: Okay.
Them: habría, Isra, por ahí lo tiene más claro eso, lo lo que vimos en la reunión, después si no, preguntale. Tengo entendido que lo que iba a hacer igual el primer digamos, el proyecto en sí, iban a levantar el Yamel con Terraform, y ahí nos lo iban a pasar, pero no estoy tan seguro. Ok. ¿Ellos iban a hacer ese proyecto, entonces, o...? No estoy tan seguro, pero creo que sí. Habría que preguntarle a esa. Ver qué entendió.
Me: No grabada en la reunión, de casualidad, ¿no? No.
Them: Porque No, Porque en un momento habían dicho de que le iban a hacer seis CD, después nos dijeron la cuenta de Sandbox, y y no entendí bien en qué qué situación quedó eso. Dale, yo lo averiguo. Básicamente, sería eso. Con eso vamos a poder probar, también el tema de las planillas de los de los documentos, con contra el s tres. Además, decir que crearon un canal de dev en per quarks, donde van a estar haciendo preguntas técnicas ellos, o nosotros, así que, si no, te puede preguntar por ahí por el canal de de del Eso sería en cuanto a la reunión.
Me: Bien, Ok. Ahí, entonces, lo hablan con Israel, cómo
Them: Habría que abonarlo y pasarle el el punteo a ellos para que no se habiliten la cuenta. Y en todo caso, decirles, si no, bueno, de que no hagan la el sandbox y de que nos den el el entorno ya de vibra.
Me: Ahí fijate de dejar la la pregunta en el chat, así lo lo te todos ahí. En el el canal. Sí, sí, puede ser, sí, sí, sí, así.
Them: Ciao.
Me: Bien. Entonces, el uno y el dos estamos de firma, documentos finales y restricciones, de los HTML. El cinco habían respondido algo, Nico, vos no estabas muy contento con la respuesta. De eso no se habló nada, ¿no?
Them: Eso les pregunté, sí, eso les pregunté,
Me: Sí.
Them: si en qué formato iban a
Me: Sí,
Them: estar los documentos y todo eso, para saber nosotros qué hacíamos, dijo que como la app es Flutter, lo más probable es que tengan que ser devueltos al cliente en formato PDF, entonces, que que igual iban a arrancar en HTML.
Me: Pero en el en el back office, ¿qué van a subir?
Them: Va a ser un ACT Mele después va a haber que devolverlo como PDF. O sea, la librería no va ser de convertir de PDF a HTML, sino de HTML a PDF.
Me: Okay. Okay.
Them: Eso sería todo, así sí.
Me: Bueno, o sea, lo... Bien, o sea, en la tarea que tendrá que hacer o sea, lo lo compliance por si cambia el documento, es ellos aparte, operativamente, van a tener su su punto doc, doc x, lo pasan a HTML, por su
Them: No, punto h, no, no, ahí va. Sí.
Me: pasan a HTML, y recién ahí lo suben al al back office, entonces.
Them: Sí, en teoría sí.
Me: Ok. Bien.
Them: Según lo que se habló ahí, porque dijeron que iba a tener que ser HTML para que
Me: Is
Them: todo el tema de dinámica y toda la bola, pero que después lo devolvamos nosotros en PDF.
Me: ¿Eso lo dijo Seba o lo dijo alguno de los
Them: Sì,
Me: de de los devs? ¿José? Bien, listo, me genera más confianza
Them: Miró que, o sea, es nuestro ideal ese, Oli, lo único que me genera duda es después quién va a ser el operador de ese back office, ¿no? Esa gente sabe pasar de PDF, HTML, o te sube un XML, porque pensó que era parecido. Entonces,
Me: Sí, habrá que ponerle un cartelazo así, pero, bueno Qué sé.
Them: Ah, entiendo que lo convertirán ellos igual o no
Me: Yo.
Them: sé, no sé, como con input.
Me: Ver, si se pidió la reunión, mucho más. A ver, yo, de última, en las reviews, y quieren, les digo, en la en en la review es ojo, esto es pura y exclusivamente HTML, lo tanto, operativamente, lo van a tener que integrar. Y listo. ¿Lo quiere en la mejora? Bueno, podemos poner una semanita más.
Them: Bien.
Me: Ok, gracias, ahí, por la definición. Bien. De documentos finales,
Them: Dijeron Julie, Julie,
Me: bien, gracias. Yo creo Sí.
Them: ¿puede ser Julie, Julie, Julio?
Me: Stefano, Giuliano.
Them: Julie. S, dijo que pasó algo a compliance.
Me: Ok, perfecto.
Them: Y que está esperando resolución.
Me: Ok, perfecto. Yo, si no me recuerdo, ahora tengo que buscar, creo que tengo unos documentos hace mucho tiempo, que eran como estructura básica, Voy a buscarlos, porque por ahí podemos robar esos. Obviamente, nosotros no, necesitamos el último no necesitamos el último documento, necesitamos solo la estructura. Voy a ver si lo si lo consigue y se los paso. Hoy hoy se los paso. Bien, más allá de de la reunión, que tenemos algún pendiente, qué cosas no quedan, qué qué cosas van a estar trabajando esta semana.
Them: Bien. Yo, por mi cuenta, estoy laburando al tema de los de las cuotas. Ahora estoy por meter dentro de un rato un pull request con el fix, como me comentaba Nico, de de sacar el recordarme cuál era. Sí, es de sacar, digamos, básicamente, todo esto del digamos, la Ah, sí, que no quede Hercod, que Así es, en todos lados. Sí. Habían varios archivos que también metían como el el french, así que lo estoy cambiando todo para que sea todo más dinámico. Según lo que venga en el crédito. Así que eso. Y después tendría que hacer toda la para que se creen las cuotas, porque actualmente es tipo solamente la la base de datos. Y ya cuando tenga todo eso, les mando un request a ellos. Ya está asfixiado el tema de los cálculos, ya está subido, así que si lo querés testear Oli también estaría bueno.
Me: Voilà.
Them: Todo asfixiado eso. También mergeado hasta el front, entonces es todo development. Y cuando tenga eso, igual voy a tardar un tipito, no sé con qué voy a encarar.
Me: Bien. Ahí, Joapi,
Them: Buenas. Yo ahora tengo que corregir una parte de las secciones de los documentos con estas definiciones del viernes.
Me: Yes.
Them: Y no. Y armor, con eso.
Me: Bien, ¿tenés ahí tareas asignadas? No, no.
Them: No. No. Don't care. Sorry. I don't care.
Me: Bien. Bueno, avísame y lo y lo chequeamos, pues.
Them: Sí, sí.
Me: Bien. Juan y Nico, ¿alguna duda, algo que que vean? Que esté pendiente.
Them: ¿Deminado? No, parece que don Robin así que Sí, por ahora no, Oli, no sé lo último que habíamos visto con Seba, que él se había llevado cosas para ver.
Me: So
Them: Si eso quedó
Me: Sí.
Them: queda algo más o
Me: Le
Them: No sé si ya tuvo respuesta.
Me: El gran pendiente, bueno, la los documentos, al fin y al cabo, me parece. No, no, no, no había mucho más que eso. Ahora te voy a revisar, porque ya le mandé varias cosas, pero no no eran estas estas cinco estas cinco dudas. Sí o sí, ahora ya esta, entre ahora me fijo los horarios que tengas disponible, pero estos días nos tenemos que
Them: Dale.
Me: adjuntar para el próximo, que es el último. Que tiene ahí definiciones pendientes que si no, no las tenemos, nos van a bloquear otra vez. Bien, Así que, bueno, bien. Bueno, chicos,
Them: Bueno,
Me: muchas gracias.
Them: vamos a darle, entonces, y tú
Me: Todos modos,
Them: Malandú. Abraste, grande. Chao, chao.
