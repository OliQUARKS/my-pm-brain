# Project context: plantilla y reglas

> **Qué es:** un archivo por proyecto/engagement, en `briefings/<client>-project-context.md`.
> Muta (crece) en cada etapa; una vez agregada, una entrada del Timeline nunca se reescribe.
> Referenciado por [`/briefing-context`](../.claude/commands/briefing-context.md),
> [`/discovery-context`](../.claude/commands/discovery-context.md),
> [`/build-context`](../.claude/commands/build-context.md) y
> [`/close-context`](../.claude/commands/close-context.md); cada una de las cuatro le agrega
> su propia entrada al Timeline cuando corre.
>
> **No reemplaza** el archivo propio de cada etapa (la prep de briefing, la biblia de discovery,
> la biblia de build). Esos siguen siendo la fuente completa; project-context es el resumen de
> una línea por etapa para ver de un vistazo dónde está el proyecto sin abrir cuatro archivos.
>
> **Distinto de client-context** (`knowledge/org/<client-slug>.md`, mismo patrón que
> [`knowledge/org/ryd-abogados.md`](../knowledge/org/ryd-abogados.md)): project-context es por
> proyecto; client-context es por cliente y puede abarcar varios proyectos en el tiempo. Las
> cuatro etapas actualizan ambos, cada uno para lo suyo.

## Meta
- Cliente: <nombre>
- Proyecto: <nombre corto>
- Estado: prospecto | en discovery | en build | cerrado
- Última actualización: YYYY-MM-DD (etapa que la actualizó)

## Timeline (append-only, nunca se reescribe una entrada ya agregada)
- YYYY-MM-DD — Briefing context. <resumen de 1-2 líneas>. → [link al Prep Document]
- YYYY-MM-DD — Discovery context. <resumen de 1-2 líneas>. → [link a la biblia de discovery]
- YYYY-MM-DD — Build context. <resumen de 1-2 líneas>. → [link a la biblia de build]
- YYYY-MM-DD — Close context. <resumen final>. → [link al postmortem]

## Links
- Briefing: `briefings/<...>-briefing-context...`
- Discovery: `briefings/<...>-discovery-context.md`
- Build: `briefings/<...>-build-context.md`
- Postmortem: `briefings/<...>-postmortem.md`
- Client context: `knowledge/org/<client-slug>.md`
