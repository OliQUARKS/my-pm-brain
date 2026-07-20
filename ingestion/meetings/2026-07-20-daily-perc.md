# Ingesta — Daily PERC (Quarks interno, 2026-07-20)

- **Fuente (transcript):** [../../source/meetings/2026-07-20-daily-perc.md](../../source/meetings/2026-07-20-daily-perc.md)
- **Shape:** meeting (daily interno del equipo Quarks; briefing de contexto a Pablo Folgar + plan de trabajo)
- **Participantes:** Olivier (PM, "Me"), Marcos Perez (dev back), Nicolás Paez (TL), **Pablo Folgar** (nuevo en el hilo PERC — testing/QA, remoto en Valencia).
- **Contexto:** daily del mismo día que el [SYNC Producto](2026-07-20-sync-producto.md). Olivier pone en contexto a Pablo (la demo del jueves 17/7, la bomba de lambdas, el call AMFAYS) y se define el **plan de trabajo/secuencia** (cash out → threshold → refactor de lambdas), el **estado del entorno** y una **estrategia de UAT asistido por IA** que arma Pablo. Mayormente **confirma/refina** lo ya ingestado los 16–17/7.

---

## 1. Estado del entorno dev (refina el bloqueante de entorno)

- **(observation)** Con lo que **subió Gonza**, el dev env está **al estado del día de la demo** (en rigor, "un poquito antes" — había un PR abierto que Marcos tenía en local el día de la demo). O sea: Olivier entra a dev y ve la versión ~demo. **No es el "100%"** todavía: cuando se haga el refactor de lambdas se vuelve a mover todo. — Marcos + Olivier, [source](../../source/meetings/2026-07-20-daily-perc.md)
- **(decisión operativa)** Próximo paso: **Marcos sube el front al repo → le pide a Gonza que deploye la web apuntando a stage** → recién ahí se puede **probar sobre la web (no solo Insomnia)**. Olivier se ofrece a ayudar con ese testing. — Marcos + Nico + Olivier.
- **(observation)** Marcos tiene ventana de trabajo acotada para el cash out: **de 9 a 18** (cuando se deploya todo). — Marcos.
- **(acción, Olivier)** Va a **mandar los pendientes al canal de PERC todos los días** y **"romper la pelota" con el tema del entorno**. (Marcos pide que **no agregue todavía** el front — aún no lo subió.) — Olivier + Marcos.

## 2. ⭐ Secuencia de trabajo (plan técnico — NUEVO)

- **(decisión, equipo Quarks)** Orden de los cambios grandes pendientes:
  1. **Cash out / desembolso** — en curso ahora; cambio **grande y meticuloso**. Agrega **4 lambdas más** (total ~**60→64**). Marcos le pide tiempo a **Nico** para revisar y **destrabar el PR rápido**.
  2. **Threshold de decimales** — tercera etapa; se puede meter **mientras se aprueba el PR de cash out** (si tarda).
  3. **Refactor de lambdas** — otro cambio grande (**~60 archivos, ~30 de test**); **no se puede meter hasta que pase el PR de cash out** (conflicto de código). — Marcos.
- **(interpretation)** El refactor "hubiese estado bueno meterlo antes" del cash out (así no se agregan 4 lambdas que después hay que reagrupar), pero ya está encaminado el cash out → se sigue en ese orden. — Marcos.

## 3. Re-arquitectura de lambdas — causación CONFIRMADA por el equipo técnico

- **(observation)** Nico (TL) da la explicación técnica más precisa: **no es que a PERC "no le gustó"**, sino que **se dieron cuenta de que eran muchas lambdas a deployar → el CI tardaba ~45 minutos + los costos se disparaban** (AWS serverless, no infra propia). — Nico Paez.
- **(observation)** Sobre "¿la arquitectura era nuestra o de ellos?" (pregunta de Pablo): "**fue viajando**" (evolucionó/creció con el tiempo) hasta que **surgió el problema de costo/CI**. — Marcos + Nico.
- **(nota — resuelve parcialmente la contradicción del SYNC)** Esta es la voz técnica confirmando la causa: **costo + tiempo de CI (45 min)**, consistente con la [ingesta del 16/7 (CI/CD + auditorías Amazon)](2026-07-16-uat-prestamos-lambdas-perc.md) y con la re-atribución de Norverto en el [SYNC](2026-07-20-sync-producto.md). El matiz "arquitectura de PERC desde el inicio" (Norverto) se atempera a "**fue evolucionando** hasta que el costo lo hizo inviable" (Nico). Cifra: ~**60** lambdas hoy (coherente con ~65 del 16/7). **Dato nuevo concreto: CI = ~45 min.**

## 4. Threshold de decimales (refina la decisión pendiente)

- **(observation)** Confirma: threshold **configurable**, del orden de **~3 dígitos después de la coma** ("y después ya está"). Es un **margen de error** para no exigir el número exacto al conciliar. — Marcos.
- **(observation → rationale de negocio)** PERC **rechazó** la función de **"dar por pagada"** (marcar como pagado con un clic, sin enviar el monto) **porque implicaría tener a alguien operativo** haciendo ese clic sobre miles de cuotas — justamente lo que quieren evitar. Por eso piden el threshold automático. — Olivier + Marcos.
- **(nota)** Marcos siente que **no supo explicar bien** la función "dar por pagada" en la demo; su intención era ahorrar el envío del monto, no crear trabajo operativo. Refina la decisión [2026-07-16-threshold-tolerancia-pago-cuota](../../decisions/2026-07-16-threshold-tolerancia-pago-cuota.md): agrega el **valor candidato (~3 decimales)** y el **motivo del rechazo del clic manual**.

## 5. Firma / KYC — auditoría de identidad (confirma 17/7)

- **(observation)** AMFAYS **auditará el proceso de validación de identidad de PERC/Perk**, no impone el suyo. Lectura de Marcos: si PERC pide **TOTP**, "ya es válido" (verificación en dos pasos); la **foto / prueba de vida** ya se hace en el **onboarding**; **sujeto obligado / PEP** también se resuelve en el onboarding. Olivier: no hay que re-capturar nada, solo **traer del onboarding** la identidad ya validada al armado del documento. — Marcos + Olivier. Consistente con [ingesta AMFAYS 17/7 §4](2026-07-17-call-amfays-documento-prestamo.md).

## 6. ⭐ Protección de datos del documento AMFAYS (NUEVO — compliance/liability)

- **(observation, arquitectura)** **Quarks NO guarda ningún dato del documento** — solo **guarda la referencia** al documento, que está **almacenado del lado de ellos** (AMFAYS/PERC). — Marcos + Nico.
- **(open question)** ¿Viajan / se loguean datos sensibles (DNI, importe, cuota) en el request o en logs? La **cuenta de la persona sí viaja** en el request. Idea: **hacer un check al final** para verificar que no queden datos sensibles en logs/docs. El request va por HTTPS (segurizado en tránsito); el foco es que **no quede persistido en logs**. — Nico + Pablo + Marcos.
- **(interpretation, Pablo — recomendación de gobernanza/CYA)** Dejar un **registro documentado** de que Quarks **planteó y se ocupó de la protección de datos el 2026-07-20**, para que Olivier pueda **defenderse a futuro** ("el 20/7/2026 dijimos esto") — la responsabilidad del tratamiento de datos queda del lado de PERC/AMFAYS, pero Quarks debe **cubrirse por escrito**. (stakeholder-verbal, Pablo Folgar, 2026-07-20)
- **(interpretation, Marcos)** **Quizás el documento lo tengan que hacer ellos** (AMFAYS/PERC), para que **no viaje toda esa data por Quarks**. — Marcos.
- **(nota de alcance)** Olivier: "no nos metimos en el tema de protección de datos" en el call. Queda como **frente abierto** — se conecta con el diseño de consentimiento/cesión ya existente ([knowledge/compliance/datos-personales/diseno-consentimiento-mantovana.md](../../knowledge/compliance/datos-personales/diseno-consentimiento-mantovana.md)), que hoy cubre Mantovana pero **no a AMFAYS como tercero**.

## 7. Placeholders del documento AMFAYS — enfoque de implementación (refina el SYNC)

- **(decisión en principio — vía WhatsApp Fefe/Seba)** Confirma lo del [SYNC](2026-07-20-sync-producto.md): dejar **placeholders** en el documento ("acá va este campo") y **cablear la función** para capturar los datos más adelante. — Olivier.
- **(interpretation, Marcos — approach técnico)** Levantar un **HTML pelado con texto plano + variables** (NO el documento real de AMFAYS, porque va a cambiar), con **toda la lógica de firma**, y **entregar la función**; **AMFAYS/PERC adaptan el documento después**. — Marcos.
- **(interpretation, Marcos — expectativa de plazo)** El tema del documento AMFAYS **"va a durar meses y meses"**; conviene **desacoplarlo de la entrega del MVP** (dejar la función cableada y seguir). "Nos subcontrataron para hacer el producto; ellos tienen equipo de sistemas (Jo, Gonza) y probablemente no lo implementen ahora." — Marcos.

## 8. ⭐ UAT asistido por IA (NUEVO — estrategia de testing, la trae Pablo)

- **(idea/plan, Pablo + Marcos)** Armar **casos de testeo ejecutables por IA** a partir del **Excel de casos de uso de Olivier** + la **colección de Insomnia**: la IA prueba un endpoint como si fuera humano, **verifica el resultado y el estado en la base de datos** (acceso de lectura), y valida que lo esperado se cumpla. — Marcos + Pablo.
- **(observation)** No hace falta que Olivier cargue input+output para "entrenar" la IA — los esperados ya están en los casos; hay que **contemplar la lógica propia del proyecto** (ej. no se puede firmar un crédito sin documento asociado; no se puede pedir un 2º préstamo si hay uno activo). — Marcos + Pablo.
- **(decisión de alcance)** Arrancar **acotado — una tabla por vez** (ej. crear credit template → chequear DB → ver logs → filtrado/ordenamiento), correr una prueba, juntarse y ver qué falta. **No** ir al detalle fino ("10 millones de casos de uso") todavía; los casos de horror/edge se agregan después. — Pablo + Marcos.
- **(acción, Pablo)** Toma el link al Excel, **modifica su colección de Insomnia** basada en los casos de uso, corre una prueba y se juntan a revisar. — Pablo.

## 9. Ruteo — destinos durables (PROPUESTOS, requieren OK del PM — Autonomy = propose-and-wait)

- **`stakeholders/pablo-folgar.md` — NUEVO.** QA / testing (UAT asistido por IA), Quarks, remoto (Valencia). Influencia media sobre mi trabajo (dueño del enfoque de testing del UAT). + fila en `stakeholders/INDEX.md`. **Requiere OK (nuevo stakeholder).**
- **`stakeholders/marcos-perez.md`** — touchpoint 2026-07-20 (daily): secuencia cash out→threshold→refactor; +4 lambdas; approach HTML-pelado para el documento; enfoque de UAT-IA. Last-touched 2026-07-20.
- **`stakeholders/nicolas.md`** — touchpoint 2026-07-20 (daily): explicación técnica de la re-arquitectura (CI 45 min + costo AWS serverless); va a revisar el PR de cash out. Last-touched 2026-07-20.
- **`decisions/2026-07-16-threshold-tolerancia-pago-cuota.md`** — agregar a Evidence/Remaining: valor candidato **~3 decimales configurable** + **motivo del rechazo del clic "dar por pagada"** (evitar operador). Sigue pending (valor de negocio lo define PERC).
- **`knowledge/product/features/flujo-credito.md`** — §Timeline 2026-07-20 (daily): secuencia de trabajo + entorno al estado demo + plan de deploy a stage + UAT-IA + flag de protección de datos. §Risks (lambdas): agregar dato **CI ~45 min** y que la causa la confirma el equipo técnico (costo/CI). §Documento AMFAYS: approach HTML-pelado + expectativa "meses" + desacople del MVP. §Open questions: protección de datos del documento (¿qué viaja/se loguea?).
- **`knowledge/product/pendientes-produccion.md`** — §1 (entorno): estado demo tras subida de Gonza; siguiente = deploy front a stage. §2 (lambdas): CI 45 min + orden (post cash out). §6 (cashout): en curso, +4 lambdas, ventana 9–18. §8 (threshold): ~3 decimales, clic manual rechazado. Nuevo ítem: **UAT asistido por IA** (Pablo) como enfoque de §5. Nuevo ítem Tier 3: **registro de protección de datos del documento AMFAYS** (¿qué viaja/se loguea? + registro CYA).
- **`knowledge/compliance/datos-personales/`** — **PROPUESTO (judgment-heavy, requiere OK):** nota de que **AMFAYS entra como nuevo tercero** en el tratamiento de datos (además de Mantovana), y que el diseño de consentimiento/cesión debería contemplarlo; + la decisión arquitectónica "Quarks solo guarda la referencia, no los datos" y la recomendación de dejar registro fechado. Puede ir como sección nueva en `diseno-consentimiento-mantovana.md` o archivo nuevo `tratamiento-datos-amfays.md`.
- **`decisions/`** — sin decisión formal nueva. La secuencia de trabajo y el approach HTML-pelado son operativos (no ameritan decisión). Candidata futura: *"Documento AMFAYS desacoplado del MVP: se entrega la función de firma cableada con placeholders, AMFAYS adapta después"* — si el PM quiere anclarla tras la C12.

## 10. Contradicciones / tensiones con evidencia previa

- **Lambdas — CONVERGE, no contradice:** la voz técnica (Nico) confirma costo + CI 45 min como causa; atempera el "arquitectura de PERC desde el inicio" (Norverto) a "fue evolucionando". Consistente con 16/7. **Cierra buena parte de la contradicción que quedó abierta en el SYNC.**
- **Protección de datos — frente nuevo, no conflicto:** el diseño de consentimiento existente ([datos-personales](../../knowledge/compliance/datos-personales/diseno-consentimiento-mantovana.md)) cubre Mantovana pero **no AMFAYS**. Amplía, no contradice.
- **Placeholders/HTML-pelado — coherente** con la decisión de documentos dinámicos HTML→PDF ([2026-06-01](../../decisions/2026-06-01-documentos-dinamicos-html.md)) y con "el usuario no carga nada". Refina el "cómo".
