# Skill: prototipador (arma el prototipo funcional navegable, POST build-context)

**Tu objetivo:** convertir lo que entendimos del cliente en un **prototipo funcional navegable** — un archivo HTML/CSS/JS autocontenido y clickeable que muestra las pantallas core del MVP imaginado. No es un mockup estático ni un documento: es algo que el cliente abre, navega y "toca". Fin último: que el cliente *vea* la solución y diga que sí.

**Uso 100% privado — nunca se publica como Artifact.** El prototipo contiene información del cliente (marca, flujos, a veces datos de ejemplo cercanos a los reales). Un Artifact publicado queda accesible por link a cualquiera que lo tenga (y potencialmente indexable si el link se filtra) — eso es exactamente lo que este skill tiene que evitar. El entregable es siempre el `.html` como archivo, nunca un link público (cambio 2026-08-14, ver [ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md](../../ingestion/meetings/2026-08-14-sync-jony-preventa-feedback.md)).

## Dónde encaja en el ciclo

Ver [`briefings/_ciclo-preventa.md`](../../briefings/_ciclo-preventa.md). Corre **después de `build-context`**. Su relación con [`/propuestador`](./propuestador.md) depende de si `propuestador` corrió en modo multi-camino (ver `propuestador.md § Fase 0`):

- **Si `propuestador` ya decidió un camino** (pasó su checkpoint de Fase 0) → prototipá **ese camino elegido**, no el build-context crudo. Es el default a partir del rediseño de `propuestador`.
- **Si `propuestador` todavía no corrió, o corrió en modo "caso simple" sin comparar caminos** → cae al comportamiento de siempre: prototipá directo del build-context (§ Gate duro abajo).
- Si el caso amerita prototipar más de un camino (poco frecuente — solo si el equipo lo pide explícitamente), está bien generar más de un `.html`, uno por camino.

## Gate duro — sin brief no hay prototipo

- **Ideal:** existe el camino decidido por `propuestador` (o, si `propuestador` no corrió en modo multi-camino, el `build-context` del cliente) → se prototipan las pantallas del MVP con fundamento.
- **Mínimo aceptable:** hay `briefing-context` + transcripción del briefing → prototipo más conceptual (menos pantallas, más simulado).
- **Menos que eso (solo cold start, sin reunión):** **no se arma.** Decilo y pará. Prototipar sin haber escuchado al cliente es inventar.

## Regla de oro — cara al cliente, lo interno nunca cruza

Mismo criterio que `/propuestador`. El prototipo muestra **el producto**, nunca nuestra cocina: sin tensiones internas, sin lectura de stakeholders, sin competidores, sin montos, sin activos internos reutilizados. Si algo es interno, se queda en el build-context.

**Ojo con la lógica interna del producto ≠ UI del cliente.** Una cosa es lo que el sistema **valida por detrás** (controles de stock/cupo/precio/crédito, reglas de negocio, colas de aprobación) y otra es lo que el **usuario final ve**. Esos controles no se muestran como un checklist en la pantalla del cliente — se manifiestan en su UX (un badge de stock, su saldo de cuenta, un mensaje si algo no da) y su **vista completa vive en el backoffice**, no en la app del cliente. Preguntate por cada bloque: "¿esto lo ve el cliente o es operación interna?".

## Branding — cascada de 3 niveles

1. **Manual de marca del cliente (si lo mandó).** Colores, tipografías, logo, tono visual. **Todo inline, sin excepción** — paleta en CSS variables, logo/imágenes como `data:` URI, tipografías embebidas o el fallback de sistema más cercano. Nada de `<link>` a fonts o CDNs externos. Ya no es una restricción técnica de Artifact (dejamos de publicar ahí) — es una regla que se mantiene **por el mismo motivo de privacidad**: un archivo 100% privado no debería hacer llamadas a servidores externos (fuga de metadata de que el archivo se abrió, y dependencia de internet si se manda como adjunto offline).
   - **Logo y tipografía = assets, no se improvisan.** El manual suele **prohibir modificar la composición del logo**, y las webfonts externas quedan afuera por la regla de arriba. Si no tenés el logo en SVG/PNG usable ni el archivo de fuente para embeber como `@font-face` data-URI, **prototipá con una aproximación pero rotulala como tal** (logo aproximado / stack de sistema que evoca el original) y **dejá pedido el asset oficial** como gap. No deformes el logo real para que "entre".
2. **Sin manual, con web relevada.** Deriva la paleta y el estilo de los sitios del cliente que `briefing-context`/`build-context` ya investigaron (colores, tipo de la marca, densidad visual del rubro).
3. **Sin nada.** Sistema estándar limpio y neutro, sobrio, apto para el rubro. No inventes una identidad de marca falsa.

## Alcance del prototipo

- **MVP navegable, no producto real.** Flujos clickeables con **data mockeada**; sin backend, sin auth real, sin integraciones vivas. Lo simulado se ve como simulado (datos de ejemplo evidentes, no cifras que parezcan reales del cliente).
- **Las pantallas core primero.** Del alcance MVP del build-context, elegí el camino feliz que mejor demuestra el valor. No cubras todo el roadmap — eso confunde MVP con futuro.
- **Formato: web vs mobile — es una decisión, no un default.** Elegí según el producto y sus usuarios: un backoffice/panel interno o una web app B2B es **web de escritorio** (no lo enmarques en un teléfono); una app de consumo o de operarios en la calle es **mobile-first**. Un PWA puede ser ambas: definí cuál es la vista primaria del caso. No metas todo en un frame de teléfono por costumbre.
- **Producto con dos caras → prototipá las dos (o dejá dicho cuál falta).** Muchos productos tienen **app del cliente + panel interno**. Si el alcance del build-context lista ambas, el prototipo idealmente muestra las dos (con un switch para alternar), o al menos deja explícito cuál quedó pendiente y por qué.
- **Responsive y theme-aware** por defecto (el Artifact se ve en claro/oscuro, y en el ancho que corresponda al formato elegido).
- **Honestidad de factibilidad.** Si el flujo real no es prototipable (ej.: depende de integración con WhatsApp / un ERP), prototipá la parte que sí muestra valor y dejá la otra como pantalla ilustrativa rotulada — nunca simules una capacidad que no vamos a poder entregar.

## Buenas prácticas de UX — happy path

Estas son las decisiones que separan un prototipo con criterio de uno improvisado. Aplican solo al camino feliz — no es un checklist de edge cases.

- **Jerarquía visual clara.** Una acción primaria por pantalla, visualmente dominante (tamaño/color/posición). Las secundarias no compiten con ella.
- **Feedback inmediato.** Cada acción del camino feliz responde visualmente — estado activo, confirmación, transición. El usuario nunca hace click "al vacío".
- **Consistencia de componentes.** Mismo patrón de botón/card/input repetido en todas las pantallas del prototipo. No reinventar el patrón pantalla a pantalla.
- **Navegación predecible.** El usuario siempre sabe dónde está (tab activo, título de sección, breadcrumb si aplica) y cómo volver.
- **Carga cognitiva mínima.** Mostrar en cada paso solo lo que el camino feliz necesita — no todos los campos/opciones de una vez.
- **Affordance clara.** Lo clickeable se ve clickeable; lo no interactivo no se disfraza de botón.
- **Formularios legibles.** Labels visibles (no solo placeholder), agrupación lógica de campos, tamaño de campo acorde al dato esperado.
- **Densidad acorde al producto.** Backoffice/panel interno tolera más densidad de información; app de consumo, menos.
- **Accesibilidad básica.** Contraste suficiente en texto y CTAs, tap targets ≥44px en mobile.

## Cómo trabajás

1. Cargá el **mejor contexto disponible** (build-context si existe; si no, briefing-context) + branding (manual / web / estándar).
2. **Antes de escribir el Artifact, cargá el skill `artifact-design`** — calibra cuánto diseño amerita el caso.
3. Definí el conjunto mínimo de pantallas del camino feliz del MVP.
4. Antes de escribir cada pantalla, repasá § Buenas prácticas de UX (happy path).
5. Escribí el HTML/CSS/JS autocontenido (todo inline, sin llamadas externas) como un único archivo. **No lo publiques con la tool `Artifact`** — queda como archivo, nunca como link.
6. Guardalo versionado en el repo y cerrá al PM (ver § Salida) — la distribución al cliente es decisión y acción del PM, no del skill.

## Entrada

- **El build-context** del proyecto (alcance MVP de `§ B`, usuarios/roles de `§ A3`) — o el briefing-context si el build-context aún no existe.
- **Manual de marca del cliente**, si lo mandó.
- **Investigación de las webs del cliente** relevada por skills previos (para derivar estilo si no hay manual).
- **Decisiones internas** de alcance (qué entra al MVP, con diseño o no).

## Salida

1. **Archivo HTML versionado en el repo:** `briefings/<YYYY-MM>-<cliente>-prototipo.html` — autocontenido, clickeable localmente en el navegador. **Es el entregable**, no un respaldo.
2. **Nota de respaldo:** `briefings/<YYYY-MM>-<cliente>-prototipo.md` — qué pantallas se prototiparon, de dónde salió el branding (manual/web/estándar), qué quedó mockeado o ilustrativo, qué falta para volverlo real.
3. **Cierre al PM:** ruta del `.html` y el `.md` + qué se prototipó + qué quedó simulado + gaps que el cliente tiene que confirmar. El PM decide cómo y cuándo se lo hace llegar al cliente (adjunto por su canal privado) — el skill no publica ni comparte nada.

> **Puente a Figma (opcional, evaluar caso a caso).** Sin un link público de Artifact, importar a Figma requiere subir el `.html` por otra vía privada (o generar un Artifact temporal solo para ese fin puntual y borrarlo después). No es el default — solo si diseño lo pide explícitamente, y pesando si vale la pena la excepción de privacidad para ese caso.

## Fuera de alcance

- La **propuesta** cara-al-cliente (documento comercial) → [`/propuestador`](./propuestador.md).
- La **minuta** de la reunión → [`/minutero`](./minutero.md).
- Producto real con backend / integraciones vivas → post-venta, no acá.

## Criterios de calidad

✅ Gate respetado: sin al menos reunión de brief, no se arma
✅ Si `propuestador` corrió en modo multi-camino, prototipa el camino elegido — no el build-context crudo sin decisión
✅ Entregable = archivo `.html` autocontenido y navegable (clickeable), **nunca publicado como Artifact**
✅ Branding en cascada: manual → web relevada → estándar; todo inline (nada de fonts/CDN externos), por privacidad y portabilidad
✅ Cara al cliente: sin montos, tensiones, stakeholders, competidores ni activos internos
✅ MVP nítido, camino feliz; lo simulado se ve como simulado; roadmap no se prototipa como si fuera MVP
✅ Cada pantalla del happy path respeta el checklist de § Buenas prácticas de UX (jerarquía, feedback, consistencia, navegación, carga cognitiva, accesibilidad básica)
✅ Factibilidad honesta: no se simula una capacidad que no vamos a entregar
✅ Responsive + theme-aware
✅ Fuente `.html` versionada en el repo + nota `.md` + link del Artifact devuelto al PM
✅ Sin placeholder ni scope inflado; 100% español, registro del cliente
