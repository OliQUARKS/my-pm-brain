# Ciclo de vida del prospecto: instancias de preventa

> **Qué es:** el mapa canónico de etapas por las que pasa un prospecto, y qué skill corre en cada una. Referencia compartida por [`/briefing-context`](../.claude/commands/briefing-context.md), [`/discovery-context`](../.claude/commands/discovery-context.md) y [`/minutero`](../.claude/commands/minutero.md). Si hay dudas de "¿qué instancia es esta?", se resuelven acá.

## Las etapas, en orden

1. **Cold start.** El cliente llama o escribe para iniciar la conversación. Input crudo y vago; todavía no hablamos con nadie en profundidad.
2. **`/briefing-context`**: *preparación para la primera reunión.* Releva objetivos de información y ejes (regulatorio/legal/stack) → Documento de Preparación. **Pre-reunión.**
3. **Reunión de briefing** *(rótulo: **briefing**, preferido; también "preventa").* La primera reunión. El cliente explica sus procesos, problemas, usuarios y su visión del contexto de negocio. Resultado: **transcripción** y, en el mejor de los casos, **documentación** (empresa, productos, herramientas, dolores).
4. **`/discovery-context`** (ex `/build-context`): *post-briefing.* Es el briefing-context **con más sustancia**: parte de la transcripción del briefing + (idealmente) la documentación que mandaron. Produce el contexto interno del proyecto + la pre-propuesta cara al cliente. Se renombró 2026-09-21: "build context" describe mejor a un futuro skill separado (ver nota abajo), no a este.
   - **`/propuestador`** y **`/prototipador`** corren acá, derivando del discovery-context: `propuestador` arma el documento comercial cara-al-cliente (primero comparando 2-3 caminos internamente, con un checkpoint de decisión (ver `propuestador.md § Fase 0`) y recién después expandiendo el elegido); `prototipador` arma el prototipo funcional navegable (archivo HTML privado, nunca un Artifact publicado) de las pantallas core del MVP, sobre el camino que `propuestador` ya decidió. Ya no son estrictamente paralelos: `prototipador` espera la decisión de `propuestador` cuando este corrió en modo multi-camino. Ambos son cara-al-cliente y respetan la regla de oro (lo interno nunca cruza).
5. **`/minutero`**: *puede correr pre o post discovery-context.* Ver [§ Timing de minutero](#timing-de-minutero).
6. **Propuesta formal del proyecto.** Recién acá se comprometen equipo, tiempo y costo. Es el "sí/no" del cliente.
7. **Discovery**: *post-venta, pre-desarrollo.* Ver [§ Discovery ≠ briefing](#discovery--briefing).

## Timing de minutero

`/minutero` redacta la minuta cara al cliente. Corre en cualquiera de los dos momentos, y **embebe el mejor contexto disponible**:

- **Pre discovery-context.** Con el **briefing-context + la transcripción del briefing** ya alcanza para pasar en limpio lo entendido y hacer seguimiento de los accionables que surgieron. Se usa así cuando **todavía no llegó la documentación** del cliente.
- **Post discovery-context.** Si la documentación ya llegó y se armó el discovery-context, minutero **embebe el discovery-context** en lugar del briefing-context.

**Regla:** minutero embebe **discovery-context si existe; si no, briefing-context.** Uno da mejor contexto que el otro; usar siempre el más completo disponible al momento de redactar.

## Discovery ≠ briefing ≠ discovery-context

No confundir tres cosas que comparten la palabra "discovery":

- El **briefing** (etapa 3) es la primera charla de preventa: gratuita, exploratoria, una reunión.
- El **`/discovery-context`** (etapa 4, este skill) es el contexto interno **pre-venta**, post-briefing; no tiene nada que ver con la etapa de discovery pago.
- El **discovery** (etapa 7) es una **etapa posterior a la propuesta formal** (post-venta, pre-desarrollo) y es un **servicio que se comercializa**: un ejercicio minucioso de varias sesiones que baja a detalle extremo los flujos, el problema y los usuarios, e investiga a fondo todo lo que trae el cliente.

Cuando la pre-propuesta (discovery-context § B) "vende un discovery", se refiere a la etapa 7, no a la reunión de briefing ni al skill `/discovery-context`.

**Nota sobre el skill `/build-context`:** distinto del skill de esta página. `/build-context` ([`.claude/commands/build-context.md`](../.claude/commands/build-context.md), creado 2026-09-21) consolida las definiciones ya aprobadas (PRD, backlog, baseline DoR/DoD, design system, setup técnico) para arrancar el Build, es decir, ocurre en el puente entre 4-Define/3-Setup y 5-Build, **después** de que termina la etapa 7 (discovery pago). No confundirlo con el skill de esta página, que quedó renombrado a `/discovery-context` justamente para liberar ese nombre.

**Etapa 7 tiene su propio kit de skills.** Ver [`_kit-discovery.md`](./_kit-discovery.md): catálogo
de 15 metodologías (`/discovery-*`), agrupadas por lo que resuelven, con tabla de combo recomendado
según madurez del cliente y forma del problema. No se corren todas en cada engagement; el kit
existe para elegir 2-4, no para ejecutar el catálogo entero.
