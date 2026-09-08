# Ciclo de vida del prospecto — instancias de preventa

> **Qué es:** el mapa canónico de etapas por las que pasa un prospecto, y qué skill corre en cada una. Referencia compartida por [`/briefing-context`](../.claude/commands/briefing-context.md), [`/build-context`](../.claude/commands/build-context.md) y [`/minutero`](../.claude/commands/minutero.md). Si hay dudas de "¿qué instancia es esta?", se resuelven acá.

## Las etapas, en orden

1. **Cold start.** El cliente llama o escribe para iniciar la conversación. Input crudo y vago; todavía no hablamos con nadie en profundidad.
2. **`/briefing-context`** — *preparación para la primera reunión.* Releva objetivos de información y ejes (regulatorio/legal/stack) → Documento de Preparación. **Pre-reunión.**
3. **Reunión de briefing** *(rótulo: **briefing**, preferido; también "preventa").* La primera reunión. El cliente explica sus procesos, problemas, usuarios y su visión del contexto de negocio. Resultado: **transcripción** y, en el mejor de los casos, **documentación** (empresa, productos, herramientas, dolores).
4. **`/build-context`** — *post-briefing.* Es el briefing-context **con más sustancia**: parte de la transcripción del briefing + (idealmente) la documentación que mandaron. Produce el contexto interno del proyecto + la pre-propuesta cara al cliente.
   - **`/propuestador`** y **`/prototipador`** corren acá, derivando del build-context: `propuestador` arma el documento comercial cara-al-cliente (primero comparando 2-3 caminos internamente, con un checkpoint de decisión — ver `propuestador.md § Fase 0` — y recién después expandiendo el elegido); `prototipador` arma el prototipo funcional navegable (archivo HTML privado, nunca un Artifact publicado) de las pantallas core del MVP, sobre el camino que `propuestador` ya decidió. Ya no son estrictamente paralelos: `prototipador` espera la decisión de `propuestador` cuando este corrió en modo multi-camino. Ambos son cara-al-cliente y respetan la regla de oro (lo interno nunca cruza).
5. **`/minutero`** — *puede correr pre o post build-context.* Ver [§ Timing de minutero](#timing-de-minutero).
6. **Propuesta formal del proyecto.** Recién acá se comprometen equipo, tiempo y costo. Es el "sí/no" del cliente.
7. **Discovery** — *post-venta, pre-desarrollo.* Ver [§ Discovery ≠ briefing](#discovery--briefing).

## Timing de minutero

`/minutero` redacta la minuta cara al cliente. Corre en cualquiera de los dos momentos, y **embebe el mejor contexto disponible**:

- **Pre build-context.** Con el **briefing-context + la transcripción del briefing** ya alcanza para pasar en limpio lo entendido y hacer seguimiento de los accionables que surgieron. Se usa así cuando **todavía no llegó la documentación** del cliente.
- **Post build-context.** Si la documentación ya llegó y se armó el build-context, minutero **embebe el build-context** en lugar del briefing-context.

**Regla:** minutero embebe **build-context si existe; si no, briefing-context.** Uno da mejor contexto que el otro — usar siempre el más completo disponible al momento de redactar.

## Discovery ≠ briefing

No confundir la **reunión de briefing** (etapa 3, preventa) con el **discovery** (etapa 7).

- El **briefing** es la primera charla de preventa: gratuita, exploratoria, una reunión.
- El **discovery** es una **etapa posterior a la propuesta formal** (post-venta, pre-desarrollo) y es un **servicio que se comercializa**: un ejercicio minucioso de varias sesiones que baja a detalle extremo los flujos, el problema y los usuarios, e investiga a fondo todo lo que trae el cliente.

Cuando la pre-propuesta (build-context § B) "vende un discovery", se refiere a la etapa 7 — no a la reunión de briefing.
