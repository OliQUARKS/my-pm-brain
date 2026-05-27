# Source: WhatsApp — Preguntas Pendientes Resueltas (27/5/26)

## Participants
Olivier Luce (PM, Quarks), Sebastián Cárdenas (PO, PERC)

## Chat Transcript

**[27/5/26, 1:53:21 p. m.] Olivier Luce:**
te mando preguntas pendientes:

1. IVA en cancelaciones — ¿confirmamos que aplica según el Excel (flag B8 = 1)?
2. Cancelación anticipada — ¿confirmamos que el monto se precalcula en el template o se calcula on-demand al momento de la solicitud? me suena raro porque si el usuario la paga bien hasta el final, porqué le cobro la cancelación?
3. Documentos HTML — ¿cerraste con Patricio si son dinámicos (con variables del usuario) o estáticos?
4. Empleados PJ — confirmar si están discriminados en los datos que llegan, para poder que identificarlos en BO
5. PRs pendientes — tenemos pendiente el reporte de Jose
6. Plazo de desembolso — vos sugeriste 24hs. y marcos no confirmó jeje
7. Reporte para La Mantovana — ¿pudiste hablar con Isis al final?

**[27/5/26, 2:10:50 p. m.] Sebastián Cardenas:**
7. hable con ella, quedaron en pasarnos los excel para ellos subir las cuotas para que sean descontadas y el informe para que se puedan descargar.

**[27/5/26, 2:11:12 p. m.] Sebastián Cardenas:**
6. no hay confirmacion aun. lo mando por mail

**[27/5/26, 2:17:34 p. m.] Sebastián Cardenas:**
5. te lo averiguo
4. si la persona juridica a la cual pertenecen es un dato que ustedes nos den? no entendi
3. No tengo respuesta. me preocupa, podras pedir una reunion con todos los interesados? asumo que son, nicolas ortiz, patricio ertola, uds y yo

**[27/5/26, 2:18:08 p. m.] Sebastián Cardenas:**
2. es una decision de ustedes. lo que sea mejor. nosotros no tenemos un requerimiento

**[27/5/26, 2:18:39 p. m.] Olivier Luce:**
good

**[27/5/26, 2:18:46 p. m.] Olivier Luce:**
del 1 vemos que es configurable
eso me hace ruido

**[27/5/26, 2:23:17 p. m.] Sebastián Cardenas:**
estoy rehaciendo la tabla para que les quede bien
es mas simple
de lo que estamos pensando

**[27/5/26, 2:24:15 p. m.] Olivier Luce:**
De la 4. La cuestión es que ustedes tenían la necesidad de poder filtrar las personas jurídicas ¿no? Vos me dijiste igual que no van a tener ningún cambio en la experiencia, que va a ser todo igual.
Pero al fin y al cabo mi pregunta va más desde cómo manejamos el dato en back. Nosotros, en los datos que nos envían ustedes, tenemos identificado el campo que dice que es una persona jurídica?
Por qué digo esto? Porque si no me recuerdo una de las criterios de aceptación era poder filtrar por persona jurídica, persona física. Por eso.

**[27/5/26, 2:24:23 p. m.] Olivier Luce:**
joya

**[27/5/26, 2:26:54 p. m.] Olivier Luce:**
el punto 2… decidir sobre si incorporar o no la cancelación al valor del préstamo?
jajaja

**[27/5/26, 2:27:03 p. m.] Sebastián Cardenas:**
esto tambien deberia resolverse despues de estar reunion con nicolas y patricio. sumaria a marcos tambien

**[27/5/26, 2:27:04 p. m.] Olivier Luce:**
dejame verlo con fefe

**[27/5/26, 2:27:50 p. m.] Sebastián Cardenas:**
mmmm no es al valor del prestamo no lo entendi asi. entendi la pregunta como "precalculamos o lo calculamos en el momento a lo que cuesta precancelarlo?" o me equivoque

**[27/5/26, 2:28:34 p. m.] Olivier Luce:**
en el excel, en el cálculo del préstamo está tenido en cuenta el porcentaje de la cancelación
perdón, la mora

**[27/5/26, 2:29:34 p. m.] Sebastián Cardenas:**
en que parte? la parte de precancelacion? ya te dije lo estoy rearmando, es mas simple. si ves el excel hice un sheet nuevo. solo tengo que consultar si se cobra algo de los interese futuros como penalidad o no
la mora si
se cobra como un adicional jajajaja es un % extra un chiquitin especial

**[27/5/26, 2:30:10 p. m.] Olivier Luce:**
pero si el tipo la paga en término
jajajajaja
cómo es eso?

**[27/5/26, 2:30:19 p. m.] Sebastián Cardenas:**
good luck
es parte del costo.
no hay devoluciones de nada

**[27/5/26, 2:30:22 p. m.] Olivier Luce:**
si es así, listo el pollo
jajaja
perfecto
