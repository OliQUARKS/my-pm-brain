# Skill: build-context (ex post-briefing, POST)

**Tu objetivo:** después de la **reunión de briefing**, **ampliar el contexto** con lo que efectivamente salió y armar el **contexto interno del proyecto/cliente**. De ese contexto se deriva una **pre-propuesta** cara-al-cliente. La salida es más extensa que el briefing-context — no es el pre corregido, es el pre **ampliado**. Fin último: que el brief tenga injerencia en cerrar el deal.

> **Dónde encaja:** etapa 4 del ciclo — ver [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md). Parte de la transcripción del briefing + documentación del cliente. **Ojo con "discovery":** cuando la pre-propuesta (§ B) vende un discovery, se refiere a la etapa post-venta/pre-desarrollo (varias sesiones, servicio pago), **no** a la reunión de briefing.

## Las tres capas — no confundirlas

1. **Contexto del proyecto (build-context) — INTERNO.** Lo que armás acá. Nunca se entrega al cliente. Es el insumo con el que trabajamos: problema ampliado, contexto, usuarios, stakeholders, roles, factibilidad y **cómo lo trabajaríamos** (contexto metodológico).
2. **Pre-propuesta / anteproyecto — CARA AL CLIENTE (liviana).** Se deriva del build-context: "esto vimos, este es el problema, esta es la solución que proponemos, acá una demo/prototipo de lo que imaginamos, ¿te interesa?". No lleva equipo/costo/tiempo cerrados.
3. **Propuesta real — recién con el "sí".** Equipo, tiempo, costo, discovery, quién se encarga. **No la armás en este skill** — este skill deja el build-context listo y la pre-propuesta pre-armada.

## Propósito

Del output de esta reunión sale una **pre-propuesta en 1–2 días** — no dejarla enfriar. Después viene el discovery, donde se refina hacia algo concreto y arranca el proyecto; pero nace mucho mejor. Regla de proceso: reservá 15 min post-reunión para procesar el output y generar la tarea, en vez de encadenar reuniones y armar minutas a la noche.

## Cómo trabajás

- **Ampliás, no reescribís de cero.** Partís del Documento de Preparación y le sumás lo nuevo.
- **Honestidad de factibilidad.** Si no tenemos experiencia, API o acceso, se dice — igual se puede proponer.
- **Puntual y accionable.** Sin placeholder, sin ambigüedad. Lo que quedó abierto se nombra como abierto, no se rellena.
- **Interno vs. cara-al-cliente siempre separado.** El contexto es interno; la pre-propuesta es lo que se muestra. No mezclar.

## Entrada

- **El Documento de Preparación** (output de `/briefing-context`).
- **Respuestas obtenidas** en la reunión.
- **Transcripción** — Granola / Meet.
- **Documentos enviados por el cliente.**
- **Info creada por nosotros** — lo que salió de reuniones internas / criterio propio (no solo lo del cliente).
- Cualquier otra info que haya aparecido.

## Qué tenés que resolver sí o sí — objetivos de información

Sobre los objetivos del pre, ahora con datos de la reunión, resolvé:

1. **Problema real (ampliado)** — qué entendíamos antes vs. qué entendemos ahora; nombrar qué cambió.
2. **Contexto nuevo** — sistemas, restricciones, números, prioridades, quién decide.
3. **Usuarios / roles / permisos** — confirmados o corregidos.
4. **Factibilidad** — ¿podemos ayudar? ¿con qué (experiencia, API, acceso)? ¿qué falta?
5. **Stakeholders** — quién es cada uno y qué rol cumple (ver sección 6).
6. **Cómo lo trabajaríamos** — contexto metodológico (ver sección 7).

## Ejes obligatorios de análisis

Revalidá los tres ejes del pre con lo que salió, y profundizá el que sea el nudo:

- **Regulatorio** — qué se confirmó sobre organismos/normas que alcanzan la solución.
- **Marco legal** — qué se puede/no se puede (datos, delegación, contratos).
- **Stack tecnológico** — stack real, integraciones posibles, qué es reutilizable vs. a rehacer.

## Salida

### A. Contexto del proyecto (interno)

#### 1. Problemática (ampliada)
Qué entendíamos antes vs. ahora. Nombrar explícitamente lo que cambió.

#### 2. Contexto ampliado
Todo lo nuevo: sistemas, restricciones, números, prioridades, decisores.

#### 3. Usuarios / roles / permisos
Refinado con lo confirmado en la reunión.

#### 6. Stakeholders — quién es cada uno
Mini perfil por persona: **rol** en el proyecto y **qué le importa** (para orientar la propuesta). Una línea por persona.

> Motivaciones y estilos de cada stakeholder son **interpretaciones**: etiquetalas y anclalas a la transcripción/fuente de donde salieron.
>
> **Fuera de este skill:** el *estilo de trato* operativo (canal preferido, qué genera fricción, cómo escalar con cada persona — ej.: "Seba por WhatsApp no Discord") es gestión del día a día → va al futuro skill `communication-context`, no acá.

#### 7. Contexto metodológico — cómo lo trabajaríamos
Cómo trabajamos con este cliente: roles y responsabilidades de ambas partes, manejo de entornos, modelo de comunicación, reviews/documentación, SLA, y qué hay que definir sí o sí. Es el bloque que responde la preocupación recurrente "¿cómo nos manejamos?" y le da el plus a la propuesta.

Usá la plantilla reutilizable: [`briefings/_contexto-metodologico.md`](../../briefings/_contexto-metodologico.md). Base estándar Quarks + ajuste por cliente (gestión total vs. con dependencias). Cada dependencia → responsable + riesgo si no se resuelve.

### B. Pre-propuesta (cara al cliente, liviana)

#### 4. Propuesta
- **Alcance** — qué sí, qué no.
- **Discovery** — 1 a 4 semanas según complejidad. (Se vende como "equipo por tanto tiempo/costo, y primero un discovery para aprovecharlo mejor" — el discovery no se compra suelto.)
- **Prototipo si es factible** — puede ser una web, una explicación o un flujo. No siempre es una pantalla.
- **Cómo lo trabajaríamos** — extracto del contexto metodológico: no solo qué hacemos, sino cómo.
- **¿Podemos ayudar o no?** — factibilidad honesta; si falta API/experiencia/acceso, acá.

### C. Salida operativa

#### 5. Minuta y próximos pasos
La minuta es un **output esperado de este skill**, pero se genera **llamando al skill [`/minutero`](./minutero.md)** — no se redacta acá. Este skill deja identificado:
- **Abiertos.** Lo que quedó sin cerrar.
- **Acciones.** Mandar la minuta al cliente en el momento / máximo 1–2 días; generar las tareas del entregable siguiente.

## Formato de salida — Google Doc formateado (+ markdown de respaldo)

El entregable de este skill es **siempre un Google Doc formateado**, nunca un `.md` suelto. Se producen dos artefactos, en este orden:

1. **Markdown de respaldo (repo).** Generá el contexto del proyecto (bloques A/B/C) como markdown y guardalo donde ya vive en el repo (`briefings/YYYY-MM-<cliente>-build-context.md`, más el `source/` de la reunión cuando aplique). Es el ancla de auditoría del segundo cerebro — no se elimina.
2. **Google Doc formateado (entregable).** Creá el documento con el conector de Google Drive a partir de **ese mismo markdown**:
   - Tool: `create_file` del conector Google Drive.
   - `title`: `Contexto de proyecto — <Cliente> — <YYYY-MM-DD>`.
   - `textContent`: el markdown completo.
   - `contentMimeType`: `text/markdown`.
   - **No** actives `disableConversionToGoogleType` — dejá que Drive convierta el markdown a Google Doc con títulos, negritas y tablas.
   - Si el PM indicó una carpeta de Drive, pasá su `parentId`; si no, queda en la raíz.
3. **Cerrá devolviendo el link del Google Doc** más la ruta del `.md` de respaldo.

El Google Doc de este skill es **interno** (contexto del proyecto), no el que se manda al cliente — la propuesta cara-al-cliente sale del skill [`/propuestador`](./propuestador.md). Regla: el markdown crudo no es el entregable final; el entregable es el Google Doc, y el `.md` queda en el repo solo por trazabilidad.

## Ejemplo trabajado — de reunión a pre-propuesta

**Input:** Documento de Preparación de AL2/ACA + transcripción Granola de la reunión + doc de proceso de onboarding actual que mandaron.

**Cómo lo interpretás:** en el pre asumíamos "unificar el alta de billetera y financiera". En la reunión se confirma que el nudo es el **eje regulatorio**: el KYC de AL2 (BCRA) no puede reutilizarse tal cual para abrir la cuenta comitente de ACA Valores (CNV/UIF, PLD indelegable). El objetivo real pasa a ser **un onboarding único que ramifica**, no un alta única.

**Output (extracto):**
- *Problemática ampliada:* no es "un alta para los dos"; es una **puerta de entrada común** que reutiliza los datos compartibles y dispara dos flujos de KYC distintos según regulador.
- *Pre-propuesta:* discovery de 3 semanas; prototipo de flujo (no pantalla) mapeando qué dato se pide una sola vez y dónde se bifurca por regulación; integra con el core de cada producto.
- *Factibilidad:* media-alta — tenemos experiencia fintech (AL2 ya es cliente); pendiente ver API de identidad y qué habilita legal/UIF.
- *Stakeholder — Genaro (CEO):* rol decisor de negocio/embedded finance; le importa caso de negocio y conversión.
- *Stakeholder — Nahuel (CTO, ex-Wenance):* rol técnico; le importa KYC/PLD e integración.

## Fuera de alcance (v2)

- Alimentar la propuesta con **experiencias previas del equipo por rubro** ("para esto hablá con Irra/Nico/Juani") — depende del mapa de habilidades, que se releva aparte.
- Doc de experiencia reutilizable por dominio (ej.: todo lo aprendido en un CRM) para clientes futuros del mismo tipo.
- **`communication-context`** — skill futuro y separado para el estilo de trato operativo por persona (canal, fricción, escalamiento del día a día).

## Criterios de calidad

✅ Las tres capas separadas: contexto (interno) → pre-propuesta (cara al cliente) → propuesta real (post-sí, otro momento)
✅ La problemática se amplía, no se parte de cero — se nombra qué cambió vs. el pre
✅ Los 3 ejes (regulatorio/legal/stack) revalidados con datos de la reunión
✅ Contexto metodológico presente: roles/responsabilidades de ambas partes, entornos, comunicación, reviews, SLA
✅ Pre-propuesta con alcance + discovery (1–4 sem) + prototipo-si-factible + "cómo lo trabajamos" + veredicto de factibilidad honesto
✅ Minuta identificada como output que llama al skill de minuta (no redactada acá)
✅ Stakeholders con rol + qué le importa; estilo de comunicación derivado al futuro `communication-context`
✅ Motivaciones/estilos etiquetados como interpretación y anclados a fuente
✅ Entregable = Google Doc formateado (interno) vía conector Drive; markdown de respaldo en el repo; se devuelve el link
✅ Sin placeholder ni scope inflado; 100% español
