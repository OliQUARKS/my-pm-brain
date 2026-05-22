# Source — Sprint 1 Review PERC

- **Date:** 2026-05-18
- **Original file:** `/Users/olivierluce/Downloads/Review - PERC - 2026_05_18 15_59 GMT-03_00 - Notas de Gemini.txt`
- **Duration:** 37:49
- **Participants:** Olivier Luce (PM, Quarks), Marcos Perez (Dev, Quarks), Juan Pablo Norverto (CTO, Quarks), Juan Ignacio Moyano (Dev, Quarks), Nicolás Paez (TL, Quarks), Israel Fernandez Cabrera (TL, Quarks), Federico Fernandez (COO, Quarks), José Salgado (Dev, PERC), Sebastián Cárdenas (PO, PERC), Ezequiel Manfredi (CTO, PERC), Ariel Gendelman (Cyber, PERC)
- **Matching ingestion file:** `../../ingestion/meetings/2026-05-18-sprint1-review-perc.md`

---

Key verbatim exchanges (full transcript in original file):

**LUID para IDs (00:10:29–00:12:10):**
> Jose Salgado: "Yo yo tengo una duda, no estaba viendo eh me preocupaba un poquito el tema de los ids que estaban usando. Eh los entendía numéricos, o sea, los veo numéricos. Eh quería saber qué posibilidades tenemos de cambiar eso a algo que no dé información de la cantidad de entradas que tiene la base de datos. Eh, es sería interesante usar un LUID o algo por el estilo."
>
> Israel Fernandez Cabrera: "Justo eso iba a decir. Justo eso iba a decir. Listo."
>
> Jose Salgado: "porque si usamos un UID normal no son ordenables, por tanto nos va a traer grandísimos problemas en DB. [...] Son ordenables. Es la la única gran diferencia que tienen. Se parecen más a los object de Mongo, que por detrás son una fecha."
>
> Nicolás Paez: "Okay." [confirma]

**Audit table con JSON diffs (00:18:51–00:21:17):**
> Jose Salgado: "por lo que veo están guardando todo como si fuese Jason [...] eso es solo auditoría, ¿no es cierto?"
>
> Nicolás Paez: "Básicamente es para tener un snapshot en una sola línea, porque si en esa tabla te va a crecer eternamente si lo manejas por estructuras."
>
> Jose Salgado: "que además mantener después esa estructura si tenés más objetos, si querés track, no va a ser muy muy doloroso, no está perfecto. [...] Esto está perfecto."

**Tasas: decimal 0–1 (00:31:18–00:32:10):**
> Federico Fernandez: "la tasa anual, imagínate que es, no sé, un 10,5%. Esa tasa la podemos escribir como 10,5%, la podemos escribir como 0,0005, ahí que preferís"
>
> Jose Salgado: "entiendo que entre 0 y un está es correcto. Eh, tiene buena densidad para hacer cuentas [...] está bien."
>
> Sebastian Cárdenas: "No sé cómo guardamos hasta Ahora los porcentajes."
>
> Jose Salgado: "Sí, entre cer y uno."
>
> Sebastian Cárdenas: "Listo. Entonces sigamos con la misma lógica."
>
> Ariel Gendelman: "Para mí debería guardarse entre cer y un también, chicos."

**Fechas: ISO 8601 con timezone (00:33:05–00:35:30):**
> Israel Fernandez Cabrera: "la las fechas, ¿cómo las guardan? con toda la precisión o ponemos los milisegundos desde la época en UTC"
>
> Jose Salgado: "estábamos usando Local Daytime, que es ISO 8106 [sic, ISO 8601]"
>
> Nicolás Paez: "8601 creo."
>
> Nicolás Paez: "Okay. Tipo timeamp o TZ."
>
> Jose Salgado: "el 8601 lleva time zone, por eso lleva la zz final. [...] para nosotros sería 03, o sea, menos03"
>
> Nicolás Paez: "Lo guardamos de esa forma."

**Ariel Gendelman — código queda en repos PERC (00:25:46–00:26:38):**
> Ariel Gendelman: "el código nos lo quedamos nosotros al final para poder trabajar como corresponde."
>
> Jose Salgado: "Es propiedad de Perc, de hecho se está creando dentro de repositorios de la compañía."
>
> Ariel Gendelman: "Okay. Bueno, o sea, que nosotros vamos pasándole escaneos todos los días"
>
> Jose Salgado: "Sí, tenemos dos estrategias, una son las automatizadas que son las que va a poner el Tano, y la otra es PR cruzado contra nosotros"
