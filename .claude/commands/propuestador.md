# Skill: propuestador (arma la propuesta cara-al-cliente, POST build-context)

**Tu objetivo:** convertir el `/build-context` (interno) en el **documento de propuesta que se le entrega al cliente**. No es un resumen del contexto: es la pieza comercial que ordena qué entendimos, qué proponemos, qué hace, cómo lo trabajamos y hacia dónde escala — escrita en **lenguaje profesional, positivo y cerrado**, lista para leer del otro lado. Fin último: que el cliente diga que sí.

## Las tres capas — de dónde viene y qué es esto

1. **Contexto del proyecto (`/build-context`) — INTERNO.** El insumo. Nunca se entrega. De ahí sale la sección B (pre-propuesta) que este skill expande.
2. **Propuesta (este skill) — CARA AL CLIENTE.** El documento que se comparte. Toma la pre-propuesta del build-context y la vuelve un documento completo, profesional y navegable. Alcance funcional + cómo trabajamos + roadmap. **Los montos y el equipo cerrado van en una hoja de presupuesto aparte** (ver § Salida operativa).
3. **Propuesta real / contrato — post-"sí".** Cierre de equipo, tiempo, costo y arranque de discovery. No se arma acá.

## Regla de oro — interno nunca cruza a cara-al-cliente

El build-context tiene material que **jamás** aparece en la propuesta. Al derivar, dejá afuera:

- **Montos, rates, márgenes** — van en la hoja de presupuesto aparte, no en el cuerpo funcional.
- **Tensiones internas y lectura de stakeholders** — escepticismos, "empezar chico como táctica", quién es el gatekeeper, qué le irrita a quién.
- **Análisis de competidores / cómo ganamos el deal.**
- **Dudas de factibilidad sin resolver** — lo abierto se nombra como "a definir en el discovery", nunca como "no sabemos si podemos".
- **Nombres internos de riesgo, aprendizajes de otros clientes, activos internos** (ej.: "reusamos el CRM de X").

Si algo del build-context es interno, se queda en el build-context. La propuesta habla de **valor para el cliente**, no de nuestra cocina.

## Cómo trabajás

- **Derivás, no inventás.** Cada afirmación de la propuesta se apoya en el build-context y sus fuentes. Nada nuevo que no esté respaldado.
- **Lenguaje profesional y completo.** Ni bullets telegrama ni prosa inflada. Cada punto dice **qué** y **por qué le conviene al cliente**. El registro es el del cliente (español, tono del rubro).
- **MVP nítido, futuro separado.** Lo que entra al MVP se distingue con claridad de lo que es fase posterior. No prometer el roadmap como si fuera el MVP.
- **Iterativo.** La primera versión es la base; se revisa con el equipo y se "azucara" (lenguaje más profesional y detallado) antes de enviar. Los **flujos de trabajo** (los agrega quien corresponda) y la **hoja de presupuesto** se suman al final.

## Entrada

- **El `/build-context`** del proyecto (sección B pre-propuesta como esqueleto; secciones A y factibilidad como insumo).
- **Decisiones internas** ya tomadas (alcance MVP vs. fases, diseño sí/no, modalidad de trabajo).
- **Mockups / prototipos** del cliente o nuestros, si los hay.
- **Correcciones de la review interna** (lo que el equipo marcó al revisar el borrador).

## Estructura del documento — las 7 secciones

Adaptá los títulos al caso, pero este es el esqueleto que funciona:

1. **Qué entendimos.** El problema del cliente en su lenguaje, con el dolor concreto y por qué ahora. Demuestra que escuchamos. Una o dos frases, sin rodeos.
2. **La solución en una frase.** Qué es el producto, dicho simple. Si tiene varias caras (ej.: app del usuario final + panel interno), nombrarlas acá.
3. **Qué hace — funcionalidad del MVP.** El corazón. Desglosado por cara del producto cuando aplica (ej.: *A. App del cliente* / *B. Panel interno*). Cada funcionalidad en una línea clara. Cerrá con un bloque **"Fuera del MVP (fases posteriores)"** que liste explícitamente lo diferido — protege el alcance.
4. **Cómo se apoya en los sistemas del cliente.** Cuando hay legacy o equipo de IT propio: dejar clarísimo que **no reemplazamos nada**, qué se consume/lee vs. qué sigue viviendo en su sistema, y cómo se integra (middleware/servicios, cadencia de sync). Baja la ansiedad técnica del cliente.
5. **Cómo trabajamos.** Metodología (ágil/Scrum), etapa inicial de alineación, implementación por fases, gestión transparente (reuniones, visibilidad, documentación), calidad/validación (pruebas en vivo, adopción), y propiedad del cliente + partner de largo plazo. **Cada punto con su porqué** — es la sección que más confianza cierra. Registro profesional y desarrollado, no telegráfico.
6. **Roadmap a futuro.** Las fases siguientes al MVP, como camino de valor, no como promesa incluida.
7. **Próximos pasos.** Acciones concretas para avanzar (cerrar puntos técnicos, demo de trabajo previo, confirmar insumos, arrancar).

## Ejes a cuidar según el caso

- **Legacy / IT propio del cliente** → la sección 4 es crítica; enfatizar acople y propiedad.
- **Cliente sensible al diseño** → nombrar la experiencia/estética como parte del valor (no como costo).
- **Producto de cara a usuarios cautivos** → la adopción es parte del proyecto, decirlo en la sección 5.
- **Regulado** → dónde toca cumplimiento, sin prometer de más.

## Salida operativa

- **Documento** en el formato acordado (Markdown en el brain + **Google Doc** para compartir).
- **Hoja de presupuesto** — se suma como sección/hoja final, aparte del cuerpo funcional. Equipo, tiempo, inversión. **Se completa con criterio del PM** (montos nunca inventados).
- **Flujos de trabajo / diagramas** — los agrega quien corresponda como anexo.
- **Cierre al PM:** ruta del documento + qué quedó listo + qué falta antes de enviar (presupuesto, flujos, "azucarado" final) + gaps que el cliente tiene que confirmar.

## Ejemplo trabajado — Lodiser (canal profesional)

**Input:** build-context de Lodiser (ecommerce cerrado B2B) + decisiones internas (con diseño, arranque por fases) + correcciones de review.

**Cómo lo derivás:**
- La pre-propuesta del build-context ("front PWA + login + guarda cabecera/detalle contra la DB que Lodiser sirve") se vuelve el cuerpo funcional, desglosado en **A. Web app del cliente** (catálogo, mis habituales, carrito con controles de stock/cupo/precio/crédito, checkout sin pago, seguimiento) y **B. Panel de Lodiser** (ABM de clientes, carga de pedido por el vendedor, tablero, vista por producto/cliente/vendedor).
- La sección 4 deja claro que **la plataforma no reemplaza nada**: consume los maestros/controles vía middleware liviano y solo registra el pedido; el catálogo se **lee** (el ABM de productos/precios sigue en su sistema).
- **Queda afuera** (interno): el escepticismo del gerente de sistemas, el activo interno para la fase WhatsApp, los montos y la táctica de "empezar chico".

**Output (extracto):**
- *Qué entendimos:* los pedidos dependen 100% del vendedor que carga a mano desde audios de WhatsApp → se pierden ventas fuera de horario.
- *Cómo trabajamos:* etapa inicial de alineación con el equipo de sistemas + Scrum + implementación por fases con clientes definidos en conjunto + propiedad del cliente. Cada punto con su porqué.
- *Roadmap:* data/marketing, WhatsApp (bot que toma pedidos), otros canales.

## Fuera de alcance

- Cierre de **equipo/tiempo/costo definitivo** (post-"sí", en la propuesta real/contrato).
- La **minuta** de la reunión (skill de minuta).
- Diseño de los **flujos de trabajo/diagramas** (los aporta quien corresponda; este skill deja el lugar).

## Criterios de calidad

✅ Deriva del build-context, no arranca de cero — cada afirmación respaldada
✅ Interno nunca cruza: sin montos en el cuerpo, sin tensiones/stakeholders/competidores/activos internos
✅ Las 7 secciones presentes y adaptadas al caso; MVP nítido y separado del roadmap
✅ Sección 4 (apoyo en sistemas del cliente) presente cuando hay legacy/IT propio
✅ "Cómo trabajamos" desarrollada y profesional, cada punto con su porqué
✅ Bloque "Fuera del MVP" explícito para proteger alcance
✅ Presupuesto y flujos identificados como hojas aparte (no en el cuerpo funcional)
✅ Lo abierto se nombra como "a definir en discovery", nunca como duda de factibilidad
✅ Sin placeholder ni scope inflado; 100% español, registro del cliente
