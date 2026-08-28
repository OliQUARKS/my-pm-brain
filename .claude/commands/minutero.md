# Skill: minutero

**Tu objetivo:** después de la **reunión de briefing** (preventa), redactar la **minuta cara al cliente** — el mail que demuestra que entendimos, pide que lo validen, pide la evidencia que falta y deja pedida la próxima reunión con el decisor. Se deriva del contexto que tengamos (briefing-context o build-context) y de la transcripción del briefing; no reemplaza a ninguno, los capitaliza hacia afuera.

## Dónde encaja en el ciclo

Ver el mapa canónico: [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md). Dos cosas que importan acá:

- **Corre pre o post build-context.** Con el **briefing-context + la transcripción del briefing** ya se puede correr (pasar en limpio lo entendido, seguir los accionables) — útil cuando todavía no llegó la documentación. Si el build-context ya existe, mejor.
- **Embebé el mejor contexto disponible:** **build-context si existe; si no, briefing-context.** Uno da mejor contexto que el otro.
- **No es discovery.** La minuta cierra una reunión de briefing (preventa). El discovery es una etapa posterior a la propuesta (post-venta, pre-desarrollo) y no se toca acá.

## Qué es y qué no es — las dos capas

1. **Minuta cara al cliente (lo que arma este skill).** Un mail claro y accionable. Objetivo doble: (a) que el cliente **valide** lo que entendimos y (b) que nos **habilite lo que necesitamos** para avanzar (info, evidencia, la reunión con el dueño).
2. **Contexto interno (build-context).** No es esto. La minuta nunca vuelca stakeholders, factibilidad, incógnitas técnicas ni el "cómo lo trabajamos" interno. Lo interno queda en el build-context.

**Entregable = borrador.** La minuta sale como `.md` **borrador que el líder de cuenta aumenta antes de enviar** (ej.: Oli redacta, Jony suma lo suyo). **Este skill no envía el mail** — lo deja listo para copiar/enviar.

## Entrada

- **El mejor contexto disponible** — `briefings/<...>-build-context.md` si ya existe; si no, el Documento de Preparación de `/briefing-context`. (Regla del ciclo: build-context si existe, briefing-context si no.)
- **La transcripción del briefing** (`source/meetings/<fecha>-<cliente>-briefing.md`, o `-discovery.md` según cómo se haya rotulado la fuente).
- **Documentación del cliente**, si la mandaron.
- **Correcciones de calls internas** posteriores (qué prometer y qué no, a quién se escala, qué camino se prioriza).

No hace falta esperar al build-context para correr el skill: alcanza con el briefing-context + la transcripción. Pero si el build-context ya está, usalo — da mejor contexto.

## Cómo trabajás

- **Reflejás lo que entendimos, no lo que suponemos.** Todo lo del flujo se enmarca como **"esto entendimos, validanos"** — nunca como verdad establecida sobre un proceso que no vimos.
- **Pedís evidencia concreta, no data vaga.** Fotos de las planillas, ejemplo real de un mensaje, capturas de cada pantalla del sistema. (Aprendizaje frigorífico: "mandanos info" no alcanza; hay que enumerar qué foto/captura de qué.)
- **Honestidad de alcance.** No prometas lo que no es factible (prototipo, integración) — alineado con la factibilidad del build-context. Si el prototipo no se puede, no se menciona.
- **Tono intermedio profesional** (ver abajo). Ni acartonado ni relajado.
- **Habilitás el próximo paso.** La minuta siempre deja pedida la validación + el material + la reunión con el decisor.

## Regla de tono

Punto medio entre profesional y cercano. **Sin** emojis, **sin** modismos coloquiales ("che", "abrazo", "boludo", "un abrazo"), **sin** exceso de confianza. Cálido pero medido: "gracias por el tiempo", "quedamos a disposición", "Saludos, Equipo Quarks". Verbos formales ("insume", "vuelve a cargar", "registra") en lugar del registro hablado. 100% español.

## Estructura de la minuta

Incluí, cuando aplique al caso:

0. **Header interno (no enviar).** Bloque `> Nota interna` arriba de todo: objetivo del mail, **qué NO prometer**, a quién se escala, quién aumenta el borrador. Se borra antes de enviar.
1. **Saludo breve.** Agradecer el tiempo. Anticipar que va resumen para validar + pedido de material. Indicar que lo pueden hacer circular con el decisor.
2. **Quiénes somos.** Bloque reutilizable con el diferencial Quarks (ver abajo). Va salvo que el cliente ya nos conozca.
3. **Lo que entendimos del proceso actual.** El flujo en pasos numerados, en lenguaje del cliente. Cerrar con un pedido explícito de validación ("¿es correcto este flujo?").
4. **Dónde identificamos el dolor.** Concreto, con números si los hay (tiempos, errores, volumen).
5. **Qué necesitaríamos para avanzar.** Lista enumerada de evidencia + preguntas abiertas. Cada ítem, puntual.
6. **Próximos pasos.** Validación + material → reunión con el decisor para propuesta conceptual → lo que hacemos en paralelo.
7. **Cierre profesional.** "Quedamos a disposición. Saludos, Equipo Quarks."

### Bloque reutilizable — "Quiénes somos"

> A diferencia de una solución puntual —un bot, una mini-app o una integración aislada—, en Quarks miramos la operación y el negocio de punta a punta: **diagnóstico primero, herramientas después**.
>
> Muchas veces los procesos ya están rotos. Sin ese diagnóstico previo, se terminan implementando herramientas que replican los mismos problemas, o se fuerza el flujo de trabajo para que encaje en la herramienta de moda. Nosotros no forzamos nada: combinamos lo que ya existe con lo que hace falta crear a medida, para resolver los dolores reales y destrabar los desafíos particulares de cada cliente, respetando sus recursos y su realidad operativa.
>
> En síntesis, los ayudamos a crecer y escalar a través de la tecnología.

Ajustá redacción al cliente, pero mantené el eje: **diagnóstico > herramienta**, no forzar, combinar existente + ad-hoc, crecer/escalar.

## Salida

Un archivo `briefings/<fecha-reunión>-<cliente>-minuta.md` con:
- El **header interno** (no enviar).
- El **cuerpo cara al cliente**, listo para copiar.

Respetá `CLAUDE.md § Operating preferences § Autonomy mode`. Bajo `propose and wait`, presentá el borrador y esperá confirmación antes de guardar.

### Formato de salida — Google Doc formateado (+ markdown de respaldo)

El borrador se entrega como **Google Doc formateado**, no como `.md` suelto — así el líder de cuenta lo aumenta antes de enviar (ej.: Oli redacta, Jony suma) sin pelearse con markdown crudo. Dos artefactos, en este orden:

1. **Markdown de respaldo (repo).** Guardá el borrador en `briefings/<fecha-reunión>-<cliente>-minuta.md` como hasta ahora. Ancla de trazabilidad — no se elimina.
2. **Google Doc formateado (borrador editable).** Creá el documento con el conector de Google Drive a partir de ese mismo markdown:
   - Tool: `create_file` del conector Google Drive.
   - `title`: `Minuta — <Cliente> — <YYYY-MM-DD> (borrador)`.
   - `textContent`: el markdown completo, **incluido el header interno "no enviar"** (el líder de cuenta lo borra antes de copiar el cuerpo al mail).
   - `contentMimeType`: `text/markdown`; **no** actives `disableConversionToGoogleType`.
   - Si el PM indicó una carpeta de Drive, pasá su `parentId`; si no, queda en la raíz.
3. **Cerrá devolviendo el link del Google Doc** más la ruta del `.md`.

Sigue siendo un **borrador que no se envía** desde el skill: el Google Doc es para aumentar y luego copiar el cuerpo (sin el header interno) al mail.

## Ejemplo trabajado — Frigorífico Merlo

**Input:** [build-context](../../briefings/2026-07-frigorifico-merlo-build-context.md) + [discovery 23-jul](../../source/meetings/2026-07-23-frigorifico-merlo-discovery.md) + call interna Oli↔Jony 24-jul.

**Cómo lo interpretás:**
- La call interna decidió: **no prometer prototipo** (el flujo completo no es prototipable por la integración de WhatsApp) → sale del mail.
- El objetivo del mail pasa a ser **validar el flujo + pedir evidencia** (fotos de las hojas, ejemplo real de pedido por WhatsApp, capturas del ERP, cómo diferencian premium/estándar) y **pedir la reunión con el dueño**.
- El enfoque punta a punta (vs. curita aislada) se posiciona en la reunión con el dueño, no se martilla en el mail.

**Output:** [minuta 23-jul](../../briefings/2026-07-23-frigorifico-merlo-minuta.md) — header interno + "Quiénes somos" + flujo a validar + 7 pedidos de material + próximos pasos, en tono intermedio.

## Criterios de calidad

✅ Se llama `minutero`
✅ Embebe el **mejor contexto disponible** (build-context si existe; si no, briefing-context) — nunca confunde briefing con discovery
✅ Cara al cliente y como **borrador** que el líder de cuenta aumenta — no lo envía el skill
✅ Nunca vuelca lo interno (stakeholders, factibilidad, incógnitas técnicas, "cómo lo trabajamos")
✅ Incluye el bloque "Quiénes somos" (diagnóstico > herramienta)
✅ El flujo entendido se enmarca como **a validar**, no como verdad establecida
✅ Pide evidencia **enumerada y concreta** (qué foto/captura de qué), no "mandanos info"
✅ No promete lo no factible (prototipo/integración) — alineado con el build-context
✅ Deja pedida la reunión con el decisor + propuesta conceptual
✅ Tono intermedio profesional: sin emojis, sin modismos, sin exceso de confianza
✅ Header interno (no enviar) arriba de todo; 100% español
✅ Entregable = Google Doc formateado (borrador) vía conector Drive; markdown de respaldo en el repo; se devuelve el link
