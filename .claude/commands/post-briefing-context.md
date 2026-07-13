# Skill: post-briefing-context (POST)

**Tu objetivo:** después de la primera reunión, **ampliar el contexto** con lo que efectivamente salió y convertirlo en una **propuesta** con alcance, discovery y (si es factible) prototipo. La salida es más extensa que el pre — no es el pre corregido, es el pre **ampliado**. Fin último: que el brief tenga injerencia en cerrar el deal.

## Propósito

Del output de esta reunión sale una **propuesta en 1–2 días** — no dejarla enfriar. Después viene el discovery, donde se refina hacia algo concreto y arranca el proyecto; pero nace mucho mejor. Regla de proceso: reservá 15 min post-reunión para procesar el output y generar la tarea, en vez de encadenar reuniones y armar minutas a la noche.

## Cómo trabajás

- **Ampliás, no reescribís de cero.** Partís del Documento de Preparación y le sumás lo nuevo.
- **Honestidad de factibilidad.** Si no tenemos experiencia, API o acceso, se dice — igual se puede proponer.
- **Puntual y accionable.** Sin placeholder, sin ambigüedad. Lo que quedó abierto se nombra como abierto, no se rellena.

## Entrada

- **El Documento de Preparación** (output de `/briefing-context`).
- **Respuestas obtenidas** en la reunión.
- **Transcripción** — Granola / Meet.
- **Documentos enviados por el cliente.**
- Cualquier otra info que haya aparecido.

## Qué tenés que resolver sí o sí — objetivos de información

Sobre los objetivos del pre, ahora con datos de la reunión, resolvé:

1. **Problema real (ampliado)** — qué entendíamos antes vs. qué entendemos ahora; nombrar qué cambió.
2. **Contexto nuevo** — sistemas, restricciones, números, prioridades, quién decide.
3. **Usuarios / roles / permisos** — confirmados o corregidos.
4. **Factibilidad** — ¿podemos ayudar? ¿con qué (experiencia, API, acceso)? ¿qué falta?
5. **Stakeholders** — cómo operar con cada persona (ver sección 6).

## Ejes obligatorios de análisis

Revalidá los tres ejes del pre con lo que salió, y profundizá el que sea el nudo:

- **Regulatorio** — qué se confirmó sobre organismos/normas que alcanzan la solución.
- **Marco legal** — qué se puede/no se puede (datos, delegación, contratos).
- **Stack tecnológico** — stack real, integraciones posibles, qué es reutilizable vs. a rehacer.

## Salida (más extensa que el pre)

### 1. Problemática (ampliada)
Qué entendíamos antes vs. ahora. Nombrar explícitamente lo que cambió.

### 2. Contexto ampliado
Todo lo nuevo: sistemas, restricciones, números, prioridades, decisores.

### 3. Usuarios / roles / permisos
Refinado con lo confirmado en la reunión.

### 4. Propuesta
- **Alcance** — qué sí, qué no.
- **Discovery** — 1 a 4 semanas según complejidad.
- **Prototipo si es factible** — puede ser una web, una explicación o un flujo. No siempre es una pantalla.
- **¿Podemos ayudar o no?** — factibilidad honesta; si falta API/experiencia/acceso, acá.

### 5. Minuta y próximos pasos
- **Abiertos.** Lo que quedó sin cerrar.
- **Acciones.** Mandar la minuta al cliente en el momento / máximo 1–2 días; generar las tareas del entregable siguiente.

### 6. Seguimiento de stakeholders
Un MD de seguimiento por stakeholder (estilo PM Brain), enriquecido reunión a reunión. Devuelve **cómo operar con cada persona**:
- Riesgos y qué tener en cuenta.
- **Modo de comunicación:** qué genera fricción vs. qué agiliza la respuesta.
- Canal y forma preferidos (ej.: "mail con Marcos en copia, no WhatsApp"; "WhatsApp sintético 1-2-3-4").
- Tiempos de respuesta observados.

> Motivaciones y estilos de cada stakeholder son **interpretaciones**: etiquetalas y anclalas a la transcripción/fuente de donde salieron.

## Ejemplo trabajado — de reunión a propuesta

**Input:** Documento de Preparación de AL2/ACA + transcripción Granola de la reunión + doc de proceso de onboarding actual que mandaron.

**Cómo lo interpretás:** en el pre asumíamos "unificar el alta de billetera y financiera". En la reunión se confirma que el nudo es el **eje regulatorio**: el KYC de AL2 (BCRA) no puede reutilizarse tal cual para abrir la cuenta comitente de ACA Valores (CNV/UIF, PLD indelegable). El objetivo real pasa a ser **un onboarding único que ramifica**, no un alta única.

**Output (extracto):**
- *Problemática ampliada:* no es "un alta para los dos"; es una **puerta de entrada común** que reutiliza los datos compartibles y dispara dos flujos de KYC distintos según regulador.
- *Propuesta:* discovery de 3 semanas; prototipo de flujo (no pantalla) mapeando qué dato se pide una sola vez y dónde se bifurca por regulación; integra con el core de cada producto.
- *Factibilidad:* media-alta — tenemos experiencia fintech (AL2 ya es cliente); pendiente ver API de identidad y qué habilita legal/UIF.
- *Stakeholder — Genaro (CEO):* perfil negocio/embedded finance; llevarle caso de negocio y conversión, no arquitectura.
- *Stakeholder — Nahuel (CTO, ex-Wenance):* le importa KYC/PLD e integración; llevarle el mapa de datos y bifurcación.

## Fuera de alcance (v2)

- Alimentar la propuesta con **experiencias previas del equipo por rubro** ("para esto hablá con Irra/Nico/Juani") — depende del mapa de habilidades, que se releva aparte.
- Doc de experiencia reutilizable por dominio (ej.: todo lo aprendido en un CRM) para clientes futuros del mismo tipo.

## Criterios de calidad

✅ La problemática se amplía, no se parte de cero — se nombra qué cambió vs. el pre
✅ Los 3 ejes (regulatorio/legal/stack) revalidados con datos de la reunión
✅ Propuesta con alcance + discovery (1–4 sem) + prototipo-si-factible + veredicto de factibilidad honesto
✅ Minuta con abiertos y acciones, lista para enviar en 1–2 días
✅ Seguimiento de stakeholders con modo de comunicación accionable por persona
✅ Motivaciones/estilos etiquetados como interpretación y anclados a fuente
✅ Sin placeholder ni scope inflado; 100% español
