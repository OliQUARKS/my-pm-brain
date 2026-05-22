# Source — Kickoff Flujo Crédito PERC

- **Date:** 2026-04-20
- **Original file:** `/Users/olivierluce/Downloads/Kickoff Flujo Crédito - PERC - 2026_04_20 16_59 GMT-03_00 - Notas de Gemini.md`
- **Duration:** 1:07:22
- **Participants:** Olivier Luce (PM, Quarks), Federico Fernandez (COO, Quarks), Israel Fernandez Cabrera (TL, Quarks), Nicolás Paez (TL, Quarks), Juan Pablo Norverto (CTO, Quarks), Juan Pablo Moyano (Dev, Quarks), José Salgado (Dev, PERC), Eugenio Valeiras (TL, PERC), Stefano Giuliano (Cyber, PERC), Ezequiel Manfredi (CTO, PERC), Sebastián Cárdenas (PO, PERC)
- **Context:** Kickoff técnico real de la integración Quarks–PERC para flujo crédito. Pre-kickoff formal (el kickoff oficial Quarks–PERC fue 2026-05-20).
- **Matching ingestion file:** `../../ingestion/meetings/2026-04-20-kickoff-flujo-credito.md`

---

Key verbatim exchanges (full transcript in original file):

**Stack TypeScript + Lambda (00:00:00):**
> Jose Salgado: "haciendo un poquito de repaso, sií, la primera es Sam con es TypeScript, lambdas de TypeScript"

**Heimdal — arquitectura auth (00:18:44–00:24:11):**
> Jose Salgado: "Hemdal es un objeto central, lo usan todos, tiene, o sea, permite hacer verificación asimétrica de tokens mediante JWKS. Eh, también tenemos una SHQue, que es la que comenta, o sea, en donde están mandados los token que se queman por cuestiones particulares [...] Estamos pasando a usar OPA."
>
> Israel Fernandez Cabrera: "el token viene un rol, alguien valida el rol, eh, que es algo externo y cuando llega al servicio, digamos, solo llega si lo puede consumir. Es así."
>
> Jose Salgado: "Sí, señor."
>
> Israel Fernandez Cabrera: "Con lo cual en los servicios no hay que ocuparse de nada relativo a seguridad de ese tipo."

**TOTP = requerimiento BCRA para operaciones sensibles (00:25:20):**
> Stefano Giuliano: "si la idea es también por cumplimiento normativas del BCRA para operaciones sensibles, o sea, como regla general también por cumplimiento regulatorio lo tenemos también para como requerimiento. O sea, esto de préstamos también es una operación sensible, o sea, al momento de la solicitud debería pedirse el multifactor de aplicación al usuario"

**S3 para documentos + Sherlock service (00:38:42–00:39:48):**
> Jose Salgado: "en S3 todo lo que es PDF [...] de hecho, en este en este sprint sale la posibilidad de guardar documentos sobre una cuenta. Eh, hay un servicio que que mantiene toda la información eh propia del cliente que se llama Sherlock, eh que este Sprint saca una te está sacando una nueva feature que es la que te permite tachar documentos a la cuenta, o sea, decir, 'Che, este documento es tuyo, te lo guardo.' Eh, obviamente ese documento todavía no es que soporta el binario, eh, lo que soporta es el es el key del presigned de de S3"
>
> Juan Pablo Norverto: "Bien, bueno, estaríamos usando eso capaz."
>
> Jose Salgado: "Sí, eso está disponible, lo pueden usar."

**FIFO waitlist cuando recaudadora se vacía (00:48:01–00:49:11):**
> Sebastian Cárdenas: "la idea de Marcos [...] es, yo le voy a dar préstamos a todos los que me pidieron hasta que se me acabe la plata y una vez que se me acabe la plata los quiero poner en lista de espera [...] a medida que voy poniendo plata voy dando esos créditos."
>
> Juan Pablo Norverto: "primero lleguemos a acabar la plata [...] vamos al paso uno primero"
>
> Juan Pablo Norverto: "del primero al último, ¿no? El el fifo."

**Tag mechanism — comenzar permisivo (00:06:09–00:08:43):**
> Jose Salgado: "yo creo que va a haber el tag Mantovana es va a existir, es ajeno a créditos [...] luego lo que le hagamos sea agregar nuevos tags donde decir, 'Che, estos son mis gerentes.'"
>
> Juan Pablo Norverto: "Yo iría por ese lado primero. [...] a priori lo dejaría como algo operativo y después lo complejizaría"

**Multi-tenant question (01:00:57–01:03:31):**
> Sebastian Cárdenas: "Mi pregunta era si era escalable y esto era una versión MVP por una cuestión de alcance y con el mismo desarrollo y vamos a poder después ver una algo o si esto era tipo tenemos que escraear todo esto y empezar un módulo de crédito nuevo si quisiéramos escalarlo un B2."
>
> Juan Pablo Norverto: "si vos querés, va a pasar esto seguramente a futuro [...] hay que verlo cómo lo podemos hacer, pero nada, si son parámetros no hay mucho problema."
>
> Sebastian Cárdenas: "estamos haciendo un sistema de créditos preaprobados."

**Watson = Angular + opción módulo separado (00:51:28–00:55:46):**
> Israel Fernandez Cabrera: "ustedes que usan de front"
> Eugenio Valeiras: "Angular."
>
> Ezequiel Manfredi: "es un módulo aparte de crédito y nosotros lo metemos"
> Eugenio Valeiras: "si le damos el backof está bien, o sea [...] tenés un montón de funcionalidades que ya están ahí como al tacto funcionando"
