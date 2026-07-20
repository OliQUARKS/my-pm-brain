# Documento de Preparación — AL2 / ACA Valores

**Cliente:** AL2 + ACA Valores (ecosistema digital de ACA — Asociación de Cooperativas Argentinas)
**Contactó:** Genaro Gozdziewski (CEO AL2)
**Objetivo declarado:** unificar el onboarding de los dos productos
**Reunión:** Genaro Gozdziewski (CEO), Pablo López (líder PMs), Nahuel Branda (CTO), Mauro Bayo (líder producto)
**Tipo de trabajo:** build de proceso (unificación de flujo) → análisis de competidores no corrido (opcional)
**Fuente:** `/briefing-context` · research web jul-2026

---

## Contexto de empresa y rubro

Dos piezas del ecosistema cooperativo del agro, mismo dueño (grupo ACA: ACA + La Segunda + Coovaeco + Avalian), usuario de base compartido (el **productor agropecuario asociado**):

- **AL2** — billetera virtual (PSP, marco BCRA). Integra la Cuenta Corriente Cooperativa (CDC) como medio de pago; pagos, QR, VEP de ARCA, tarjeta AL2 Visa. +2 años en mercado. iOS y Android. ([ANSOL](https://ansol.com.ar/servicios/al2-billetera-virtual/), [Bichos de Campo](https://bichosdecampo.com/un-viaje-al-mundo-cooperativo-de-la-vieja-libreta-a-la-billetera-virtual-al2-los-productores-asociados-a-aca-ya-pueden-gestionar-sus-cuentas-desde-el-celular/))
- **ACA Valores** — la **ALyC** (bróker, marco CNV): acciones, letras, bonos, MEP, cuenta comitente, 100% online. ([acavalores.com.ar](https://www.acavalores.com.ar/))

La estrategia de ACA es consolidar un ecosistema digital único para el productor → de ahí la lógica de unificar el alta.

## Glosario específico del cliente

- **ALyC** — Agente de Liquidación y Compensación; el bróker registrado ante CNV. Es ACA Valores.
- **Cuenta comitente** — cuenta de inversión ligada al CUIT/CUIL; donde se acreditan los instrumentos.
- **PSP / PSPCP** — Proveedor de Servicios de Pago (con cuenta de pago); figura fintech regulada por BCRA. Es el marco de AL2.
- **CDC** — Cuenta Corriente Cooperativa; saldo del productor en su cooperativa, integrado como medio de pago en AL2.
- **KYC / PLD-UIF** — conocé-a-tu-cliente / prevención de lavado (Unidad de Información Financiera).
- **MEP** — dólar comprado vía bonos en el mercado.
- **CNV vs. BCRA** — los dos reguladores en juego: bróker (CNV) y billetera (BCRA). Núcleo del problema.
- **VEP / ARCA** — volante electrónico de pago; ARCA (ex-AFIP).

## Dolores del rubro y del caso *(interpretación — validar en reunión)*

1. **Doble regulador → doble alta.** El KYC de billetera (BCRA) y la apertura de cuenta comitente (CNV) tienen requisitos distintos: unificar un solo flujo es exactamente el punto difícil. ([ALyC/CNV](https://alfyinversiones.com.ar/blog/alyc-en-argentina-que-es-y-por-que-es-clave-para-invertir/), [BCRA billeteras](https://www.bcra.gob.ar/en/registering-in-the-interoperable-digital-wallet-registry/))
2. **PLD indelegable.** La ALyC no puede delegar el conocimiento del cliente → límite duro sobre cuánto se comparte el alta entre productos.
3. **Fricción → abandono**, más agudo en base rural (conectividad, familiaridad digital, edad del productor).
4. **Identidad duplicada** — misma persona, dos altas, datos repetidos: eso es lo que "un onboarding" promete resolver.

## Usuarios

- **Para quién:** el productor agropecuario asociado a una cooperativa ACA es el usuario común entre ambos productos — argumento del alta unificada.
- **Dos perfiles por producto:** pagador cotidiano (billetera) vs. inversor / cuenta comitente. ¿Es la misma persona o segmentos distintos? → **a preguntar.**
- **Roles y permisos:** persona humana vs. jurídica (cooperativa/empresa agro), apoderados, alta asistida por la cooperativa → **a preguntar.**

## Stakeholders en la mesa

| Quién | Rol | Qué le importa (inferido) |
|---|---|---|
| **Genaro Gozdziewski** | CEO AL2 (ex-finanzas ACA, ex-PwC; foco embedded finance) | Caso de negocio, conversión, encaje en el ecosistema. ([LinkedIn](https://www.linkedin.com/in/genaro-gozdziewski-b7b47018b/)) |
| **Nahuel Branda** | CTO (ex-Wenance, core banking / Risk IT; MBA Di Tella) | Arquitectura, integración, **KYC/PLD**, deuda técnica del flujo actual. ([The Org](https://theorg.com/org/al2/org-chart/nahuel-branda)) |
| **Mauro Bayo** | Líder de Producto | Sin dato público confiable (nombre común) — **confirmar**. Probable: drop-off, UX del alta. |
| **Pablo López** | Líder de PMs | Sin dato público confiable — **confirmar**. Probable: ejecución, coordinación entre productos. |

Van los cuatro decisores clave (CEO + CTO + producto + PMs) → señal de tema prioritario y reunión de definición, no exploratoria.

## Riesgos y restricciones — ejes obligatorios

- **Regulatorio (el nudo):** dos marcos (BCRA/PSP y CNV/ALyC) sobre la misma persona. El BCRA endureció reglas de billeteras/PSP en 2025-26 (registro, alta por terceros, transparencia) → el flujo nuevo debe nacer alineado a lo último. ([Infobae abr-2026](https://www.infobae.com/economia/2026/04/30/el-bcra-refuerza-la-proteccion-a-los-usuarios-de-billeteras-virtuales-una-por-una-las-medidas-que-adopto/))
- **Legal:** PLD/UIF limita reutilizar el KYC de un producto para el otro — confirmar qué dato es compartible.
- **Stack:** desconocido — core de cada producto, proveedor de identidad/biometría (¿Renaper?, ¿tercero?), qué API existe. → **a relevar.**

## Preguntas de discovery contextualizadas

**Problema / objetivo**
- Cuando dicen "un onboarding para los dos", ¿es **un alta única** que habilita ambos productos, o **una puerta común** que después ramifica?
- ¿Qué disparó rehacerlo ahora: un número de abandono, una exigencia regulatoria, o la decisión estratégica de unificar el ecosistema?

**Regulatorio / legal (profundizar — es el nudo)**
- ¿El alta de ACA Valores puede apoyarse en el KYC ya hecho en AL2, o UIF/CNV lo prohíbe?
- ¿Qué dato pueden pedir una sola vez y cuál obliga la regulación a duplicar?

**Impacto / negocio**
- ¿Tienen medido el drop-off del alta actual por producto y por paso? ¿Dónde se caen hoy?
- ¿El objetivo es conversión, costo operativo de alta, o cumplimiento? ¿Cómo lo miden?

**Usuario y proceso**
- ¿Es la misma persona en ambos productos o son segmentos distintos? ¿Persona humana y jurídica?
- ¿Qué rol juega la cooperativa (y la CDC) en el alta?

**Stack / factibilidad**
- ¿Con qué está hecho el onboarding actual y qué proveedor de identidad usan?
- ¿Tienen API y documentación de ambos flujos? ¿Qué es reutilizable vs. a rehacer?
- ¿Qué intentaron ya que no funcionó?

---

## Gaps explícitos (a preguntar en la reunión)

- Perfiles de Mauro Bayo y Pablo López.
- Si el usuario es el mismo entre productos o son segmentos distintos.
- Roles / permisos y persona jurídica.
- Stack actual y proveedor de identidad.
- Métricas de drop-off del alta.
- Qué permite/prohíbe legal compartir entre el KYC de BCRA y el de CNV.

## Opcional — no corrido

Análisis de competidores FODA no aplica (el pedido es unificar un flujo interno, no posicionar un producto). Como *vuelta de tuerca* se puede correr un **benchmark de onboarding** (no FODA) de cómo resuelven el alta billetera + inversión players como Ualá, Mercado Pago, Cocos Capital, Balanz o IEB — útil para llevar ejemplos concretos de flujo único.
