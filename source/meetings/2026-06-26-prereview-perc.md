# PreReview PERC — 2026-06-26

**Participants:** Olivier (PM), Marcos (dev, Quarks), Juan Ignacio Moyano / Juampi (dev, Quarks)  
**Purpose:** Pre-review check — estado del front + back historia por historia, sprint actual (ciclo 6)

---

## Verbatim transcript

Me: Allô. ¿Quién, ¿Todo bien?  
Them: Buenas. Andamos.  
Me: Hoy es un día de reviews en la l dos.  
Them: Sí.  
Me: Ya eso hace rato ya no tenemos más.  
Them: Me contaba, ¿no?, que ahora la hacen a las once.  
Me: A las once.  
Them: En  
Me: Sí. Ah, puede ser, pero porque GAI está desconectado. Del resto. Aló, aló.  
Them: Buenas buenas. ¿Todo bien?  
Me: Bien, estoy justo comiendo  
Them: Bien.  
Me: Dice unos mostacioles, Muy bien.  
Them: Same. Yo tomando el cafecito.  
Me: Bueno. Sí. Muy bien, claro, ahora le estás dando duro y parejo, me imagino. ¿No? Qué bien, qué bien.  
Them: Sí, sí  
Me: ¿Qué les iba a decir? Bueno, les cuento, o sea, más o menos la idea es quiero ver en dónde estamos. O sea, más o menos eso, Más que nada lo que es la el front y back. Es todo juntito. Idealmente, me gustaría ver historia por historia, hacer un chequeo para para para ver el front, y si qué es lo que está qué es lo que no está qué es lo que falta, qué es lo que hay que corregir. Etcétera.  
Them: Bien.  
Me: Vamos a hacer como quieran, podemos ir historia por historia,  
Them: ¿Sale?  
Me: validando que eso esté, y y listo, es como después más allá de eso.  
Them: Dale, vamos a  
Me: Bien. No sé, ahí, Juampi, ¿querés querés compartir? Y vamos y vamos chequeando. Así por el  
Them: Sí, dame tu seconds.  
Me: Así por, sí, sí, así por encima,  
Them: Allí, por encima, estamos  
Me: ¿qué cosas? Qué cosas faltan?  
Them: como como a Yealry, te te te cuento, digamos, o sea, no es más que eso.  
Me: Bien.  
Them: Me manda, te manda mensaje hoy, Marcos, no sé si lo viste. No. Sí, que me tira, desde ayer me tira quinientos el endpoint de de payroll, el novities, y la parte de documentos no está en level aumento. ¿Y lo buscaste? ¿Sí estaba? Sí, el del en development no está, porque yo le pregunté cuál era lo último y no no está, y pero yo estaba usando una de las ramas de documents, Primero estaba usando la la rama de documents, que que subiste, porque dice sí está, y después, cuando te pregunté lo último que estaba en development, y empecé a usar ese y me di cuenta que no estaba document. Así que nada, Igual, en ninguna de las dos me funcionaba el el export, por las dudas. El de nuevo, Ortiz, metida quinientos todo el tiempo. En insomnia, como en cuando conecto con el con el front.  
Me: Bien.  
Them: No sé si será por algún error de de entornos. En el tema variables, las cambié todo el tiempo, en el sentido de si todas las migraciones no todos los build, Ok. Así que ese tema tengo con la parte del Tú, cuando Nobel te dice, está en development. Sí, sí, sí, ese sí está, lo que no está es la parte de documents. Ah, la parte de documento, no, hay PRs abiertos. Justamente. Ah, ok. Hay PRS abiertos con todo eso. Bien, bien, bien, perfecto.  
Me: Bien.  
Them: Bueno, igual, yo de todas maneras los trabajé en con el drama que vos subiste. Pero igual hay que ver un par de cosas en eso.  
Me: Bien,  
Them: Ok.  
Me: a ver, ahí seguí compartiendo, yo voy a ir pasando Serían, en realidad, lo del ciclo, a ver. ¿Cuál es? El seis. Bueno. O voy a verlo por Bueno, template de préstamos estamos, diseño estamos, project management estamos, autenticación estamos, solicitud de consulta de préstamos estamos, Ajuste de gestión de préstamos. Estamos. Bueno, vamos, firma de documento, descuento de cuotas y cancelaciones, son los tres básicamente, los tres hitos que tenemos. Entonces, vayamos a a documento, hay cosas que están en PR. ¿Qué es lo que falta aprobar?  
Them: Y faltan cuatro PR de document templates, que es básicamente cuando se van a crear  
Me: Sí.  
Them: los archivos, se van a crear, digamos, se van a subir y toda la bola, pero bueno, por lo pronto estaría el tema de que se creen se suban y se vinculen a un tipo. Esos cuatro están todavía abiertos, que son los que le devolví ayer a la tarde a la tarde a Jo, que me los devolvió, fue bastante una una forrada esa que tiró, pero bueno, estuve corrigiendo lo las cosas que puso y realmente no hay cosas que no tienen sentido que puso ahí.  
Me: Lo rollo con inteligencia artificial y en Synchrony, sí.  
Them: Con inteligencia artificial y y le debe haber puesto literalmente, de alguna forma, que los rebote por algo. Porque todos todos tienen bloqueantes, tipo, todos tienen bloqueantes, y tipo, un bloqueante major, tipo de como debido a esto no se puede mergear, es como no sé, era una boludez de documentación de que decía, no sé, credit, y y tenía que decir, payment, una cosa así. Pero bueno,  
Me: Sí, ahí entramos en un problema, porque si hay mala leche,  
Them: Sí.  
Me: me tengo que ir a putear.  
Them: Sí.  
Me: No tengo ningún problema, le van a hacerlo igual, pero  
Them: No, no, no pasa nada, dejala pasar ahora, Yo me di cuenta de eso, que la corrección de los PR fue cualquier cosa, es más, corrigió cosas que ya habíamos hablado, corrigió cosas que, por ejemplo, en el mismo PR tenía un texto explicando que eso entraba en el próximo PR, y me lo corrigió, o sea, pero bueno, ya está, ahora estoy terminando de los últimos dos, porque es bastante largo lo que me puse en uno de esos.  
Me: Bien.  
Them: Y lo mando. Y ya está. Dos segundos, paramos la pelota que necesito dos segunditos con Marcos acá, porque tuve un problema también, que me acabo de cobrar. Cuando  
Me: Sí,  
Them: hago el get, Marcos, el get de los documents, Sí. Acá me tira en el front me tira primero, me tira doscientos, pero me lo me lo trae vacío, y cuando veo los logs los logs del back, me tira un cuatrocientos uno primero, después el doscientos. Eso me me pasa en este contexto, pero cuando lo hago en el insomnia, me tira el doscientos de una y me trae el único que cree, digamos. El cuatrocientos uno es porque tenés no le estás mandando el token. Como una Claro, sí, sí. Sí, pero ¿cómo soluciono eso? Tenés que mandarle el token en el tiro, en el front, tenés que Estoy en el en el header, digamos. Del la... Bien, perfecto, listo, eso bien, bien. Perfecto, bien, eso listo. También mi consulta, pero es más para los dos, en el sentido de que en qué qué archivo se sube acá. Porque yo tenía entendido que se subió un archivo. Como como un post.  
Me: A ver, a ver, a ver, espera, bancame porque estaba justo viendo mi pantalla.  
Them: En la parte de subir los los templates de documentos. Esto es así. Sí, bien. Ahora voy a compartir yo, vamos a estar para un poco. Sí, tranquilo. Vos tenés lo que me preguntaste el otro el otro día, que era el el create y el delete, sí. No, tenés el type del archivo, que va a ser el que va a encapsular las versiones. Después tenés el archivo en sí con el versionado. O sea, los archivos con el versionado. Entonces, vos, para hacer referencia y no perderlo nunca, vos vas a tener acá file, y en realidad después tenés los documentos. ¿No? Acá. Ok. No, mentira, sería files. Entonces, vos tenés los files, por ejemplo, y tenés los types. Entonces, por ejemplo, un type va a ser no sé, ¿cómo se llama el archivo?, por ejemplo, acuerdos y condiciones, ¿no? En este caso, va a haber uno solo, pero podrían haber más también, por eso lo pensé para que podían pudieran haber varios. Ah, ya Pero va a haber uno que va ser acuerdos y condiciones, y va a venir el operador del back office, y va a crear un acuerdo y condición. Después va a venir y va a decir, ok, quiero actualizar este y en realidad no va a actualizar este archivo, va a crear otro nuevo, bien así, y le va a hacer referencia a acuerdos y condiciones. Sí. Y de él, total Y es de este, va a estar desactivo y este va a estar activo. Va a ser la versión uno y este va a ser la versión dos. Sí. Después puede activar de vuelta la uno o puede activar la dos. Por eso tenés la tabla types. Entonces, vos ahí, en ese caso, tenés que poner en algún lado de que pueda crear un tipo de archivo, que va a ser ¿con qué...? Ok. O no lo crees, no sé, Oli, cómo le vamos a dar eso, y que sea, listo, un un único archivo ya  
Me: O sea, a ver, el  
Them: precreado y listo. ¿No? ¿Entendiste lo que  
Me: Es lo mismo.  
Them: ¿Entendiste lo que acabo de compartir?  
Me: Sí, sí, sí, sí, sí, sí, sí, sí, entendidísimo. O sea, vos podés subir un nuevo archivo, pero obviamente tenés que poder tener solo un un archivo activo. Entonces, vos vas a poder vos vas a poder decidir  
Them: Al qual?  
Me: entre dos tipos de archivo o, y el o sus versiones, pero concretamente,  
Them: Claro, y es  
Me: uno seleccionado. Es  
Them: el día de mañana, el día de mañana, si te dicen, che, al final no va a ser sábana, ahora en vez de agregar acuerdos y condiciones, vamos a agregar también este de servicios. Es tan fácil como crear un nuevo tipo y listo, ya está, ¿entendés? O sea, es bastante más escalable que simplemente crear un versionado directamente.  
Me: Et Me a mí me encanta. La pregunta es, hoy, cuando vos visualizás de cara al usuario, por más que o sea, por más que el criterio es hay un solo documento. Vos estás visualizando o lo construiste para que sea un documento sábana, que te ponga uno por encima del otro, o...?  
Them: No, no, no, vos después pedí, hacés un get que te devuelve el archivo.  
Me: Claro, entonces, si el día de mañana vos tenés que escalar a  
Them: No, no. Es hacer el mismo get  
Me: más de un archivo, ellos  
Them: es hacer el mismo get, pero enviando cuál es el archivo que querés. ¿Entendés?  
Me: O y y visualizás dos archivos, no uno uno  
Them: Claro,  
Me: no uno sábana, o sea, tiene que cambiar el front  
Them: Claro. Y nada, si querés, si querés, Abana, después se hace un endpoint que los  
Me: Claro, claro, claro.  
Them: los nuclee los dos, no pasa nada. Es bastante Pero, básicamente, es así, vos hacés el get y le decís, traeme el archivo de acuerdos y condiciones.  
Me: Sí, sí, sí, sí, sí, sí.  
Them: Y agarra y te lo trae. Bien, acá, bueno, acá, bueno, agrego el botón para el create,  
Me: Clarísimo.  
Them: del del del type, bueno, que me tocaba la tabla. Y la parte para subir el documento, acá obviamente esto no va. No, no, no le agregues el botón para create el type. No, no se lo agregues porque después puede ser que pidan algo con eso. No? Ok. ¿No? ¿Olí?  
Me: Sí.  
Them: Se escapa del entregar.  
Me: El este plus, sí, se  
Them: Claro, Claro, el club lo lo dejamos como como que lo hicimos así, era estaba bueno hacerlo escalable, pero no le agregues el botoncito, porque si no después te van a decir, Ah, bueno, haceme dos documentos. Y no. Bien. Entonces, dejo la tabla  
Me: Claro,  
Them: y qué más? El botón de del alta y de la baja, Sí, vas a poner ahí, ingresa el ID asociado,  
Me: Si  
Them: lo menos poneme una tabla para ver el ID, porque si no ¿de dónde tengo que...? ¿De dónde saco el ID? Ahí Ahí está el documento. O sea, meteme una una tabla de documentos, también. Donde yo pueda ver los documentos y el ID. Pueda copiar el ID y después subirlo ahí. Acá acá esta esta es la esta es la tabla, acá es la tabla. Ah, bien. Ah, ahí está, claro, vos creas un tipo de documento, ahí está, copiás el ID, lo ponés ahí abajo, subís documento. Bueno, y ahí falta una tabla de visualización de las versiones del documento, versión uno, versión dos, versión tres, cuatro y eso. Ok. Bien.  
Me: Eso eso lo habíamos puesto ahí en el prototipo ese que ese kármamo.  
Them: Entonces,  
Me: Así que, en ese sentido, superbién.  
Them: Bien, perfecto. Entonces, vamos de nuevo para Bueno, acá va tabla de documentos, con su ID, sus sus datos, otra tabla con el versionado, o lo puedo hacer todo en una, ¿o no?  
Me: Todo en una lo podés hacer. Sí, sí, no nos  
Them: Que tenga  
Me: Hacé la de última, es troleable, ordenable, y, o sea,  
Them: Bien.  
Me: ordenable por versión, ponele, no sé.  
Them: Este botón no Bien, bueno, vamos a poner la tabla. Con sus datos, blablablá, sacamos, no ponemos ningún botón de crear nada, Acá subimos el documento. Y está el endpoint para subir el documento, ¿verdad o no? Está el endpoint, pasa que está debe estar en PR, creo que sí, create and delete endpoints. Ah, sí. ¿En en create puedo subir un documento? Un file, por por Badia, ¿no? ¿Cómo? ¿Puedo subir un documento por en el create? No, no, porque todavía no tenemos el s tres, pero Ah, bien, perfecto. Perfecto. Vos te hacés el que envías el documento y listo. Listo, listo, bien, perfecto. Yo también eso no lo vemos después del documento de así que hacemos el mocapese. Listo, por eso no no me no no se ha grabado porque no no podía con este endpoint no podía subir ningún documento, dije, ¿qué está pasando acá?, así que nada, bueno. Listo, ya entiendo.  
Me: Bien.  
Them: Se lo hago, este caso. Bien.  
Me: Bien. Por las dudas, creo que está en una de las historias. Bien, vayamos vayamos una por una.  
Them: Sí, eso.  
Me: Estoy compartiendo, ¿no? Sí. Gestionar del template como operador de ver listado de los documentos, dar de alto un documento, dar de bajo un documento, reemplazar el documento, si te distinta versión de un documento, poder seleccionar el correcto y el activo, cada acción en auditoría, y los documentos son Esto es un poco lo que nosotros ya estuvimos hablando recién. ¿No? Bien.  
Them: Sí, sí, como, sí, que falta básicamente pasar los PRs y que Juanpi lo lo termine de conectar. No, traque yo ahora me me suma  
Me: Bien.  
Them: me subo a la rama esa y lo completo, así ya lo tengo más o menos probado y después me uno de nuevo a development, cuando suba, como para noquear eso y ahí  
Me: Bien. No, no se cuelguen después con esta subtarea, ya sé que ya lo hablamos todo y estoy es  
Them: Sí, sí. Sí, sí.  
Me: todo obvio, pero por las dudas. Bien, descargar el documento firmado del préstamo.  
Them: Bueno, ese endpoint, si no me equivoco, ya pasó. Ya está.  
Me: Bien. Este endpoint para  
Them: Pasa que, bueno, descargar es relativo, porque no tenemos el s tres en realidad. O sea, tené en cuenta que todo lo que diga descargar no, Ah, por eso el el export Nobel que también me da ese error, ¿por el s tres? O sea, o estoy hablando por ahora. El export el export hay un PR abierto, El payroll el payroll notice. Está en development, eso, por las dudas. Sí. ¿Y qué error te da? Ay, tengo una segunda segunda Me da un error quinientos, pero no descifro cuúal es, mientras paso por privado.  
Me: Por las dudas, recordemos, el cliente tiene que poder, después de haberlo firmado, cuando entra en la sección de su préstamo, lo haya, o sea, lo hayan desembolsado, No, mentira. Sí, dale.  
Them: Para abrir, tus Ahí te muestro, sí, mi pantalla. Eso que, lo que está diciendo Oli, sí, el tema es que todavía no sea, eso sí que no lo puedo lo lo podemos harcodear también un poco, pero no tenemos el s tres.  
Me: ¿Qué te bloqueó?  
Them: Para subir el documento. Igual, el otro día, Jo marcó algo, pasa que no le di bola porque puso la documentación ya estaba en el repositorio que nos habían pasado. Dejame que eso lo chequee bien.  
Me: Sí.  
Them: Si es verdad. Y si puedo subir algo a un s tres, pero yo creo que todavía no. Después le pregunto a Gonza también.  
Me: Bien, porque si no está, yo lo tengo que y no y no  
Them: Sí. Sí. Déjame que termine de cerrar los PRs,  
Me: en algo  
Them: porque tengo un quilombo de branches y código acá, déjame que termine de cerrar los PRs,  
Me: Dale, dale, obvio, obvio, sí, sí, sí.  
Them: y y veo eso. Veo eso que le preguntaba a Gonza, en todo caso, de subir un archivo. Si ya podemos subir un archivo, empezamos a hacer el tema de las firmas, pero bueno, esa parte, por ejemplo, va a faltar todo lo que es el front, si querés lo podés avanzar, Juanpi, tenés que hacer. Básicamente es, el get me del crédito del template, perdón, del template del documento, el get me, y apretá un botón que diga firmar, y eso va a ser un tiro a la firma. Lo va a guardar, y después vos te vas a poder descargar el documento guardado. Bien. Estoy en el proceso de simulación, ¿verdad?, durante todo el proceso de simulación, el todo lo que es simulación, acordate que usa el mí y no el otro. Ok. Bien. Perfecto. Y una vez que esté firmado, viene acá mis préstamos, y cuando cuando lo ve tiene un botón de descargar el documento acá, ¿verdad, Oli? ¿Sí te parece? Descargar documento firmado, sí.  
Me: Ojo, sí, es es absolutamente correcto, yo tengo que poder seleccionar una cierta cantidad, nosotros le pusimos veinticinco, veinticinco como límite, porque si no, puedes hacer un un chorizo gigantesco,  
Them: ¿Veinticinco qué? Veinticinco qué.  
Me: Veinticinco es el límite de documentos que yo puedo descargar desde el back office a la vez.  
Them: No, no, No, no, igual él está diciendo ahí los de  
Me: En un ZIP.  
Them: los firmados, el firmado va a ser el único.  
Me: Sí, sí, sí, sí, sí, sí, sí, o sea,  
Them: ¿Estás viendo mi pantalla?  
Me: Sí, sí, sí, sí, sí, sí. El caso uno ya está aprobada.  
Them: Bueno,  
Me: Exactamente, sí, sí, sí, sí, sí, sí.  
Them: bueno, acá, cuando ya esté otorgado,  
Me: Perfecto. Ese es el ese es el, la Persa sesenta y tres es esa. Bien. Perfecto.  
Them: Está otorgado, una vez otorgado, quede y firmado, me aparezca acá el botón para descargar el documento.  
Me: Bien, perfecto. Entonces, esta  
Them: Ok.  
Me: hay que pasarla a estado, yo creo que en en review o en PR, Bueno, generar una nueva versión de un documento previamente dado de... Ah, bueno, acá ya entramos en las en las tareas de gestionar, así que ningún momento ahí. Visualizar auditoría de los documentos firmados.  
Them: Lo mismo, hasta que no tengamos la firma, no podemos hacer la  
Me: Hasta que no tengamos la firma, no podemos tener la auditoría.  
Them: Para  
Me: La firma es el PR de los que están pendientes que estás corrigiendo.  
Them: consulta, Iori.  
Me: No.  
Them: No, la firma todavía no está. Nosotros ahora estamos cerrando lo que es todo lo el template que, ¿viste?, el tipo de documento que te mostré ahí,  
Me: Sí.  
Them: Este que te, ¿viste que hice un grafiquito?  
Me: Sí.  
Them: Dice type,  
Me: Sí.  
Them: bueno, los cuatro PRs que ahora están son los del type.  
Me: Sí.  
Them: Una vez SPR me los haga pasar, yo puedo avanzar con el versionado, digamos, bien, con con lo los documentos en sí. Una vez me deje pasar lo de los documentos en sí, voy a poder hacer el de el usuario firmando el documento.  
Me: Bien, bien, bien, bien.  
Them: Y y a la vez que hago el del usuario firmando el documento, te agrego el de auditoría.  
Me: Bien.  
Them: O sea, este sería un tercer step.  
Me: Perfecto.  
Them: Si querés algo hoy y me podés liberar los PR, que están, por ejemplo, eso sería algo a muy importante.  
Me: Perfecto. Bien. Pásame pásame siempre el el el listado de los que están activos.  
Them: Todos. Todos, todos, todos los mismos, porque no me dejó pasar  
Me: Lo Ok, pero lo ahora o te o te te banco a que terminen las correcciones?  
Them: ahora, porque  
Me: Dale.  
Them: mandando una y me falta la última. O sea, andá porque el va a ver de abajo para arriba.  
Me: L'étape, Sí.  
Them: Oye, consulta, te creo, para las auditorías, querés que te cree una un una sección aparte. Sí.  
Me: En el mejor de los casos, sí, en el mejor de los casos sí,  
Them: Así, sí,  
Me: sí.  
Them: la web debería Vale. Igual. Fijate que Fijate que está quedando por ahí un quilombo de Sí. Agrupa, por ejemplo, create update gate template, agrupá las template por create applications, por simulator, documentos, ¿entendés?, como las que tienen Bien Te ponélas juntas ahora. Ya. ¿Listo? Voy a anotarlo también eso.  
Me: Bien. A ver, ¿en dónde está? ¿En dónde está el último? Paso al de los que mandé ayer a la mañana, ¿no?  
Them: Sí. Decí que están devueltos los PRs, si, por favor, puede chequear, porque yo ya le mandé un mensaje ayer, pero hoy no recibí novedades.  
Me: Listo. Bien, continuemos, entonces. Auditorio de documentos firmados, ya sabemos. Firma, aplicar firma digital al documento, lo mismo.  
Them: La misma.  
Me: Validar TOTP ingresado antes de firma, TOTP.  
Them: Tiate pena.  
Me: Pendiente para desarrollar.  
Them: No. Sì. Sì.  
Me: Solicítate para firmar. ¿Tenemos todo lo necesario para poder hacer eso?  
Them: Sente fuori. Tengo que hablar, lo he hablado con Nico, no he obtenido muchas respuestas de qué vamos a hacer, de cómo lo vamos hacer, así que te diría que no. Estamos medio a la espera de de algunas definiciones por ahí de Nico con con ellos.  
Me: Okay. Mandale mensaje por el por el grupo.  
Them: Más que Dale.  
Me: Definiciones ok. Almacenar documentos generados en el en servidor, estamos hablando de s tres. ¿No? Cliente visualiza documento.  
Them: Sì. Ahora mismo, ese tres.  
Me: S tres. Bien.  
Them: Ya lo hice, más o menos, está avanzado. El endpoint de LME, pero claramente no hace nada porque no hay ningún documento.  
Me: Bien. Vamos a descuento de cuotas. Entonces, de documentos resumen, PR pendientes, desarrollo de algunos,  
Them: Sí.  
Me: validar del s tres y  
Them: Sí.  
Me: efectivamente hay algo que no vimos, y lo podemos usar, si no, tengo que salir a patear una puerta a que me lo den cuanto antes.  
Them: Sí. Ajá.  
Me: Ok.  
Them: Efectivamente. También, ya.  
Me: ¿Cómo? Ese ese  
Them: Patete un aumento.  
Me: me encantaría decirte, dale, te juro que estamos todos en la misma, querido. Sí, sí, sí. Bien, bueno, vamos a  
Them: Cuotas.  
Me: vamos a descuento de cuotas.  
Them: Descuento de cuotas, básicamente, el cien por ciento de las  
Me: Puta kilo de  
Them: cosas están frenadas por un gran refactor que tengo que meter, es el de money precision, que es la pregunta que saqué, que, bueno, que no nos contestaron, y es el PR que estoy corrigiendo exactamente en este momento, que me le corrigió un par de cositas.  
Me: Con eso, con lo del con lo de los decimales,  
Them: Él  
Me: ahí avanzamos con lo que dijimos,  
Them: Sí, él me, sí, sí, pero ya mandé el PR, por eso estoy esperando que lo apruebe ahora, Cuando él aprueba este PR, yo meto todo el refactor, que tengo planteado para el tema precisión. Una vez pasa tema precisión, yo puedo hacer todo lo que sea descuento de pagos, carga de pagos, después hay otra que por ejemplo, tenés carga de pago realizado manualmente, la setenta y uno, tenés básicamente, también la que dice visualizar solicitudes pendiente de fondo, medio que esa va va va, eso se puede avanzar un poco, a ver. No. ¿Cuál es la que yo digo? Acá, aplicar los pagos importados a las cuotas correctas e importar el archivo de liquidaciones y obtener el resumen. Todo eso se va a poder hacer una vez esté el tema de los decimales. Que es la setenta, la sesenta y nueve, y la setenta y uno.  
Me: Bien. Ok. Más allá de los PRs,  
Them: Sí.  
Me: es desarrollo pendiente nomás, entonces.  
Them: Sí, desarrollo pendiente.  
Me: Bien. Cancelaciones, esto es más chiquitito.  
Them: Cancelaciones,  
Me: Bien.  
Them: Lo mismo, falta de desarrollo. Básicamente, está esperando lo mismo, el tema de la precisión, pero no porque sea bloqueante, sino para ir más o menos en orden, porque el tema de la precisión va varios cambios, muchos archivos. Entonces, no quiero meter mucho más código antes de hacer el refactor grande.  
Me: Ok, pregunta y acá cero cero bullshit. Hagamos de cuenta de que es el cliente perfecto y nos contesta al segundo, a la pregunta que nosotros le hagamos. ¿Llegamos al lunes a la tarde o lo muevo al martes, miércoles? Haciendo de cuenta de que ellos son perfectos.  
Them: ¿Todo lo que dijiste?  
Me: Sí.  
Them: Y, o sea, todo lo que vimos hasta ahora.  
Me: Claro, claro, claro, claro.  
Them: No, no sé, no, no, no sé, No,  
Me: O sea, acá no acá no hay no hay acá no hay cambio de alcance ni ni nada, No no no le sé.  
Them: no, no. No, no se llega ni en pedo, pero ¿por qué? Pedo. Estamos viernes a la tarde, o sea, lunes a la tarde no. Son muchas cosas, son como cinco o seis frentes que hay que atacar, teniendo en cuenta todo esto del precision y toda la bola, Igual no no movería la reunión, me parece copago tener la reunión, Dejame que me anote como pendiente. Vamos a hacer así, yo me voy a anotar los pendientes míos, que son ver lo de s tres, ver si nos pueden desbloquear eso, probar tema del entorno, porque no lo probé mucho, probar tema entorno y definir definir los puntos que pujear en la reunión, tengamos la reunión, porque ellos ahora, en este momento, se están fumando ocho pull requests, y ayer o antes de ayer se fumaron seis siete. Sea, tenemos mucho código que mostrar y avances, no es que no tenemos avance,  
Me: Sí.  
Them: Claro, no es que no No movería la reunión por eso, pero sería más por ahí una reunión de hablar y me parece bien hablar ahí con Jo y decir, por ejemplo, si nos falta algo,  
Me: Bueno.  
Them: ahí en misma reunión. Estoy de acuerdo con con Marcos. Capaz no mostrar nada porque es mostrar cosas a medias, porque no se va a llegar.  
Me: O sea, no mostrar, o sea,  
Them: Pero  
Me: mostrar nada no puedo, eso eso es eso sí que eso sí que no.  
Them: O mucho no sé, lo de documentos capaz. Sí, sí, lo de documentos. Si si ahora pasan todos los PR, tenemos toda la parte de documentos para mostrar, Oli.  
Me: Bien.  
Them: O sea, tendría que terminar de conectarlo ahí, pero estaría todo para mostrar eso. Sí, más casi que lo tengo, o me  
Me: O sea, o sea, más o menos tenemos como veinte PRs pendientes más allá de los que de los que tienen que aprobar ellos, entre las cosas que nos queda pendiente de desarrollar, Los voy a necesitar a ellos, encima, o atentos a hacer PRs inmediatamente.  
Them: Sí.  
Me: Ok.  
Them: Podemos mostrar esa parte de de documentos,  
Me: Ahora pregunta, yo pregunto.  
Them: y  
Me: Si no dependiéramos de los PRs, o sea, hay cosas que se pueden mostrar local y que yo no tenga que o es muy que valerme de  
Them: No, a ver,  
Me: de su aprobación?  
Them: a ver,  
Me: Y que y que lo dejamos después para el spring que viene?  
Them: poder  
Me: ¿Toda esa parte de correcciones? Porque la función medio es esa del del del que viene, del spring que viene. El spring que viene, o sea, viste que ustedes no no, o sea, refinar, no refinamos nada, porque no hay más nada.  
Them: Poder se puede, el tema es que a ver, en local vas a presentar los de documentos, punto y y final, porque después es un tema todo de, como te dijo Marcos, tiene un enjambre de de de ramas, por el hecho de que no hace el anuncio y la aprueban los los PRs, entonces también te te va a complicar para a vos también mostrarlo.  
Me: Claro.  
Them: Porque tienes que estar viendo qué funciona y qué no, y hay que combinar las programas que sí funcionan para que vos muestres solamente eso. ¿Tanico o Oli?  
Me: Debe estar en el  
Them: Debe tener, sí.  
Me: de AL dos, del otro cliente, esa  
Them: Mil millones de  
Me: Pero  
Them: Bueno. Bueno, si no, ahora cuando terminamos esta reunión te llamo diez minutos más y vemos qué podemos solucionar de eso.  
Me: A ver, si si si me tiene que decir que no,  
Them: Parece? No, no, es que podemos hacer, pero por eso  
Me: yo, si decir, sigo por eso.  
Them: hay que hay que pensar variantes. O sea, por ejemplo, si vos querés mostrarlo mostrar algo, hacemos una branch de development, que tenga todos los pull requests, y Juampi avance por ahí, y vamos a la chapas como hacíamos antes. El tema es que va a ser también un poco una pérdida de tiempo, porque nos va a pasar lo que nos llegó a pasar en un momento, y era que nosotros íbamos muy rápido y ellos íbamos muy lento y se se hacía doble laburo. Entonces, como poder poder, podemos. Como recomendable, no lo es. Ahora, a mí me parece copado tener la reunión el lunes. Sí, coincide. No sé lo que vos quieras, si vos querés mostrar  
Me: No, no, no.  
Them: para mostrar algo, yo agarro, hago una branch aparte, mergeo todos los PRs ahí y empiezo a mandar PRs como un sacado a a esa branch, los mergeamos todos, aceptamos todos, avanzamos y mostramos eso. Si querés eso, el lunes podemos tener muchas cosas para mostrar. El tema es que nos van a ir quedando ellos atrasados, como pasó en su momento. Creo que es más decisión tuya que nuestra.  
Me: Esta este era el debate que quería tener.  
Them: Lo que hay ahí. Yo,  
Me: Este era, por eso por eso lo preguntaba.  
Them: Es que tenés la Es que tenés las pros y las contra de las dos cosas, si vos querés mostrar algo, hago una plancha aparte, mergeo todo ahí y saco todos los PRs de ahora. Hasta el lunes a las a las doce, los meto en esa branch, tac, tac, tac, tac, tac, tac, listo. Y Juanpi trabaja sobre esa esa rama, y que esté toda la parte de documentos, que esté toda la parte de de cancelaciones, que esté toda la parte de todo, básicamente.  
Me: ¿A ustedes les?  
Them: Ahora, en paralelo,  
Me: Les resulta cómodo laburar así o no?  
Them: en Sí, sí que yo no tengo ningún problema, me me adapto. El único problema es que es, probablemente, le voy a abrir doscientos pull request a ellos, asumiendo que lo anteriores van a estar bien. Llegan a hacer un cambio en uno de los primeros pull request, y nos parte recontra al medio, o sea, hay que decir si no que adaptamos esta modalidad y que y que, en todo caso, nos dejen pasar las cosas como se habló en su momento y que y que nos hagan comentarios para corregir después, ¿entendés?  
Me: Ok, no, no, ok, entiendo.  
Them: Yo no tengo problema, yo no tengo problema y y tiene pros y tiene contras, las dos modalidades, porque una va a dejar avanzar mucho y la otra nos puede llegar a atrasar después, a la larga. Como a la vez no, porque si ya no se están atrasando ellos, poco es que podemos avanzar muy rápido. Entonces,  
Me: Sí, pero estoy pateando la pelota para el problema, estoy  
Them: no sé. Vamos partiendo de problemas,  
Me: problema para adelante, pero en algún momento lo  
Them: Vamos partiendo el problema tal cual, en algún en algún momento lo vamos a tener, pero vas a tener algo para mostrar el lunes y vamos a poder resolver los temas que tenemos. Son dos formas de encararlo, creo que es una decisión  
Me: Sí. No, no, no, obviamente.  
Them: más tuya que nuestra eso, por eso te digo. Lo que vos digas es,  
Me: Yo creo que prefiero no patearlo, ¿Por qué? Porque en la discursiva del día de hoy, ellos están atrasados,  
Them: Igual.  
Me: los empujamos, o sea, le metimos el dedo en el traste, todos los días, Entonces, si yo de repente dejo de aparecer, muestro, y digo, ojo, porque tenemos todos este problema, vamos a tener un segundo problema por más que sea el mismo. Entonces, prefiero que explote la bomba ahora, y tenemos dos esas esas dos semanas de Changüí, Sí, sí, sí, sí, sí. Prefiero. Prefiero, y después, y pongamos una sección en la presentación, es bloqueos. Esto, esto, esto, esto, esto, esto, esto. O sea, yo lo agrego, no tengo ningún problema, y lo digo a cara de perro, es como Sí, sí, sí, mantengamos, sigamos trabajando como hasta ahora.  
Them: Bien, ok. Entonces,  
Me: Sí.  
Them: documentos vas a tener hasta el lunes, por lo menos, para mostrar, abrir documentos.  
Me: Bien.  
Them: ¿Alguna que otra cosa que se pueda? Pero esa parte, esa parte es que si querés, lo que, la la rama esta que te digo la podemos hacer para mergear todos los PRG están, si Jo no los corrige hoy a última hora, hacemos esa branch, porque lo más probable es que ya pase porque una vez que los rechaza, ya la próxima los debería de aceptar, en teoría. Entonces, si si querés, esperemos a que jo a ver si los corrige hoy. Si no los corrige, mergeo todos en una rama, y y mostramos toda la parte de documentos andando.  
Me: Bien.  
Them: Sí.  
Me: Bien, bien, bien, bien, pero no vayamos por la la otra opción más nazi, así que no Bien, mantengámonos así. Perfecto. Bueno. ¿Algún comentario más? El ferón está está está perfecto. Así que falta conectar esas cositas. A lo más? Bien.  
Them: Por ahora, no, yo por ahora no.  
Me: Bien, bien, bien, bien, bien, bien. Estoy muy contento con el trabajo, chicos, sí, ¿vale? Sépanlo. Así que  
Them: Two seconds.  
Me: Sí, sí.  
Them: Yo yo quiero hacer más, pero la verdad,  
Me: Sí, sí, sí, sí, sí. Y otra cosa que me alegra es que por lo menos hasta ahora, Las la las cosas que que fuimos viendo de lo que fueron trabajando están excelentes, y es tal cual como como están las historias. Entonces, sí, como no hubo un problema de comunicación ahí, como que eso generalmente es un problema, la historias vacías, los alcances fuiste poco claros, Bueno, pero en realidad ahí me tienen que decir más ustedes que yo Sí.  
Them: Ah, bueno, bien. So, venimos, excelente,  
Me: Bien, bien, bien, bien, bien.  
Them: Sí, sí. Marcos, un segundo, dos segundos, hace que me vaya a abrir porque yo  
Me: Dale, dale.  
Them: le vi las cosas. La última de documents, de la última que usaste, ¿cuál es? Es la hola, Sí, la de versioning. La de versioning, ok, listo, esa uso.  
Me: No, no, no, esa esa esa nomás, esa nomás.  
Them: Listo, sigue ahorita, vamos, no te preocupes,  
Me: Así que bueno. Bueno,  
Them: Bien.  
Me: listo.  
Them: Bueno, ahora mando el último, vos ya mandaste mensaje igual, ¿no?  
Me: Ya le mandé, lo puse en copia. Ahora le voy a mandar un mensaje a a a a Seda, le hago un resumen de lo que acabamos de hablar, el que avisa no traiciona, es esa es esa es mi política, ¿viste? El cabeza no traiciona, yo no  
Them: Yeah.  
Me: prefiero ser honesto y que duela y  
Them: Igual, para mí no, a ver,  
Me: y  
Them: no no no creo que haya tanto drama porque ellos saben, básicamente, no es que no hicimos los pelotudos esta dos semanas, o sea,  
Me: No. No. No.  
Them: el Discord de de Marco y tuyo en el  
Me: Claro. Si hay algo que, si hay  
Them: en el canal de de  
Me: si hay algo que sobre ese evidencia, así que en eso en eso estoy estoy estoy estoy más que tranquilo.  
Them: Pero bueno.  
Me: Laboramos, laboramos, eso es. Más que obvio. Bueno, listo, no les quito más tiempo, perdón por sacarles tanto tiempo,  
Them: No,  
Me: Odio la reunionitis, pero bueno, necesitaba más o menos entender. A veces es necesario, sí.  
Them: No era más. Es necesario definir Valídate. Tres,  
Me: No, no, no, no, no, no, yo en AL dos no sé más.  
Them: todavía o no? ¿Me alegas?  
Me: No sé si suerte, como Alex eran Pero era otro, es  
Them: Ah, no, español.  
Me: era otro tipo de caos a resolver, Y es  
Them: Expaña, ir a las oficinas, LV2.  
Me: Y eso, era buenísimo. Me manda una foto, Juanma, vos no lo conociste. Marcos. Un un amigo mío que trabajaba con nosotros,  
Them: Delincuente, no, no, no, no, Sí. Cuente, no,  
Me: Y se, y lo contrataron desde allá, así que me manda.  
Them: Ah, mira,  
Me: Me manda fotos, ¿sí?, que le traen frutas, que lo que le pone  
Them: Ahí está.  
Me: que se lo llevan a ver los partidos. Ahora lo invitaron a un  
Them: Ah,  
Me: a un hotel, no sé cuántas estrellas en Rosario, ¿viste?  
Them: Hermoso. Ah, bueno. Ah, bueno. Ah, yo, porque de que el rock no aproveché eso.  
Me: Claro, el hermano el hermano de Juampi también está  
Them: Muy boludo.  
Me: es parte de, también lo contrató la empresa.  
Them: Ya, adiós.  
Me: Sí, sí, sí, sí, sí.  
Them: Mira. La ventaja de tener un hijo en la  
Me: Sí. Sí, sí, sí, igual justo Roque está en la mejor célula de de todas para mí. La es la única que funciona bien y que tiene buena gente. En fin,  
Them: Pero bueno, va.  
Me: Ah, dale, bueno, bueno, chicos.  
Them: Los dejo, tengo una de de mega lapses, ahorita sí que... Listo.  
Me: Bueno. Gracias. Chau, chau.  
Them: Bye bye. Vale.
