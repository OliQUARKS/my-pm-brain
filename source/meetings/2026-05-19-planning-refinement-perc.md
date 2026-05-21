# Source — Planning and Refinement PERC

- **Date:** 2026-05-19
- **Participants:** Olivier (PM, Quarks), Marcos Perez (Dev, Quarks), Nicolás Paez (TL, Quarks), Juan Ignacio Moyano (Dev, Quarks), Giuliano Trincavelli (Dev, Quarks), Israel Fernandez (TL, Quarks)
- **Matching ingestion file:** `../../ingestion/meetings/2026-05-19-planning-refinement-perc.md`

---

```
Meeting Title: Planning and Refinement - PERC
Date: May 19
Meeting participants: Olivier, Marcos Perez, Nicolas, Juan Ignacio Moyano, Giuliano, Israel

Transcript:
 
Them: En insomnia. Yo recuerdo un solo usuario que pasaron, pero habían el caso de algún usuario que tenga un tag puntual, tipo empleado acuerdo. Ok, porque si no, Ok, porque si no, sí, es empleado con con tal x, y hacés un preview del listado que vería, más directo ¿Usamos algún servicio de estos de...? Le das un JSON y te responde eso? Y por ahora ahí hacemos los todos los empleados que necesitemos o los que necesitemos, y ya, mira, Que algo básico, no un diseño como si se fuese a ver en la aplicación mobile, vean el la info que llega la info total ¿no?, la que después va ver mobile, así ya saben toda la info que está disponible. Después mobile se arregla en mostrar y pedir punto al que necesite. Sí, Sí, pero no oigo en detalle, pero digo, por ahí nos conviene un poco seguir al flujo, ¿no?, de quiero listar el coso, y no sé Sí, claro. Quiero, seleccionó el que tengo, el play, que nos ayude a diseñar el API que hace falta eso. Porque esto, es un o sea, no sé, no vamos a hacer otra API y esto va a ser una mezcla de el API que tenemos con el PFF de de la aplicación. ¿No? Pero no es nada, fronteando esto, digo. Pues las dos. Ahí el título sería, eso consulta al template, no consulta préstamo, ¿no? Eso claro, en realidad, con Zoom, el el template es lo que ya hicieron, que es, básicamente, tipos de préstamos disponibles. Después, la palabra préstamo o crédito en sí es la que tiene un empleado asociado. Por si no, era superconfuso hablarlo con ellos y por eso quedó como  
Me: Claro, o sea, todo es préstamo o solicitud, pero no conviene usar template, porque, si no, no lo podemos separar.  
Them: ¿Y el tag es del empleado? Porque Sí. Claro, el, es como en un banco para verlo más simple, vos en el banco sos o o Classic o Gold, Platinum o Black. ¿Sí? Esos serían los tax Después del lado de ellos van a tener otros tax, pero como para que se entienda rápido qué sería. Ok. Y el user sabe sus tax.  
Me: No.  
Them: No. Directamente le aparece lo que tiene disponible y ya, digamos. Ya, lo tiene desde el token, lo saca. Hoy. Entonces, la consulta no es por tax, sino es por user? Es claro, el usuario pregunta qué tiene disponible, que eso se transforma en el tag del usuario. Que Que eso lo que teníamos que ver que hablamos la no sé si fue la semana pasada con Seba, era para no andar decodiando el token nosotros, que sea un barra mío, símil, que te dé el tag del usuario,  
Me: Ok.  
Them: Oh, pero el el evento de AWS, trae el token decodificado, Ok. Y Ok, y ya parcea ese atributo tag, no me acuerdo cómo era la respuesta del JWT. Si al desencodirlo, Sí, revisemos eso, porque me parece que viene como que los claims, si viene una estructura ahí de Pero vamos, revisé, no sé si era el Yo uso más el ¿puede? ¿Cómo es? No escuché. Revisar, desencodearlo, decís vos, Irra. No, no, lo que digo es que el evento de AWS, te da el token de cinco día a ver. Viene una estructura en el evento que son como el token con las cosas. Igual, a chequear, revisemos bien, pero casi seguro que es así. Por lo menos con el API HTTP. Con esto ahí está usándonos.  
Me: Bien. Perfecto. Esto quiere en una subtarea por las dudas. ¿Es una obviedad?  
Them: Está bien para que no se pase, declaralo si querés, y ahí ya puede validar Marcos si llega o no.  
Me: ¿Me Cómo lo escribimos?  
Them: Revisar evento, que llegue el JWT plano o así en codeado, ¿cómo se llama?  
Me: Bien. Con esta historia estamos ok, ¿algún comentario más? ¿No? Bien. Tenemos esto, a ver, vamos a hacer así más fácil. Es gestionar solicitud y consulta de préstamo. Ahora sí. Bien, estos son subtareas, entiendo que estuviste agregando sus tareas, Marcos, ¿puede ser? Ahí o estás?  
Them: No, no, sus tareas no, las de improvements, digamos, que creaste,  
Me: Ah, listo.  
Them: están todas en proceso. O sea, dentro de un toque mandó mandó PDF.  
Me: Bien. It las habíamos generado nosotros, creo, en el refinamiento. Ok, bien. Segundo paso, empleado crea solicitud de préstamo. Como empleado, quiero crear una solicitud de préstamo de uno a los disponibles, y formalizar mi intención de obtener crédito. Escenario número uno, cuando tengo todos los préstamos disponibles, ¿bien? Y elijo estoy leyendo para el orto, cuando seleccione uno de los tres préstamos disponibles, entonces se crea una solicitud con estado en curso. ¿Bien? Y se graban los valores de las variables del préstamo del template, si quieren, de préstamo vigentes en ese momento. Y se graban las cuotas correspondientes a esa solicitud en ese momento. Acá, digo, corregime donde me equivoco, ellos todavía, el Excel en donde ustedes que utilizaron para para la última entrega o sea, el la la última versión no me la pasaron todavía, Ahí es decidir si hacemos la construcción de las cuotas en base a ese Excel, o si las moqueamos y luego, cuando nos lo pasen, debería ser entre hoy y mañana, el ajuste posterior. Ahí lo que ustedes me digan,  
Them: Es que, si vos lo vais a buscar directamente el cálculo de o sea, la lógica de cuotas, como el usuario no elige el monto, se crea con el interés y demás al momento de dar de alta el template. Para el usuario que lista es transparente, no no varía para él la cuota según qué persona es.  
Me: Ok. Bien. Acá yo tengo una duda también, es, entiendo que las cuotas las deberíamos guardar en una tabla e ir e ir listando a futuro después cuando esas cuotas son pagadas, que cada cuota sea un registro, Entiendo que sí, ¿no?  
Them: Al Al final, ¿en qué quedó lo lo último que dijo Seba? Porque no era un francés estándar, que la cuota varía,  
Me: Y me lo debe, me debe esa respuesta Entonces, no podemos arrancar con las cuotas todavía.  
Them: No, porque él quería que la cuota sea igual el monto en todas. Entonces, se iban a jugar con algo del seguro de  
Me: Sì. Bueno.  
Them: y no sé qué cosa rara.  
Me: Vamos a hacer así, yo quito la referencia a las cuotas,  
Them: Igual, las cuotas habría que guardarlas igual, en alguna tabla de pago. No? Y aparte es transparente para esta esta etapa, Oli, porque el empleado en sí va a recibir las cuotas, ya sean iguales o no, de algún lado las va a recibir. Cambia para la que hacen del template y con el final.  
Me: Okay.  
Them: Es ok, que quede ese ítem.  
Me: Bien, perfecto. ¿Tengo que hacer alguna referencia acerca del cálculo? Correspondiente a las cuotas, o ya con el Excel que tenemos está está ok. Ahí en el Excel está todo, no no solo se queden con esa con esa pestaña, hay otras que que hacen el el ejemplo de el armado de las cuotas.  
Them: Ah, ok.  
Me: Bien, estaba ¿Bien? Estaba en una estaba en el en el backlog y también está en el en el Discord, por cualquier cosa. Bien. No sé si quieren revisar quieren revisar eso mejor, Sí. A ver si lo tengo acá.  
Them: ¿En Excel? No sé si vale la pena ahora. Si no es el final, incluso,  
Me: Bueno. Bien. Solicitud en curso expirada, dado que existe una solicitud en curso sin confirmación, cuando transcurre una hora sin completar el proceso, entonces la solicitud expira. ¿Bien?  
Them: Eso chicos, no sé, Nico Irra, con un cron, con un ¿O o cómo? Una consulta antes, Oli, el sin completar, era no, literalmente completado, sino el usuario confirmó y firmó los documentos, ¿no?  
Me: Esto es, en realidad, Buena pregunta. Vamos a poner varios varias etapas del proceso, yo creo que acá voy a voy a traer el speech, así sea más fácil. Comparte esta pestaña, tuki tuki, En breve, a estar el diseño, obviamente, nosotros no nos importa, pero pero bueno, pero mi idea de este sprint es que nosotros lleguemos hasta terminar este segundo paso. À ver, cambio de template, en Wat son consulte templates? No. Es hasta acá. La confirmación Porque esto más de front, ahora me agarró la duda. Perdón, chicos. Sí, esas,  
Them: Aber das  
Me: ¿Cómo cómo?  
Them: Si hay que listar la solicitud, se puede hacer eso, ¿no?  
Me: Claro, Exactamente. Entonces, van a haber distintas etapas, distintos estados. El momento en donde... Pero yo esto lo tenía escrito en una de las historias. Acá está. Estos son los estados que que pensé. Los estados de la solicitud. En curso, desde que se crea la solicitud hasta que se confirma la firma de documentos con el OTP, TOTP, pendiente desde la confirmación hasta la el otorgamiento del crédito otorgado, cuando yo ya lo desembolsé, ¿bien?, hasta que es pagado totalmente, anticipado, sí.  
Them: Entonces, te se expira, si no llega completado, ¿cierto? Sí, llegó completado, pero no está otorgado, no no se autoexpira, es solo esperar que fondeen la cuenta y se les acredite en algún momento.  
Me: O sea, se expira si no llega a pendiente.  
Them: Claro, pendiente sería con el acepto términos y condiciones.  
Me: Es correcto.  
Them: Y, pues, expira, si no llega, ¿en qué tiempo?  
Me: Una hora.  
Them: En realidad tampoco sería con el confirma. Sería con el confirmar tu identidad.  
Me: Acá acá lo tengo, no estaba compartiendo, perdón.  
Them: ¿O no? O sea, entiendo que tampoco sería con la firma del documento, sino con eso también. El pendiente me confunde, che, porque desde la confirmación hasta el otorgamiento, Sería como un estado de confirmado, pendiente de otorgar eso.  
Me: Exacto, expediente de otorgamiento, sí, tres.  
Them: Ok. No, o Oli, no sería tampoco desde la firma, porque hay un step más, que es la confirmación de identidad. Ahí fijate en el stitch,  
Me: Eso, estoy de acuerdo, lo que lo que hablamos con con Seba es que la confirmación es la suma de los dos,  
Them: Por eso, entonces, no, a nosotros no es cuando nos llega el documento, sino cuando termina la confirmación de identidad. Claro.  
Me: Claro, pero, por ejemplo, si yo digo acá, si si si digo, ok, quiero el de cien mil,  
Them: Sí,  
Me: o, bueno, quinientos mil, veo los datos, o sea, me informo un más profundamente, le digo, dale, voy a confirmar solicitud entre esta pantalla, y esta pantalla, o o estas dos, si yo digo, tengo que leer documento, no, ¿sabe qué? No, mejor no. O leo el documento y directamente digo, no, no lo quiero, y dejé el celular ahí, quedó, ahí es donde yo nunca pasé al estado pendiente de otorgamiento, porque nunca lo firmé. Entonces, eso, ese tiempo es el de una hora. ¿Bien?  
Them: Pero en curso tampoco está, porque no, en verdad, no hiciste nada todavía.  
Me: Quizás es solicitando, podríamos decir, que es el es el el nombre, si querés.  
Them: Para mí todo lo que hace el usuario ahí con las vistas, que vuelve, que hasta que no firme y o hay un botoncito ahí de abajo que, si leíste y leíste ok después de la identidad, ahí para mí se crea el la solicitud. Porque todo lo otro vos podés ir y volver, las veces que Claro, se crearían un montón de préstamos con todas las perdón, es el panel, ahí, o sea, no sabes en qué momento se te queda el usuario. Está bien. Pero, básicamente, sería el estado firmado en adelante, es el que ya no te deja expirarlo. Listo. ¿No? Ok.  
Me: Exactamente. Exactamente. Es correcto, sí. Es exactamente. Ahora, volviendo para atrás por las dudas. El el este print llega hasta acá, o sea, no, todavía no nos con documentación ni TOTP ni mucho menos con confirmación ni desembolso ni ni casos excepcionales, demás. Es, quedamos acá.  
Them: Bien.  
Me: Perdón. Quedamos acá. Bien, Bueno, ahora vuelvo, vuelvo para acá, y estábamos en crea solicitud de préstamo. Entonces, una hora sin completar el proceso, ¿Quieren que lo  
Them: En recibir la firma del empleado, por en vez de completar el proceso. Ahí creo que queda un poco más  
Me: Bien, Bien. Cambio de template, con solicitudes en estado en curso, dado que existen solicitudes en curso asociadas a un template, cuando se modifica ese template, entonces las solicitudes pendientes o inconclusas asociadas expiran. Esto es muy importante. Las que quedan acá, en este estado, si yo le cambio, el template las tengo que matar.  
Them: Bien.  
Me: Bien. ¿Hay algún otro caso que se le ocurra? Hasta ahí lo elaboramos con  
Them: Ahí una cosa.  
Me: con Seba y con Nico, sí.  
Them: Ahorita hablaron del tema del Chrome y eso, para, o sea, tenemos que pensar ahí, Nico, bueno, todos, vamos a hacer esos eventos, ¿no? Sí. De si pasa esto, hago lo otro, No sé si vamos a usar step functions o vamos a usar algún evento de esto de una SQS o, no sé, de un SNS o Pero de alguna manera hay que ir enganchando esas landas, para para para que pasen ¿no? Cuando ocurra tal cosa, en función de tal estado, no sé, mande un evento o llamo tal o Landa, claro que sí. Ahí para el el paso dos, podés usar el job o, si no, cuando el user va a buscar la solicitud, que ya pasó una hora, te fijás y pasó una hora y no le dejás. También. No sé si va con Joves o no. Bien, eso bien, desde el punto de vista del usuario, sí, O sea, cuando me dices job, no sé bien, ahora me dices a qué te refiere, El tema es que, por ejemplo, no veo, supón que el usuario no no no mira más la cuando yo vaya al back office, nunca lo voy a expirar, ¿no? O tendría que poner la lógica de cuando listo, me fijo si está expirado y lo expiro y no, es raro. Sí. Un es que ahí el shop debería ir declarado no me acuerdo los nombres, Seven creo que es el que dispara los los eventos asociados a Lambda. Sí. Para que ese o sea, que tenga un cleaner que que se fije cuáles expiraron. Pero bueno, sí, eso pensémoslo después, a ver cómo va a quedar. No metería el Chrome tan atado a la a la Landa actual. No, el Chrome, la Landa, o sea, o sea, lo que sí hay que limpiar algo, o sea, hacemos, o sea, el punto de vista de desarrollo es una Landa y el Chrome es el trigger. Claro. Pero eso no me preocupa tanto como lo otros eventos de bueno, si el usuario cuando firme tiene que ir hasta el otro lugar, qué sé. Cuando firme... No te entendí la última parte. Sí, pasan cosas, ¿no?, el usuario firma determina todo y a partir de ahí pasa algo, ¿no? Bueno. Como Ah, todos... Ok. Sí. Pero ¿cómo cómo enganchamos el proceso para que Bien,  
Me: ¿Algo que tenga que agregar de eso?  
Them: No, es para otra otra etapa no honesta, que recién empiezan a  
Me: Bien. Perfecto. ¿Algo alguna casuística que se les ocurra? Que haya que agregar? Bien. Por las dudas, yo después les vuelvo a enviar el el para que para que vuelva a quedar, me preguntan por por cualquier cosa. ¿Bien? Entonces, hasta ahí es desde el lado de del empleado. ¿Bien? Del lado de de Watson, son estas dos. Concretamente es quiero ver los préstamos que fueron solicitados. ¿Bien? Entonces, dado que soy operador de back office, cuando consulto las solicitudes de préstamos, entonces recibo el listado con todas las solicitudes. Y acá, importante, las variables que yo quiero ver son monto de préstamo, tasa, cuotas restantes, cuotas totales, tax, FT, capital adeudado, estado. Y al ingresar al detalle de una solicitud, puedo ver el resto de las variables asociadas. El resto es la fija, las calculadas automáticamente, las que las que eran originalmente eran, o sea, definidas por el back office, Bien,  
Them: Y ahí eso, préstamos solicitados, es todos los que estén en estado de pendientes de aprobación, aprobados, o qué cosa es un préstamo solicitado ahí?  
Me: Las solicitudes Las solicitudes de préstamo... Buena pregunta. Las solicitudes de préstamo, en este caso, ahí nos no sé cómo sería la arquitectura, pero por eso lo que  
Them: Ahí dice, en curso pendiente, entregado, cancelado, arrepentido y pagado.  
Me: Claro, pero en algún momento, esa solicitud se convierte en un préstamo ya propriamente dicho, es como ya, o sea, ya lo di.  
Them: Claro, ahí  
Me: No sé si eso cambia mucho,  
Them: Claro, ahí habría que ver con Seba, qué es lo que les interesa ver. Si tipo prospect y y préstamos reales, o sea, los que ya están confirmados, firmados y otorgados, y los que están en curso, por si quieren darle a otros sectores aparte, para que le haga el push de dale, pedilo.  
Me: A ver, o sea, si yo con un A ver, o sea, si yo con un estado puedo tener la diferencia entre los dos, o sea, si los, por ejemplo, los primeros los primeros dos son solicitudes estos ya son parte de de un préstamo,  
Them: Claro. Sí, yo haría dos endpoints, pero es depende qué qué Por eso, para mí depende un poco de qué quieren ver, porque si le dejás una sola vista de solicitudes y ve todo, va a ser un vómito de información, o sea, todo el que entró a jugar y ver cómo eran las cuotas y demás, en ese rato que están viendo, van a tener un montón de casos en en progreso que capaz que se desestiman, entonces, no sé si mezclaría los préstamos otorgados, contra la solicitud que están en proceso.  
Me: Y deja de ser una solicitud y ya se convierte en un préstamo. Entonces, dejo de verlo, en la tabla solicitudes y lo veo en la tabla préstamos.  
Them: Chiaro.  
Me: ¿Y ahí y habría una Debería. Sí, cuando uno se cuando se convierte la solicitud en préstamo,  
Them: Del cambio de estado y sí, eso, A nivel base de datos, Oli, para que te des una idea, es lo mismo, es el la la tabla es template, es perdón, credits, por ejemplo,  
Me: Okay.  
Them: y va va a ir cambiando nada más el estado de ese credit. Si va a ser en curso pendiente otorgado blablablá, blablablá,  
Me: Pero son dos endpoint distintos, por lo tanto, lo veo en dos lugares  
Them: Claro,  
Me: Bien, listo.  
Them: yo diría sí, pero bueno, por eso es, como dice Nico, hay que ver por ahí qué es lo que quieren ver o cómo lo quieren hacer.  
Me: ¿Y  
Them: Sí, eso, dejamelo que me lo lleve mucho, porque yo tengo dudas en generar las solicitudes en créditos directamente, Pueden suciar mucho la base, como quieren mantener o sea, ver dónde lo pierden al usuario, guardar todo eso en créditos va ser hacer una tabla en vano que que no es data real, o sea, es Eso sí.  
Me: Bien. Hija, duda respondida,  
Them: Two Más o menos. No sé si era para que me respondieran hace  
Me: Bien.  
Them: Respondieran así, necesariamente era como pensar.  
Me: Bien.  
Them: Ahí sí estoy de acuerdo con lo que dice Nico, de mantener los créditos y las solicitudes A ver, tienen ciclos de vida distintos, digamos.  
Me: Bien. Bueno, acá los lo las variables los puse por las dudas, pero son lo que lo que está en el Excel, no no hay ninguna variación de eso. ¿Bien? Bueno, escenario dos, poder filtrar según persona física, persona jurídica, eso no sé si estamos recibiendo ese dato, pero bueno, sí prepararlo para para recibir este tipo de usuarios. Cuotas totales, el cliente y, lógicamente, el estado en el que está. Después, bueno, ordenamientos. Sí.  
Them: Pon Pará, déjame ver para ver quién estoy hablando huevas. Sí, un empleado de la mantovana o de cualquier otro, puede ser J?  
Me: Si te respondo, te miento. Es una buena pregunta. Pero yo creo que es una cuestión de escalabilidad, me parece.  
Them: Sí. Bueno, pero hay que ver eso que si nosotros responder una pregunta tenemos que ir a otro servicio, a otra API a consumir eso, probablemente, eventualmente vamos a terminar haciendo algo alguna vista local de esos usuarios para ¿no?, y eso nos obliga a tenerlo sincronizado, no sé, está raro eso.  
Me: Ok, bueno.  
Them: Y no sé si te puede dar ese caso igual,  
Me: Me llegó a esta pregunta.  
Them: Que haya PJs. Como empleados.  
Me: Me lo llevo, me lo llevo para consultar. Bien. Hasta ahí, es entonces lo lo que tenemos, Y después, el último, ¿Dónde está? Acá. Es para poder exportarlo en un XLSX. Que es lo que yo tenga filtrado, en la tabla de las solicitudes, Bien. Con todas las variables disponibles. Bien.  
Them: Sí, me exporto Ok.  
Me: Acá, Juan Pill, ¿alguna duda? ¿Sí o Marcos? Perfecto.  
Them: No.  
Me: Bien. Bueno, acá estaríamos, vuelvo sobre esta sobre esta Hay una de las historias que tiene en cuenta, más que nada, esta pantalla, pero como el front no lo hacemos, yo pregunto ¿el el mismo endpoint me sirve para responder estas dos consultas, ¿no? Porque los datos que vienen son prácticamente los mismos. Salvo, por ejemplo, la cuenta destino, que es a dónde lo va a recibir el préstamo el el usuario.  
Them: Ed, Perdón, la consulta es si esas dos pantallas se resuelven con el mismo endpoint. No, una lista y la otra te da el detalle, por si después quieren agregar más info en el detalle, préstamo que seleccionó.  
Me: Correcto. Ok, entonces deberíamos generar una historia por esto. Bien. Bien. Disponibilizar endpoint para visualizar  
Them: Para obtener el detalle de un préstamo.  
Me: las variables  
Them: De un template. Sería.  
Me: De préstamo, sí, lo único que me hace ruido es la cuenta destino. Pero eso no sé si viene de de front o cómo es.  
Them: En la cuenta de aquí, ¿no?  
Me: Claro, si yo estoy en o sea, ¿a dónde lo voy a recibir? ¿A a a mi CVU?  
Them: No, eso es responsabilidad del mobile. Mobile sabe comunicarse con el core,  
Me: Perfect.  
Them: Apá, no, ahí me quedan dudas, ¿sí?, nosotros nos vamos a tener que comunicar para que nos dé qué cuenta, porque ahí crédito se estaría metiendo en algo que no le corresponde. Tendríamos que hacer un un pasamanos con su corp para que nos dé la cuenta de ese usuario.  
Me: Okay.  
Them: Y no sé si eso es viable.  
Me: Okay.  
Them: Claro, pero pero más adelante, cuando avance el tema de créditos, o sea, Stapi debería dar el crédito, pero como dice en esa pantalla, ¿a quién se lo da, digamos? A qué cuenta es el mandado, cómo es. Obviamente, es mucho más adelante, pero o sea, voy a lo que dice Nico también. Cómo nos unimos con el score y todo eso.  
Me: Algo que te haga preguntarles a ellos, ¿Cómo cómo quieren hacer? No.  
Them: No, a ellos no no hace falta preguntar. Porque el dato de la cuenta es un dato interno de ellos. A nivel de crédito, ¿le le interesa qué empleado se lo dio? Y sí se puede guardar la traza de a qué cuenta en ese momento se asignó. Pero como es  
Me: Ok, ahí te sigo.  
Them: Claro, pero como son, medio sensibles con la información que quieren dar y la que no, Pensé que no nos quisieron dar un endpoint para alistar los tags, que es algo superbásico,  
Me: Mucho menos Mucho menos a la cuenta, ok.  
Them: No sé si obtener los datos de la cuenta de un usuario,  
Me: Bien.  
Them: es viable.  
Me: Bien. Bien. Perfecto. Bueno,  
Them: Los datos igual de la cuenta del  
Me: después sí, sí.  
Them: usuario, acá estoy viendo, están en el insomnio. Nos dieron el get account to see mil, Sí, hay un user account, sí. Ok, se podría hacer ahí por lo que estoy viendo acá, sí. Dice, obtener cuenta mediante client ID. Envías el client ID y te envío todo, el titular, el el tipo de persona, las wallets, Porque está abriendo el el insomnio, sí.  
Me: Bien. Bueno,  
Them: Hay problema, entonces, Solís.  
Me: Bueno.  
Them: Y ahí en lo que estás viendo, Marco, ¿ahí en hacer la cuenta? Sería la cuenta de la billetera siempre, ¿no? Dice wallets, y es una list de wallets. Así que tendría varios. Hay que ver, sí, tiene varias wallets. Supongo que podría tener varias cuentas. Eso, Alicia, hay que preguntarle a Seba. ¿En qué caso un usuario puede tener más de una cuenta? Y si tiene más de una, ¿cómo seleccionar una?  
Me: Esos ya te que sí, pueden tener cuenta recaudadora, cuenta sueldo, pueden tener cuenta en dólares, pueden tener a futuro cuentas cripto, o sea, van a a poder tener varias cuentas.  
Them: Esto igual solo aplica para la cuenta sueldo, ¿no?  
Me: Si te digo, te miento, yo creo que no, estoy  
Them: ¿Y cómo  
Me: seguro que  
Them: ¿Y cómo lo metemos un crédito en pesos en en la cuenta en dólares, cripto?  
Me: Low key.  
Them: Igual no te perdón, cuando pagas la cuota no te des cuenta del de la cuenta de solvencia. Del solaria. Mándalo ahí. Sí, capaz que validar con ellos que esto siempre va parar a la cuenta de sueldo, y y ver ahí cómo identificar la cuenta sueldo cuando tiene muchas cuentas.  
Me: Eso eso me lo llevo, mañana justo tenemos reunión por por diseño de del del flujo así que ahí que lo tengo a Marcos y a Ceva les puedo matar esa duda. Para lo que es el para lo que es la el pago de las cuotas es fácil porque siempre va a ser el depósito en la cuenta sueldo. Y, además, el el descuento lo hace lo hace la mantovana, no es algo que nosotros tengamos que hacer el descuento. Entonces, esa parte la corremos a un lado. Ahora, el desembolso de el préstamo creo que sea en la cuenta remunerada, tampoco en la cuenta... No, porque sería agregarle, sí, tiene razón, tiene razón, debería ser sí o sí en la cuenta en la cuenta sueldo, pero aún así me lo llevo para preguntar.  
Them: Vale. Yo tengo una pregunta, por ahí es volver un poquito, pero bueno, me quedó la la duda, por eso estaba buscando también el insonnia. El JWT, ¿dónde? Vos, Nico, que viene por ahí el usuario? Porque yo veo acá como que no O sea, ¿o lo tenemos que codear nosotros o o qué onda? Lo que decía Isra es que en el evento ya te llega el tipo el pre del el decode, de hecho, del usuario que está consumiéndolo, ¿En qué evento? En el evento de la Landa de HTTP. Ok. Pero, de nuevo, ahí, ¿viste? Amazon tiene dos dos versiones del API manager. Hay una que es la que creo que es la que está usando, y otra que es más sencilla, es la la HTTP. Ahí te lo podías, era muy fácil configurarle a un proveedor o auth y lo que sea. Yo siempre usé esa, la otra es muy cara. Pero entonces, en ese evento sí estoy noventa y nueve coma cuarenta tres raya cuatro por ciento seguro de que viaje. Hay que ver acá si no si no viene. Ok.  
Me: Bien. Bueno, ¿cómo vamos a a dividir el el el trabajo? Como a quien enlazar.  
Them: Sí, yo, si no les molesta, los dejo ahí con eso, me bajo que hay un quilombo ahí con el L dos, tengo que ir a una reunión un momentito. Vale. Vale.  
Me: ¿Ra?  
Them: Yo, lo que es improvements, ya lo pasé todo a  
Me: Perfecto.  
Them: Estoy con eso. Y de Después lo otro, no sé,  
Me: Bien,  
Them: Yo ya tengo asignada la de crear, la de coso, o sea, haría lo del crude y mientras tanto puede ir Juanpi haciendo las vistas.  
Me: Juan B, ¿cómo la cómo lo es? Bien.  
Them: Bien.  
Me: Buenísimo.  
Them: Por ahí lo que se puede hacer para la parte de simular el préstamo es hacer una vista similar a la de Stitch, Sí, sí, eso eso iba a decir, que igual hay que crear una tarea de eso, ¿me puedes crear una OLE? Para la simulación del de sacar el préstamo y ver eso,  
Me: Para ¿Para para las vistas? Dale, ya veo.  
Them: Eso, JP, no no te vuelvas loco con un diseño ultra fancy de mobile. No, obvio, obvio, obvio, obvio. Nada, va a seguir la el estilo que tiene el Playground, no sé, no... Con la  
Me: Bien, cualquier cosa o cambio, si alguno toma terminó con alguna tarea y toma otra, por favor, ahí no dejen de de comunicarse, así de de avisarse, así no hay bueno, obviamente, doble trabajo, es mucho menos. Y y después, no, creo que nada más, Hay Bien, Nico, Juampi, Marcos, algún comentario,  
Them: No, perdona, Nico, que le va caer un pull request de la hostia. Pero Otra vez, este muchacho. Nada más.  
Me: bien. Después,  
Them: Pásale nomás.  
Me: gente  
Them: Es pasar? Este es grande en serio, Nico, igual.  
Me: y después, a modo medio retro, ¿hay algún comentario de del último sprint?, ¿cómo lo cómo lo vieron?, qué cosas les pareció bien, qué cosas hay que mejorar, cómo  
Them: Però,  
Me: Ahí cómo lo Sí.  
Them: Una consulta. Marcos, ¿querés que...? ¿Cómo el hombro de la ruta? Para eso? Pongo créditos o simulación o cómo, sea, contesta lo de eso. Sea, como sea, más cómodo. Bien, perfecto, Listo, Doris, seguí preguntando.  
Me: No, bueno, era eso, este, ¿cómo vieron el spin pasar? Si les, si tuvieron a las corridas, si si si vieron algo o algo que cambiarían de la metodología interna o o con definiciones pendientes, bloqueantes,  
Them: No, superbién. No, superbién, sí. Yo creo que bien, lo único que capaz, un poco más de comunicación, nos faltó a todos, ¿veo? Un poquito, no mucho, pero, bueno, en el sentido de que no tenemos de IDs ni nada de eso, es como que estamos trabajando por aparte, solos. Pero donde todo bien, no, capaz que eso mejora un poco más la complicación y estamos bien.  
Me: Perfecto. Bueno, a partir de mañana, ahí sí pongo daily para ver cómo cómo funcionamos. Y de última, sí, nos repetimos bastante y estamos aceitados, las termino sacando, una cada dos días,  
Them: No sé si ahora en cortita, si no,  
Me: Sí, sí, sí, por eso.  
Them: diez minutos, sí.  
Me: Yo también soy, antirreuniones. No te rías, Nico, mentira. Así que así que, bueno. Bueno, cualquier duda que tengan, levanten la mano y salgo disparado a a molestar al cliente.  
Them: Consulta rápida, Marcos, todo en en dev, ¿verdad? Porque hice un pool ahí de Y lo de la app, no, está todo en new refactor. Porque todavía no no pasó. Bien, bien, por eso, ese es porque hice un pool acá que había, entonces dije, no está todavía en Me llevo de ahí, entonces, sí, bye. Que es lo último.  
Me: Bien. Bueno, ahí les vuelvo a compartir, de nuevo Igualmente, ya casi que está el el diseño terminado, pero conceptualmente es esto que les que les muestro. Bien. Bueno, Listo, entonces.  
Them: Buenísimo.  
Me: Bueno.  
Them: Bueno, vale.  
Me: Muchas gracias.  
Them: Abrazo, grande. Chau, chau.  
Me: Chau, chau.
```
