# Meeting — Préstamos: templates, validaciones, y casos de prueba (verbatim)

- **Fecha:** 2026-07-16
- **Título:** Préstamos — templates, validaciones, y casos de prueba
- **Participantes (declarados):** Olivier
- **Participantes (inferidos del transcript):** Olivier (PM Quarks, "Me"), Marcos Perez (dev back Quarks, "Them" principal), un TL de Quarks (Nico/Isra — voz que plantea el tema de entorno), Gonza/Gonzalo (infra PERC, vía mensaje). Menciones: José (dev PERC), Fefe (COO Quarks), Juampi (dev front Quarks), Seba (PO PERC), Jo (reviewer PRs PERC).

> Audit anchor. Never edited after creation.

---

Them: Template de crédito. Tiene que haber cuatro, justamente. 
Me: Bien, 
Them: Tres altas, y un cambio. Acá dice, antes, después, 
Me: Perfecto. 
Them: acá están las altas. Qué locura, ¿ah? 
Me: Hermoso. Bien, bien, bien, bien. 
Them: Me lo probás. Template de préstamo cuando ingreso, listo, entonces visualiza todos los templates registrados, y cada registro exhibe monto, tasa, este lo vamos a mover. Para acá, y ya está aprobado, porque ya lo vimos. Cuando abre su detalle, entonces visualiza todos los campos. Listo, vamos a eso. Eso también tendría que estar arriba. Tendría que estar acá. No. Acá. Está aprobado. Vamos a hacerlo igual, porque no no lo hice. Ahí está. Y cuando aprieto ver, me hace el tirío, y acá tengo todo. Costos, tasas, costos computados, datos del template, cuadro de marcha, que sería cómo quedan las cuotas, y listo. 
Me: Excelente. 
Them: Cuando actualiza los campos, entonces, variables de préstamos son editables en el caso de modificar un TAC se deben validar las reglas de negocio. Nunca probé a modificar un tag. Sinceramente. 
Me: Si vos modificás, acordad, ojo ojo con esto, si vos modificás un tag, te tiene que la sesión del usuario. 
Them: Sí, pero pará, eso es bueno, sí, entiendo lo que decís. 
Me: Creo que hay un escenario de eso, 
Them: Por eso hay un escenario estamos como bastante más adelantados con eso. Deberíamos meter, si no, las solicitudes antes. Pero bueno, sí. Lo que dice de reglas de negocio es que si yo tengo préstamo oro uno, préstamo oro dos, préstamo oro tres. Nunca probé ese caso, Si yo ahora quiero editar el silver y ponerle y ponerle gold, no me tiene que dejar. Porque ya hay tres gold. 
Me: Bien. 
Them: Gloria a dios. 
Me: Vamos, vamos. 
Them: Bien. Aprobado, entonces, esto. 
Me: Bien. 
Them: Este está aprobado, ya lo vimos. Dar de baja el template. Ahí lo dimos de baja. 
Me: Bien, 
Them: Trazabilidad, sí, Trazabilidad, sí, y va a estar, obviamente, en logs y auditorías. Acá, baja. Se ejecuta cuando finaliza, entonces, el sistema registra acción para auditoría, cualquier eliminación de un template no modifica las solicitudes previamente asignadas a los usuarios. Entonces, lo que habría que hacer es nosotros tenemos, por ejemplo, en templates, tenemos el Tenemos el préstamo uno silver, ¿no? Si yo entro al simulator, 
Me: Correcto. 
Them: podemos acá probar todos los casos, podemos ir uno por uno los del simulator, si querés. Simulator, caso uno. Cliqueo el préstamo, solicito el préstamo, Acá no firmo. No está firmado esto. Y el operador del back office, ah, esto, bueno, Este caso, cuando lo edite, En realidad, lo que En realidad, lo que va a pasar... A ver, préstamo uno editado. Expirada. Ay, no había olvidado qué lo había hecho. Expira 
Me: Bueno, acá tengo expirada, ¿por qué? Porque... Ah, ok, pero al 
Them: Eso, que se verificó el préstamo. 
Me: Bien. Pero pregunto acá. ¿Este es el el simulador o un playground? 
Them: Sí. 
Me: Pero en el front real, real, real, del día de mañana, no se van a ver, listo. 
Them: No se van a ver. Lo lo dejamos porque habíamos dicho que servía, ¿te acordás? 
Me: Ok, me sirve verlo, pero bueno, después el de el de front tiene que decir, este no va. 
Them: Ajá. 
Me: Bien, bien, bien. 
Them: Después. Entonces ahí lo que hice fue crearla, no firmarla, por lo cual, cuando lo edité, se cerró. Ahora, si la solicito ¿La solicité? Ah, sí, ya lo solicité. Ahí lo solicité. Que yo ahora voy al simulator, mis préstamos, está en progreso, todavía no está firmado. Pasa una hora, voy a correr el cron. Vos fijate ir ordenando ahí el UAT en el orden este que estoy haciendo, ¿no? 
Me: A ver, 
Them: Ahora, acabo de correr el Chrome, sin firmar, o sea, es la de que cuando pasa una hora sin firmar, debería expirar. Ya corrí el cron, y el cron ya la cerró, por lo cual está expirada ahora. 
Me: Ok, lo muevo para arriba, solicitud en curso expirada, una hora sin completar. Bien. 
Them: Bien. Ahora, algo que me olvide, que esto lo vamos tener que hacer antes, si no, Es que no Es que no le creé al al template de no le crea el documento. 
Me: Bien. 
Them: Vai. 
Me: O sea, entonces, a ver, el de la solicitud expirada lo vamos por ok. 
Them: Sí. Ahora sí. Listo. Entonces, siguiente caso. 
Me: A ver, 
Them: Entro al ¿Qué qué sería ahora? Ya probamos el de expirada, probamos el otro de expirada, 
Me: Pará, auditoría de bajas, INEF solicitudes vigentes. Dado que la eliminación se ejecuta correctamente, cuando finaliza la operación, entonces el sistema la acción para auditoría. Cualquier eliminación de un template Ok. 
Them: Sí, eso ya lo vimos. Estaba bien. 
Me: Dar baja lógica, ok. Bueno, pero ese este caso lo deberíamos ver antes, de la del Chrome, ¿no? 
Them: ¿Cuál? 
Me: La La que acabo de decir, la de 
Them: ¿La línea catorce? 
Me: la línea catorce. 
Them: No, porque sería sería otro caso, sería porque en realidad acá lo lo tenías mal escrito porque tenías y tiene que ser crédito, no solicitud. 
Me: Ok, dado que la alineación 
Them: Te la moví. No modifica los créditos previamente asignados. Las solicitudes de crédito, sí. Es lo que acabamos de ver, que cuando lo modifiqué, la cerró. 
Me: Los créditos previamente 
Them: Claro. 
Me: otorgados. 
Them: Claro. Sí. En este caso, 
Me: O los préstamos, más o menos, 
Them: ahí va, otorgado, sí. 
Me: préstamos, ya que hablamos de préstamos y otorgados, vamos por ahí. 
Them: Entonces, ahora 
Me: Bien. 
Them: Entonces, ahora sí podemos probar eso, si querés. Vamos con este. Ya lo, ah, ya lo tenía solicitado. Lo aprobamos, En este caso, está aprobado. ¿Bien? Lo voy a otorgar, 
Me: Bien. Acá acá hagamos un comentario porque el aprobar pues, nosotros estamos aprobando manualmente. En realidad es el es pre el préstamo siempre es pre aprobado, no hay ningún 
Them: La la probé acá 
Me: de aprobación. 
Them: La lo aprobé acá porque no lo firmé en el paso anterior, pero si la firmás, ya se aprueba automáticamente. O sea, no firmé el documento, cuando dije aprobar significa que firmé el 
Me: Ok. Okay. Okay. Okay. Okay. 
Them: Bien, ahí ya está otorgado el préstamo uno editado. Entonces, si yo ahora voy a templates, delete, y elimino el préstamo uno editado, y voy a simulator, Sigue estando acá aprobado. Y garantizado mi crédito. 
Me: Vamos con aprobado, buenísimo. Bien. Bien, vamos trece. 
Them: Este ya va mucho más arriba. 
Me: Vamos. 
Them: Porque ya lo hicimos. 
Me: Claro que soy empleado y tengo un tema asociado, cuando consulto los préstamos, entonces recibo las templates y así no, bueno, este 
Them: Este 
Me: mucho más rápido, listo. Lo vamos 
Them: Este también. Línea dieciséis también. 
Me: Este lo pongo acá, Incluso, 
Them: El diecisiete también. Voy con el Voy con el dieciocho. Dado que soy operador de back office, cuando consulto las solicitudes de préstamo, entonces recibo un listado con todo las solicitudes. Bien. Acá está listo. Dos aprobás, una expira, dos expirás y una aprobada. 
Me: Bien. Bien. 
Them: Hermoso. Aprobado también. 
Me: Bien. 
Them: Vamos con el exportar. Hago la exportación, me descarga, lo abro y tiene que tener una sola, que es la aprobada. Listo. Aprobada. 
Me: Estamos en promedio de un caso por minuto. 
Them: Bien, vamos bien. Dado que abro mi préstamo cuando lo veo, entonces veo el monto otorgado, el estado, la de acreditación, este va más arriba porque ya lo hice. Va junto con toda la parte de usuario del simulator. Dado que veo el detalle cuando lo reviso, entonces veo cuántas cuotas pagué sobre el total y cuántas restan. Este ya lo hicimos también aprobado. 
Me: Esta 
Them: Claro, después de de 
Me: Esto es después de la creación, ¿no? Ve el monto otorgado. Ok. 
Them: Claro, después de sería después de la creación y después de probar acá. Sería No sé, dentro de después de crear solicitud, Sería por ahí. 
Me: Okay. 
Them: Es imposible, igual, parece, porque es como que vas citando varias veces. 
Me: Bien. Crear sección de créditos otorgados, bueno, acá hay que ponerle el escenario. 
Them: Listo. Dado que soy operador del black office, puedo ver los créditos otorgados. Filtrar y ordenar. ¿Qué te parece? Bueno, ahí está. No sé, voy a filtrar por un estado que no no hay. Y bien, tengo con todos y me trae todos. 
Me: Bien. 
Them: ¿Bien? 
Me: Bien. 
Them: Una query que no iba, esperes ahí, listo. Dado que tengo cuotas Dado que tengo cuotas pendientes, cuando veo el detalle, entonces se destaca el monto de la próxima cuota y el mes que vence. Bueno, eso básicamente sería acá en el simulator. Sería esto, ya lo vimos también. Que es todo esto. Que es todo esto. Cuota restante veinticuatro, próximo vencimiento, total del crédito, pagado, deuda restante y las cuotas. 
Me: Bueno, acá tengo una pregunta. Yo no tengo manera, como, o sea, como el cobro de las cuotas es por descuento de en el pago de haberes, la fecha de vencimiento no sé cuál es la no sé cuál es la, o sea, no no hay ninguna no tenemos una lógica de decir, ok, es el dieciséis y no es el catorce, y no es el cinco. O sea, ¿cómo cómo definís, cómo cómo tenés vos pensada esa esa lógica para la fecha de vencimiento y qué pasa si se pasa de la fecha de vencimiento. 
Them: A ver, yo creo que por ahí hay que cambiarlo. La fecha de vencimiento sería, debería ser el día que la mantoana paga. Como nosotros no sabemos, 
Me: El quinto, es el quinto, cuarto, quinto 
Them: no pasa nada. 
Me: cuarto día del mes, el cuarto día hábil del mes. 
Them: Cinco del mes que viene, por ejemplo, que sea siempre el cinco. Ahora, actualmente, lo que hace es, si vos registras un crédito el trece, te va a poner la próxima cuota el trece. Si entra en el lapso de la mantovana, se te va a descontar. Que igual yo creo que está bien así, porque había una que decía, tipo, como que cuando la fecha de corte es ahora, por ejemplo, es el veinte, entran todos aquellos préstamos que llevan más de un mes y que tienen como primer cuota ahora. Una cosa así decía. Entonces, está bien que sea la fecha de pedido del préstamo más un mes. Creo yo. Que es lo que está ahora. 
Me: Okay. 
Them: Si yo lo ahora dieciséis de julio, pero vencimiento el dieciséis del ocho. Porque entraría el mes que viene. Dieciséis del siete, dieciséis del ocho. Y el próximo mes, cuando se haga el reporte, se va a cortar hasta el día veinte y se le va a enviar. 
Me: Si la fecha si la fecha es posterior al día de corte, pero está dentro del mismo del mismo mes, de la fecha de, o sea, es el veintidós, 
Them: Al otro, entra al próximo mes. 
Me: y al y al ya sé, pero al usuario, ¿qué se le muestra? ¿El próximo mes o el mes 
Them: Se demostraría el próximo mes. 
Me: Okay. 
Them: Si no me equivoco. 
Me: Bien. 
Them: Ahora lo probamos, 
Me: Perdón que pregunte esto, pero es 
Them: No. Está bien. Pero bueno, lo podemos dar por aprobado. 
Me: Bien, dale, bien. Bien. 
Them: Bien. Dado que veo el detalle cuando lo reviso, entonces veo el saldo que me queda por pagar. Aprobado. Dado que mi préstamo está otorgado, cuando abro las cuotas, entonces veo todas las cuotas ordenadas por número aprobado. Dado que miro una cuota, cuando la reviso, entonces veo número, fecha de vencimiento total y el desglose. Bueno, el desglose no es medio que no está. En realidad. Sea, capital, interés y el total. El de El desglose total del capital, interés, IVA, todo eso, no. Bueno, 
Me: Esto tiene que tiene que estar. 
Them: Bueno, pendiente. Listo. 
Me: Iba sobre el interés y gasto administrativo, 
Them: Eso igual, a ver, yo voy a cuotas, Tengo el interés y el total, no, claro, no lo tengo. Bueno, 
Me: Nunca lo mostramos el desglose de las cuotas, ¿no? 
Them: No, lo que hemos mostrado era esto. Cuotas. Así. O sea, la palabra desglose, no. 
Me: Si vos te metés Si vos te metés en el préstamo, negociando para nosotros, 
Them: Esto. Esto es todo lo que Esto es todo lo que mostramos, No no hemos mostrado otra cosa que no sea esto. 
Me: Ok, entonces, yo no tengo en ningún lado el total de las variables 
Them: No. 
Me: Bueno, ahí tenemos un tema. 
Them: O sea, ya las viste cuando pediste el préstamo. Ahora ya no. Lo agregamos, pero no lo hemos mostrado, no es que se se lo robamos ahora, digamos. Ay, consulta, igual. Es para que lo cierre al final vea las las variables de su préstamo en el momento que lo pidió, En el momento después que quiere revisar las cuotas. Por ejemplo, ahora Claro, digo, el la imagen 
Me: No, mais 
Them: de cuándo lo dos meses después, por ejemplo. Claro. 
Me: Posso, posso. El usuario no me importa, El, o sea, lo del usuario ya está captura, pará que lo, me quiero sacar la duda. 
Them: Ah. Pará, entonces sí, vos decís en en en templates. 
Me: Creo que, sí, sí, sí, sí, sí. 
Them: Si vos en templates, sí, vos entrás y está todo. Costos, costos acá, interés, IVA, seguro, o sea, está todo. 
Me: Listo. Io tengo que tener en el lado del usuario tengo que tener el total el monto total de tu préstamo, la cantidad de cuotas, la cuotas restantes, cuándo se acreditó, el ID del préstamo, es la próxima cuota, cuánto es la la deuda restante, el estado de las cuotas, 
Them: Sí, es la vista que pasaste, por eso. 
Me: Sí, sí, señor, y los botones. 
Them: Lo que es el operador del back office, sí, acá. Este sí. Fijate que acá tiene. 
Me: Okay. 
Them: Costos o sea, está todo. 
Me: Detalle del préstamo, ok. Claro, bueno. Ahora, el desglose de cada cuota Bueno, pero pará, pará, pará, vamos a cambiar esto, entonces. 
Them: Sería como operador de back office. Hay que aclararlo en algún lado. 
Me: Sí, sí, sí. De glossy de cargota, dado que Bueno, no importa. Estoy Ahí veo. Y miro una cuota Cuando la reviso, entonces veo números, fecha de, viendo, veo todos los los datos, entonces. Entonces, voy a ver todos los datos, de todos los préstamos. 
Them: Sí. 
Me: ¿Listo? 
Them: Bien. Esto ya lo vimos, aprobado. Dado que mi préstamo todavía no fue otorgado sin desembolso, Cuando intento ver las cuotas, entonces todavía no hay cuotas generadas. Este lo puedes poner más arriba, está aprobado igual porque no no existen, así que está ok. 
Me: El préstamo no fue otorgado, con intento de las cuotas, entonces no hay cuotas que negar, ¿listo? 
Them: Dado que busco un empleado o un préstamo cuando lo abra, entonces veo su estado, monto, fechas, identificador. 
Me: Pará, pará, vamos a pausa. Dónde lo muevo? A ver. Operador, soy empleado, tengo préstamo de Ok, lo pongo después de solicitud en curso expirada. Ah, no, sin desembolso. Y este escenario hasta me lo guardaría para los casos de desembolso, me parece. 
Them: ¿Cuál? 
Me: El de el, ahora lo tengo seleccionado, fila diecisiete. Il scialle da Ya lo tenemos aprobado. 
Them: No, sería sería más arriba, sería toda la parte 
Me: Pero lo 
Them: esta, ¿está bien?, de cuando creamos antes de otorgarlo, apretamos ver cuotas y y nos va a decir que no están. Está bien. Es cuando la parte de usuario está bien. 
Me: Datos principales, solicitud en curso, expira, es que es es acá. Es acá. Listo, bien, continuamos. 
Them: Bien. Dado que busco un empleado o un préstamo cuando lo abro, entonces veo su estado. Ahí no entiendo, porque yo puedo ver créditos los veo acá, veo el listado, Puedo ver los logs de auditorías, por ejemplo, de, no sé, de las solicitudes de crédito, Puedo ver las de créditos, O sea, podés ver todo, 
Me: Busco un empleado o 
Them: pero no sé, son varias tablas distintas. 
Me: Busco un empleado o un préstamo, Cuando lo abra, veo su estado, montos. Listo, está bien. 
Them: Acá y ves el, por ejemplo, acá, el usuario. Lo lo filtrás. 
Me: A ver. 
Them: En realidad, acá al front le falta el copiar, porque no me deja ver el 
Me: Sí. 
Them: el dato total. Pero bueno, sí. 
Me: Eso lo podemos 
Them: Sí, lo lo 
Me: lo lo pongo 
Them: la agrego. Copy paste acá. 
Me: le pongo el, la probé con comentario, entonces. En ese, si querés. 
Them: Ahí me va a dar toc, no me haces. Yo me lo anoto. Dale, 
Me: O que el stream, porque, ojo, porque hay varias tablas que queda el stream cortado. 
Them: bien, dale. 
Me: O le ponés el botón de copiar o le estirás el string para que esté todo. 
Them: Sí. 
Me: Sí, una, dos. 
Them: Vale. 
Me: Te lo dejo en el estirado, si quieres. 
Them: Bien. 
Me: Vamos. 
Them: Dado que veo el préstamo cuando reviso las cuotas, entonces, veo cada una con su desglose y su estado. ¿Eso ya lo hicimos? En realidad, Bueno, esto después complementan ello. Eso después, ¿cómo lo implementan ellos?, porque tenemos el listado 
Me: ¿Cómo dice? 
Them: acá del template, o sea, que vemos todo el 
Me: Yo a este lo movería movería este 
Them: y 
Me: este escenario para después de probar el el ida y vuelta con la mantovana, me parece. Porque ahí yo ya yo ya voy a tener casos parciales pagados con error y y pendientes. 
Them: Dale. E igual, chats... Sí, está bien, se puede hacer igual. Se puede hacer porque lo estamos medio que lo lo podemos hacer a mano. Pero sí, igual sería más la parte de pagos con 
Me: Lo lo muevo para abajo. 
Them: está bien. Si querés sacarla, sacala. 
Me: Yo ya sé que funciona igual, pero a ver, el histórico de importaciones, generar, importar el archivo, obtener un, aplicar los pagos y 
Them: Y y hay otro punto 
Me: Bien, 
Them: Y y hay otro punto abajo también, lo mismo. Que dice liquidaciones de la mantovana. Que lo mismo, ya lo hice, la podemos hacer, podemos importar algo, pero si querés cambiarlo para el próximo o lo que sea, mejor. 
Me: Estamos coordinando ahí con la con la manto, oh, lo vamos a hacer el lunes, ojalá nadie pueda trabajar el lunes, ojalá, pero bueno. Por razones obvias, ¿no? Pero bueno, lo tenemos pensado para el lunes. 
Them: Bien. 
Me: De última, de última, lo que podemos hacer es toda la casuística de ida y vuelta de la Manto, sin estamos mal de tiempo, lo dejamos para ese momento. 
Them: Hecha igual. Si querés, órale a trabajo. 
Me: O sea, por mí, o sea, lo la vamos, o sea, la repetimos, pero sí, sí, sí, por mí, hoy probamos la, sí, sí. 
Them: Bueno, acá, dado que veo el préstamo, veo el historial. Sería acá en créditos, Acá en créditos vemos todo el historial de de los cambios en el crédito, si no tenemos, por ejemplo, los pagos. Nosotros podemos hacer lo siguiente, mirá, vamos a ver si podemos hacerlo ya. 
Me: Veo liquidaciones de la Madonna, es que es lo mismo, me parece que acá ya lo, este este caso también lo tengo que mover para 
Them: Dale, múvelo. 
Me: Se aplicaron las cuotas y cuando se... Es más, hasta seguro tenemos este escenario duplicado. Onde va? Cancelaciones, Descuento de cuotas. Bien. 
Them: Pues acá tenés unas filas que te las pinté en verde, que son desembolso de fondos. 
Me: Desembolso de fondos. Ok. Bueno, esa lo dejamos pendiente, entonces. 
Them: Sí. 
Me: Bueno. 
Them: ¿Dónde estás? 
Me: Vamos a la fila setenta y cuatro, ¿no? 
Them: Listo, sí. Dado que tengo un préstamo que tengo préstamos en distintos estados, cuando genero el antes del día del corte, entonces el archivo incluye solo las cuotas de préstamos otorgados, cuyo descuento cae en el mes corriente y excluye préstamos en cualquier otro estado y se registra en auditoría. Bueno. 
Me: O sea, concretamente es, dame los otorgados. Del mes corriente. 
Them: Sí. Te digo, así como Así como exportar, para que me, tengo que crear la configuración de la cuenta. Podemos moverla, por ejemplo, al doce, ya que tenemos un crédito el dieciséis, igual no va a entrar porque es el el mes que viene, Y esto te está dando excesivamente mucho. ¿Va a fallar? No, no, mirá, me aviso. Mantoana, exportar cuotas. Tenemos archivo. Y Ok. Cuatrocientos uno. Cuatrocientos uno es porque no estoy autorizado a acceder al vault, porque se me venció el token. Файлы. Ahí está. Ahí subí el baúl. No, y ahí metido time out. Se murió por el por la memoria, este. Ahí está. Me lo descargó. Mentira, no murió. Ahí están. ¿Cuántos a descontar del día dieciséis? Nada. Ahí está el nombre del archivo cuotas a descontar, dieciséis del siete del dos mil veintiséis. No entró ninguna. No, está bien, ¿por qué mal? 
Me: Bien. Vale. Bien. 
Them: Tendríamos que ver acá en installments, cuota uno. Sería siete dieciséis del siete, y habíamos dicho que edit installment ID es este, Credit ID es este de acá. Edits. Es el único. Granted add vamos a poner que estuvo el dieciséis del seis. Ahí corrimos la cuota. Un mes. Y, si no me equivoco, y genero el archivo ahora, regenerar archivo, otra vez por lo mismo. Me generó el archivo, y no entró tampoco. ¿Por qué no entró? Es una regla de corte que no respetamos. Vuelvo en un toque, 
Me: ¿Sale? 
Them: Sí, o por Hay alguna regla de corte que no respeta muy bien. Este sí le agarró de no tener la posibilidad de hacer casos reales. È un po' contro. ¿En qué mes estamos? ¿En qué mes 
Me: ¿En qué caso? 
Them: ¿En qué mes estamos? 
Me: Oi, Julio? 
Them: Enero, febrero, marzo, abril, mayo, junio, julio, siete. Siete. Estaría ahí siete. Sí, te debería entrar. A ver. ¿Querés seguir con los siguientes casos y después volvemos a este o no quedamos en este hasta que lo saquemos? 
Me: Vamos a tener pasa que nos va a bloquear todo lo que es 
Them: Listo, quedamos, no, no, sino en este. 
Me: la generación del archivo mensual. Sí, sí, Sí, sí, sí, sí. Sí, porque es la base de todo, básicamente. 
Them: Bien, 
Me: Sí, sí, sí, sí. 
Them: El el cutoff, la ventana es, mes de la cuota, fecha de otorgamiento versus el día de corte. La ventana del ciclo de julio sería fecha de vencimiento, entre el uno de julio del treinta y uno, que el crédito haya sido 
Me: Mhmm. 
Them: antes del veinte de junio, y que el crédito esté, obviamente, grande, activo, con la pendiente activa. O sea, due date, entre julio uno y julio treinta y uno, eso lo tenemos, y gran te edad antes del veinte de junio. Antes del veinte de junio. Ahí está. 
Me: Antes veinte de junio. Exacto, sí. No, 
Them: Y yo le 
Me: No, para, sí. Sí, 
Them: dieciséis del junio, dieciséis de junio, 
Me: Si yo lo pido el primero de julio, 
Them: bien. 
Me: en agosto, yo tengo que tener la primera cuota. 
Them: Oli, no sé si habías visto que respondió Seba, que prefiere el lunes. 
Me: Y me, o sea, lo lo lo sabía, lo sabía. Sí, sí, sí, sí. 
Them: Me bajo un ratito para ver el tema de r dos. Si necesitan que vuelvan, me avisan y 
Me: Allez. 
Them: Vale. Vuelvo nomás. A las cuatro es la otra, ¿no? 
Me: A las cuatro, sí. 
Them: Perfecto. Esto, hablamos en un rato. 
Me: Also 
Them: Una abrazo. Ok. Estoy frustrando de una forma, 
Me: Salir, va a salir. ¿Sabe por dónde va? 
Them: Sì, però no... Ya te digo. Está fallando, se vio la subida al vault, porque ahí la fecha de corte entró bien. Y me exportó la cuota que debería haber entrado, que entró. En la query está bien. Sabe que cuando sube al, pero si está subiendo al documento, que cuando está subiendo el documento ese ID cuota legal, concepto empleado importe, está pasando algo que no le gusta y no lo está subiendo bien. O estoy guardando Que no, es siempre es otro documento, o sea, es rarísimo. ¿Por qué no está entrando? 
Me: Okay. O sea, si no podemos probarla ahí, O sea, si no podemos probar la ida, no podemos probar la vuelta, Porque si yo no a ver, si no puedo marcar correctamente las que van, ¿cómo las...? 
Them: Sí. Sí, como poder se puede, pero porque es venir acá a create installments, cuota uno. Agarrar el ID, Venir acá. Venir a 
Me: Okay. 
Them: Noveltis. Sería import acá. 
Me: Bien. 
Them: No, sería... Este de acá. Body. Acá le pongo credit installment ID, 
Me: Bueno, continuemos con, sí, continuemos con el resto. 
Them: Vale. 
Me: Así estamos, cualquier cosa, en el peor de los casos, acá con este tenemos un issue conocido, sabemos cómo resolverlo, queríamos suplir la mayor cantidad de sí. Sí, sí, sí, continuemos, continuemos mejor. 
Them: Listo. 
Me: Bueno, 
Them: Entonces, credit installments, tenemos esto acá, Está la cuota, ¿verdad? Tenemos credit y 
Me: Pará, dado que un préstamo fue otorgado después de la fecha del gol, cuando cae ese escenario tampoco lo vamos a poder probar. 
Them: No. 
Me: Bien. 
Them: Por ahora, no. 
Me: Tranqui, tranqui, tranqui. Dado que genera el archivo, a ver, peor de los para para darte tranquilidad, ida y vuelta de la mantovana, si no lo podemos hacer, lo hacemos el lunes, porque es es es algo que tenemos que ver en ese escenario. Me sirve si lo puedo mover antes, obvio, Peor de los escenarios, lo vemos el lunes, así que no te no te frustres por eso, tenés tiempo como para como para como para laborarlo. Bien, 
Them: Está. Te te muestro esto. 
Me: Entonces, 
Them: Sí. Dale. 
Me: vamos con la fila setenta y seis. Dado que genera el archivo, cuando revise su contenido, entonces, incluye únicamente número de legajo, no tenemos el número de legajo, Acá tenemos aprobado de aprobado con comentario, todavía no nos lo dieron, ¿no? 
Them: No. 
Me: Está aquí los re mil parios. Número de legajo, ID cuota, nombre del empleado, importe de la cuota. Eso estaba. Entonces, bien. No te frustres, no te frustres. Bien, bien. O sea, lo lo que lo que quiero lograr para la reunión, estamos superbién, así que Bien. Bueno, dado que soy administrador, cuando accedo a la configuración, entonces puedo definir el día del mes que se genera y envié el archivo. Y ese valor es un valor en base. Eso está bien. 
Them: Este es el nombre del archivo también, porque ya lo generamos bien. 
Me: Bien. Bueno, día de corte, o sea, se envía automáticamente por mail a la casilla configurada. 
Them: Este lo dejaría en pendiente porque hay que testearlo con ellos en en stage. 
Me: Bien. Y, este, el el que le sigue también. ¿No? ¿Qué pasa cuando se envía y no Si querés, lo borrá, si querés, lo borró a la mierda. 
Them: Sí. 
Me: Porque de, o sea, este escenario lo puse porque es 
Them: Claro. 
Me: ¿se mandó o no se mandó? Quizás yo dependo del mail automático 
Them: Sí, sí. 
Me: ¿Hay algo que me avisa? 
Them: Sí. 
Me: Ahora, ¿tu sensación es que está o está...? 
Them: No, sí, sí, eso sí, está en los logs. 
Me: Listo. 
Them: Están los logs acá de envíos, mantovana. 
Me: Claro, pero no hay un 
Them: Acá. Hay un log de envío, hay un log de envío que cada vez que intenta enviar, 
Me: cartelás 
Them: se se guarda acá. 
Me: Listo, perfecto, me alcanza, es como 
Them: Antes de que lo porque si falla te lo lo está registrando el logo. 
Me: el operador vaya y se fije, a ver si se mandó. Bien. Bueno, Entonces, pendiente, pendiente, pendiente, en la fila ochenta y uno. Envío automático falla, error de cuando ocurre, notifica al back office, para acción manual y el archivo queda disponible para descarga y envío manual. Siempre va a estar disponible para, porque yo lo puedo descargar de nuevo. 
Them: Eso sí. 
Me: Le borro ese I, entonces. Bien, dado que accedo 
Them: Sí. 
Me: pero los dejo pendientes. Bien. Dado que accedo al histórico, cuando lo consulto, entonces, veo todas las exportaciones, desde la más reciente a la más antigua. 
Them: Sí, eso lo lo acabamos de ver acá. En Montebana. Histórico de exportaciones. Acá. 
Me: Bien, vamos, ok, aprobado. Arriba, arriba de los ánimos. Bien, bien. O sea, ya con lo que tenemos, ya estamos superbién. Yo ya te y te y ya te y estoy feliz. Sim, sim, sim, sim, sim. Bien. Dado que miro una fila del histórico, cuando la reviso, entonces, feo, fecha, cantidad de registros, monto total, 
Them: Sí, el operador no lo puse acá, está, creo que está acá, a ver. 
Me: y el operador que la generó en el caso de los manuales. 
Them: Sí, eso va a estar acá en cosas, exportaciones y envíos. Usuario, acá está. Usuario, origen, cuotas, ciclo y fecha. 
Me: Aprobado. Dado que hay muchas exportaciones, paginado, básicamente. 
Them: Sí. Pero, en este caso, tenemos cuatro. Tendremos que 
Me: ¿O qué vas a tener que generar? Ping, pin, pin, pin, vamos a tener que 
Them: A ver, sí. 
Me: veinticinco. 
Them: O venía acá, O sea, este tiene Ah, está bien. 
Me: Ponle Bien. 
Them: Que no sé si si me deja no ponerle nada acá y que se autogenere. Ah, ok, sí. No, lo pegué todo mal. Ah, no, mira. No, no me deja. Ahí no hay una forma de planearla? No. ¿Y esto qué es? Ah, duplicate robo, ahí está. Ahí va. Ah, sí. Vamos de vuelta. A ver, me da la imagen. Ahora que funciona esto que estoy haciendo, pues, si no son error. Listo. A ver ahora. 
Me: Sí, 
Them: Página uno. 
Me: Sí. 
Them: Página 
Me: Aproveite Vamos, vamos. Tado que accedo al histórico de cuando filtro por fecha, veo las exportaciones. 
Them: Acá no tengo filtro. 
Me: Me falta 
Them: Me parece que es por el front, porque acá sí tengo. Voy a meter una que diga sí, club acá. Desde el veinticinco del siete no entra ninguna. Desde el veinticinco del cero tres, entran todos. ¿Viste el fin? 
Me: ¿Ha probado? Vamos. Bueno, dado que tengo el archivo de liquidaciones enviado por la mantovana, tengo que tener uno ya preparado. O lo tenemos que ir medio preparando ahí porque vamos a ir generándolas 
Them: Sí, hay que, no hay forma de de autoprepararlo antes. 
Me: Bueno, 
Them: Pero es básicamente esto que tengo acá, en este momento. 
Me: Bueno, acá van a poder, o sea, para probar esto, lo pongo así. Que tener, una cuota pagada correctamente una cuota que sobre, una cuota que falte y una cuota que tenga mal el ID. ¿El ID? Y y una cota que tenga mal el name, 
Them: El name no pasa nada porque es 
Me: Okay. 
Them: orientativo. Bien, entonces ahí tenemos cuota uno, cuota dos, Tres. Y la cuota cuatro que tiene mal el ID. ¿Todas tienen la misma plata? Employee installment. Ah, gracias. Ah, está bien. Sí, todos tienen la misma plata. No sé si lo puse bien, pero yo creo que sí. Está, la primera está ok. La segunda va a tener menos plata, la tercera va a tener más plata, y la última tiene mal el ID. 
Me: Bien, hay que tener cuidado con el tema de los centavos. ¿No? Que hay tenemos, ¿cuánto son? Ocho. 
Them: Bueno, ahí metió metió cuatro errores. Dice. No matching installment, este está bien. Este está bien. Partial, este está bien. No modging installment. Ah, porque está mal, copié mal un ID. El de la uno. Esta de acá sería... Ahí está. ¿Qué pasa si reaplico? Ahí, encima provee, porque le metí dos veces. Bueno, ahí importé, dos veces, ¿no? Yo voy a créditos, como este de acá, y acá tengo, mirá, el dar por pagada era lo que decíamos, el cambio de texto no lo hice. Tenemos cuota una pagada. ¿Bien? 
Me: Ok, bueno, 
Them: Que era la que estaba bien pagada. 
Me: ¿Bien? Bien. 
Them: Después tenemos 
Me: Falta lo del lo del botón... Ah, no, lo del botón... Ok, lo pongo... Bien, a ver, tenemos poco con error. 
Them: Sí. Pago con error y pago con error. Este dice devolución, porque justamente este, el pago con error esto es del front, pero en realidad yo tengo, ¿ves que dice devolución?, y este dice dar pagada, porque sabe que uno es de más y el otro es de menos, ¿bien? Tengo acá el monto percibido y el monto total. El monto total debería ser 
Me: Okay. 
Them: ciento once mil cero veintidós, cero veintidós, y acá tengo ciento ciento un mil cero veintidós. Este es ciento once mil y este tiene doscientos once mil. 
Me: Bueno, acá yo te pregunto qué pasa con los centavos, me me vuelve loco eso. 
Them: Los centavos tienen que estar tal cual, porque la lo la comparación es igual igual. 
Me: Igual, igual, ok. 
Them: Entonces, 
Me: Bien. 
Them: por un lado, yo puedo poner pago acá, 
Me: No, nos metamos ahí y 
Them: y registrarle, por ejemplo, que pagó diez pesos. 
Me: No nos metamos ahí, es un escenario posterior. No nos metamos ahí. 
Them: ¿En qué? 
Me: Si no, no... 
Them: Ah, está. 
Me: Pero bien. Ok. 
Them: Está, bueno, habría que traer igual esos escenarios ahora, ya que los tenemos acá. 
Me: Buen punto. Archivo con ok, archivo con formato incorrecto. Importante una 
Them: Sí, que está Debería estar antes que este. 
Me: ¿Cómo dice? ¿El archivo con pago incorrecto? 
Them: Claro, porque yo lo primero borro algo, y después lo lo mando bien, ¿me entendés? 
Me: Bien. 
Them: Vamos a hacer así, por ejemplo, vamos a meterle, no sé, pasa Ahí está. Invalid request. 
Me: Ahí está. Aprobado. Bien. ¿Qué manda? Está visado el PR sesenta y siete. 
Them: Bien. 
Me: Perá, vamos a vamos a ponerle, buenísimo. Aprovecho a consultar. Sí. Aprovecho, aprovecho a consultar. Si está lo de la cuenta para lo del desembolso, Se lo voy a mandar en listadito. Para que quede bien estructurado Si ya tienen el tienen capturado el legajo en el endpoint del usuario. ¿No? 
Them: K. 
Me: Porque me deben el endpoint, o en el endpoint del usuario, de los datos del usuario, o en los datos, vamos a poner así. Aprovechó con su Aprovecho a consultar si está lo de la cuenta, lo de la segunda cuenta para lo del desembolso, para, y si ya tienen capturado el legajo en los datos del usuario. 
Them: Sí. 
Me: Es a vos, ¿no? ¿Qué más falta? Documentos, bueno, se ya eso ya lo estamos hablando aparte. 
Them: No. 
Me: Nada más, ¿no? Nos odia, 
Them: Sí. 
Me: José. Nunca laburó tanto Bueno, continuemos. Entonces, tenemos un escenario bien que la importación cuando termina con, consulto el resultado, entonces, cuando consulto, entonces recibe un resumen con total de registros recibidos, Vos fuiste directo a la al desglose de las de lo de las cuotas. ¿No? De las de los 
Them: Sí. 
Me: ¿Dónde está el resumen? 
Them: ¿Cómo? Resumen. 
Me: Fila 
Them: El resumen, sí, ya lo devolvimos, es es la respuesta del endpoint. Ahí, y si no, bueno, está en logs. 
Me: Ah, pero no no dice, ¿te acordás que en algún momento JP habíamos uno uno aprobado, dos con error? 
Them: Sí, eso va a ser acá en exportaciones. Acá. No, esto es exportaciones, no es 
Me: Es es importaciones, claro. 
Them: A ver. Claro, es, está bien, es lo que igual debería estar acá en liquidaciones, no me equivoco. Acá está, acá está. Eso es. Lo que mostró JP, básicamente, es lindo lo que yo te mostré de acá. Esto. ¿Entendés? No porque lo hice por 
Me: ¿Y no está? 
Them: y no por el coso, pero acá está lo otro, ¿ves? Acá está igual. El log de de todo, de la importación. 
Me: Pará, dejame ahí. Las líneas de cuenta importada y la más reciente, vos lo que fuiste es, te vas al historial de la licitación, o sea, pero no tenés una 
Them: La la vista que vos estás diciendo que que te 
Me: me chupo, nadie es honestamente, O sea, sí, 
Them: JPEG, 
Me: sea, que vendría a ser un un un data analyst de una cuantificación de casos, básicamente, 
Them: ¿El qué? 
Me: Este escenario. 
Them: No entendí. Mirá, es así, lo que, sí, lo que vos me decís que te mostró es esto de acá. ¿No? Yo no estoy subiendo el documento desde acá, sino que lo subí desde el insomnio. Como lo subí desde el insomnia, mostré la insomnia. Él te mostró la respuesta acá. 
Me: ¿Lo ves ahí? 
Them: Porque justamente la trajo de acá. Si no, después tenés liquidaciones, que tenés el load de todo lo que importaste, que fue con errores, ¿ves? Cuota ya procesada, cuota ya procesada, aplicada. O sea, básicamente es esto el log, 
Me: Bien. 
Them: Lo otro era lo mismo que te mostré yo desde acá, desde el insomnio. Que sí, 
Me: O Ok. 
Them: estaría aprobada esta. 
Me: Bueno, en el UAT tendríamos que mostrar la pantalla. 
Them: Tendríamos que mostrar esto de acá. 
Me: Ese es el escenario, el de la fila ochenta y nueve. El de la fila ochenta y ocho 
Them: No, bueno, a a 
Me: el de la fila ochenta y nueve está ok, lo... 
Them: No, bueno, lo consulto, sí, mostraría esto, mostraría el insomnia que está más lindo. O sea, está lindo de acá. 
Me: ¿Cómo va y tal? Me estás peleando, bien, pasa. 
Them: Okay. No, es que el documento o sea, si no sabés lo que tengo que hacer, tengo que generar un CCB y después cargarlo desde acá. Y esta parte yo no la probé, 
Me: Es la Sí. 
Them: es lo mismo, yo lo lo mandaría desde el insomnia. Desde acá, que es lo que acabo de hacer. 
Me: Porque, bueno, si pasa pasa, pero si nos hacemos los boludos, pero alguien nos dice, ojo, lo tenemos que hacer manualmente, o sea, lo tenemos que hacer a través de ahí. 
Them: Creo que sí. No tenemos que entregar el front. ¿Esto es lo del front? 
Me: Bueno, bien, bien, nos ve. Me corrías con eso, no me corrías. Bien. Mostrame lo del resumen del error por error. 
Them: ¿Cuál? ¿Es de acá? 
Me: La el ese. Cuota, esa es la número tres. Me falta una columna me me falta eso. Sí, acá me están faltando cosas. Está en el comentario, que era agregar columnas con el monto esperado el monto descontado, la diferencia positiva o negativa, el número de cuota, 
Them: Eso es esta. 
Me: y la cuota total. ¿Cómo dice? 
Them: Estás mezclando con esto? Estás mezclando con el resumen que nosotros devolvemos después de la importación. Esto decís vos. 
Me: A ver, shop, 
Them: Acá está todo, ¿ves? Expected, discounted, deviation, description, 
Me: Ok. 
Them: Igual, a ver, 
Me: Es el el anterior, entonces, decís. La fila cinco ochenta y ocho. 
Them: Déjame ver, Déjame ver si, a ver. 
Me: No me podés poner un refinamiento mañana a las tres, la puta que te parió, obvio. 
Them: Dejalo con pendiente con Coso y lo agrego acá al lobby, listo. Porque me parece que eso se pierde. 
Me: ¿Se pierde? 
Them: Claro, es un log, pero después se pierde. 
Me: O sea, en concreto es en el en la historia, es me llega el el archivo, lo subo, me dice, estos están bien, estos están mal. Ah, ok, estos están mal, bueno, 
Them: Ah, está acá, está acá, está acá, está acá. 
Me: ¿Qué tan qué tan desfasado está? 
Them: Listo, está está acá. Import Rose, acá está. Acá está. Pay with error. Expected expected ciento once. Está el main number number tres, employee number, deviation amount, description, outcome, discounted amount, todo. 
Me: El deviation amount ¿te dice si es positivo o negativo o algo así? 
Them: No, el deviation amount, justamente, es si 
Me: Pero, entonces, yo le tengo el partial o el over 
Them: Nada, Listo, eso lo mandamos. 
Me: eso se lo tengo que mostrar. O sea, si yo no marco el signo negativo, se lo tengo que mostrar. 
Them: Sí, sí, sí. 
Me: Bien. 
Them: Esto en el front nada más. 
Me: Ah, no no está en el front. Ok, listo. 
Them: Esto acá. 
Me: ¿Cuántos...? O sea, esos dos, te los paso como aprobados, como con con comentario, pero bueno, faltan esas. Bien? Bien. 
Them: Sí. 
Me: Continuamos. Vale. Llevemos, llevemos. Hoy no sé si voy a llegar a, no voy a o sea, no me da el estómago para almorzar algo. Dado que un pago apunta a un legajo o identificador que no existe en el sistema, cuando intento emparejarlo, entonces lo registro como error y continúo con el resto. 
Them: Ya ya lo hicimos. 
Me: Bueno, pero eso ya lo hicimos. Lo ponemos como aprobado. Dado que el monto pagado es igual que la la primera que no esté pagada previamente, cuando lo aplico queda pagada. Este esté aprobado. Dado que en rally o sea, estaría bueno para este caso ir a ver desde el lado del cliente que esa cuota esté pagada. 
Them: Bien, sería esto de acá. Tiene una pagada y dos pagadas con error. 
Me: Ok. La pregunta del millón es, si al front del cliente se le va a mostrar pagada con error. O se le va a mostrar pendiente. Is 
Them: ¿Me estás diciendo a mí? John, 
Me: sí, no, 
Them: No me enfocaría en eso en todo caso, si ellos lo quieren cambiar, que nos digan. 
Me: Bueno, bien, boludo. Bien, Dado que el monto pagado es es menor, entonces, queda pagado con error y se genera descripción, un error con y marcando el monto faltante. Ok, aprobado. Dado que con este pago todas las cuotas del préstamo quedan cuando se completa la aplicación, entonces el préstamo pasa a estado pagado. Con esto, para mí, tendríamos que tener un caso 
Them: Sí. 
Me: que sea de tres cuotas. Porque si tenemos que hacer 
Them: Está bueno eso. 
Me: eso, nos pegamos un tiro. De una gota? 
Them: Una cuota mejor todavía. 
Me: Veo una quota? Nos quedan treinta y siete casos. 
Them: Lo que no sé, si me va a dejar pedir el préstamo, tengo el tag tengo el tag este de mierda. No me va a dejar solicitarlo, a ver. 
Me: Mhmm. 
Them: No. Ya tengo una solicitud. Bueno, vamos a hacer, vamos a dar por pagado este que tenemos. 
Me: Yeah. 
Them: Y listo. Ah, podemos podemos venir acá, Ah, bueno, igual, mirá, vamos a hacer así. Vamos a venir acá. ¿Dónde era? Acá, créditos otorgados. Vamos a ver así, listo. 
Me: Estamos en una hora y media. 
Them: Todavía quedan cosas encima. 
Me: Mira, Mirá cómo podemos ganar tiempo. Porque obviamente tenemos que seguir revisando los casos y no nos va quedar tiempo para revisar eso de lo de la generación de la mantovana. Podemos saltear lo de la generación y podemos ir directo a cancelación. 
Them: Sí, pero pará porque primero tengo que 
Me: Bien. 
Them: terminar de pagar esto. 
Me: Dale. 
Them: Eso es lo que tiene. O sea, sí o sí tengo que terminar de pagar esto. Porque tenemos un solo usuario. Solamente podemos pedir un solo préstamo. 
Me: Solo Solo podemos pedir un solo préstamo, entonces nos conviene tener desde en el cuando hagamos el make fresh 
Them: Sí. 
Me: hacer adelantarnos a tener un caso de tres de tres cuotas. 
Them: Sí. 
Me: Y sí, sí, sí, porque si no, 
Them: Me estoy estoy llamando a la Kaiser. 
Me: ¿Querés que paremos? Paremos, 
Them: No, si no, vamos a llegar. Pero estás, sí. Son en errores, aunque no no sé, son completamente aleatorios, ¿no? ¿Ves? No me está dando el pagado. El refunto. Son cosas Son cosas completamente aleatorias, yo no sé por qué las hace, no hace problema todo el tiempo. Ahí falló, no sé por qué. No te explica ni siquiera por qué falló. 
Me: Ahí te está Ahí te está te está te está puteando con la el pago de las cuotas o el pago del préstamo total? 
Them: No, con el pago de las cuotas. No, 
Me: Okay. 
Them: Aí, mira, do Ves, ahí me la tomo bien, pero cuando le cuando quiero hacer la devolución, ¿Ves ahí, me ¿Ves? Ahí me dejó, ¿ves? No, no me dejó tampoco, no, es una cosa que no... Ahora sí, paga, ¿ves? Sinceramente, es muy aleatorio esto. 
Me: Ahí se, ahí anduvo. 
Them: Sí. Me parece, no tiene sentido. Que pase eso. Es peor, porque se te rompe la mitad de las veces y la otra mitad no. No, o sea, prefiero que se me rompa siempre. 
Me: Claro. 
Them: La computadora chicheando encima La computadora chillando encima. 
Me: No 
Them: Estoy matando, me parece. A las cuatro es con ellos, ¿no? 
Me: Sí, sí, claro. 
Them: ¿Y cómo vamos a hacer esto? 
Me: ¿Cómo vamos a hacer este? 
Them: Estas cosas que se están de la romper, ¿cómo se llama? Está ahí, por por poner cómo pagás las últimas dos cuotas. 
Me: Men. 
Them: Por ahí tendríamos que tener pero bueno, aquí jalón, pendientes. Un botón de pagar todo de una. ¿No? 
Me: Va a quedar medio raro. 
Them: Bueno, ahí quedan todas las cuotas pagadas. No. 
Me: Cuando tu préstamo está pagado, 
Them: No, no, no no le marco como para Alberto. 
Me: Ok. Bueno. Bien. Ok, bueno. 
Them: Ah, status paid, igual, me puso en el crédito. Ok. 
Me: ¿Te gusta más el ¿Te gusta más el insomnia que...? Bien. 
Them: No, no, pero esto es un error porque no me está dejando no me está dejando pedir otro crédito. No me está dejando pedir otro crédito y yo ya lo pagué. 
Me: Porque no te lo Porque no te lo no te lo quita, o sea, la no no te lo, listo, listo, está pagado o bueno, no te no te saca esa 
Them: Claro, pero me lo tiene que sacar, ya está. 
Me: Claro, te lo tienen que sacar, es decir, este este préstamo ya está con está completando. 
Them: Pero ¿por qué me lo está trayendo acá? Todavía? ¿Y por qué ¿Y por qué el filtro este no pasa? Porque ya tengo el préstamo como terminado. Y es porque no me puso la application como terminada. Esto es. La esta tendría que estar como completada. Recién ahí, ahora sí me va a dejar pedir un Sí, ahora me dejo. 
Me: Bien. 
Them: Esto se lo chequeo ahora. Déjalo seguir al pendiente. Se lo estoy chequeando ahora. ¿Qué, con qué vamos? 
Me: Continuamos. Então, pará. Entonces, ¿qué pongo? La cuota queda pagada, lo quedo, lo dijo, aprobó con comentario, rechazado. 
Them: No, la cuota queda pagada, está bien, dado que el monto pagado es menor, está bien. Todas las cuotas del préstamo quedan cuando se completan, entonces el préstamo pasa a estado pagado. El préstamo sí, pero no me está pasando la application, por eso no me está dejando pedir otro préstamo. Si querés, déjalo ahí. Pendiente, Aprobado con comentarios, o pendiente? ¿O rechazado?, ¿qué preferís? 
Me: A ver, funcionar no funciona. Bien. 
Them: Rechazado, dejémoslo. 
Me: La compra estamos ya está en stop pago, llega un nuevo dato para ese préstamo, se genera un préstamo ya pagado y el registro no se modifica. Ese no lo 
Them: Bueno, esto, en realidad, no lo probamos. O sea, está el préstamo ya pagado. 
Me: Ese no lo probes. 
Them: Y, por ejemplo, voy a meter con el insomnio esto, estamos ya pagados. Las cuotas ya están. Y me tiró 
Me: Bien. 
Them: crédito ya pagado. Credit al ready paid. 
Me: Sí. O sea, el insomnia está bien desde el front, no tanto. Bien, bueno, aprobado este. ¿No? 
Them: Sí, no sé. O sea, el front esto no lo tiene yo, anoche volí y tuve que meter un montón de cosas, de front no el front era un desastre, no no sé 
Me: Ya eso 
Them: treinta modificaciones, 
Me: quédate tranquilo, ya lo estamos 
Them: acá, todavía me faltan un montón de cosas, y fijate, mirá esto, 
Me: Sí, sí, sí, sí, sí, sí. 
Them: Ah, no sé qué... 
Me: Desde eso, Desde eso, ya lo estamos charlando, ya lo estamos laburando, no no no te preocupes. 
Them: Mira esto. Mirá. Fijate esto. Comit mío, commit mío, commit mío, commit mío, mío, acá está un commit, de 
Me: Listo. No, no, no, no, no, despreocúpate. 
Them: O sea, hay cosas que, no sé, que hay que mostrarla con la insemnía, porque no 
Me: ¿Cree que lo lo llame por las dudas a a a Irra, me acaba de preguntar. Le digo para que se sume un ratito. Y Bien, bueno, Ok. Préstamos ya pagado, el registro no se modifica. ¿Ese está aprobado? Bien. Dado que el monto pagado es mayor al monto de la cuota. Cuando lo aplico, entonces, la cuota no queda pagada, queda con estatus, oh, con error, y se marca el excedente para habilitar su devolución. 
Them: Sí. 
Me: Este está aprobado, lo habíamos visto. Este, pendiente. Está validado, validado, validado. Bien. Dado que estoy en el detalle del préstamo, panel de diferencias, cuando el botón de carga manual de pago, entonces, selecciono primero al cliente, luego la cuota del préstamo y registro el monto de pago y la fecha, y se crea una dentro los pagos del préstamo. Si no me recuerdo, creo que lo habíamos visto. 
Them: Sí, eso lo Sí. Sí, pero si quieres lo hacemos de vuelta. 
Me: Bueno. 
Them: Ahí otorgué. Voy acá al crédito, que tienen la cuota. Y Y acá registró el pago, ¿es? Como diez, por ejemplo. Registrar pago. Y ahí me tiraba, ¿ves?, parcialmente 
Me: Ah, qué piloto ya lo invité. 
Them: Y ahí me tirás, ¿ves?, parcialmente pagada. 
Me: Parcialmente, paga, bueno, bien, bien, bien, bien. Estos casos son más pesados porque son más sencillos. Bien, Está, yo lo veo bien. 
Them: Sí, sí, sí. 
Me: ¿No? Sí, sí. Bien, vamos, vamos. Dado que una cuota quedó en estado pago con error y con un monto faltante, cuando cargo manualmente el monto faltante, entonces, la la cuota queda pagada y con su fecha. Buen día, Isra, Y Bueno, Y si con esa cuota se sale el préstamo paso a pago. Bueno, estamos acá. Sea, es completar una cuota. Que es completar el pago de una cuota. 
Them: Buenas. ¿O va? ¿Cómo? Perdón. Sí, acá, sí, yo le pongo acá noventa. Registro el pago y la voy dar por paga. Listo. 
Me: ¿Va bien? 
Them: Sí. 
Me: Aprobado. Lo tenemos acá al queridísimo ¿Querés que aprovechemos para revisar algo de lo que rechazado? 
Them: Sí, o sea, está en proceso ahí, lo estoy lo estoy chequeando mientras vemos lo demás. Yo diría, si no, es seguir 
Me: Bueno. 
Them: y mientras tanto corrijo esto. Mientras vos lees, yo voy Yo quiero como que me me empiecen a dar estatus ahora de algo, por le decía a OLE y me pongo a disposición si necesitan algo, no sé, ¿ves que está el ahora? Si hay algo que pueda ayudar o algo. 
Me: Te te paso te paso estatus. Pasamos 
Them: Para que 
Me: o sea, son los casos que, la cantidad de casos que vamos a ver hoy son noventa y dos. Los que vamos a, en el mejor de los casos, noventa y dos. De los noventa y dos, 
Them: Dame un segundo, que tiene esto. 
Me: Dale. De los noventa y dos, tenemos sesenta chequeados, o sea, el sesenta y seis por ciento, de los sesenta hay uno dos, tres que están rechazados, y el resto están aprobados. Hay algunas que quedan pendiente porque hay cosas que nos deben incluso hasta ellos así que esos no los vamos a poder probar. Pero como que te digan, no sé, de de de de noventa y pico, hay cincuenta que ya están aprobados. Nos falta chequear, nos faltan chequear treinta casos. Va a ser largo. 
Them: ¿Y y cómo chequean los casos a todos cien por ciento a mano? 
Me: Sí. 
Them: Sí. Bueno. Seis, sigue de Solía. 
Me: Bien, ese es el el estatus. 
Them: ¿Y los pasos que no pasan es por error o...? O qué? Algunos sí. Algo que está pasando mucho es que es medio aleatorio el tema de las landas, a veces tiran un time out, te vuelve con un estatus quinientos, porque no encontró no no no llegó a levantar la lambda y correrlo, tipo como que me está matando eso un toque la PC a veces en algunas cosas. Porque son muchos endpoints y como que no llega a levantarla y a ejecutarse el tiro, entonces te tira time out o te tira un quinientos, después la volvés ejecutar otra vez y ahí sí anda. Entonces, es como que una pérdida de tiempo eso, porque hay veces que tenés hacer el tiro dos, tres veces, ese es el mayor problema en este momento. ¿Y no tiene forma de mandarle un ping a todas las landas para que se levanten todas antemano, te voy hacer la prueba. Y ya lo hicimos, pero es como que no sé, a veces igual no no las agarra. Ya lo hicimos con Nico, pero a veces, eso, no, no llega a levantarlas igual. Y eso, ¿no todo lo que estás probando ahí está desplegado, porque estás probando el local? Sí, hay cosas desplegadas, pero no sé en qué estado está el deploy. Faltan variables, por ejemplo, que hablé el otro día con o sea, hay cosas que pueden dar error también, pero no realmente no probé el deploy. Ok. Ahí te hago pregunta. Cuando levantas las landa, ¿esa lo estás levantando con...? De ¿cómo lo estás haciendo? Con Docker y SaaS. Ok. ¿Y no hay forma de ponerle un la como tú me dices eso, se levantan la demanda cuando consumes el endpoint, ¿no? Sí, igual le pusimos algo en un momento, que era para que levante todas, pero por eso no funcionó, así que como que ahora ahora estoy con el levantándolas y llamándolas cuando las necesito, digamos. Docker con post up, some build, some local. Start. Ok. ¿No tienes un health check o algo ahí para pegarles algo? ¿Qué? Con un health check o algo para pegarles. ¿Un tiro de de health? Sí, algo que llame al endpoint cuando se levanten y force que se ejecuten. No, tiro por tiro no. Tengo un health general, pero no tiro por tiro. Pues a veces, un simple health tarda un montón, Eso es otra cosa que tiene, ¿ves? Mirá, ya va quince segundos. Y ahí entró. Claro. Hay veces, tardó dieciocho segundos. Hay veces que por el time out entran treinta y está, y esto vos pensás que hizo un health nomás. Bueno. Fijate que tiró memory size quinientos doce, memoria usada quinientos doce, o sea, no llegó prácticamente a levantar nada y cuando hizo pegando en el palo, ya cuando le pedís que procese algo que tarda diez segundos, ya ya no hubiese entrado prácticamente. Ese es el problema. ¿Y Y los problemas que están teniendo por ahora son esos, ¿no?, principalmente, ¿no? Son error de código Ajá. Ok. Y el UAT lo van a hacer en local. Sí. Bueno, ahí, oli, tenemos un tema ambiente, o sea, ¿cómo es que? Yeah. ¿Qué qué combo tú tienes? Nada más. Una m uno pro con dieciséis gigas de RAM. ¿Cuánta landa estás levantando? Uf, un montón. No sé cuántas, pero son como mirá. No sé, serán como cuarenta endpoints. Busca ahí AWS Landa coso de cuánto se encuentra. Eso, solve the function, eso, no, eso, busca eso. Ciento treinta. Ah, esperá, pará, hay muchos que no van. Sí, acá le dice serverless function, Ah, y cinco. Ah, son sesenta y cinco Sí, a veces me me llega al límite de de RAM, por ejemplo. Claro. Más la OCDATA o más lo que sea que se vea, Bien. Bueno, ahora parece ser que va andando bien. El tema es ese, que cuando ya empezás a hacer muchas pruebas, se se colapsa y ya no llega. 
Me: Ahí Algún momento a lo largo del UAT que podamos o o sea, no sé si hacer un make fresh y y arrancar para que esté menos menos sobrecargado. 
Them: Sí, borrar todo lo borrar lo del Docker cuando se rompe, como así a como así a 
Me: Hacemos la gran JP. Si te sirve eso, a mí me alcanza, no sé si lo más prolijo del mundo, pero bueno, obviamente, es lo que hay. 
Them: Sí. Okay. Si no está todo empleado, no sé no cómo ATV no está empleado, o sea, muy muy no hay eso, como una demo esto, no hay a María OOT eso. Mí el UAT tiene que ser en la infraestructura, en en algo que parezca la infraestructura completa y, pronto, acá estás estás probando un montón de cosas que no hay. ¿Vos le pasaste esta menilla a Oli? 
Me: No, todavía no. 
Them: ¿Y qué te parece si en el UAT hacemos un testeo más controlado de lo que les de lo que les mostramos y listo? Y no probar caso por caso. El UATE lo dejamos para nosotros y a ellos les mostramos tipo un happy path de todo, que vean que todo anda, y después nosotros nos enfocamos en el bate es Y no, toca dibujarla ahora, porque no hay chance de que vayan a hacer eso. Veo de juntarme mañana con Gonza, ver el deploy cómo está. Una cosa así. 
Me: Ahí te escribió Gonza, de hecho. 
Them: ¿Ahora? 
Me: Bad, sí, bad moment. 
Them: Bien. ¿Qué te parece así de eso? Un happy path. 
Me: Sí. 
Them: Nosotros. Si ellos no tienen esto, ya igual mirá todo lo que están aprobados, acá 
Me: No, es es 
Them: bastante bien dentro de todo. Pero 
Me: No, eso no me no, ¿viste?, no me tensiona, no me tensiona eso. 
Them: A mí sí. Estoy O sea, prefiero eso que ir caso por caso y y tener estos problemas de entorno y y por ahí Claro, eso no, si nosotros no hemos corrido un UAT completo, nosotros la primera vez a correrlo, no lo haría delante del cliente. 
Me: Bien, el tema no tenemos más tiempo. No puedo pasar el esta 
Them: No, no, pero no la pases, hagamos un happy pass con ellos. 
Me: Ok. 
Them: ¿Quién planilla? ¿Quién planilla? No no tenemos más tiempo con qué. 
Me: No no tengo mucho más tiempo con de de de proyecto, entonces termina el martes. 
Them: Va, buenísimo. ¿Y qué hacemos? ¿No tenemos la infraestructura? ¿No me podía probar todo? 
Me: No, no, no, está bien, está bien. 
Them: Completo de tener tenemos problema de ambiente. El de local, digamos, no es posible correr todo eso local. 
Me: Bien. 
Them: O sea, 
Me: Ahora, si nosotros hacemos solo happy path, bueno, hay que ir a a elegir los escenarios, entonces. 
Them: Quiere que sacar a... Déjame a Marco que pruebe esas cosas, lo hablamos con Nico y con Fefe o algo de eso o o no sacarle tiempo a Marco con estas cosas de gestión? 
Me: Dale, dale, dale, buen punto. Sí, bien. Dale, vamos con con Fefe y con Cos. 
Them: Hablemos con Nico primero, yo no soy de nada y 
Me: Sí, sí, sí, sí, sí, sí. Bien. Bueno, y vamos y después volvemos, entonces. 
Them: Ya. 
Me: Bueno. Vamos, ¿qué sale? Vamos, ¿qué sale? Vamos, ¿qué sale? Listo. Bueno, Vale, bueno. 
Them: Dale. Ahí 
Me: Eso. Good job. Chadi, la madre, bien de tiempo. Yo me estreso. Yo, yo, yo. 
Them: Comandan? 
Me: Myself? 
Them: Se escucha mucho ruido, ¿mirar? El pero no tanto, tranca. 
Me: Sí, los ronquidos de Juanma nomás. 
Them: Vale. Claro. Bueno, ahí estaba con Noly, no sé, vi que estaba la reunión ahí de pregunté al chico del commandant, y no ayuda con algo. Me llamaron con un meet y estaban viendo tema de búate, pero me llamó la atención un par de cosas. Uno, están haciendo el UAT en la local de de de de Marcos, y está teniendo, no sé, con toda la mayoría de los problemas que tienes, sino todos, son problemas de time out, de infraestructura local, digamos, de ambiente, no levanta función, se demora, qué sé yo. Y después, no, no sé, me como que me preocupa que haya un UAT con Perco, oiga, las cuatro y todavía no hemos corrido uno completo y que pretendamos correrlo primera vez frente al cliente, ¿no? Entonces, no sé, cómo Después me dice, Oli, que estamos sin tiempo, que el martes ya acaba, pero todavía no hemos podido hacer un deploy completo de todas las en la infraestructura de ellos y probarla. Entonces, no sé. Yo, personalmente, lo que veo es que no estamos comprando problemas que no son nuestro. Sí, lo que respecta a dev, que fue lo que le pregunté hoy a Marcos temprano, el entorno de ellos faltaba en configurar algunos puntos, por eso no lo podían usar. Y el y la traba que tiene, una era por por recursos en un endpoint puntual, y después la otra era lo que le tarda en levantar, pero eso sí, cien por ciento el el stack que intenta deployer todo en el local. Lo ideal sería con dieciséis GB de run, y son cincuenta y pico de Landa que tiene levantar más o base de datos, a no sé qué. Sí, y de por sí los container que Mac con Docker empieza a morir al toque. Claro. El el tema del entorno OLI, ahí no se poció en la última con con José no estuve. ¿Qué es lo que falta de su lado para poder mostrarlo ahí? Termine de probar los PR, configuración de entorno, 
Me: Lo último que hablamos con José, particularmente, era para lo de el desembolso de las de los préstamos. Eso es lo lo único que que recuerdo. 
Them: Y del del entorno en sí, ¿qué restaría? O capaz que le podemos sumar a Marcos, 
Me: No. No. No. No. Ahora justo está morfando y 
Them: Ah, ok. 
Me: muriendo en el proceso. 
Them: Imagina, 
Me: No sé. 
Them: Imagina, para variar qué es lo que falta de dev para poder usar dev, y que en en sí se tendría que hacer ahí la UAT. Del 
Me: Bueno, sí, 
Them: de nuestro lado está perfecto hacerla, no importa el ambiente, pero sí que pase todo, como un check previo, ¿no? Pero después lo que ellos deberían ver es es en sus entornos, no en en nuestro local, 
Me: Sí, 
Them: por si tenemos algún cambio en local que todavía no llegó, no sería transparente tampoco, ¿va? 
Me: Si le pregunto a Jo, 
Them: Es que antes de preguntarle, capaz que Marco sabe qué es lo que faltaba, entonces la pregunta es un poco más clara después para hacer. 
Me: No lo tengo. 
Them: Me dijo que faltaban unas variables de entorno, y esas cosas, y justo ahora le había escrito el de infraestructura para juntar y ver a ella. Gonzalo, este. 
Me: Sí. A ver, bueno, justo me puso que se iba a comer rápido, bueno, le pregunto igual. 
Them: Bissö I plan to lärn. Pero si faltan PRs por aprobar, y todavía no tenemos el ambiente del se acaba el martes, sé, me parece que hay algo ahí que está que no va a funcionar, ¿no? ¿Qué pasó, Eli? Exprésate. Te veo con... 
Me: Es que no sé, no 
Them: Sentimiento, 
Me: no, no, es que no sé cómo no saltó esto antes. A ver, 
Them: ¿Qué es lo que no saltó antes? 
Me: Esta necesidad de tener el el entorno Porque no, no, no, no me la no me la o sea, no no no me la mencionan nunca. Entonces, 
Them: No, però però, però, un nostro però, né? Ahí discrepa un poco, porque la última vez que yo supe el proyecto, 
Me: Sí, sí, sí, sí. 
Them: estaban con el tema del ambiente, y habíamos dicho que era 
Me: Por 
Them: que era una necesidad el ambiente. O sea, fácil, 
Me: Por supuesto, sí, sí. 
Them: llevamos un bocho de semana y todavía no tenemos un ambiente. Pero bueno. Y después, para entregarles eso a ellos, en en algo que todavía no se desplegó nunca, en un ambiente de ellos cien por ciento, no sé. Por ahí, me Marcos estaba, bueno, no sé, tratando de ir con lo que tenía, tratar de resolver el problema. Pero Ay, ya 
Me: Ok. 
Them: Yo te pregunto, ¿no? Yo... Te pregunto, tú estás al tanto de que el ambiente no está listo y que faltan PRs. 
Me: Sí. 
Them: Supón que el UAT funciona todo ahí. Con eso, si el UAT llegara a funcionar todo hoy local, ¿con eso lo damos por bueno? Y listo, le decimos, mira, esto está, de ahí para allá es tu problema desplegarlo, corra, todo eso, y nosotros el martes ya se acabó el proyecto, nos inyectamos y no hacemos más nada. Ahí para organizar un poco y que Oli no no entre en un colapso mental, 
Me: ¿Está ahí, está ahí, está ahí, está ahí. 
Them: hay dos opciones. Una es, apenas arranque y lo guaté, porque pasarlo de nuevo sí puede ser medio conflictivo, 
Me: Bien. 
Them: pero apenas arranque mencionar que no estar en torno de todavía, que la boatece podría ser en local, pero que por el consumo de recursos de toda la slanda puede 
Me: Okay. 
Them: a generar algún inconveniente. No necesariamente de código, sino de infra. 
Me: Bien. 
Them: Ahí una cosa informarte, Nico, lo que propuso Marco, a mí me parece bien, después lo que tenemos que ver es qué hacemos ahí salió iPhone de él y me menciona el tema del tiempo del proyecto, Lo que dijo Marco es, hagamos un happy path ahora, y no un UAT de que caso por caso de los noventa y pico de casos. Sea, eso es una cosa, Y, de nuevo, si al día de hoy todavía no lo tenemos y pasan sesenta de los noventa y pico, que ya han podido probar, en dos horas y media que queda o menos, para correrlo todo eso por primera vez frente al cliente, no sé, me parece, no está. Dijo, hagamos el local un happy path, de todo, de de lo que hay, y después el bateo lo hacemos, no sé. Sí, eso 
Me: Bueno, puedo es... Sí. 
Them: eso es bueno, porque aparte dudo que te alcancen dos horas, 
Me: Sí, sí. 
Them: para el boate. Porque hoy a la mañana estuvimos, creo que una hora y cuarto, cuando yo me bajé, una hora y media, 
Me: Sí. 
Them: y no íbamos ir ni a la mitad, Encima hay que usar la mano, soy que... 
Me: Bien, bueno. 
Them: Ahí igual, et, esa opción está, bueno, la de que sea un camino feliz, y mencionar lo del entorno. Lo único, sí estaría bueno en cuanto pueda sumarse, Marcos, para ver qué es lo que lo que resta del entorno, o vemos con él y Gonzalo, creo que fue quien le escribió recién, ¿no? 
Me: Sí. 
Them: ¿O leí mal el nombre? Sí. 
Me: Sí, sí, sí, sí. 
Them: Ver qué resta para dejarlo operativo ese entorno. 
Me: Bien. Bien. Bueno, ok, entonces vamos a hacer así, en la reunión de las cuatro, voy a mencionar que esto es en local porque todavía no tenemos el entorno de development en condiciones y con los últimos PR aprobados. Como para tener un entorno estable, lo que planteamos es hacer o sea, para no perder el espacio, una una demo general de todos los casos, o de la mayoría de los casos, necesitamos cuanto antes tener el entorno para poder hacer justamente, Después te tengo que elegir mejor las palabras igual, pero para hacer la validación caso por caso, El lunes, igual, nosotros te supuestamente, vamos a agendar para hacerlo con el ida y vuelta con la mantovana. Y seguramente los plazos se terminen extendiendo porque hay un hay una demora por parte de ellos, por por la entrega de un documento que nunca lo hicieron, tenemos todo ese desarrollo pendiente. 
Them: Bueno, ahí, por eso, el lema con Feifi también, porque después no quiero, pues no sé, yo no en día ahí el proyecto, tú me dijiste así como un hard stop, el martes se acaba esto. 
Me: Sí. 
Them: ¿Suena a a lo que diría jefe? Entonces, no sé, ver bien las expectativas que hay, no sé qué Tú tú mismo me acabas de decir ahora, no sé por qué nadie me dijo que esto era importante. Pero bueno. Si tú piensas eso, no me imagino lo que piense Fefe. Y atajemos eso antes de de que llegue el martes. 
Me: Sí. No, no, no, no, no me no me callo la ficha. 
Them: Sí, 
Me: Lo de tendría que haberme saltado antes. Bueno, 
Them: No. 
Me: No sé si si es para la mía, es 
Them: No, eso 
Me: tendría que haber, tendría que haber sabido, no sé. No lo sé, no lo sé. 
Them: No. 
Me: No sé, no 
Them: En ese caso yo no buscaría de quién es el tema, porque 
Me: No, no sé, no sé. 
Them: o sea, así mismo, como Néstor mencionó, yo tampoco me di cuenta de esa parte para mencionártelo antes, ¿sí? Entonces, es algo más más general. El tema es ellos saben que todavía no han el documento Claro. Ambiente, y que tienen Que si con poco más para atrás, Tuvimos un montón de conversaciones sobre el tiempo que tomaban los PRs, se nos acumularon un montón de PR, hubo que hacer algún retrabajo para que pudieran revisar 
Me: Sí, sí, sí, sí. Sí, sí, sí, sí, 
Them: no sé, te digo las cosas que yo me acuerdo nada más al principio, ¿no? 
Me: Sí, sí, sí, sí, que son todas ciertas, sí, sí, sí. 
Them: Por eso, entonces, sí, nada. Pero lo que sí, hablar hablara eso a Confecio un poco que lo que sea que vaya a pasar, lo y que no se no se acabe en... Ah, pero el martes hay que acabar todo con todo el techo y todo en AWS, y el documento que no mandaron tiene que estar implementado. 
Me: No. No, no, no, lo del documento, hacelo a un costado, 
Them: Es una una reducción al absoluto, 
Me: Sí, sí, sí, sí, sí, sí. 
Them: digo, en alguna versión de eso. Sí, no terminemos en alguna versión de eso. 
Me: Bien. Bien. De... ¿Cómo se dice? A ver, ahí está. Buenas. 
Them: Ahí Ah, 
Me: ¿Cómo va? 
Them: Todo bien. 
Me: Bueno, sí. 
Them: No, falta o sea, testear, ver qué onda, cómo está, porque no sé hasta dónde está deployado, no sé hasta dónde deployó, tipo, no sé, las variables tampoco sí las puso, que las que le pedí el otro día. Por eso, o sea, a mí me da cosa probar en un entorno que no probé a dos horas de la demo, por eso, pero Básicamente, sería eso. 
Me: Ok. Si mando la pregunta, ¿está el entorno disponible como para poder 
Them: No, ahí ahí hablo 
Me: realizar el o sea, medio medio fantasma. 
Them: Sí, deja que ahora le pregunto a él si todo lo último y listo. Cuando entre en la llamada... Y me fijo de que el front, de ponerlo apuntando a 
Me: Bueno, Bueno, otra cosa que podemos hacer es, nosotros, por lo menos en local, te te rezando, ¿no? Sabemos que los que que gran cantidad de los casos, o por lo menos hasta hasta más de la mitad, funcionen bien. Yo con eso, y además va a llevar más tiempo, que que en la prueba que hicimos hoy, yo con eso puedo decir che, continuamos mañana, o puedo ganar un poquito de tiempo. Si alcanza ese tiempo, felices. Si no alcanza, me dicen y, bueno. 
Them: Creo que Pero que, espera, tú que aunque el alcance el tiempo, ¿para qué? 
Me: Estoy estoy evaluando opciones, acá me me dicen ustedes igual, 
Them: Sí, sí. 
Me: ¿Para qué? Para que validemos que el entorno esté perfecto. Correcto, con las variables, con con todos los PR subidos, 
Them: Si me preguntás la opinión a mí, yo te diría que hagamos un happy path con ellos, 
Me: Oh, yep. 
Them: como dijo Juampi el otro día, que tenía razón, Juampi, Norberto. ¿Qué puso? Si el uva te lo propusimos nosotros, 
Me: No, no, tiremos el tiro en el pie. El tema es que ya 
Them: No, claro. 
Me: sí. 
Them: Tá, bro, eu hasta el martes tenemos tiempo para entregarle. Ellos en paralelo podrían estar haciendo su propio UAT porque tienen todo el código, y está corrigiendo todos los PRs, en teoría. Entonces, en realidad, si el lunes o el martes se les ocurre que falta algo, no sé, lo corregimos, en todo caso, pero en realidad ellos podrían estar no es que no pueden. O sea, si no están haciendo es porque no o si no están testeando y falta algo, es porque realmente no lo no lo han testeado. No por otra cuestión. Entonces, creo que 
Me: No sé si me gustaría jugar esa carta, porque de de 
Them: Ahí está, Gonza, ahí voy con Gonza, ahí, bueno. 
Me: Bueno. 
Them: Bueno, ahí eso cambia un Bueno, ahí eso cambia un poco, eso no lo sabía, o sea, el es algo que propusimos nosotros. 
Me: Correcto, sí, sí. 
Them: Bueno. 
Me: No no me arrepiento 
Them: Bien. No, no, 
Me: No no me arrepiento de dar la propuesta, 
Them: No, no, io se, però 
Me: Porque saltaron ochenta mil millones de cosas, 
Them: pero mantengámoslo como algo interno, digamos, y que sea nuestra métrica de calidad de lo que estamos entregando y completitud, versus lo que hay que mostrar hoy. Claro. Algo 
Me: Claro, por Claro. O sea, yo la reunión la tengo que agendar como UAT, Entonces, le digo, ah, esta reunión agenda UAT, no va a ser UAT. 
Them: bien. Ahí No necesariamente, no no sé, capaz que parece medio oscuro lo que voy a decir, pero si vos arrancás mencionando el tema de que no es el entorno para hacer el UAT en dev, que es como ellos lo deberían ver, ¿sí? Porque el el UAT que se hizo sobre el local 
Me: Sí. 
Them: ahí le mostraron la pinilla, con todos los casos que ya se probaron y pasaron, no sé si ellos ya vieron esa planilla, 
Me: No. 
Them: Ok. Con todos esos casos fueron sobre local y pero en en local tenemos el tema de infra, que no le suele dar la la sangre a a la PC local para correrlo, entonces, que sepan qué casos probamos, si ellos tenían algún UATE especial, o sea, algún caso puntual que no esté dentro de ese UATE, y que ahora en esa meet se va a hacer el camino feliz de de lo que proponía Marcos, y una vez que esté en el entorno de sí podemos hacer esa misma sobre en conjunto con ellos. Eddie. 
Me: Okay. 
Them: El enfoque del nombre Lamit, el tema es que no sé qué como lo ve ahí, sea, porque yo le acabo de decir, mi cerebro suena bien, pero no sé si Sí, yo banco, o sea, no no hemos podido, no no no no puedo, por eso dije ahorita en poniendo un problema, encima si lo va estar lo propusimos nosotros. No todavía. Estamos poniendo comprando en un problema que no es nuestro. 
Me: Bien. 
Them: Poniéndonos la barrera de, ok, tengo que poder correr lo mismo que planificado, correr en esa infraestructura, en la computadora que sea que tiene esta persona, en sé qué. Si no, no sé, mínimo, démosle una instancia en AWS a a este, pagar por Quartz, con más RAM y no sé qué, y un SSH, y que lo corra ahí arriba, ¿no? 
Me: Claro. 
Them: Pero Ahí vemos que Con esa versión only, te te sentís cómodo, 
Me: La tengo que preparar. La quiero hasta escribir Tengo que hacer, bueno, claramente tengo que hacer mención al al entorno, Obviamente, necesitamos que vuelva después Marcos a ver si tiene alguna y verdad, revelada con la reunión que está teniendo ahora. Las razones de ambiente, 
Them: La cosa es simple, 
Me: el entorno no está listo del todo, sí. 
Them: o sea, nosotros tenemos un UAT, planificado, que no lo hemos podido correr completo, porque, y hasta ahora tú dime si me equivoco, 
Me: Sí. 
Them: todo lo que nos nos falla, todos los temas que tenemos son temas de 
Me: Sí. 
Them: ambiente. Sea, ¿por qué? Porque tenemos que correr cincuenta y pico de Landa, la la la no sé qué, no sé qué, en una máquina con dieciséis sierras, y no le está dando la sangre, así Taraní. Entonces, todo bien, nosotros queríamos hacer esto, pero no lo hemos podido hacer. 
Me: Bien. 
Them: Sería ideal que podamos hacer esto en el ambiente de development, que no está listo todavía, y para terminar de hacer cosas, o sea, ese UAT lo pensamos hacer, entiendo ahí esto es lo estoy aportando yo, si no es verdad me lo dicen, este UAT lo estamos pensando hacer, con Perry, que todavía no están aprobados. Con los cual ni siquiera para hacer un UAT, ¿no? Entonces, hagamos un end to end de las cosas ahora, y necesitamos para cerrar esto en los tiempos que quedan, poder correr los noventa y pico de casos del UAT en un ambiente de 
Me: Bien. 
Them: development y y ahora que está todo bien. Porque hoy todavía no hemos podido integrar todo 
Me: Ok. 
Them: por eso... 
Me: Okay. 
Them: Y por eso te digo, eso se lo tenemos que decir a Fefe, porque hoy no hemos podido integrar todo, quiere decir por eso hay que controlamos algo. 
Me: Sí. 
Them: ¿No? 
Me: Ok. 
Them: Sí. Vaya, yo no sé qué tiempo, qué es lo que pasa con esta gente que necesitan tanto tiempo para el ambiente eso, pero bueno. 
Me: Bien. ¿Lo llama jefe? 
Them: Aquí. Aquí. Aquí. Chegó, ¿Bastor? O todavía no? No, todavía. No, tenemos que esperar a las vacunitas y eso. 
Me: ¿Cómo 
Them: Pero ya 10 en cuenta de Instagram, así que... Bien. ¿Y TikTok? 
Me: ¿Cómo, cómo, cómo? ¿De 
Them: Después pásame y le digo a yo que Frenchy Brothers lo siga. Dale. 
Me: Bien. Buenas. 
Them: Buenas. Bueno, Gonza me acaba de pedir básicamente, que hagamos un cambio en todas las lambdas. 
Me: No? 
Them: Gracias, Gonza. Por Sí. Me pidió perdón, porque no lo vio antes, me dice. Básicamente, como que no le gustó que que la separáramos, como están separadas, que las separamos así desde el día uno, What? Porque hace como... Antes teníamos veinte lambdas, ahora son sesenta y pico, entonces, dice que le está explotando el flujo de CICD, y que encima es como que se les está yendo en costos o se les va a ir en costos, por el tema de la compañía. Por la cantidad de lambdas y que merciemos Pero si vos no pagas por cantidad de lambdas vivas, o sea, que existe vos vos, sé, dijo que que es por las auditorías de Amazon, que como que cada lambda le dispara una auditoría, entonces, son sesenta auditorías, y que, por ejemplo, podemos juntar los get get delete, post, put, no sé, lo que sea que tengamos, y agruparlos, mercharlos por por coso y que sea una misma landa para todo. Ok. Y que no está deployado ni en pedo lo último. Sea, está deployado cuando teníamos veinte lambdas, o sea, donde quedó el el el ambiente aquella vez, ahí quedó, nunca más se volvió a deployer. 
Me: Me Me está jodiendo. 
Them: Bueno, ahora sí, 
Me: Bueno, A hora? 
Them: Ahora sí 
Me: Ahora sí. 
Them: Sumá los jefes y, además, básicamente, la auditoría de Amazon te acaba de facilitar un montón, el pitch de antes. 
Me: Sí. A ver, Bien. Ok. 
Them: ¿Y es lo que me escucharon y me piden que le pase TikTok o así que pasarle nomás. 
Me: Vivida. 
Them: Sí, anyway, ahí. Tiene la oreja para la otra, parece. Voy a hablar más bajita, si no me escucha. 
Me: A ver, vamos así. Antes de empezar, le queremos dar contexto de cómo planteamos esta sesión. La idea de hoy es mostrarles un recorrido end to end de los flujos principales para que podamos validar juntos el funcionamiento general, Hoy no tenemos el entorno de development completamente estable con los últimos ajustes integrados. Ahí podemos agregar un gran paréntesis en base a lo lo que acabas de decir, Marcos. Así que para, sí, 
Them: Podés arrancar 
Me: Antes de empezar, sí. 
Them: Arrancá de nuevo, por que capaz que cambiaría el inicio. 
Me: Antes de empezar, le queremos dar contexto de cómo planteamos esta sesión. La idea de hoy es mostrarles un recorrido end to end de los flujos principales para que podamos validar juntos el funcionamiento general. Es el primer párrafo. 
Them: Bueno, es que ahí ya le estás diciendo que vas a hacer una UAT, en realidad. Y no te entendí mal. 
Me: Okay. 
Them: Yo le diría, 
Me: Recorrido general, sí. 
Them: es mostrarle el end to end que nosotros verificamos en nuestros entornos, ya que debu no está disponible. ¿Y lo mostrás la planilla? Le mostrás el en tu venda en vivo. 
Me: Ojo, porque la planilla no la tenemos todavía toda completa. 
Them: ¿Y si lo ponés todo en verde ahora y nadie se entera? 
Me: Pero lo pongo todo en verde ahora y a la mierda todo. Sí, sí, sí. 
Them: Enveré una copia. 
Me: Me gusta. 
Them: Ah, vos decile de no compartir pantalla y probarlo, sino mostrarles la planilla? Una, lo que hablábamos antes es mostrarle la planilla para que sepa qué fue la UAT que se estaba lidiando en local, y, si ellos quieren, lo que vos habías recomendado, Marcos, que estuvo bueno, es hacerle un happy pass básico, ¿sí?, no toda esa planilla. Porque aparte dos horas no alcanzan para hacer esa planilla con, y menos con un cliente te va a empezar a preguntar ante cada punto. Sí. 
Me: Bueno, Entonces, la 
Them: ¿Está bien? 
Me: ok. Marcos, vos que estás en la planilla, ahí generé una que dice UAT, voy a pasar todo verde, salvo 
Them: Et parà, 
Me: las cosas que Sí. 
Them: ¿Por qué no te hacés una copia si no pierdes el track real? 
Me: Hice la ¿Y se la duplique la la hoja? Duplique, duplique. Sí, sí, sí, sí, sí. Y oculto la la la anterior. Oh, duplico, esperá, no. Ser mejor, vamos a ser más prolijos, duplicar. Bueno, 
Them: Ahí una cosa que Ali entienda. O sea, lo que pidieron fue cambiar código, y mucho código. 
Me: Okay. Sí, sí, sí, eso me quedó clarísimo, 
Them: Okay. Claro, el el mayor tema es que ahora esa boté hay que hacerla completa nueva, o sí, con todos esos cambios. Y ahí Porque don van a cambiar los Claro, donde antes tenías un handler por lambda, ahora vas a tener uno agrupado que resuelve varios, y el el movimiento de código es en todo el proyecto. 
Me: Bien, Gracias, Gonzaí. Excelente. 
Them: Gonzo es nuestro DT de Inglaterra hoy. 
Me: Ah, Tal cual. Hermoso. Tengo alguna filtrada, algún campo filtrado. Acá. Bueno, bien, hago eso. Continuamos, entonces, con el Hoy todavía no tenemos el entorno de deepvelopment completamente estable, pero los últimos ajustes integrados, hay que agregar, entonces, eso es lo de el último cambio solicitado. Así que para aprovechar, viene el espacio, vamos a hacer esta demo sobre local, les aclaramos, es que en realidad ya ni la puedo hacer, en realidad, porque en base a esto que me que que nos dice Gonza es, me acabás de cagar la boaté. 
Them: Sì, no. Porque en teoría él no te está modificando lógica. Él te está modificando la implementación nada más. Pero después sí la vas a tener que probar para ver que no se haya roto nada. 
Me: Mis 
Them: Claro, pero lo que sí va a cambiar es todo el frontend que va a usar hacer la UAT. Ah, eso sigue yendo a código, pero bueno, en teoría, los casos de la UAT no cambian, lo que te cambian son los resultados verificados que tienes, ¿no? Claro. 
Me: Claro. Les aclaramos esto porque puede parecer algún comportamiento propio del ambiente y no necesariamente del código funcional. En paralelo, nosotros ya venimos avanzando con una validación detallada de casos, y la idea es continuar esta validación esta validación fina caso por caso, apenas tengamos el entorno listo y estable. Si ustedes tienen algún caso puntual que quieran priorizar o mirar con más detalle, lo sumamos. Pero bueno, esto es antes de la última verdad. Lo necesito, jefe. 
Them: Ya está arreglado el tema de los pagos de hoy, Oli. 
Me: E Sin duda, esto es algo que podría haber surgido al recontra principio, ¿no?, lo de los lambas. 
Them: El segundo día de que empezamos el proyecto. 
Me: Bien. 
Them: Claro, sí. Y además, ojo, porque 
Me: Bien. 
Them: si lo que dice mí, que no estaban mirando esto, o sea, el foco en otra cosa, fue que lo que es no han visto nada de Marco. No, no, no han visto nada, sí. Los los PRs, por ejemplo, cada vez le mando PRs más grandes a y el otro día me mandó uno, tipo, me me corrigió cuatro en cinco minutos. Y los cuatro tenían, tipo, un comentario como blocker, no sé, cambiarle el nombre a la migración. O sea, y Claro. 
Me: Lo voy a tener que prender fuego de no bajó. 
Them: No, no, no, porque si Ah, es es típico de que tienen su sus prioridades y sus cosas y está esto acá, lo único que nosotros sí tenemos que tener esa información y esa estadísticas para... Para saber, para pueda salte el tema con Fitbit, Fitbit tenga argumento digamos, wording, ir si si, bueno, mira, tuki, tuki, tuki, tuki. 
Me: Sí. 
Them: Tal cual. Cual. No sé si, bueno, no sé, a lo mejor, Fefe no sé cuánto entiende eso por ahí, con Juampi, lo puede se lo puede traducir al Al Yes. 
Me: No, en no es no nos prestaron atención, y ahora que nos prestan atención, saltan cosas que deberían haber hecho cuando arrancó. En el momento en donde estaba. ¿Necesitas estirarlo? Estirémoslo. Pero bueno, buting boss de bus. 
Them: Oh, te lo dejamos acá y tú te haces cargo de, si no quieres pagar más, bueno, tú te haces cargo de aquí, ahora en más, y 
Me: Sí. 
Them: el esposo, ¿no? Pero había unas precondiciones poder entregar esto. 
Me: Sí. Bien. Bueno, 
Them: No. 
Me: En la 
Them: No, comunicar y ver qué dicen. 
Me: sí, sí, sí, sí. 
Them: Y ahí esto que dijo este muchacho, bueno, no sé, se podría empezar a hacer en un branch o algo eso, pero hay que confirmar bien, porque a lo mejor cuando van arriba dicen, no, ¿sabes qué? Ahora ahora no vamos a hacer eso, porque no sé cuánto tiempo toma reescribir todo eso, la UI y ver qué Pues lo peor que tiene, que son cambios boludos, sea, son cosas que no digamos, que no salta en el compilador, son temas de integración. 
Me: Como solución, no sé si es la palabra correcta, ofrecible, Nosotros estamos usando un playground para facilitarnos la exposición, la demo, etcétera. Dado que teóricamente, no van a usar el playground. Pero bueno, al fin y al cabo, terminó haciéndose en en Angular. 
Them: Mhmm. 
Me: Si les sirve, se lo quedan, si no les sirve, 
Them: Mhmm. 
Me: no lo usan. Pero lo comprometido es el insomnia. El API, perdón. 
Them: Penso che cambiarla también porque no, 
Me: Eso 
Them: van a cambiar todos los Van a cambiar todos los paths, claro. 
Me: Okay, listo. Gracias. Pero es una solución un poquito más más corta, que entre es lo es exactamente lo mismo. 
Them: Ah, lo mismo. Es lo mismo. 
Me: Ok. 
Them: A ver, si no tienes que cambiar el el primero, no cambiar el playground, quiere decir que nosotros no tenemos forma de probar como hemos venido probando hasta ahora, integrado todo. Lo cual es más que más que ahorrar tiempo es peor, ¿no? Ahora imagínate que la prueba hay que hacerla por ¿cómo se llama?, un Postman, el el Insomnia me lo paró en k s, y es un humano el que tiene que agarrar lo del que está, la respuesta, copiar, pegar el ID, no sé qué, o sea, eso, hacer eso para noventa casos, sé. Acuerdo, estoy de acuerdo. O sea, altura, y es más, con el UAT, y viéndolo en el front, para mí están saltando que por ahí no nos habíamos dado cuenta que una clave. O sea, yo creo que sí, que hay que hacerlo Pero bueno, no sé. 
Me: Ahí le manda mensaje al WhatsApp. 
Them: No sé como cuándo, dónde dónde y por qué. Pero de ti, me namare. Claro. Yo no no sé o sea, para mí el front habría, que hacerlo, Pero bueno. Más tiempo humano no No, es que esta este cambio va va a requerir otro sprint más, así que se va a tener que estirar, o sea, lo del martes no hay forma de llegar. 
Me: Que de todas maneras ya se tendría que estirar por lo de los documentos. 
Them: Claro. 
Me: O sea, ya ya se los confirmó. 
Them: Por eso y por toda la en realidad, todos los atrasos que fuimos teniendo desde un principio, cada uno de esos sumó una semana también. 
Me: Acá va a venir jefe y va a decir, bueno, enlistemos todos y cada uno de los de los atrasos que fuimos teniendo. Me los me los sé de memoria igual, No se preocupe. 
Them: Yo igual intentaría ir por las buenas primero, no sé si es posible o no. 
Me: No, no, no, no, obvio, pero la carta la tengo que tener. 
Them: De decirle c atrasemos el o agregamos un sprint más, listo, pumba. Ah, no, pero ¿por qué? Y ahí sí le estirás todo el... El berretín. Pero si no, no, no lo tiraría de uno. 
Me: Qué bronca, qué bronca. Le pusimos amor, che. 
Them: Oh, Pero ojo, porque 
Me: Bueno, no no Sí, sí, sí. 
Them: el 
Me: Sí, sí. 
Them: el tiempo entregable estuvo perfecto, no no hubo una falla. 
Me: No. No. 
Them: Pues sí, 
Me: Bueno, estamos estirando 
Them: Igual, 
Me: ¿Cómo dice? 
Them: Yo lo siento como una derrota igual. 
Me: Estamos en penales todavía. Estamos en penal, estamos en 
Them: No, no, no sé si derrota. O sea, la única métrica de un proyecto no es que se acabe en el tiempo que se dijo no sé cuántos meses antes. Eso es. Impensado. 
Me: Si se logra el valor si los usuarios usan, Bueno, no me contestan, Feche. Bueno, cuando me contesten, les aviso y vamos. 
Them: Далее. 
Me: Listo. 
Them: Dale. Dale. 
Me: Bueno. Gracias, chicos. Chau, chau. 
Them: Una hora
