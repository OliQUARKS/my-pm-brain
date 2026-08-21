# Pestaña 1

# Briefing PRE — Loginet — 2026-08-19

**Cliente:** Loginet (razón social: LoginetSA) **Contactó:** a preguntar — el input recibido fue únicamente el nombre del cliente y la URL de su web (`Loginet https://loginetsa.com/`), sin quién hizo el contacto ni por qué canal. **Asistentes Quarks:** a preguntar — no provisto. **Asistentes Loginet:** a preguntar — no se identificó ningún nombre propio en la web pública ni en el input. **Página del cliente:** loginetsa.com **Disparador declarado:** a preguntar — el input crudo no incluye el motivo del contacto ("me llamó tal persona porque tiene tal problema"). Este es el gap más grande de este documento: todo lo que sigue está inferido de la web pública de la empresa y de conocimiento de industria, no de nada que el cliente haya dicho todavía.

> **Nota de proceso:** con un input tan mínimo (nombre \+ URL, sin trigger, sin asistentes), este documento se apoya casi enteramente en investigación externa (web del cliente \+ búsqueda de industria). Todo lo que no sea observación directa de la web pública está marcado como interpretación o como gap explícito. La reunión de briefing en sí debe cerrar la mayoría de los huecos de este documento.

---

## 1\. Contexto de empresa y rubro

**Observación (web pública, loginetsa.com).** Loginet es un operador logístico argentino especializado en comercio exterior: transporte marítimo, aéreo y terrestre, gestión aduanal y depósitos fiscales. La web menciona explícitamente servicios de consolidación/desconsolidación de mercadería, exportación de perecederos y carga general, transporte multimodal, y asesoría en documentación de comercio exterior para el despacho aduanero. La empresa se presenta como fundada por profesionales con trayectoria en el mercado local — la web da cifras distintas según la fuente (una versión dice "+25 años de experiencia", otra referencia externa dice "+15 años"; **a confirmar** cuál es la correcta).

**Observación.** Mencionan tres pilares corporativos ("Conocimiento, Conducta, Actitud proactiva") y un "servicio inteligente que se adapta a las políticas y estrategias" del cliente, además de "acuerdos con socios estratégicos a nivel global" sin nombrarlos.

**Interpretación.** Loginet es un **operador logístico / freight forwarder de tamaño chico-a-mediano**, no una naviera ni un despachante de aduana per se (aunque ofrece el servicio de gestión aduanal, probablemente vía despachante asociado — **a confirmar**). Vende principalmente a empresas que exportan/importan (perecederos y carga general), sin un vertical de cliente único declarado. (chat, no artefacto — inferido de la web, 2026-08-19)

**Gap.** No se sabe: tamaño del equipo, facturación, volumen de operaciones mensuales, si tienen oficinas fuera de Argentina, ni si el "acuerdo con socios estratégicos globales" implica partners tecnológicos o solo comerciales/navieras.

## 2\. Glosario específico del cliente y del rubro

| Término | Significado en este contexto |
| :---- | :---- |
| **Freight forwarder / operador logístico** | Intermediario que organiza el transporte de mercadería entre exportador e importador, sin ser el transportista final. Rol que ocupa Loginet. |
| **Despachante de aduana** | Profesional matriculado habilitado para representar al importador/exportador ante la Aduana. La web de Loginet no aclara si tienen despachante propio o tercerizado — **a preguntar**. |
| **Depósito fiscal** | Recinto habilitado por AFIP/Aduana donde la mercadería permanece bajo control aduanero antes de nacionalizarse o exportarse. Loginet lo ofrece como servicio ("red nacional de alianzas"). |
| **Consolidado / desconsolidado** | Agrupar cargas de varios clientes en un mismo contenedor/envío (consolidado) o separarlas al llegar a destino (desconsolidado). Servicio explícito de Loginet. |
| **Multimodal** | Transporte que combina más de un medio (marítimo \+ terrestre, por ejemplo) bajo una sola gestión. |
| **VUCEA (Ventanilla Única de Comercio Exterior Argentina)** | Plataforma estatal que centraliza trámites de comercio exterior entre organismos públicos. Prorrogada hasta el 31/12/2026, con foco en interoperabilidad. (industry-knowledge) |
| **VUMA / VUA** | Ventanillas únicas sectoriales en desarrollo: VUMA para operatoria portuaria/marítima, VUA para el equivalente aéreo. (industry-knowledge) |
| **Declaración Aduanera Digital / Carpeta Digital** | Iniciativas de Aduana Argentina hacia un esquema 100% electrónico de declaración y documentación del operador, en curso durante 2026\. (industry-knowledge) |
| **OEA (Operador Económico Autorizado)** | Certificación aduanera que simplifica controles para operadores de bajo riesgo verificado; su programa se está ampliando en 2026\. (industry-knowledge) |
| **OLES (Operadores Logísticos Habilitados)** | Figura que consolida la operatoria de depósitos/logística habilitada ante Aduana. Relevante si Loginet opera depósito fiscal propio. (industry-knowledge) |
| **MIP** | Nuevo sistema en desarrollo por Aduana para regímenes especiales (importación temporal, drawback, zonas francas). (industry-knowledge) |

## 3\. Dolores del rubro y del caso

**Del rubro (interpretación, industry-knowledge).** El comercio exterior argentino está en medio de una ola de digitalización estatal fuerte para 2026 (VUCEA, VUMA, VUA, Declaración Aduanera Digital, Carpeta Digital, MIP, expansión de OEA, y discusión de un nuevo Código Aduanero). Esto típicamente genera dos tipos de dolor en operadores logísticos chicos/medianos: (a) presión para digitalizar procesos internos y de cara al cliente al mismo ritmo que exige el Estado, y (b) fragmentación — múltiples sistemas/ventanillas que un operador tiene que operar o integrar en paralelo, muchas veces a mano (Excel, mail, WhatsApp) por no tener sistema propio.

**Del caso puntual.** **Gap total** — no hay ninguna transcripción ni comunicación del cliente todavía. La web no menciona ningún sistema, portal de cliente, tracking online propio (más allá de "seguimiento 24/7" y "sistema de rastreo de contenedores", que suena más a mensajería informal con el cliente que a un portal self-service). Es una **hipótesis a validar en la reunión**, no un hecho: el disparador del contacto podría ser (i) construir un portal/tracking propio para sus clientes, (ii) digitalizar el back-office de gestión de embarques/documentación, (iii) algo completamente distinto no relacionado a comex (ej. un sistema interno de RRHH o facturación). **No inventar el motivo antes de la reunión.**

## 4\. Usuarios

**Interpretación, no confirmada.** Si el proyecto toca la operación de Loginet, los roles típicos de un operador logístico de este tipo serían: personal de operaciones/comex (arma los embarques, gestiona documentación), personal comercial (cotiza y sigue clientes), y clientes finales (exportadores/importadores que quieren visibilidad de su carga). **Gap explícito:** no se sabe si el proyecto involucra usuarios externos (clientes de Loginet con acceso a un portal) o es 100% interno.

## 5\. Stakeholders / personas en la mesa

**Gap total.** No hay ningún nombre de persona disponible — ni en el input, ni en la web pública de Loginet (no tiene una sección de equipo/quiénes-somos con nombres identificados). **A preguntar antes o al inicio de la reunión:** quién de Loginet participa (rol/cargo) y quién de Quarks va a asistir.

## 6\. Riesgos y restricciones relevantes

- **Regulatorio — eje probablemente relevante, profundidad a confirmar en la reunión.** Cualquier sistema que toque documentación de embarques, depósito fiscal o gestión aduanal en Argentina corre bajo el paraguas de AFIP/Aduana (Código Aduanero, VUCEA y las ventanillas sectoriales en desarrollo). Si el proyecto es un portal de tracking o gestión documental, hay que entender si necesita integrarse (o al menos coexistir) con estas plataformas estatales, y si Loginet ya tiene certificación OEA u opera bajo el régimen OLES. (industry-knowledge)  
- **Legal.** Sin datos aún — depende de qué tan integrado esté el sistema propuesto con datos de terceros (clientes de Loginet, navieras, Aduana). A relevar en la reunión.  
- **Stack tecnológico.** La web no menciona ningún sistema/plataforma existente más allá de "seguimiento" y "rastreo" genéricos — no hay evidencia de un TMS, ERP o CRM propio. **Pregunta central a resolver:** ¿parten de cero (Excel/mail/WhatsApp) o ya tienen algún sistema que haya que integrar o reemplazar?  
- **Horizonte de tiempo / urgencia.** A preguntar — sin ningún dato. Dado el contexto regulatorio 2026 (VUCEA prorrogada a fin de año, nuevas ventanillas en rollout), vale la pena indagar explícitamente si alguna fecha de Aduana está empujando el timeline del cliente.

## 7\. Perfil de experiencia previa

**Gap total — no hay evidencia para inferir un arquetipo.** No se sabe si Loginet viene de un desarrollo fallido con otro proveedor, si es greenfield (probable, dado que no se detecta sistema propio en la web), o si es una empresa consolidada innovando dentro de su operación. Es una de las primeras preguntas a hacer en la reunión, no algo para asumir de antemano.

## 8\. Preguntas de discovery contextualizadas

**Contexto de la empresa**

- ¿A qué tipo de cliente le dan servicio hoy — exportadores de perecederos, carga general, ambos por igual? ¿Hay un sector que concentre la mayoría de la facturación?  
- ¿Manejan depósito fiscal propio o tercerizado ("red nacional de alianzas")?  
- ¿Tienen despachante de aduana propio o trabajan con uno externo por operación?

**Problema / objetivo de la reunión**

- ¿Qué los trajo a buscar ayuda ahora? ¿Hay algo puntual que cambió (un cliente grande que lo pide, un problema operativo recurrente, presión de Aduana/VUCEA) o es una inquietud general de modernizarse?  
- ¿Qué esperan que salga de esta primera reunión — un diagnóstico, ya vienen con una idea de sistema en mente, o quieren explorar posibilidades?  
- Hoy, ¿cómo hacen el seguimiento de un embarque de punta a punta — Excel, mail, WhatsApp, algún sistema?

**Usuarios**

- ¿El sistema que tienen en mente es para uso interno de Loginet, para que sus clientes vean el estado de su carga, o ambos?  
- Si hay usuarios externos: ¿cuántos clientes activos tienen hoy, y qué tan seguido piden información de estado?

**Horizonte de tiempo / urgencia**

- ¿Con qué plazo cuentan para este proyecto? ¿Hay alguna fecha externa que los presione (un compromiso ya asumido con un cliente, un cambio regulatorio de Aduana, un cierre de ejercicio)?  
- ¿Qué pasa si esto no se resuelve en ese plazo?

**Factibilidad / stack**

- ¿Tienen algún sistema hoy (TMS, ERP, planillas compartidas) que haya que integrar o reemplazar?  
- ¿Trabajan ya con VUCEA / alguna de las ventanillas sectoriales (VUMA, VUA) de forma directa, o eso queda del lado del despachante?  
- ¿Tienen certificación OEA o participan del régimen de Operadores Logísticos Habilitados?

**Experiencia previa**

- ¿Es la primera vez que encaran un desarrollo de software a medida, o ya intentaron algo antes (con otro proveedor o con equipo propio) que no funcionó?

---

## Competidores

**No corresponde en esta etapa.** Sin saber el objetivo de la reunión, no se puede determinar si el proyecto ayuda a Loginet a competir con otros operadores logísticos (caso en que aplicaría) o si es un problema puramente interno (caso en que no aplica). Retomar después de la reunión si corresponde.

---

## Gaps a cerrar en la reunión (resumen)

1. Quién contactó y por qué canal.  
2. Motivo/disparador real del contacto (hoy 100% desconocido).  
3. Asistentes de ambos lados.  
4. Objetivo concreto de la reunión.  
5. Horizonte de tiempo / urgencia.  
6. Perfil de experiencia previa del cliente.  
7. Sistema(s) actuales, si los hay.  
8. Si el proyecto involucra usuarios externos (clientes de Loginet) o es 100% interno.

---

*Fuentes consultadas: loginetsa.com, loginetsa.com/servicios, búsqueda web sobre Loginet Argentina y sobre digitalización de comercio exterior/aduana en Argentina 2026 (VUCEA, VUMA, VUA, OEA, Declaración Aduanera Digital).*

# Pestaña 2

Jony,   
¿Cómo estás?

Según lo que estuvimos hablando. te paso los números/cantidades que tenemos mensualmente (en temporada alta):

Total de files por mes: 1200  
Promedio de facturas de costo por FILE: 5 facturas  
Promedio de facturas de venta por FILE: 2 facturas

Promedio de Files con extra costos: 40%   
Estos extra costos, los debe cargar operaciones al momento que se generar: Ellos cargan ITEM de COSTO (para que admin chequee y cargue la factura cuando llegue) \+ ITEM de VENTA (para que admin facture al cliente) \+ COMENTARIOS sobre el extra costo (porque se genero cual es el costo \- venta y a quien se debe facturar)  
Este paso es el que en el 50% de los casos, no se llegan a hacer y se está PAGANDO \+ CARGANDO facturas 1 mes más tarde, y cuando yo hago el análisis de estos files, noto que no se facturó al cliente. Es decir algunos de los extras costos se están facturando 1 o 2 meses más tarde del momento que se generaron.

Por último y no menos importante, tener en cuenta que nosotros hoy tenemos 2 cuentas de KHAI en uso:  
Cuenta 1: LNET  
Cuenta 2: AZZURRO  
La 2da cuenta es la de la empresa en Uruguay. Nosotros algunas operaciones las facturamos desde esta otra empresa, y también cargamos las facturas de costos que pagamos desde alli, esto es importante, ya que por algunas operaciones nosotros tenemos 2 FILES en uso (1-LNET / 2-AZZ). Yo cuando saco la rentabilidad tengo que estar entrando en las 2 cuentas para ver que hay cargado en ambas.

No se si me estoy olvidando de algo más. Avísame cualquier cosa.  
Besos\!\!

**Anahi Cappi**  
Quality Control Manager

# Pestaña 3

**Optimización de Procesos Logísticos y Automatización de Datos Documentales**  
Luego de profundizar con Loginet cuál es el primer foco de ataque para una solución que hoy es prioridad absoluta, tenemos el siguiente insight:  
Prioridad: la conexión entre operaciones y admin. Empezamos en el proceso con las alertas de cutoff (documental y físico). Luego hacer un chequeo entre declaraciones y draft de BL. El problema reside en que la declaración del cliente (excel) es leída por un empleado de operaciones y luego esa info es cargada a mano en las paginas de las navieras (con usuario y contraseña) y aquí residen la mayoría de los errores por tipeo en alto volumen de cargas. Tenemos que encontrar una forma de leer la data del excel, cargarla en cada formulario de la naviera correspondiente automáticamente. El siguiente punto de dolor es que una vez hecha mal la carga de datos, cuando se recibe el draft de Bl, por falta de tiempo, también se omite un paso de chequeo y se le envía directamente al cliente dicho draft, lo que causa malestar en el cliente y mayor perdida de tiempo. Si se pierde el cutoff documental, se tiene que pedir un late que conlleva costo adicional, o se pierde la salida.  
Una vez que sale la carga (onboard) se puede facturar al cliente. Operaciones recibe un reporte cada 6 horas del servicio de tracking cargoes via mail, el cual es leído por el bot de extract y cargado en Kai. El problema es que muchas veces, mas de 1/3, el bot no completa todos los campos, lo cual origina un ida y vuelta friccionado ya que facturación no puede facturar, operaciones no llega a dar el ok de la documentación porque no revisó que el bot haya cargado toda la info, y se llegan a perder días o una semana.  
Al margen del chequeo de la carga del bot de extract y corregir en KAI la data faltante, necesitamos actualizar la fecha real de salida en KAI una vez que cargoes envia el reporte. Esto se hace manualmente y tarde. Se le podría pedir a Extract que incorpore esta tarea. Lo mismo debería hacer extract con los cambios de ETA para que administración no apure cobros y pagos de cargas se retrasaron. Si se llega a adelantar una carga, no suele suceder, también se resolvería el apuro crítico de tener todos los pagos hechos para la liberación en de la carga en destino final.

# Pestaña 4

Loginet 2do mapeo Invitado vanina.focaraccio@loginetsa.com Jony Ayerbe Juan Pablo Norverto manuel.vasquez@loginetsa.com Danilo Luce anahi.cappi@loginetsa.com Archivos adjuntos Loginet 2do mapeo Registros de la reunión Grabación  
Resumen El equipo analizó flujos operativos y automatización mediante herramientas externas para optimizar procesos de facturación interna.  
Análisis flujo comercial operativo La discusión cubrió la carga de cotizaciones en KAI y los desafíos operativos al gestionar documentación para embarques. Se identificó la falta de cotizaciones cargadas como un cuello de botella crítico para la facturación.  
Automatización con herramientas externas El uso de la herramienta Extract facilita la carga masiva de facturas, aunque requiere generación manual de una prefactura. El equipo explorará mejoras para validar datos antes de cargarlos en KAI.  
Optimización del proceso administrativo Se decidió fortalecer los controles previos a la carga en KAI mediante herramientas externas y reportes. El objetivo es mantener el sistema actual optimizado en lugar de implementar cambios estructurales complejos.  
Próximos pasos \[El grupo\] Implementar Recordatorio: Configurar aviso automático en el sistema para cotizaciones faltantes. Disparar el recordatorio al iniciar la operación en Excel. \[Juan Pablo Norverto\] Analizar Conversión: Evaluar la construcción del patrón de datos de Carghost. Desarrollar una tabla de conversión de siglas a nombres de puertos para Kai. \[Anahi Cappi\] Coordinar Reunión: Agendar encuentro con Kai para discutir compatibilidad del sistema. Analizar opciones de automatización y nomenclaturas. \[Anahi Cappi\] Preguntar Extract: Determinar requisitos necesarios para automatizar proceso de validación de facturas. \[Anahi Cappi\] Consultar Kai: Solicitar a Kai un reporte más detallado de costos pendientes para apoyar validación externa. \[Jony Ayerbe, Juan Pablo Norverto\] Revisar Estrategia: Digerir, analizar información recopilada. Volver con preguntas pendientes para generar sugerencia, análisis, propuesta. \[Manuel Vasquez\] Coordinar Circuito: Avisar a Manuel Vasquez para coordinar una reunión adicional. Revisar dudas sobre el circuito administrativo si es necesario.  
Detalles Revisión de la Parte Comercial y Operativa Anterior: Jony Ayerbe inició con un resumen de la parte comercial, que abarca desde la consulta hasta el cierre de la cotización, identificando posibles "puntos de dolor" como la comunicación por WhatsApp con el cliente y el asistente. El proceso continúa con la carga de la cotización en KAI y el *booking*, lo que da inicio a la operación en un archivo Excel. Consolidación y Documentación Operativa: La fase operativa se describió, comenzando con el Excel, y abordando opciones de consolidación en origen o en depósito fiscal. Se mencionó que el seguimiento de contenedores, si lo contrata el cliente, es un servicio que, si se automatiza, añadiría valor. Los documentos clave para las instrucciones de envío (*shipping instruction*) incluyen la declaración de embarque, permiso de embarque y *packing list*, y la información del *bill of lading* (BL) se carga en KAI después de ser enviada al cliente. Proceso de Facturación y Liberación: Una vez que el barco opera (sale), se procede a la facturación. Antes de esto, se envía el aviso de embarque (*onboard*) al cliente con copia a "liberaciones," y se espera el envío para facturar. Las trabas aduaneras se revisan manualmente en el sistema de la terminal. Discusión sobre Rutas por Chile vs. Buenos Aires: Se discutió la frecuencia de las rutas que salen por Chile, que es casi 50% y 50%, y si el enfoque debe ser en la parte chilena o continuar con la parte de Buenos Aires. Se acordó enfocarse en la parte más amplia del negocio y continuar con el proceso establecido, ya que la operativa de Chile es más manual y carece de funciones de seguimiento en línea como las disponibles para Buenos Aires. Inicio de la Fase Administrativa y Facturación: Manuel Vasquez indicó que el trabajo administrativo comienza con la facturación, que se activa automáticamente tras la carga de la cotización comercial. La facturación se realiza una vez que el buque ha zarpado, utilizando la información de las cotizaciones cargadas en el sistema. Participación Administrativa en Cotizaciones: Se aclaró que, por lo general, la administración no se involucra en la creación o definición de cotizaciones, siendo esta una responsabilidad de la parte comercial. Sin embargo, la administración sí interviene en operaciones específicas donde el cliente tiene un contrato directo con la línea marítima. Manejo de Extracostos y Vínculo Comercial-Administrativo: Se explicó que la parte operativa sí interviene para aprobar y cargar "extracostos" adicionales fuera de la cotización inicial, en colaboración con la parte administrativa. El flujo general va de comercial a administración a través de la cotización en KAI, que se vincula a un archivo operativo ("file") con todos los datos del embarque. Definición de "File" en KAI: Se aclaró que el "file" en KAI es el nombre que se da a la operación, la cual pasa a ser una operación cerrada con un número de referencia una vez que la cotización es aprobada por el cliente. La cotización se carga en el sistema únicamente cuando está aprobada. Problema de la Falta de Cotización en el Sistema: Se identificó un problema recurrente donde las operaciones se realizan, y el embarque incluso sale, pero la cotización no está cargada en el sistema, lo que impide la facturación. La parte comercial es responsable de cargar el número de cotización en el file operativo de KAI. Causas de la Demora en la Carga de Cotizaciones: Se señaló que la falta de carga de la cotización puede ocurrir debido a que la temporada acaba de empezar, y el monto final de la factura al cliente de destino aún no está definido por el cliente local. Esta demora, que puede ser aceptable, a menudo se debe a que se está ajustando el margen o "on top" que se cobrará al cliente final. Necesidad de Condiciones y Recordatorios en el Proceso: Jony Ayerbe propuso que, si no se puede imponer una condición para que la cotización esté cargada, se podría establecer que al iniciar la operación en Excel (el primer paso interno), se dispare un recordatorio si la cotización falta en KAI. Un recordatorio recurrente podría servir como un incentivo para que el equipo comercial complete la información. Flujo de Facturación y Cuentas Corrientes: Una vez que la data está completa, administración factura al cliente. El siguiente paso es el envío de los estados de cuenta a los clientes, un proceso que actualmente se está automatizando en KAI. El reclamo de pagos depende de si el cliente tiene cuenta corriente (pago a 30 días) o si requiere liberación de carga con pago anticipado, información que se sigue a través del sistema y el Excel. Desafío de la Actualización de Fechas de Arribo (Carghost): La actualización de las fechas estimadas de arribo de los buques se gestiona con una herramienta externa (*Carghost*), que genera un Excel con los cambios. Esta actualización se hace manualmente en KAI, ya que el sistema no puede automatizar la carga debido a la discrepancia en la nomenclatura de los puertos (siglas vs. nombres completos), lo que requiere una conversión. Obstáculos para la Automatización de Datos en KAI: La automatización para actualizar KAI con las fechas de arribo desde Carghost y para cargar facturas de proveedores a través de *Extract* enfrenta problemas de coincidencia de campos y formatos. Se concluyó que cualquier mejora requerirá el esfuerzo de "caifificar" la data externa y potencialmente negociar cambios en el sistema central de KAI. Chequeo de Facturas de Costos contra Cotización: El proceso administrativo también maneja la parte de costos, donde las facturas de las líneas marítimas llegan al correo de "liberaciones". La factura recibida es revisada manualmente contra la cotización de costos cargada en KAI. Control de Facturas y Uso de Extract: Manuel Vasquez y Anahi Cappi describieron el proceso actual para controlar las facturas de líneas marítimas antes de la carga en el sistema Kai; este proceso es crucial porque las facturas deben ser validadas antes de la carga. Para validar, Manuel Vasquez selecciona todos los ítems de costo que coinciden con el total facturado, genera un 'rock' (una prefactura o precarga sin número de factura ni fecha). Este PDF del 'rock' se envía a Extract, que lee la factura, la envía a Kai, y Kai automatiza la carga de la factura, incluyendo número, fecha y PDF, si el contenedor y el importe coinciden con el 'rock'. Volumen de Facturación y Ahorro de Tiempo: Anahi Cappi resaltó la necesidad de este proceso automatizado debido al alto volumen, ya que se reciben aproximadamente 500 a 600 facturas de líneas marítimas por mes durante la temporada alta. La automatización con Extract ahorra una cantidad significativa de tiempo al evitar tener que teclear manualmente el número y la fecha de la factura, y cargar el PDF. El proceso ideal sería que un sistema leyera la factura y la enviara directamente a Kai para que coincidiera con los datos. Proceso de Generación de 'Rock' y Carga de Factura: Manuel Vasquez demostró que la generación del 'rock' se realiza seleccionando los costos en el archivo de operación que coinciden con el monto de la factura del proveedor. Una vez generado, el 'rock' se sube al sistema y posteriormente el PDF de la factura se envía a Extract. La función de Extract es leer el PDF, pasar la información a Kai, y Kai concilia la factura basándose en el número de contenedor y el monto del 'rock'. Revisión de Información antes de Generar el 'Rock': Jony Ayerbe preguntó sobre los pasos previos a la generación del 'rock', lo que llevó a la explicación de que la información se coteja en el archivo (file) de la cotización. La cotización se carga en el módulo comercial y esto automáticamente trae los conceptos de venta y costo a la solapa de ítems. Se identifica que un ítem proviene de la cotización si tiene el icono de un "billetito" al lado. Flujo de Trabajo Manual para la Facturación: El proceso manual requiere que el personal de administración revise qué operaciones tienen ítems pendientes de facturación en el sistema. Cuando llega una factura de una naviera, la persona la revisa, la coteja con los costos de la operación, y si está correcta, genera el 'rock'. Manuel Vasquez explicó que este control manual es rápido (50 'rocks' en 20 minutos) y permite que se envíen lotes de PDFs a Extract, que luego los procesa y los carga automáticamente en Kai. Función de Extract en la Carga de Facturas: Jony Ayerbe confirmó que la principal función de Extract es leer el PDF y pasar la información a Kai en un formato predeterminado, aunque esto requiere la intervención humana previa para generar el 'rock'. Se mencionó que el tiempo de demora para la carga automática puede ser de aproximadamente media hora por cada envío de documentos, no por factura individual. Desafíos y Propuesta de Optimización de la Validación: Juan Pablo Norverto y Jony Ayerbe señalaron la necesidad de validar la factura antes de generar el 'rock' (la proforma), ya que actualmente esa validación es un proceso manual de comparación. Juan Pablo Norverto propuso la idea de que Extract pudiera validar la factura comparándola con un archivo de datos (CSV o XLS) de Kai, de modo que solo se generara el 'rock' si la validación es exitosa, automatizando así el proceso de control de la persona. Discusión sobre la Limitación del Sistema Kai: Se discutió la limitación de Kai, señalando que el sistema no permite descargas de reportes detallados que separen los costos por proveedor dentro de una misma operación, lo cual complica la automatización de la validación externa. Anahi Cappi y Juan Pablo Norverto acordaron que el objetivo es evitar la necesidad de solicitar nuevas funcionalidades a Kai, enfocándose en usar la información que ya es descargable o que Extract podría procesar. Origen de la Creación del 'Rock': Se aclaró que la necesidad de crear el 'rock' surgió porque la idea original era que Extract y Kai gestionaran la carga sin control humano, pero la inconsistencia en las facturas de las navieras y la falta de información de cotización forzaron la creación del 'rock' como un paso de "precontrol" manual. Juan Pablo Norverto sugirió que el proceso actual era engorroso a menos que la tasa de error fuera muy alta. Planificación de Consultas con Sistemas Externos: Anahi Cappi concluyó que es necesario preguntar a Extract qué necesitan para validar la información de manera más automática. El plan es llevar los requisitos de Extract a Kai para ver si es posible extraer los datos necesarios, como un reporte más detallado, en lugar de intentar que Kai añada funcionalidad compleja. Manejo de Errores en la Factura: Facturación Incorrecta por Naviera: En el caso de que la factura de la naviera esté mal, la administración la compara primero con el contrato comercial que debe especificar el costo correcto. Si la naviera facturó de menos o de más, administración contacta directamente a la línea marítima para solicitar una nota de crédito o la corrección de la factura. Manejo de Errores en la Factura: Monto Incorrecto en la Cotización (COTI): Si la factura de la naviera coincide con el contrato, pero el monto cargado en la COTI en Kai es incorrecto, el proceso se devuelve a comercial. Comercial debe revisar, corregir manualmente el monto en Kai y luego se devuelve a administración para el pago. Importancia del Contrato en la Validación: Jony Ayerbe buscó clarificación sobre la fuente del precio correcto, confirmando que el contrato es el punto de referencia final para validar los costos de la naviera, y comercial es responsable de enviar el contrato a administración. Estos contratos son vigentes por temporada o por períodos definidos para rutas habituales. Proceso de Negociación y Cierre de Rutas Nuevas: La discusión se centró en cómo se cierra una negociación de ruta o cliente nuevo, lo que lleva a la creación de un contrato con la naviera. Existen dos tipos de cierres: por contrato (para grandes volúmenes, como 600 contenedores por temporada/mes), que requiere un número de contrato específico para cada *booking* y se registra en la línea, o mediante cotizaciones *spot*, que son puntuales para cada carga y se manejan por correo electrónico. El contrato o el registro de la cotización se realiza después de la negociación y es la herramienta que utiliza la administración para verificar la factura con lo ingresado manualmente en el sistema CAI. Gestión de Contratos y Repositorio Maestro: Se confirmó que los contratos por temporada completa se almacenan en una planilla maestra de operaciones, en una pestaña dedicada a "contratos". Este repositorio sirve para chequear si la facturación coincide con lo acordado en el contrato; si el valor es incorrecto en la cotización (*COTI*), se debe informar al equipo comercial para que lo corrija manualmente. Este punto de error en la carga o no carga de la cotización fue identificado como un área principal a abordar para mejorar el proceso. Problemas con Conceptos no Cargados en la Cotización: Un punto crítico de dolor es cuando un concepto de servicio (como custodia o ingreso a puerto) no se carga en la cotización, lo que resulta en que el cliente no es facturado por dicho costo. Esto puede ocurrir debido a que el servicio no se conoce bien o porque el cliente ya sabe del embarque y no requiere una cotización formal, lo que puede llevar a descubrir el costo no facturado hasta que llega la factura del proveedor. Esta falta de coincidencia en los conceptos cargados es una variante adicional a los errores en los montos de la factura. Propuesta de Inteligencia Externa al Sistema CAI: Se propuso trabajar en un sistema de "inteligencia" fuera de CAI para articular chequeos, recordatorios y notificaciones, ya sea que la cotización esté cargada o no. Este sistema ayudaría a verificar la información contra el Excel Maestro y las facturas, con el objetivo de facilitar los chequeos de validación. El equipo debe considerar si es viable acceder automáticamente al sistema CAI para verificar valores y hacer solicitudes, aunque se reconoció que el acceso a un sistema local podría resolver esta limitación. Integración y Verificación de Información Operativa: Se sugirió la posibilidad de que el equipo operativo, que maneja los detalles de la carga, valide la información del Excel Master con los conceptos cargados en la cotización. Por ejemplo, si el operativo confirma que Loginet realiza el ingreso a puerto, el sistema podría chequear si el concepto de ingreso a puerto está incluido en la cotización. El objetivo es que la información que se tiene como validada se cargue en CAI de una manera más ordenada. Limitaciones y Uso Actual del Sistema CAI: Se determinó que el equipo operativo utiliza muy poco el sistema CAI, mientras que la parte administrativa lo usa de manera más frecuente. Ya que la parte administrativa es el último eslabón del proceso, se sugirió atacar el proceso anterior a la administración para que la información que llega a CAI sea lo más limpia posible. Esto implicaría usar CAI principalmente como un sistema de planificación de recursos empresariales (ERP) para la facturación y la administración, mientras que el proceso anterior se fortalecería con herramientas externas. Enfoque en la Mejora del Proceso Antes de CAI: La fricción se genera en la carga subsiguiente de información a CAI, y el enfoque debe estar en manejar el proceso fuera de CAI hasta que la información esté lista para la carga final y necesaria. Se identificó que hay un punto de mejora significativo en el proceso, desde la carga de la cotización hasta evitar errores causados por comunicación, falta de recordatorios o chequeos pendientes. El equipo debe trabajar en recordatorios, alertas y automatizar tareas usando el Excel Maestro para diferentes departamentos, y luego intentar conectar esto a CAI para la facturación. Evaluación de Sistemas de Gestión de la Competencia: Anahi Cappi mencionó que ha trabajado con otros sistemas en el pasado que considera más amigables que CAI, notando que los cambios eran más rápidos. No obstante, por el momento no es una opción considerar un cambio de sistema, especialmente con el inicio de la temporada, sino que el objetivo sigue siendo optimizar el sistema actual y utilizar herramientas externas como Extra y Cargo para complementar las funciones que CAI no puede realizar. El equipo acordó digerir la información mapeada, volver con preguntas y avanzar hacia una propuesta de sugerencias y análisis.

## Chat

🚢

## Loginet

5 fuentes·16 mar 2026  
Loginet es un operador logístico internacional que busca optimizar su competitividad mediante la mejora de sus procesos operativos y administrativos. Los documentos detallan diversos "puntos de dolor", como errores en la carga manual de datos, falta de cotizaciones en el sistema y dificultades en la conciliación de facturas de proveedores. Para solucionar estas ineficiencias, la empresa analiza la implementación de herramientas tecnológicas como Extract, Carghost y Kai, enfocándose en la automatización del flujo documental. El objetivo central es fortalecer la comunicación entre las áreas comercial y administrativa para asegurar una facturación precisa y oportuna. Finalmente, el equipo propone el uso de recordatorios automáticos y sistemas de validación externa que complementen su infraestructura actual sin necesidad de cambios estructurales complejos.

¿Cómo busca Loginet automatizar la facturación y validación de documentos?  
¿Cuáles son los pilares y la misión estratégica de Loginet?  
¿Qué desafíos presenta el sistema KAI en la gestión logística?  
🪄  
Ahora Gemini Notebook es más inteligente. Prueba a pedirle que busque nuevas fuentes en la Web.  
3 fuentes

## Studio

Resumen de audio  
Presentación  
Resumen de vídeo  
Mapa mental  
Informes  
Tarjetas didácticas  
Cuestionario  
Infografía  
Tabla de datos  
Optimización de Procesos Logísticos y Automatización de Datos DocumentalesHace 77 días  
Gemini Notebook puede ofrecer respuestas incorrectas. Compruébalas.

# Pestaña 5

may 27, 2026

## Loginet \- Transcripción

### 00:00:00

**Jony Ayerbe:** y el el otro problema que es cargar en el Kai la información. Son esas tres grandes, si se quiere, épicas. Yo me concentré por ahora en la primera porque es la más compleja y porque las otras sin hacer demasiado deep dive lo podemos resolver porque es comparar un documento con otro básicamente. Y la parte de cargar en Kai nos queda pendiente, pero sabemos que Kai ya tiene una API para el bot de extract. Entonces ahí una vez que arranquemos el la consultoría, si se quiere o la primera parte, lo que vamos a tener que y ya lo probé yo y lo hice lo lo funcionó mejor con el skill de PDF que usé y lo que funcionó mejor que el bot de extract sin ningún error.

**Juan Pablo Norverto:** O sea,

**Jony Ayerbe:** No

**Juan Pablo Norverto:** que el B capaz lo que no capaz lo que funciona mal es la integración,

**Jony Ayerbe:** es

**Juan Pablo Norverto:** ¿no? El bot de extra. ¿Se entiende?

**Jony Ayerbe:** sí que no carga bien en adentro de

**Juan Pablo Norverto:** Claro, capaz le pasa bien la información.

**Jony Ayerbe:** calle.

**Juan Pablo Norverto:** Extrae bien la información todo porque me parece medio difícil que no lo haga y cuando manda la API nada.

### 00:01:26

**Jony Ayerbe:** Bueno, entonces o tenés API o tenés eh algo que use GUI, o sea, UI Path o alguna de esas cosas que ya requeriste un bot que que navegue, que vea la interfaz y que y eso está sujeto a un montón de errores y y digamos no es el mejor camino. Obviamente el mejor camino es es incluso con mi limitado conocimiento el mejor camino es la API, pero no sabemos con qué nos encontramos en calle. Entonces, lo que podemos escopear hoy y me parece que lleva el 60, 70, 80% del grueso para poder cotizar es este problema de la decla, transformarla en un shipping instruction, la estandarización de los datos de cómo vienen y toda esta pelota. Entonces, básicamente lo que primero hice fue empecé a fidiarle documentos, documentos eh que son el draft del Bill of Lading. Sí. Entonces, esos drafts, agarré uno de Japac,

**Juan Pablo Norverto:** Mhm.

**Jony Ayerbe:** agarré uno de Marsk, los cargué, les pedí que extrajera la información y que la normalizara en datos y me preparó un Excel único a donde lee perfectamente todo. No hay un p\*\*\* dato que no lo lea, que no lo entienda y y que encima no mejore.

### 00:02:56

**Jony Ayerbe:** Entonces, ¿cuál es el tema acá? Bueno, la recomendación es primero hacer una capa de de ingesta de documentación. Te comparto acá hacer una capa, un document injust layer, que es básicamente monitorear eh los inboxes y hacer o un forward automático o que haga un pull de los attachments estos. Clasificar los documentos, ¿sí? la misma normalización que yo hice con el con el agente para en un documento solo Excel de todo.

**Juan Pablo Norverto:** A ver, a ver, damos Un segundo. Disculpa, pasa cuando me llaman por teléfono a veces no sé si es el colegio, esas cosas.

**Jony Ayerbe:** No pasa nada.

**Juan Pablo Norverto:** Eh, ahí te iba a preguntar, ¿vamos a monitorear los inbox de mail?

**Jony Ayerbe:** O tenemos que página de línea, declaraciones, declaración draft cargos, declaración draft. Esto es lo que yo no sé. Ah, claro, me mandó directamente todo un qué paja. Okay. Eh, acá tenés un ejemplo de una declaración. Eh, si vamos a monitorear el inbox o no, no sé que es mejor hacer un forward automático, monitorear el inbox,

**Juan Pablo Norverto:** No,

**Jony Ayerbe:** no sé qué.

### 00:05:31

**Juan Pablo Norverto:** para mí al principio lo mejor es que ellos agarren, bajen los archivos y los suban a un lugar y después si eso si eso

**Jony Ayerbe:** Bueno, lo que me

**Juan Pablo Norverto:** funciona que después se automatice. vemos la manera que se automatice,

**Jony Ayerbe:** rec

**Juan Pablo Norverto:** porque capaz en vez que le enví mail a 1000 se crea unas una cuenta que es del sabemos que del bot y no sé qué que está leyendo ese mail nada más si no está leyendo todo lo que entra e no sé hay que verlo. ¿Se entiende lo que quiero decir?

**Jony Ayerbe:** Sí, puedes hacer un puedes hacer un inbox que lo deben tener específicamente para las declaraciones y decirle a los clientes, manden todas las declaraciones acá.

**Juan Pablo Norverto:** Sí, bueno,

**Jony Ayerbe:** Chao.

**Juan Pablo Norverto:** pero por eso, pero al principio como que haría esa interacción entre el algo donde va a procesar eso para que ellos validen que procesa bien y se sientan en control,

**Jony Ayerbe:** Sí,

**Juan Pablo Norverto:** porque en el momento que le sacas el mail y todo es como que

**Jony Ayerbe:** no saben lo que está pasando.

**Juan Pablo Norverto:** claro,

**Jony Ayerbe:** Sí,

**Juan Pablo Norverto:** lo leyó, no lo leyó,

### 00:06:30

**Jony Ayerbe:** está bien.

**Juan Pablo Norverto:** ¿viste? te lo marca como leído, pero en realidad vos no lo leíste como para empezar

**Jony Ayerbe:** Sí, sí, está bien, está bien.

**Juan Pablo Norverto:** progresivamente,

**Jony Ayerbe:** Esto no es ¿Dónde?

**Juan Pablo Norverto:** ¿no?

**Jony Ayerbe:** No ve la cantidad de pantallas que tengo. La concha la lola. Bueno, eh, acá está. Entonces, por arriba, por arriba eh es agarrar los documentos que que vienen

**Juan Pablo Norverto:** Eso sí.

**Jony Ayerbe:** y los documentos que vienen son este ejemplo. Este es el ejemplo del documento que viene,

**Juan Pablo Norverto:** Mhm.

**Jony Ayerbe:** en donde la información está como toda eh distinta, si se quiere, a localizada, estructurada, distinta eh por cada envío, pero no tiene ninguna no no tiene ninguna complejidad, o sea, es un Excel o podés escanear todo y podés entender el nombre del embarcador o o de quién es el client de quién es el consign, digamos, ahí sería como aplicarle reglas. Eh, y esto lo podría hacer con algún Google Document AI o algo por el estilo, como lo recomienda en una primera instancia. Después e tipo aduana, peso, eh la naviera, puerto, puerto de carga, destino final, son todas nomenclaturas que se usan exactamente igual para todos, venga de donde venga.

### 00:08:28

**Juan Pablo Norverto:** Pero eso vos qué te imaginass de flujo olvídate el detalle del documento

**Jony Ayerbe:** Entonces,

**Juan Pablo Norverto:** porque eso es después para ver en detalle. Digo, no no no sirve ahora para estimar, pero ¿qué te imaginas el flujo? ¿Qué hago con estos documentos?

**Jony Ayerbe:** sí,

**Juan Pablo Norverto:** Olvídate si lo saco de Google o si lo meten en un lugar. Me llega el documento. ¿Qué hago con el documento?

**Jony Ayerbe:** primero llega el documento, o sea, cómo los chupo, cómo los liger o lo que fuere, tengo que agarrar esos documentos y tengo que poder llegue como llegue tener una estandarización de la data de esos documentos. Sí, los tengo que convertir a algo en donde yo tenga siempre el mismo el

**Juan Pablo Norverto:** Perfecto.

**Jony Ayerbe:** mismo

**Juan Pablo Norverto:** Ponele que sea lo mismo que hizo Fefe con los lotes, ¿viste? Eso un lote tiene un montón de de bla.

**Jony Ayerbe:** eso.

**Juan Pablo Norverto:** Entonces es un barco tiene un montón de containers.

**Jony Ayerbe:** Bueno,

**Juan Pablo Norverto:** Listo. detalle, no sé, bla, por decir algo,

### 00:09:24

**Jony Ayerbe:** bien ahí, ahí. Eh, hay un una instancia en donde hay que aplicarle reglas de negocio. Ejemplo, si viene eh una decla y es una carga de limón y dice en la en el coso de temperatura, ponele 4 gr y hay una regla de negocio, el limón tiene que ir entre 10 y 12, entonces ya te salta, o sea, cierta inteligencia decir, "Che, no puedo cargar cualquier falopa que detecto." e validación de campos mandatorios, los rangos de temperatura, etcétera, reglas de

**Juan Pablo Norverto:** Todo eso no lo hace todo eso no lo hacen en K,

**Jony Ayerbe:** negociada

**Juan Pablo Norverto:** no lo hacen manualmente antes,

**Jony Ayerbe:** por

**Juan Pablo Norverto:** ¿no? Ya sé que no, pero toda esa información cuando llega acá llega porque ellos hacen todo esto antes. Estas regla de negocio, esto que estamos hablando, estas validaciones las hacen visuales. ¿Cómo las hacen

**Jony Ayerbe:** Sí, ni siquiera llega,

**Juan Pablo Norverto:** hoy?

**Jony Ayerbe:** ni siquiera llega manual después es un lo que lo que llega es un input copy boludo, me acaba de escribir de login cuáles son las chances. La estaba pensando.

### 00:10:45

**Jony Ayerbe:** Hola, Johnny, ¿cómo estás? Qué loco, reunido por vos. E no, en K, olvídate. Esto llega el Excel ese que te mostré del cliente y hay un humano que se da vuelta y carga todo en la Naviera.

**Juan Pablo Norverto:** por eso, pero no no Hay una validación antes, la validan mientras van cargando.

**Jony Ayerbe:** No, por eso hay errores costísimos,

**Juan Pablo Norverto:** La idea es la por eso la idea es hacer una validación

**Jony Ayerbe:** costosísimos con regla de negocio.

**Juan Pablo Norverto:** antes.

**Jony Ayerbe:** Correcto. regla solo regla de negocio, sino que por ejemplo, primero que tenga sentido lo que lo que mandó el cliente,

**Juan Pablo Norverto:** Okay.

**Jony Ayerbe:** o sea, de alguna manera validar que lo que el cliente cargó no tenga error. Segundo, que lo que el cliente cargó, de lo que yo voy a cargar no le falten cosas para que esté mal el shipping instruction según la regla de la naveda. Ese es el segundo paso. Tercero es el el la carga eh concretamente el entrar a la página de la naviera, el portal de la naviera y cargarlo. Y acá hay algunas que tienen API, eh, y hay otras que no.

### 00:12:02

**Jony Ayerbe:** Y de hecho me causó gracia porque en el peloteo de cuál sería un primer approach, MVP y esto y lo otro que yo también le expliqué, "Che, elaboramos así, quiero esto, quiero" y lo lo va aprendiendo mismo de del proceso con Olimpia. Eh, me dice, eh, es mucho más limpio y más reliable evitar el las automatizaciones por GUI, ¿no? Entonces, ¿qué pasa? Hay algunos que tienen EDI, que no sé qué es IDI, EDI y y que tienen developer API y hay otros que no, los que no que son más fáciles para implementar es tipo browser automation o RPA. Y de hecho me sugiere Automation Anywhere, que es la de mi amigo de acá, ¿te acordas que habíamos hablado? Eh, tenés UI Path UI Path Automation Anywhere o lo que fuere. E esta carga de datos yo lo que empezaría a hacer es porque para la venta a nosotros nos sirve y es más magia. Yo empezaría, por ejemplo, Myers o o Japlo tienen API, entonces les haría una integración con la API. y les mostraría,

**Juan Pablo Norverto:** con la Claro,

**Jony Ayerbe:** este es el Claro.

**Juan Pablo Norverto:** con la que más usen de esas dos.

**Jony Ayerbe:** y decir este es el el y dejarle andando también para el primer testeo hacer una integración con una naviera y que sea todo Jason, un Jason con el output de toda la normalización de datos de todo lo que viene, una integración vía API, un control durante un mes de qué errores, un human controlando qué errores tiene y que los pibes digan, "Boludo, el PIB va a flashear porque dudo que haya muchas empresas de estas en Argentina que tengan una

### 00:14:00

**Jony Ayerbe:** integración vía API con la Nadiera, o sea, eh, y luego está la parte de eh la orquestación, si se quiere, porque si estás usando el approach de un botcito, de un RPA que esté automatizando el browser, la la navegación, lo que fuere, ahí necesitamos meter un N8N o algo, no importa qué, no voy a decir qué ahora, Pero se necesita algo que entienda que este documento que entró va a Mars y que tiene que ir por este camino. Y si el día de mañana, por ejemplo, vamos a hacer algo híbrido porque algunas no tienen API, entonces en algunas vas a necesitar un bot que vaya a través de la GUI y en otras va a ser API. Entonces ahí necesitas un decisor.

**Juan Pablo Norverto:** ruteador.

**Jony Ayerbe:** Claro. Un decisor de esto va por acá, esto va por ahí, eso puede estar todo mapeado en N8N. e y nada, y después lo lo que estaba charlando son los aspectos de seguridad y y manejo de credenciales, eh, que nada, para entrar a las navieras vas a necesitar tener todo este manejo de de credenciales y ahí sugerían un par, no importa, pero obviamente best practices eh y como el Rap de implementación para mí es agarrar a a Jaac Lloyd o a Marsk, la que más usen, como dijiste, construir la extracción de data de la decla, que 90% es Excel, 10% es Google Doc, extracción, normalización del output, eh, validar la la parte esta de lógica de negocio, eh, y medir,

### 00:15:53

**Jony Ayerbe:** no sé, el margen de error que tiene en 50 envíos en 50 shipments o 100 shipments o 30, lo que sea,

**Juan Pablo Norverto:** Mhm.

**Jony Ayerbe:** y después empezar con RPA en el portal web y después migrar a API. El tema de empezar con RPA y esto nos va a llevar a la misma discusión en Padwor, la misma discusión en en loginet y demás, es si vos querés entrar por RPA o si y y entonces ir a un proveedor de estos que paga dos lucas la licencia con los bots, con la mano en coche o esta charla.

**Juan Pablo Norverto:** es

**Jony Ayerbe:** Esta charla hace 6 meses con Facundo de Loginet empezó yo diciéndole muy probablemente no necesitas estás automatización y yo diciéndole, ¿viste? Jose es con el que nos reunimos con Fed. Jose es el representante Latinoamérica de Automation Anywhere. Nosotros lo podemos implementar, bla bla bla. Empezó así y toda la vuelta que vimos lleva a un botito que esté haciendo esto, eh, pero por ahí es munición gruesa. Automation Anywhere por ahí,

**Juan Pablo Norverto:** Eh, seguramente hoy,

**Jony Ayerbe:** ¿eh?

**Juan Pablo Norverto:** hoy al menos sí, para mí pasa que bueno, son ideas, ¿viste?

### 00:17:17

**Juan Pablo Norverto:** Son hipótesis. Eh, yo no me puedo sacar de la cabeza que que todos necesitan un backoffice propio, porque todos tienen su regla de negocio, todos tienen sus cosas y hoy es el momento de empezar a hacer lo propio nuevamente.Amos, ninguna SAS. Eh, vos vas a estar pagando por un montón de cosas que no usas, eh, así, eh, un montón de cosas que no sé, vos te adaptas tu negocio a lo que te da el otro y no puedes hacer tu negocio, crecerlo como queres que crezca, digamos, ¿no? Porque yo lo que veo es esta parte de decir, bueno, nada, me armo ese backoffice donde empiezo tirando Excels y que esos Excel me generan un

**Jony Ayerbe:** es

**Juan Pablo Norverto:** listado de las las cartas estas de la, ¿cómo es? Las declaraciones. Esas declaraciones las abro y tengo listos los datos para copiar y pegar en cualquier lado de forma manual, ya normales, normalizados. Y si hay que uno para normalizar lo abro y me dice, "Che, ¿qué está mal de esto?" Y que te vuelve a pedir, ¿no? Se entiende lo que quiero decir entonces eso ya con usuarios y roles, ¿no?

### 00:18:29

**Juan Pablo Norverto:** De tu empresa. Y a eso después, a eso después le agregas lo que decís, "Chevia API, digo, ejecuto estos que son de coso, los mando a ejecutar." Sí, de forma manual. Veo cómo es. De forma manual y después empiezas a automatizar esa parte. Decir, bueno, listo. Ya sabemos que estos son siempre para esta naviera. Esta navera ya tenemos la app y ya la probamos todo. Cada vez que llega uno lo dispara, dispara solo, digamos. si está okay, lo dispara, eh, y eso seguramente recibirá un código de que cree esto y vas a poder seguir con algún dato que es complementario y entonces vos ahí empiezas a tener tu propio dashboard, ¿no? Entonces, a veces el estado de la cantidad de de cosas que están subidas, la cantidad que no, cuáles cuántas tuvieron errores, cuántas no, vencimientos,

**Jony Ayerbe:** Ja.

**Juan Pablo Norverto:** un montón de cosas que que te dispara el dash no que eso es lo que te da, esos dashboard es lo que te da, que es lo que decían el otro día, justo leía, que el power vi muere entre otras cosas, ¿no?

### 00:19:38

**Juan Pablo Norverto:** Porque nada, vos empezas a tener información y bueno, nada, mostrar, digamos, no es nada diferente a lo que venimos haciendo en un montón de clientes. Mi pregunta que yo no sé responder es, ¿hay alguna herramienta del mercado como todas las que usa Padwor, por ejemplo, que le resuelva todo esto realmente en vez de, se entiende? En vez de hacer algo propio,

**Jony Ayerbe:** Eso no es, eso no es el

**Juan Pablo Norverto:** el C parte,

**Jony Ayerbe:** TMS.

**Juan Pablo Norverto:** sí, por eso el tema ese tiene 1000 cosas, como hablar de un CRM, ¿me entendés? Entonces, ¿querés tener uno, no querés tener uno, vas a invertir en eso, no vas a invertir en eso, porque ponerse a hacer todas las reglas de negocio cuando en realidad es algo que configuras en un TMS capaz no vamos a un TMS, ¿se entiendes? Entonces, las expectativas, ¿cuáles son? Esto que armé en realidad me lo reservó un TMS. Eh, bueno, esa es la parte que yo tengo desconocimiento del negocio como para como para poder decir algo más concreto, ¿no? E la parte que me da un poco de miedo de de esto de

### 00:20:51

**Jony Ayerbe:** Hemos

**Juan Pablo Norverto:** qué tanto vamos a reinventar la rueda en el en el rubro. digo, e capaz es una falencia por todos lados, ¿no? Hay que ver con este chico que tiene mucho conocimiento, ¿no?

**Jony Ayerbe:** con el chino.

**Juan Pablo Norverto:** No sé cómo se llamaba el del cordobés. Este,

**Jony Ayerbe:** Sí.

**Juan Pablo Norverto:** es ahí donde yo veo, digamos, un tema, pero obviamente vos cada empresa tiene una situación actual. Estos tienen, vos me has dicho que no sé quiénes le dijeron o vos que ya no usa nadie más e caí, ¿no? Y a dónde se fueron. No creo que todos hayan ido a hacer un sistema propio. Se me ha mudado otra cosa.

**Jony Ayerbe:** Sor, para esta m\*\*\*\*\*

**Juan Pablo Norverto:** Ça

**Jony Ayerbe:** me quedó con un mail. Ah, no, está bien. Es un mail viejo. Justo estaba revisando lo de Marcos y no me mandó nada. Eh, es un tema, boludo. Si se hace, por eso para mí no es hacer no es hacer todo de nuevo, porque pensá que estos flacos pagan, no sé cuánto está pagando eh por por Kai, pero un un TMS mediano, o sea, para una empresa mediana, estás hablando de que están pagando 1000 a $,000 de implementación, o sea, de setup.

### 00:22:57

**Jony Ayerbe:** Y después están pagando entre de 50 a $00 por usuario.

**Juan Pablo Norverto:** Mhm.

**Jony Ayerbe:** No creo ni cae y debe ser regalado lo que lo que les está cobrando. Debe ser 50 por usuario o menos. Eh, obviamente no les sirve, no escalan, entonces no está listo. No, no funca. Pero eh si vos le decís ahora vamos a armar algo que sale $,000 o $,000 eh la cabeza de esta gente y lo que vamos a armar es una solución periférica a lo que ya tienen, o sea, como para resolver cositas de alrededor. La cabeza de estos pies no están ahí, no está en en reemplazar y y lo de los guinet de nuevo es un problema, no está en reemplazar cay la cabeza de ellos. Ahora saben que lo tienen que hacer,

**Juan Pablo Norverto:** No, no.

**Jony Ayerbe:** pero me parece que la venta en vez de, "Che, te voy a armar todo un backofice de cero nuevo, tu cerebro local con tu lógica de negocio, con bla bla bla, me parece que la venta es, "Che, vamos, dame tiempo, contrátame por tiempo, voy a empezar a darte todas estas soluciones y con el una vez que estemos adentro con el correr de empezar a explicarles lo que realmente estamos haciendo Como para que cuando lo entiendan vos ya estás y le decís, entendés el poder que esto tiene para adelante.

### 00:24:39

**Juan Pablo Norverto:** Ah.

**Jony Ayerbe:** Bueno, entonces sigamos. Si vos te pasás tres meses armándole el backofice, no sirve. Me acaba de escribir la mina diciéndome, "Hola, Johnny, ¿cómo estás?" Digo, "Reunido por vos." Jaja. Ah, bueno, genial. Entonces, bajo la ansiedad. están con incendio.

**Juan Pablo Norverto:** He.

**Jony Ayerbe:** El incendio es se putea administración y operaciones por el volumen que tiene, porque entra administración al CAI, está todo vacío y es esto, ¿lo facturo o no lo facturo, qué hago? ¿Puedo o no puedo? Se mete la Genta,

**Juan Pablo Norverto:** Ahí

**Jony Ayerbe:** danos unos días que estamos terminando de cargar.

**Juan Pablo Norverto:** está.

**Jony Ayerbe:** Los otros dicen, "Che, el bot no cargó la mitad de lo que tenía que cargar." Ese es el quilombo hoy. Entonces, hay que entrar con una manguera de bombero y vos no le puedes cotizar la manguera de bombero. Por eso yo decía, decimos que vamos a atacar estos tres dolores y una vez que entramos y que te dicen,

**Juan Pablo Norverto:** No.

### 00:25:44

**Jony Ayerbe:** "Bueno, listo." Si querés le explicas, mira, los dolores se atacan, no solo poniendo los parches o armando los puentes. eh los caminitos, los procesos y los puentes periféricos no me salía, sino que hay que empezar a a crear un lugar, una lógica, un cerebro de tu negocio, eh, y lo estamos empezando a hacer, que esto te va a permitir bla bla bla bla bla. O sea, si no vendés el el baldazo de agua fría y la solución en un mes, se pasa la temporada alta,

**Juan Pablo Norverto:** Pasa que no van a tener solución para la temporada

**Jony Ayerbe:** ¿no?

**Juan Pablo Norverto:** alta.

**Jony Ayerbe:** Pero pero ya empiezan a verlos.

**Juan Pablo Norverto:** Empiezan a ver qué la pregunta. Pues no sabemos qué. Con lo que estamos viendo no tenemos un un norte, o sea, tenemos tres problemas, ¿eh?

**Jony Ayerbe:** Sí, si eh empezas a laburar sobre una carga, esta carga eh en una naviera, los pies dicen, "Bueno, bárbaro, cuando la visión del dueño del negocio es cuando termina esto en x meses, eh me ahorro $,000 por por mes o 5,000 por mes de errores o 000 por mes de errores cuando termin Cuando esto funque, ya estoy haciéndolo, ya estoy, me faltan dos meses, me faltan tres meses, no importa, ya ya

### 00:27:21

**Juan Pablo Norverto:** A ver,

**Jony Ayerbe:** empecé

**Juan Pablo Norverto:** tenemos esa cuenta para que le valor o no no saben.

**Jony Ayerbe:** eh la tengo que pedir. No, no la tenemos menos. se la tengo

**Juan Pablo Norverto:** No, no. Yo, a ver, no, no, no, yo sabes que no sé,

**Jony Ayerbe:** que

**Juan Pablo Norverto:** mi parte de vender no es vender justamente eso es que entiendan cómo trabajamos y bueno, entender que entendemos su negocio.

**Jony Ayerbe:** Sí, pero del otro lado, del otro lado yo te digo cómo está la la persona que decide cómo piensa y que dice mal que mal tengo algo que pago $200, 300, 400 por mes, eh, y con esto va y entonces dice, "Che, tengo que enterrar $40,000 por decirte algo, 000 en crear todo un coso nuevo, pero tengo gente por eso va y contrata el bot de extract, porque es otro que le está cobrando 500 por mes, 00 por m lo que fuere y dice,

**Juan Pablo Norverto:** Mhm.

**Jony Ayerbe:** "Bueno, resolví la mitad de las cosas." Bueno, okay, pero si la alternativa es enterrar 40 lucas verdes, armar algo propio,

### 00:28:22

**Juan Pablo Norverto:** No,

**Jony Ayerbe:** bla bla y hay que le dice por 1000 y 50 por tenés esto que te hace todo,

**Juan Pablo Norverto:** no,

**Jony Ayerbe:** me chupo huevo lo que no uso. Me ajusto a esto. Así piensa el el dueño de

**Juan Pablo Norverto:** por eso, pero por eso te digo es nos van a contratar para también dar eso.

**Jony Ayerbe:** Pyer.

**Juan Pablo Norverto:** entiendeo porque vemos los dos tres errores, nos metemos un poco más a profundizar un poco más en el problema y decir, "Che, mira, si si implementas este sistema, eh, ya resuelve todo estos problemas. ¿Qué hacemos? ¿Lo hacemos nosotros esta lectura o tirar los Excel acá y bla bla bla?

**Jony Ayerbe:** Yo lo que lo que le vendí a la mina es empezamos a laborar sobre los incendios y empezamos a ver el reemplazo de CAI. ¿Cuál es ese reemplazo de Kai? No, si es Magalla podrá ser Magalla. Si es hacer algo de cero, podrá ser hacer algo de cero.

**Juan Pablo Norverto:** Okay.

**Jony Ayerbe:** Pero no quieren lidiar. Acá hay que aprovechar lo que lo, o sea, más allá de lo que sería lo ideal o lo idóneo, acá hay que entender la persona y lo que la persona necesita, teme, quiere, gusta, desea, flashea, anhela.

### 00:29:37

**Jony Ayerbe:** ¿Qué quiere? Están hartos de Cai, están creciendo, vienen a pagar los incendios y si vos le decís, "Ganada la confianza, déjame que yo te reemplazo esto." Les importa tres carajos. Si es TMS, JGK o HZM. Tres carajos les importa si es de un proveedor o si es algo lo O sea, primero ganarse la confianza pagando los incendios. Por eso digo 3 meses y atacar estos problemas. lo que construyamos como solución, esto que estamos viendo, si tiene la concepción, si está ideado para después hacer el backoffice propio, bienvenido sea.

**Juan Pablo Norverto:** No te entiendo perfectamente, pero digo nada quería entender qué tan abiertos o ¿Qué tanto estaban

**Jony Ayerbe:** Vale.

**Juan Pablo Norverto:** viendo? Porque viste, no es un mercado gigante que viste, no sé, no son kioscos, no son restaurantes que tienen sistemas de mesas, ¿me entendés? Eh, nada, se dan vuelta y hay tres, cinco muchos en el mercado que servicios a todos y Cai, ¿no? Que se cayó de ahí. Pero digo también la elección de Cai, me imagino que nada, en su momento fue por por pijotero, ¿no?

### 00:31:00

**Juan Pablo Norverto:** Eh, digo, qué libertad hay, no sé cómo expresarlo para eh qué me no sé si quieren una solución. No, no se no entiendo yo. Es, bueno, por tres meses yo te voy a asignar un equipo que te va a intentar resolver estos problemas. Ese es el speech, digamos, y te va a traer soluciones o qué estos tres problemas vamos a tratar de resolver y no y bueno, nada, vamos a tratar de resolver el primero y empezamos a necesitar información de ello, que pum, que pan y ahí nos damos cuenta que en realidad nada, hacemos esto, pero bueno, esto le va a durar crecer cinco container más, ¿me entendés? Cinco bill of lading más. después de la quinta y bueno, ya le queda chico otra vez. Estoy diciendo por decir eh

**Jony Ayerbe:** Es resolverle los dolores que tiene

**Juan Pablo Norverto:** eh

**Jony Ayerbe:** ahora, ganar la confianza y venderle la transformación entera.

**Juan Pablo Norverto:** Okay. ¿Y cuánto pensaje se le puede fajar por eso?

**Jony Ayerbe:** Eso, ¿qué es lo primero?

**Juan Pablo Norverto:** Lo primero, obvio, lo de ganar la confianza y resolver los problemas.

**Jony Ayerbe:** Es que es que por eso le expliqué lo mínimo que podemos hacer es 3 meses si es 5k

### 00:32:24

**Juan Pablo Norverto:** Ah,

**Jony Ayerbe:** meses.

**Juan Pablo Norverto:** listo, ya tenemos esa base,

**Jony Ayerbe:** Yo no le di el número para nosotros tenemos esa base.

**Juan Pablo Norverto:** ¿eh? Sí, lo que no lo que no va a tener es un equipo 100% dedicado por ese precio. Va a tener un equipo que va a resolver espaciadamente con poco

**Jony Ayerbe:** No.

**Juan Pablo Norverto:** control y va a resolver problemas. Va a estar bien organizado y todo, digamos. o ver un responsable, alguien que se contacte y cada dos semanas le muestre avances, todo, pero se entiende, pero otro ritmo.

**Jony Ayerbe:** lo misma discusión que tenemos con Cursija, con Fefe, con las cosas con los proyectos chiquititos o lo que fuere. Si nosotros cobramos 15 por esta normalización de la data, extracción, carga y black y lo podemos,

**Juan Pablo Norverto:** Tam.

**Jony Ayerbe:** o sea, sería 40 si lo tenemos que hacer en un mes y medio. Bueno, lo cobro 15 y nos podemos tomar 3 meses para hacerlo.

**Juan Pablo Norverto:** Sí,

**Jony Ayerbe:** Tiene que tiene que haber un un project manager de cara a ella,

### 00:33:41

**Juan Pablo Norverto:** sí.

**Jony Ayerbe:** tiene que haber un seguimiento. tiene que estoy yo y me meto yo en mi en en tiempos este que tengo que no le

**Juan Pablo Norverto:** No, no tiene que haber un pro A ver quiénes van a liderar los productos.

**Jony Ayerbe:** pongo.

**Juan Pablo Norverto:** van a ser Oli, Danilo, Lucía, Natalia y bueno, en su defecto Jefe, vos y yo, pero Fefe y yo tenemos que empezar a despegarnos de de estar ahí en en el lo minucioso,

**Jony Ayerbe:** Danilo y Oli. Lucía Natal están año luz de llevar a un

**Juan Pablo Norverto:** ¿no? Nada que ver, pero bueno,

**Jony Ayerbe:** cliente.

**Juan Pablo Norverto:** eh lo viví con yo solo con Terratio, así que eh para nada, digamos. se encargaron de todo el diseño solas sin que nadie se meta.

**Jony Ayerbe:** Pero otras dimensiones de llevar la cuenta,

**Juan Pablo Norverto:** Un año y medio de L2.

**Jony Ayerbe:** estoy diciendo.

**Juan Pablo Norverto:** No, no. Una cosa es llevar una cuenta, otra cosa es llevar el producto.

**Jony Ayerbe:** Okay.

**Juan Pablo Norverto:** Sí. No, no es cara llevar la cuenta. La llevamos nosotros, digamos, responsable de cuentas si quiere eh, por decirle algo, ellos no tienen que reportar a nosotros, pero ¿quién lleva el día a día con los desarrolladores?

### 00:34:54

**Juan Pablo Norverto:** Y tenemos que estar dejar tenemos que dejar de estar metidos ahí.

**Jony Ayerbe:** Sí, sí.

**Juan Pablo Norverto:** Porque no crecemos y no. Eh, por eso estamos haciendo todo esto. Estoy armando todo lo de la capacitación. Ahora lo de lo de lo de Curciija lo va a llevar Danilo con Lucía. Lo de ahora viene una segunda parte Megalab Natalia, ya le dije, eh, y bueno, hay que amigarse con las herramientas de gestión. me me inguniaron todo el año pasado el anterior click. Hay que amigarse. Seguramente volvamos, pero bueno, tiene que ser a fondo. va a salir para mí,

**Jony Ayerbe:** Volviendo a esto, volviendo a esto,

**Juan Pablo Norverto:** No.

**Jony Ayerbe:** para mí lo que funciona acá es decirles, no sé si hay que, no sabemos todavía si hay que darte otro sistema de de management, de transporte y hacer una transición a otro SAS. No sé si te vamos armando algo.

**Juan Pablo Norverto:** Escucho,

**Jony Ayerbe:** No sé si vamos armando algo nosotros e a

**Juan Pablo Norverto:** eh.

**Jony Ayerbe:** medida de la operación de tu empresa.

### 00:36:26

**Jony Ayerbe:** Lo vamos a saber una vez que arranquemos y que hagamos 70 doble clics distintos,

**Juan Pablo Norverto:** Mhm.

**Jony Ayerbe:** pero ahora nos vamos a meter por un tiempo de 3 meses que no se puede tener nada bueno, robusto, probado, testeado y demás. En menos de 3 meses nos vamos a meter en 3 meses a resolver estos tres puntos.

**Juan Pablo Norverto:** encarar estos tres puntos. Okay. No sé si resolver, ese es el problema también,

**Jony Ayerbe:** Sí, yo

**Juan Pablo Norverto:** una promesa de resolver en tr meses tres puntos que capaz se

**Jony Ayerbe:** sí.

**Juan Pablo Norverto:** transforman en un painting de los tres. ¿Qué hacemos? Porque capaz hacés todo lo mejor que podés, pero realmente la información que le llega siempre es tan mala que es imposible hacer que funcione bien. Y

**Jony Ayerbe:** La información,

**Juan Pablo Norverto:** ahí

**Jony Ayerbe:** la información que le llega no es eh siempre tan mala ni es mala.

**Juan Pablo Norverto:** no estoy diciendo es un ejemplo nada más, no estoy diciendo que sea así. Es es un ejemplo tonto, digamos, de decir, che, los exel esos que nos mostraron y la mitad los terminan completando ellos con información que tienen en el WhatsApp, por decir algo, ¿no?

### 00:37:46

**Juan Pablo Norverto:** Pero bueno, es

**Jony Ayerbe:** ¿Qué tajo es un punto eml?

**Juan Pablo Norverto:** eh

**Jony Ayerbe:** un documento, un adjunto del mail de la mina que es punto

**Juan Pablo Norverto:** son todos los cuatro adjuntos son mails.

**Jony Ayerbe:** em

**Juan Pablo Norverto:** Te adjuntaron mails. ¿Dónde está la información?

**Jony Ayerbe:** claro. E,

**Juan Pablo Norverto:** Le das doble clic y se abre un mail.

**Jony Ayerbe:** pero algunos me abren y otros no. Eso

**Juan Pablo Norverto:** Ah.

**Jony Ayerbe:** er enviar instrucción de transporte. El sociedad anónima.

**Juan Pablo Norverto:** Porque si, bueno, si lo vamos a hacer así, sí, yo lo que no no quiero es que prometamos algo que capaz las expectativas como siempre, No, eh, lo de lo de Curci es bastante diferente porque es super puntual, tipo F se sentó, lo pimponeó, lo solucionó y y además era super puntual, ¿no? Era este me viene 20 cosas por acá, por allá, no sé qué hacer, falla por un lado que no sé dónde falla.

**Jony Ayerbe:** Bueno,

**Juan Pablo Norverto:** Bueno, eso este que es factible que el primer mes estemos por eso yo no sé si tres meses es es muy poco, pero el primer mes estemos más deep dive en toda la problemática y en entender más eh centrados en el problema A, B y C. Sí, pero bueno, eso te puede llevar tiempo, que capaz ellos tiempo no tienen para darte pelota, entonces eso hace que se retrase poder empezar a hacer algo y

### 00:39:38

**Juan Pablo Norverto:** bla.

**Jony Ayerbe:** Mira, este es el paso a paso en la página de Mars y esto es automatizable por eh APIES de transform

**Juan Pablo Norverto:** Mm.

**Jony Ayerbe:** Porte, eligen

**Juan Pablo Norverto:** Yo yo lo que digo para mí lo que sí o sí tenemos que hacer es lograr que por lo menos las tres primeras semanas podamos

**Jony Ayerbe:** Chen.

**Juan Pablo Norverto:** hacer un deep dive en todo esto para detectar realmente que lo que vamos a construir es tal cosa. Vamos a resolver la integración esta, por ejemplo, mandándole archivos que subís acá. Punto. Sí. y le hacés el cosito donde subir archivos o que lea de una carpeta y los pase a otra. No importa, ¿me entendés? No digo desarrollar el backoffice, es desarrollar ese flujo que necesita ser automatizado. Puede ser con NHN, como dijiste

**Jony Ayerbe:** El tema es,

**Juan Pablo Norverto:** también.

**Jony Ayerbe:** no es esa la complejidad. La complejidad es cómo la cargo en la página.

**Juan Pablo Norverto:** ¿En qué página?

**Jony Ayerbe:** No, no olvíate de Cai.

**Juan Pablo Norverto:** C.

**Jony Ayerbe:** Esto es de cliente a correo y de correo a naviera, el pedido formal a la naviera, o sea, que no tenga errores.

### 00:41:11

**Jony Ayerbe:** Ese es lo crítico acá. Esto es lo crítico, agarrar esto. Agarrar esto. Por eso no, yo no para mí no debería ser, boludo, tr meses de tr semanas de de deep dive. Esto es una instrucción de embarque que llega en un documento. Sí. Entonces,

**Juan Pablo Norverto:** Entonces,

**Jony Ayerbe:** escucha, exportador, consignatario, marcas, números, número de piezas, descripción, kilos, número de permiso, eh buque, punto de

**Juan Pablo Norverto:** Perdón, eh, perdón, Johnny,

**Jony Ayerbe:** carga,

**Juan Pablo Norverto:** eh, pero yo no puedo estimar algo viendo un documento así, ¿me entendés?

**Jony Ayerbe:** boludo.

**Juan Pablo Norverto:** Hicimos, hicimos un Discovery hace un mes y medio ya, dos, no sé cuánto pasó, eh, no sé qué pretend que te diga, si es tan difícil, tan fácil. digamos, no lo sé, tengo que entenderlo de otra manera, tengo que tener el tiempo para entenderlo. Ese es el mi problema, digamos. Eh, no puede salir una estimación de si vos me decí, "Che, en tr meses hacemos esto." Sí, es una es una estimación, pueden ser cuatro.

### 00:42:27

**Jony Ayerbe:** Pero por supuesto que es una estimación. Ese no es el Es que nadie está nadie está pidiendo ahora decime en qué

**Juan Pablo Norverto:** Por eso digamos, no,

**Jony Ayerbe:** fecha se entrega y decirme cuántos.

**Juan Pablo Norverto:** No.

**Jony Ayerbe:** No, no, nadie está pidiendo eso. Este, estoy comentando con los documentos reales a dónde está el el nudo de la cuestión para nosotros decir, bueno, esto es algo encarable. le tenemos que pasar como mínimo tres o me decís como ahora,

**Juan Pablo Norverto:** para

**Jony Ayerbe:** pasémosle como mínimo 4 meses. ¿Y qué vamos a vender? Ya te dije, vamos a vender un equipo porque si no no nos resulta a nosotros ni a ellos. Vamos a vender un equipo que va a atacar el listado prioritario de problemas que tienen y que en el camino vamos a ver cómo se puede proveer una solución más escalable, más longm. Ahora es resolver estas cuestiones. Hay personas que están cargando 400 de estas por mes.

**Juan Pablo Norverto:** Mm.

**Jony Ayerbe:** Buenísimo. En dos meses o en tr meses poder reducir 30% de esa carga, yo te digo que le va a haber valido la pena y es una buena promesa y no lo podemos hacer en tr meses porque necesitamos 3 meses y medio.

### 00:43:53

**Jony Ayerbe:** es otra discusión. Eso se ve en la venta, ¿entendés? Se ve en esta propuesta que le voy a hacer a ella.

**Juan Pablo Norverto:** Mm.

**Jony Ayerbe:** Pero pongámonos de acuerdo en que hoy no podemos saber más de lo que sabemos.

**Juan Pablo Norverto:** A

**Jony Ayerbe:** Le puedo hacer un par de preguntas más que le voy a hacer. eh costo de los errores,

**Juan Pablo Norverto:** ver.

**Jony Ayerbe:** más o menos si lo tienen medido. No podemos saber mucho más de lo que sabemos hoy y tenemos que ir a venderle un plancito de gente que está pensando, una agencia, una desarrolladora de soluciones digitales que está pensando, "Te voy a ir sacando quilombos de encima sin decirte,

**Juan Pablo Norverto:** Mhm.

**Jony Ayerbe:** te voy a rehacer todo el sistema operativo o tu RP de cero." y nosotros decir, bueno, hay un project manager, puedo estar yo supervisando, investigando y llevando y llevándolo arriba con quien sea que esté acá y esa persona puede darse vuelta y consultarle a un desarrollador más que no va a estar full time, sino part time para esto. ¿No sirve cinco lucas meses, eso 3 meses o 4 meses?

**Juan Pablo Norverto:** Y ahí todo nos

### 00:45:11

**Jony Ayerbe:** No,

**Juan Pablo Norverto:** sirve.

**Jony Ayerbe:** no nos encaja dentro del modelo de tiempo de alocación de recursos, de dinero. Bueno, vendamos eso y vayamos a hacer lo mejor que podemos.

**Juan Pablo Norverto:** Sí, sí.

**Jony Ayerbe:** Yo así a ojo de almacenero tener este documento, por eso te lo estaba mostrando, este documento, tener este documento distinto a ese distinto a ese a ese Word. Este documento sigue teniendo buque, puerto de carga, cantidad, bla, bla, bla, consignatarios, el mismo nombre, carga, cantidad de bultos, contenedor, marca y número es lo mismo. Los pesos y sarasa es esto. Hm. a a ojo de almacenero, de nuevo, no estoy haciendo una estimación. Digo, bueno, podemos extraer data porque hice testeos y la pude extraer bien. Podemos extraer data la podemos normalizar. Sí. Bueno, no es una no es una una dificultad que no no sepamos cómo resolverla. La podemos normalizar, ¿sí? Después hay que entrar a la página de MASK y ahí hay que cargarla. Si en ese paso empezamos a meter soluciones de RPA, entonces arriba de nuestro costo están el costo de setup, de contratación, las dos lucas acá, las cinco, un motor.

### 00:47:00

**Jony Ayerbe:** Si vamos directamente con API, nos puede llevar un mes a hacer la API, no importa. Pero si vamos con API,

**Juan Pablo Norverto:** Listo.

**Jony Ayerbe:** va a servir solo para las navieras que tengan la carga vía API, pero tiene un valor de la p\*\*\* madre desarrollarle eso a

**Juan Pablo Norverto:** Es que cada nava tiene su API.

**Jony Ayerbe:** ellos.

**Juan Pablo Norverto:** Vos normalizás los datos para poder mandarle a cada naviera después.

**Jony Ayerbe:** Está bien. Y hay algunas que no tienen API. Entonces, esa es otra pregunta que le puedo hacer ahora. El 90% del volumen que tenés, porque la idea es sacarle las 400 cargas manuales por por mes que tiene la mina.

**Juan Pablo Norverto:** Sí.

**Jony Ayerbe:** Entonces,

**Juan Pablo Norverto:** ¿Cuál es la navera que más

**Jony Ayerbe:** che,

**Juan Pablo Norverto:** usas?

**Jony Ayerbe:** Mars y Jap, te lo soluciono por API, son dos API, lo cargo, no tengo errores, te resolví el 80% del problema este y podemos hacer solo eso por 3

**Juan Pablo Norverto:** Claro. Sí.

**Jony Ayerbe:** meses. Bueno, para mí, para nosotros no pifeiar, Juancho, lo que tenemos que hacer es determinar que un PM con un supervisor, con parttime de un developer y herramientas de IA es nuestro equipo.

### 00:48:07

**Jony Ayerbe:** Eso es lo que tenemos que resolver acá y decir y

**Juan Pablo Norverto:** es lo que estamos construyendo. No, no, no te sé

**Jony Ayerbe:** decir eso vale 5 K mes y después yo le voy al cliente y le digo,

**Juan Pablo Norverto:** decirlo.

**Jony Ayerbe:** mira, 3 cu meses mínimo y vemos a dónde llegamos. ¿Listo? Y entonces tenemos Danilo más herramienta más un Johnny, un Juan un F jefe cinco a cada mes y empezamos a vender de esos.

**Juan Pablo Norverto:** Claro,

**Jony Ayerbe:** Eso es como lo tenemos que estructurar.

**Juan Pablo Norverto:** pero bueno, pero lo estamos armando. Esto no sirve para probar,

**Jony Ayerbe:** Bueno, listo, tiremos en lances, boludo.

**Juan Pablo Norverto:** obvio.

**Jony Ayerbe:** Yo más de C Lucas, este pie no va, no creo que ponga.

**Juan Pablo Norverto:** Okay,

**Jony Ayerbe:** No,

**Juan Pablo Norverto:** okay,

**Jony Ayerbe:** no lo sé, no lo sé,

**Juan Pablo Norverto:** okay.

**Jony Ayerbe:** pero

**Juan Pablo Norverto:** Este, más servidores y esas cosas le tenes que decir, ¿no?

**Jony Ayerbe:** sí sí. todos los gatos, boludo, de todo lo que

**Juan Pablo Norverto:** Infraestructura

**Jony Ayerbe:** contratemos.

**Juan Pablo Norverto:** una no sirve para ver sin dudas. Sí, yo me tengo que otra.

**Jony Ayerbe:** Dale. Todo bien. Nacho que querías pasar a buscar algo por acá. Nosotros nos vamos en 5, 10 minutos.

### La transcripción finalizó después de 00:49:29

*Esta transcripción editable se generó por computadora y puede contener errores. Los usuarios también pueden cambiar el texto después de que se cree.*

# Pestaña 6

Las notas  
Basado en las notas de la reunión de Quarks \- Loginetsa, las principales áreas de mejora sugeridas, enfocadas en reducir la fricción, automatizar procesos internos y mejorar la integración de sistemas, son:  
1\. Propuesta de Discovery e Implementación Iterativa (Estratégica):

* Realizar un *Discovery* Completo: Formalizar la sugerencia de Jony Ayerbe. El primer paso debe ser un proceso estructurado de *Discovery* (sesiones de trabajo/workshop) para mapear el 100% de los procesos comerciales, operativos y administrativos.  
* Enfoque en MVP y Soluciones de Alto Valor/Bajo Costo: La propuesta de mejora resultante del *Discovery* debe priorizar la implementación de un Producto Mínimo Viable (MVP) que ataque inicialmente los puntos de mayor fricción y valor con el menor costo y tiempo posible, como la verificación documental o la automatización del rastreo interno.  
* Gestión del Cambio y Colaboración Interna: Abordar la reticencia de la persona a cargo del sistema *K* (Pablo). La mejora de la integración depende de la colaboración, por lo que el proceso de *Discovery* debe involucrar a todas las partes clave para asegurar la adopción de las nuevas soluciones.

2\. Automatización y Control del Proceso Documental (Operativo/Administrativo):

* Sistema de Chequeo Documental Instantáneo (IA/Automatización): Implementar una solución (posiblemente con IA) que compare automáticamente la declaración de embarque (Excel del despachante) con la confirmación de la reserva (*booking*) y el posterior *Bill of Lading* (BL), alertando sobre errores antes de enviar la *shipping instruction*. Esto reduciría los errores costosos y la necesidad de correcciones tardías.  
* Eliminación de la Transcripción Manual de BL: Automatizar la carga de la información del BL al sistema *K* para evitar la duplicidad de trabajo y los errores de transcripción manual, que se dan incluso con el uso del sistema *Extract*.  
* Estandarización de Datos de Entrada: Trabajar con los despachantes para asegurar que la declaración de embarque (el Excel) tenga un formato consistente y fácil de procesar para una posterior automatización de la carga en la plataforma de la naviera.

3\. Mejora de la Integración de Sistemas (Tecnológica):

* Integración de Rastreo de Carga (*Cargoes*): Concretar la integración entre el sistema de rastreo *Cargoes* y el sistema interno *K* para que las fechas de seguimiento y las alertas de demoras se actualicen automáticamente en el sistema de gestión, eliminando la necesidad de gestión manual de la información de corte y seguimiento en el Excel diario.  
* Unificación de la Información Crítica: Centralizar la información clave (detalles de reserva, *tracking*, cotizaciones, actividad comercial, fechas de corte) que actualmente está dispersa entre *K*, Excel y correos electrónicos, en un único sistema inteligente que soporte la operatoria completa.

4\. Optimización de Procesos Comerciales y de Facturación:

* Automatización del Proceso de Cotización: Crear una herramienta que aglomere la información de salidas, rutas y opciones de navieras (posiblemente utilizando datos históricos de la compañía) para que el equipo comercial pueda realizar cotizaciones de forma más rápida y menos manual, reemplazando el uso intensivo de Excel.  
* Automatización de la Facturación de Venta: Automatizar la facturación al cliente basada en la confirmación de la salida del buque (*zarpe*), siempre y cuando el BL esté correctamente cargado y la cotización en el sistema.  
* Solución a la Fricción de Facturas de Compra (*Extract* y *Rock*): Revisar la lógica de la coincidencia de facturas de compra. El sistema debe ser flexible para conciliar la factura de la naviera con el ítem interno (*Rock*), incluso si no hay una coincidencia exacta de monto o contenedor, o bien, generar automáticamente el *Rock* a partir de la cotización aceptada y la factura de la naviera con mayor inteligencia para la conciliación.

24 feb 2026  
**Quarks \- Loginetsa**  
Invitados Jony Ayerbe  
Archivos adjuntos [Quarks \- Loginetsa](https://www.google.com/calendar/event?eid=N2ZrNjdwbTVxb2gxcmdlcW81MmtranA0ZG0gam9uYXRoYW5AcXVhcmtzYWxjaGVtaXN0LmNvbQ)  
Registros de la reunión [Grabación](https://drive.google.com/file/d/1RqrHdAFeincbb0JawwHEJ7MvFPxsliIV/view?usp=drive_web)  
**Resumen**  
Fricciones en Sistemas Operacionales  
La compañía depende de sistemas multimodales existentes, como Khai y Extract, los cuales presentan problemas de fricción, especialmente en la carga de facturas de compra debido a la falta de coincidencia exacta con las órdenes internas (Roc) generadas manualmente a partir de cotizaciones.

Problemas Documentales e Integración  
Se identificó que la integración entre los sistemas es deficiente, impidiendo la automatización completa y generando errores costosos debido a la transcripción manual de información crítica, como los detalles de las reservas y los documentos de embarque (BL).

Propuesta de Discovery e Iteración  
Se decidió realizar un proceso de descubrimiento (Discovery) para mapear todos los procesos, enfocado en una propuesta de mejora iterada y escalable que priorice soluciones de valor mínimo viable (MVP) para automatizar los flujos internos más críticos  
**Detalles**

* Sistemas de Transporte y Operación Actual: La compañía se enfoca en transporte multimodal, combinando principalmente camión y transporte marítimo. Utilizan un sistema en línea llamado *K* (Kai o C), el cual ha evolucionado desde sus inicios y maneja aspectos administrativos, contables, financieros y comerciales. También emplean un sistema llamado *Extract* que lee facturas en PDF y vuelca la información al sistema principal, aunque presenta fricciones cuando los datos no se cargan o arroja errores.  
* Fricciones en el Proceso de Carga de Facturas: El sistema *Extract* lee las facturas perfectamente, pero el proceso de carga no es completamente automático debido a la necesidad de hacer coincidir el monto de la factura con un ítem interno (*Rock*) que se genera a partir de una cotización. Si el número de contenedor y el importe exacto del *Rock* no coinciden con el importe neto de la factura, el sistema no la carga y arroja un error. El *Rock* funciona como una orden de compra que la administración debe generar manualmente a partir de una cotización cerrada.  
* Uso de Extract para Documentación Operativa: El mismo sistema *Extract* que procesa las facturas también se utiliza para manejar la documentación operativa, como los *Bill of Lading* (BL), que son documentos de transporte esenciales. Este sistema lee los BL y carga la información directamente en el sistema *K*.  
* Proceso Documental de la Operación y el BL: El proceso comienza con una cotización que abre una operación en el sistema y coordina la carga. El cliente proporciona una declaración de embarque, que se convierte en una *shipping instruction* que se sube a la naviera, y la naviera devuelve el BL. Para optimizar el proceso, ahora se carga la información directamente del BL para evitar duplicidad de trabajo en el sistema interno y el de la naviera.  
* Sistema de Rastreo de Cargas y Alertas: Se ha adquirido otro sistema, llamado *Cargho*, que fue desarrollado por unos árabes de su rubro y se utiliza para rastrear el estado de los contenedores en las páginas web de las navieras. Este sistema, que está operativo y en prueba, envía reportes diarios y alertas a los clientes sobre posibles demoras causadas por trasbordos o incumplimientos del tiempo de tránsito. No obstante, la actualización automática de las fechas de seguimiento en el sistema *K* aún no se ha podido concretar.  
* Problemas de Integración de Sistemas y Recursos Humanos: Existe un problema de integración entre los sistemas que impide la automatización completa de los procesos administrativos y operativos. Facundo Ramirez sugirió que el problema podría residir en Pablo, la persona a cargo del sistema *K*, quien es reacio a reunirse o colaborar en las integraciones necesarias para que todo funcione de manera eficiente. El negocio, que opera con poco margen, se ve afectado por errores costosos, a menudo de tipo documental, que se dan en el proceso de transcripción manual de información.  
* Propuesta de Automatización de Chequeo Documental: Los errores son comunes cuando la información se copia y pega manualmente, a menudo a contrarreloj o después de la fecha límite. Se sugirió la posibilidad de implementar un sistema, posiblemente con inteligencia artificial, que compare la declaración de embarque con el BL y alerte sobre errores de manera instantánea. La corrección ideal debe hacerse en la etapa previa, entre la declaración y la *shipping instruction*, ya que corregir el BL después de emitido suele tener un costo.  
* Obstáculos en la Comunicación con Agentes Externos: Jony Ayerbe señaló que el protocolo estandarizado para que un sistema se comunique con otro es el *API* (protocolo MCP), y si la naviera no cuenta con este protocolo, un agente automatizado no puede interactuar o iniciar sesión en su página. Actualmente, solo utilizan el sistema *INTRA* para presentar *shipping instructions* a pocas navieras, siendo el resto manejado directamente a través de las páginas propias de cada naviera.  
* Foco en la Integración y la Automatización de Procesos Internos: La prioridad actual es evaluar si los sistemas existentes son adecuados y, de ser así, enfocarse en cómo ensamblar e integrar todas las partes desconectadas. Facundo Ramirez enfatizó que la tendencia del negocio apunta a la automatización de procesos internos, como el envío de facturas y el rastreo de envíos, mientras que el valor humano se enfoca en la personalización del servicio.  
* Automatización en el Proceso de Venta y Cotización: El proceso de venta actual es ineficiente y manual, requiriendo que se coticen clientes existentes o nuevos en base al origen y destino de la carga. Facundo Ramirez y Manuel Vasquez indicaron que la facturación se podría automatizar basándose en el rastreo del estado de la carga una vez que el buque zarpa. Manuel Vasquez también mencionó que la automatización de la facturación de compra es difícil debido a errores en la facturación de las navieras, lo que requiere intervención humana para conciliar los datos.  
* Necesidad de un *Discovery* y Enfoque Iterativo: Jony Ayerbe sugirió que el panorama actual derivaría en una propuesta de un *discovery* completo para mapear todas las áreas, seguido de una propuesta de mejora que se implementará de forma iterada. Enfatizó la importancia de empezar con soluciones mínimas y escalables, enfocándose en un *MVP* (*Minimum Viable Product*) para validar el proceso antes de invertir en una solución compleja.  
* Proceso de Cotización y Apertura de Operación: Actualmente, la cotización se realiza de forma manual en un Excel, ya que el uso del sistema resulta menos práctico debido a la cantidad de destinos y la naturaleza estacional del trabajo. Una vez que el cliente acepta, se carga la cotización en el sistema para abrir una operación, momento en el cual el equipo operativo procede a generar la reserva (*booking*) en el sistema de la naviera.  
* Flujo de Trabajo Operacional: Del Booking a la Coordinación: Un miembro del equipo operativo ingresa manualmente los detalles de la carga en el sistema de la naviera, la cual devuelve una confirmación de *booking*. Esta confirmación, que incluye todos los detalles de la salida, se carga en el sistema interno para abrir la operación y coordinar el proceso con el cliente, incluyendo el manejo de camiones y órdenes de retiro.  
* Flujo de Documentación y Necesidad de Chequeo Rápido: El despachante envía la declaración de embarque a la empresa, que luego utiliza esta información para presentar la *shipping instruction* a la naviera. La naviera devuelve el BL, el cual se chequea manualmente para verificar que no haya errores comparándolo con la declaración de embarque. Este chequeo se hace de forma visual en la pantalla y es un proceso manual y tedioso, especialmente durante la temporada alta.  
* Verificación de Diferencias en Documentos: Una revisión experimental con comandos de inteligencia artificial para comparar la declaración y el BL fue exitosa, pero requería mucho tiempo (10 minutos por BL), lo que la hace inviable en temporada alta. Vanina Focaraccio destacó que la clave es realizar la verificación de diferencias antes de presentar la *shipping instruction*, ya que, una vez emitido el BL, la mayoría de las correcciones conllevan un costo.  
* Ineficiencias en el Proceso Comercial y Operativo: El proceso operativo se ve presionado por plazos estrictos de las navieras para la entrega de documentación y contenedores. La información de las salidas y los *deadlines* de carga, que proviene del *booking*, es gestionada y actualizada manualmente por el personal, lo que implica una pérdida de tiempo. Además, en la parte comercial, la búsqueda de opciones de envío requiere que los comerciales revisen manualmente las *webs* de diferentes navieras, lo cual genera ineficiencias.  
* Propuesta de Automatización de Rutas y Seguimiento Histórico: Facundo Ramirez sugirió que se debería aglomerar toda la información de salidas, rutas y opciones de navieras para que la búsqueda comercial sea más rápida. Vanina Focaraccio propuso utilizar el historial de seguimiento de la compañía para recomendar rutas más eficientes, basándose en datos históricos de tránsito en lugar de los tiempos estimados proporcionados por la línea.  
* Compromiso de Documentación Adicional: Vanina Focaraccio se ofreció a compartir un documento detallado con el paso a paso de los procesos comerciales, operativos y administrativos, para facilitar la comprensión y la posible automatización de Jony Ayerbe. Esto ayudará a Jony Ayerbe a comparar notas y determinar dónde se puede automatizar todo el flujo de trabajo.  
* Proceso de Confirmación de Reserva (Booking) y Documentación Inicial: Vanina Focaraccio explicó el proceso de reserva, citando que la información de destino y origen de un viaje, incluida la fecha de salida y los detalles del buque, se envía a la línea naviera para su confirmación. Una vez que la línea confirma, esta información se transforma en el *booking confirmation* interno, que es simplificado para el cliente e incluye detalles como el número de reserva, la semana de salida y el buque, información crítica para que el despachante de aduanas inicie su trabajo. También se mencionó que una vez que se confirma la reserva, se solicita la Orden de Retiro (OR) al cliente.  
* Gestión de Fechas de Corte y Documentación de Carga: La conversación giró en torno a los cortes documentales (*cut-off doc*) y físicos (*cut-off ops*). La información de estas fechas se gestiona actualmente volcándola manualmente en un archivo Excel, el cual el equipo revisa diariamente para monitorear los vencimientos. Cada miembro del equipo filtra el Excel según sus necesidades, como el corte documental o la información necesaria para liberar el arribo y la salida.  
* Servicios Ofrecidos a Clientes y Declaraciones de Embarque: Se detalló que se les proporciona al cliente una orden de retiro para que puedan recoger el contenedor en la terminal, junto con el *booking* propio para que tengan todos los detalles. La empresa gestiona el espacio marítimo para el cliente, ofreciendo servicios que pueden variar desde solo la parte marítima hasta incluir el transporte terrestre (recoger, cargar, consolidar y devolver el contenedor al puerto) o el depósito para la carga. La información de las declaraciones de embarque es un Excel que el despachante envía con los detalles del *shipper*, el consignatario y el número de reserva por contenedor.  
* Proceso de Carga de Información de Embarque en el Sistema: Se confirmó que la información de las declaraciones de embarque contenida en el Excel debe ser volcada manualmente (copiar y pegar) en la plataforma web de la naviera para el *shipping instruction*. Jony Ayerbe notó que esta carga se realiza "a dedo". Vanina Focaraccio indicó que manejan un gran porcentaje de transporte marítimo (90%).  
* Navieras y Destinos Principales Manejados: Facundo Ramirez mencionó que trabajan con alrededor de diez navieras, siendo dos o tres de ellas las principales debido a los destinos comunes. Los destinos que más se manejan son aproximadamente veinte. Se señaló que existen líneas especializadas (como las asiáticas) y líneas europeas que cubren todos los destinos principales (CA, Hapag, MCC y Maersk).  
* Confirmación de Salida y Procesos de Facturación: Después de que la carga está lista para el embarque, se confirma la salida del buque y se notifica al cliente que sus contenedores han sido cargados y han salido, informando si la fecha se modificó. A partir de este momento, interviene la administración, que tiene hasta 48 horas para facturar al cliente. Para la facturación se requiere que el *Bill of Lading* esté cargado correctamente, que la salida esté confirmada (zarpe) y que la cotización esté cargada en el sistema.  
* Control de Facturas de Compra de las Marítimas: Tras la salida del buque, las líneas marítimas también facturan a la empresa, generalmente 48 horas después. El control de estas facturas de compra es manual, donde se compara la factura recibida contra la cotización de compra cargada en el sistema. Si los datos coinciden, se genera una orden de compra (*rock*).  
* Errores en la Carga de Cotizaciones y la Problemática del Sistema de Gestión: Los errores más comunes ocurren cuando el personal comercial carga la cotización de compra y venta en el sistema interno, no al enviarla al cliente. El área de facturación se basa únicamente en la información cargada en el sistema. Se identificó que el sistema actual de gestión (Kai) es limitado, ya que la información clave (detalles de reserva, *tracking*, cotizaciones, actividad comercial) está dispersa entre el sistema, Excel, y correos electrónicos, sin un sistema inteligente que gestione la operatoria completa.  
* Proceso de Liberación de Carga y Necesidad de Alertas: La liberación de la carga generalmente se realiza con la emisión de *Bills of Lading* (BLS) en destino. La empresa instruye a la línea naviera a liberar la carga cuando el cliente lo autoriza, idealmente antes de que llegue el contenedor para evitar gastos. Se necesita una alerta o notificación (por ejemplo, 48 horas antes de la llegada) para movilizar la documentación y acciones de liberación. La liberación requiere verificar si el flete fue pagado por el cliente y obtener la autorización explícita del cliente para liberarla.  
* Propuesta de Solución: Un Proceso de Discovery e Inteligencia en el Sistema: Jony Ayerbe propuso que se necesita un sistema que aporte inteligencia al proceso. Se plantea un *Discovery* (sesiones de trabajo o *workshop*) como primer paso, el cual resultará en una propuesta detallada de alcance, tiempos y costos, atacando inicialmente los puntos que ofrezcan el mayor valor con el menor costo. El equipo de Jony Ayerbe enviará preguntas estructuradas de forma asincrónica antes de proponer el *Discovery* para validar el entendimiento del proceso.

**Pasos siguientes recomendados**

* Vanina Focaraccio pasará el detalle de lo que hacen los departamentos comercial, operativo y administrativo a Jony Ayerbe.  
* Jony Ayerbe procesará la información obtenida en la reunión y volverá con un correo electrónico con una serie de preguntas más estructuradas a Facundo Ramirez, Vanina Focaraccio y Manuel Vasquez.

*Revisa las notas de Gemini para asegurarte de que sean correctas. [Obtén consejos y descubre cómo toma notas Gemini](https://support.google.com/meet/answer/14754931)*  
*Danos tu opinión sobre el uso de Gemini para tomar notas en una [breve encuesta.](https://google.qualtrics.com/jfe/form/SV_9vK3UZEaIQKKE7A?confid=O5KJ4zcv_NDLEeSDS-0PDxIUOAIIigIgABgFCA&detailid=standard)*

# Pestaña 7

# Pestaña 8

abr 6, 2026

## Loginet 2do mapeo

Invitado [vanina.focaraccio@loginetsa.com](mailto:vanina.focaraccio@loginetsa.com) [Jony Ayerbe](mailto:jonathan@quarksalchemist.com) [Juan Pablo Norverto](mailto:juan.norverto@quarksalchemist.com) [manuel.vasquez@loginetsa.com](mailto:manuel.vasquez@loginetsa.com) [Danilo Luce](mailto:danilo@quarksalchemist.com) [anahi.cappi@loginetsa.com](mailto:anahi.cappi@loginetsa.com)

Archivos adjuntos [Loginet 2do mapeo](https://calendar.google.com/calendar/event?eid=NjYyaDZrdWw0ZzFza3ZmOGIza2FuYnA3cjggam9uYXRoYW5AcXVhcmtzYWxjaGVtaXN0LmNvbQ)

Registros de la reunión [Grabación](https://drive.google.com/file/d/1FU51-XfeoQbUUkoc-iyV_0Ye450uo9t_/view?usp=drive_web) 

### Resumen

El equipo analizó flujos operativos y automatización mediante herramientas externas para optimizar procesos de facturación interna.

**Análisis flujo comercial operativo**  
La discusión cubrió la carga de cotizaciones en KAI y los desafíos operativos al gestionar documentación para embarques. Se identificó la falta de cotizaciones cargadas como un cuello de botella crítico para la facturación.

**Automatización con herramientas externas**  
El uso de la herramienta Extract facilita la carga masiva de facturas, aunque requiere generación manual de una prefactura. El equipo explorará mejoras para validar datos antes de cargarlos en KAI.

**Optimización del proceso administrativo**  
Se decidió fortalecer los controles previos a la carga en KAI mediante herramientas externas y reportes. El objetivo es mantener el sistema actual optimizado en lugar de implementar cambios estructurales complejos.

### Próximos pasos

- [ ] \[El grupo\] Implementar Recordatorio: Configurar aviso automático en el sistema para cotizaciones faltantes. Disparar el recordatorio al iniciar la operación en Excel.

- [ ] \[Juan Pablo Norverto\] Analizar Conversión: Evaluar la construcción del patrón de datos de Carghost. Desarrollar una tabla de conversión de siglas a nombres de puertos para Kai.

- [ ] \[Anahi Cappi\] Coordinar Reunión: Agendar encuentro con Kai para discutir compatibilidad del sistema. Analizar opciones de automatización y nomenclaturas.

- [ ] \[Anahi Cappi\] Preguntar Extract: Determinar requisitos necesarios para automatizar proceso de validación de facturas.

- [ ] \[Anahi Cappi\] Consultar Kai: Solicitar a Kai un reporte más detallado de costos pendientes para apoyar validación externa.

- [ ] \[Jony Ayerbe, Juan Pablo Norverto\] Revisar Estrategia: Digerir, analizar información recopilada. Volver con preguntas pendientes para generar sugerencia, análisis, propuesta.

- [ ] \[Manuel Vasquez\] Coordinar Circuito: Avisar a Manuel Vasquez para coordinar una reunión adicional. Revisar dudas sobre el circuito administrativo si es necesario.

### Detalles

* **Revisión de la Parte Comercial y Operativa Anterior**: Jony Ayerbe inició con un resumen de la parte comercial, que abarca desde la consulta hasta el cierre de la cotización, identificando posibles "puntos de dolor" como la comunicación por WhatsApp con el cliente y el asistente. El proceso continúa con la carga de la cotización en KAI y el \*booking\*, lo que da inicio a la operación en un archivo Excel.

* **Consolidación y Documentación Operativa**: La fase operativa se describió, comenzando con el Excel, y abordando opciones de consolidación en origen o en depósito fiscal. Se mencionó que el seguimiento de contenedores, si lo contrata el cliente, es un servicio que, si se automatiza, añadiría valor. Los documentos clave para las instrucciones de envío (\*shipping instruction\*) incluyen la declaración de embarque, permiso de embarque y \*packing list\*, y la información del \*bill of lading\* (BL) se carga en KAI después de ser enviada al cliente.

* **Proceso de Facturación y Liberación**: Una vez que el barco opera (sale), se procede a la facturación. Antes de esto, se envía el aviso de embarque (\*onboard\*) al cliente con copia a "liberaciones," y se espera el envío para facturar. Las trabas aduaneras se revisan manualmente en el sistema de la terminal.

* **Discusión sobre Rutas por Chile vs. Buenos Aires**: Se discutió la frecuencia de las rutas que salen por Chile, que es casi 50% y 50%, y si el enfoque debe ser en la parte chilena o continuar con la parte de Buenos Aires. Se acordó enfocarse en la parte más amplia del negocio y continuar con el proceso establecido, ya que la operativa de Chile es más manual y carece de funciones de seguimiento en línea como las disponibles para Buenos Aires.

* **Inicio de la Fase Administrativa y Facturación**: Manuel Vasquez indicó que el trabajo administrativo comienza con la facturación, que se activa automáticamente tras la carga de la cotización comercial. La facturación se realiza una vez que el buque ha zarpado, utilizando la información de las cotizaciones cargadas en el sistema.

* **Participación Administrativa en Cotizaciones**: Se aclaró que, por lo general, la administración no se involucra en la creación o definición de cotizaciones, siendo esta una responsabilidad de la parte comercial. Sin embargo, la administración sí interviene en operaciones específicas donde el cliente tiene un contrato directo con la línea marítima.

* **Manejo de Extracostos y Vínculo Comercial-Administrativo**: Se explicó que la parte operativa sí interviene para aprobar y cargar "extracostos" adicionales fuera de la cotización inicial, en colaboración con la parte administrativa. El flujo general va de comercial a administración a través de la cotización en KAI, que se vincula a un archivo operativo ("file") con todos los datos del embarque.

* **Definición de "File" en KAI**: Se aclaró que el "file" en KAI es el nombre que se da a la operación, la cual pasa a ser una operación cerrada con un número de referencia una vez que la cotización es aprobada por el cliente. La cotización se carga en el sistema únicamente cuando está aprobada.

* **Problema de la Falta de Cotización en el Sistema**: Se identificó un problema recurrente donde las operaciones se realizan, y el embarque incluso sale, pero la cotización no está cargada en el sistema, lo que impide la facturación. La parte comercial es responsable de cargar el número de cotización en el file operativo de KAI.

* **Causas de la Demora en la Carga de Cotizaciones**: Se señaló que la falta de carga de la cotización puede ocurrir debido a que la temporada acaba de empezar, y el monto final de la factura al cliente de destino aún no está definido por el cliente local. Esta demora, que puede ser aceptable, a menudo se debe a que se está ajustando el margen o "on top" que se cobrará al cliente final.

* **Necesidad de Condiciones y Recordatorios en el Proceso**: Jony Ayerbe propuso que, si no se puede imponer una condición para que la cotización esté cargada, se podría establecer que al iniciar la operación en Excel (el primer paso interno), se dispare un recordatorio si la cotización falta en KAI. Un recordatorio recurrente podría servir como un incentivo para que el equipo comercial complete la información.

* **Flujo de Facturación y Cuentas Corrientes**: Una vez que la data está completa, administración factura al cliente. El siguiente paso es el envío de los estados de cuenta a los clientes, un proceso que actualmente se está automatizando en KAI. El reclamo de pagos depende de si el cliente tiene cuenta corriente (pago a 30 días) o si requiere liberación de carga con pago anticipado, información que se sigue a través del sistema y el Excel.

* **Desafío de la Actualización de Fechas de Arribo (Carghost)**: La actualización de las fechas estimadas de arribo de los buques se gestiona con una herramienta externa (\*Carghost\*), que genera un Excel con los cambios. Esta actualización se hace manualmente en KAI, ya que el sistema no puede automatizar la carga debido a la discrepancia en la nomenclatura de los puertos (siglas vs. nombres completos), lo que requiere una conversión.

* **Obstáculos para la Automatización de Datos en KAI**: La automatización para actualizar KAI con las fechas de arribo desde Carghost y para cargar facturas de proveedores a través de \*Extract\* enfrenta problemas de coincidencia de campos y formatos. Se concluyó que cualquier mejora requerirá el esfuerzo de "caifificar" la data externa y potencialmente negociar cambios en el sistema central de KAI.

* **Chequeo de Facturas de Costos contra Cotización**: El proceso administrativo también maneja la parte de costos, donde las facturas de las líneas marítimas llegan al correo de "liberaciones". La factura recibida es revisada manualmente contra la cotización de costos cargada en KAI.

* **Control de Facturas y Uso de Extract**: Manuel Vasquez y Anahi Cappi describieron el proceso actual para controlar las facturas de líneas marítimas antes de la carga en el sistema Kai; este proceso es crucial porque las facturas deben ser validadas antes de la carga. Para validar, Manuel Vasquez selecciona todos los ítems de costo que coinciden con el total facturado, genera un 'rock' (una prefactura o precarga sin número de factura ni fecha). Este PDF del 'rock' se envía a Extract, que lee la factura, la envía a Kai, y Kai automatiza la carga de la factura, incluyendo número, fecha y PDF, si el contenedor y el importe coinciden con el 'rock'.

* **Volumen de Facturación y Ahorro de Tiempo**: Anahi Cappi resaltó la necesidad de este proceso automatizado debido al alto volumen, ya que se reciben aproximadamente 500 a 600 facturas de líneas marítimas por mes durante la temporada alta. La automatización con Extract ahorra una cantidad significativa de tiempo al evitar tener que teclear manualmente el número y la fecha de la factura, y cargar el PDF. El proceso ideal sería que un sistema leyera la factura y la enviara directamente a Kai para que coincidiera con los datos.

* **Proceso de Generación de 'Rock' y Carga de Factura**: Manuel Vasquez demostró que la generación del 'rock' se realiza seleccionando los costos en el archivo de operación que coinciden con el monto de la factura del proveedor. Una vez generado, el 'rock' se sube al sistema y posteriormente el PDF de la factura se envía a Extract. La función de Extract es leer el PDF, pasar la información a Kai, y Kai concilia la factura basándose en el número de contenedor y el monto del 'rock'.

* **Revisión de Información antes de Generar el 'Rock'**: Jony Ayerbe preguntó sobre los pasos previos a la generación del 'rock', lo que llevó a la explicación de que la información se coteja en el archivo (file) de la cotización. La cotización se carga en el módulo comercial y esto automáticamente trae los conceptos de venta y costo a la solapa de ítems. Se identifica que un ítem proviene de la cotización si tiene el icono de un "billetito" al lado.

* **Flujo de Trabajo Manual para la Facturación**: El proceso manual requiere que el personal de administración revise qué operaciones tienen ítems pendientes de facturación en el sistema. Cuando llega una factura de una naviera, la persona la revisa, la coteja con los costos de la operación, y si está correcta, genera el 'rock'. Manuel Vasquez explicó que este control manual es rápido (50 'rocks' en 20 minutos) y permite que se envíen lotes de PDFs a Extract, que luego los procesa y los carga automáticamente en Kai.

* **Función de Extract en la Carga de Facturas**: Jony Ayerbe confirmó que la principal función de Extract es leer el PDF y pasar la información a Kai en un formato predeterminado, aunque esto requiere la intervención humana previa para generar el 'rock'. Se mencionó que el tiempo de demora para la carga automática puede ser de aproximadamente media hora por cada envío de documentos, no por factura individual.

* **Desafíos y Propuesta de Optimización de la Validación**: Juan Pablo Norverto y Jony Ayerbe señalaron la necesidad de validar la factura antes de generar el 'rock' (la proforma), ya que actualmente esa validación es un proceso manual de comparación. Juan Pablo Norverto propuso la idea de que Extract pudiera validar la factura comparándola con un archivo de datos (CSV o XLS) de Kai, de modo que solo se generara el 'rock' si la validación es exitosa, automatizando así el proceso de control de la persona.

* **Discusión sobre la Limitación del Sistema Kai**: Se discutió la limitación de Kai, señalando que el sistema no permite descargas de reportes detallados que separen los costos por proveedor dentro de una misma operación, lo cual complica la automatización de la validación externa. Anahi Cappi y Juan Pablo Norverto acordaron que el objetivo es evitar la necesidad de solicitar nuevas funcionalidades a Kai, enfocándose en usar la información que ya es descargable o que Extract podría procesar.

* **Origen de la Creación del 'Rock'**: Se aclaró que la necesidad de crear el 'rock' surgió porque la idea original era que Extract y Kai gestionaran la carga sin control humano, pero la inconsistencia en las facturas de las navieras y la falta de información de cotización forzaron la creación del 'rock' como un paso de "precontrol" manual. Juan Pablo Norverto sugirió que el proceso actual era engorroso a menos que la tasa de error fuera muy alta.

* **Planificación de Consultas con Sistemas Externos**: Anahi Cappi concluyó que es necesario preguntar a Extract qué necesitan para validar la información de manera más automática. El plan es llevar los requisitos de Extract a Kai para ver si es posible extraer los datos necesarios, como un reporte más detallado, en lugar de intentar que Kai añada funcionalidad compleja.

* **Manejo de Errores en la Factura: Facturación Incorrecta por Naviera**: En el caso de que la factura de la naviera esté mal, la administración la compara primero con el contrato comercial que debe especificar el costo correcto. Si la naviera facturó de menos o de más, administración contacta directamente a la línea marítima para solicitar una nota de crédito o la corrección de la factura.

* **Manejo de Errores en la Factura: Monto Incorrecto en la Cotización (COTI)**: Si la factura de la naviera coincide con el contrato, pero el monto cargado en la COTI en Kai es incorrecto, el proceso se devuelve a comercial. Comercial debe revisar, corregir manualmente el monto en Kai y luego se devuelve a administración para el pago.

* **Importancia del Contrato en la Validación**: Jony Ayerbe buscó clarificación sobre la fuente del precio correcto, confirmando que el contrato es el punto de referencia final para validar los costos de la naviera, y comercial es responsable de enviar el contrato a administración. Estos contratos son vigentes por temporada o por períodos definidos para rutas habituales.

* **Proceso de Negociación y Cierre de Rutas Nuevas**: La discusión se centró en cómo se cierra una negociación de ruta o cliente nuevo, lo que lleva a la creación de un contrato con la naviera. Existen dos tipos de cierres: por contrato (para grandes volúmenes, como 600 contenedores por temporada/mes), que requiere un número de contrato específico para cada \*booking\* y se registra en la línea, o mediante cotizaciones \*spot\*, que son puntuales para cada carga y se manejan por correo electrónico. El contrato o el registro de la cotización se realiza después de la negociación y es la herramienta que utiliza la administración para verificar la factura con lo ingresado manualmente en el sistema CAI.

* **Gestión de Contratos y Repositorio Maestro**: Se confirmó que los contratos por temporada completa se almacenan en una planilla maestra de operaciones, en una pestaña dedicada a "contratos". Este repositorio sirve para chequear si la facturación coincide con lo acordado en el contrato; si el valor es incorrecto en la cotización (\*COTI\*), se debe informar al equipo comercial para que lo corrija manualmente. Este punto de error en la carga o no carga de la cotización fue identificado como un área principal a abordar para mejorar el proceso.

* **Problemas con Conceptos no Cargados en la Cotización**: Un punto crítico de dolor es cuando un concepto de servicio (como custodia o ingreso a puerto) no se carga en la cotización, lo que resulta en que el cliente no es facturado por dicho costo. Esto puede ocurrir debido a que el servicio no se conoce bien o porque el cliente ya sabe del embarque y no requiere una cotización formal, lo que puede llevar a descubrir el costo no facturado hasta que llega la factura del proveedor. Esta falta de coincidencia en los conceptos cargados es una variante adicional a los errores en los montos de la factura.

* **Propuesta de Inteligencia Externa al Sistema CAI**: Se propuso trabajar en un sistema de "inteligencia" fuera de CAI para articular chequeos, recordatorios y notificaciones, ya sea que la cotización esté cargada o no. Este sistema ayudaría a verificar la información contra el Excel Maestro y las facturas, con el objetivo de facilitar los chequeos de validación. El equipo debe considerar si es viable acceder automáticamente al sistema CAI para verificar valores y hacer solicitudes, aunque se reconoció que el acceso a un sistema local podría resolver esta limitación.

* **Integración y Verificación de Información Operativa**: Se sugirió la posibilidad de que el equipo operativo, que maneja los detalles de la carga, valide la información del Excel Master con los conceptos cargados en la cotización. Por ejemplo, si el operativo confirma que Loginet realiza el ingreso a puerto, el sistema podría chequear si el concepto de ingreso a puerto está incluido en la cotización. El objetivo es que la información que se tiene como validada se cargue en CAI de una manera más ordenada.

* **Limitaciones y Uso Actual del Sistema CAI**: Se determinó que el equipo operativo utiliza muy poco el sistema CAI, mientras que la parte administrativa lo usa de manera más frecuente. Ya que la parte administrativa es el último eslabón del proceso, se sugirió atacar el proceso anterior a la administración para que la información que llega a CAI sea lo más limpia posible. Esto implicaría usar CAI principalmente como un sistema de planificación de recursos empresariales (ERP) para la facturación y la administración, mientras que el proceso anterior se fortalecería con herramientas externas.

* **Enfoque en la Mejora del Proceso Antes de CAI**: La fricción se genera en la carga subsiguiente de información a CAI, y el enfoque debe estar en manejar el proceso fuera de CAI hasta que la información esté lista para la carga final y necesaria. Se identificó que hay un punto de mejora significativo en el proceso, desde la carga de la cotización hasta evitar errores causados por comunicación, falta de recordatorios o chequeos pendientes. El equipo debe trabajar en recordatorios, alertas y automatizar tareas usando el Excel Maestro para diferentes departamentos, y luego intentar conectar esto a CAI para la facturación.

* **Evaluación de Sistemas de Gestión de la Competencia**: Anahi Cappi mencionó que ha trabajado con otros sistemas en el pasado que considera más amigables que CAI, notando que los cambios eran más rápidos. No obstante, por el momento no es una opción considerar un cambio de sistema, especialmente con el inicio de la temporada, sino que el objetivo sigue siendo optimizar el sistema actual y utilizar herramientas externas como Extra y Cargo para complementar las funciones que CAI no puede realizar. El equipo acordó digerir la información mapeada, volver con preguntas y avanzar hacia una propuesta de sugerencias y análisis.

*Revisa las notas de Gemini para asegurarte de que sean precisas. [Obtén sugerencias y descubre cómo Gemini toma notas](https://support.google.com/meet/answer/14754931)*

*Cómo es la calidad de **estas notas específicas?** [Responde una breve encuesta](https://google.qualtrics.com/jfe/form/SV_9vK3UZEaIQKKE7A?confid=AWrnxK08mQEbbqyB_T5KDxITOAIIigIgABgFCA&detailid=standard&screenshot=false) para darnos tu opinión; por ejemplo, cuán útiles te resultaron las notas.*

