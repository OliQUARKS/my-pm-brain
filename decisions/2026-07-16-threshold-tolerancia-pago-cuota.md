# Decision: Evaluar el pago de una cuota con un margen/threshold (delta) configurable, no por igualdad exacta

## Status
pending

## Date
2026-07-16

## Context
Hoy la conciliación de una cuota compara el monto descontado por La Mantovana/Finegans contra el monto de la cuota por **igualdad exacta** (`igual = igual`). Si el tercero que sube el archivo **trunca** los decimales en vez de redondear, prácticamente toda cuota cae a `pago parcial` / `pago con error`, obligando a un operador de BO a aprobar manualmente miles de préstamos — operativamente inviable. Se propone introducir un margen de tolerancia (delta) para la evaluación del pago, sin tocar la precisión de almacenamiento (que se mantiene absoluta con Big.js / tipo decimal).

## Options considered
1. **Threshold/delta configurable por variable de entorno** — si la diferencia (de más o de menos) cae dentro del margen, la cuota se da por pagada. Default puesto por Quarks, ajustable. (Preferida por Jose y Marcos.)
2. Threshold configurable por el operador de BO (como el día de corte y los mails) — descartada por ahora: menos sólida hasta entender el comportamiento en producción.
3. Truncar/redondear el monto esperado al pedir el pago (en vez de tolerar en la evaluación) — Jose la desaconseja; prefiere no tocar decimales en la operación, solo en la evaluación.
4. Mantener igualdad exacta + resolución manual — descartada: volumen inviable.

## Decision
<!-- Pendiente de confirmación formal cross-team. Dirección acordada en principio: opción 1. -->

## Why
<!-- Empty for pending. -->

## Evidence
- Seba: requerir a terceros un nivel de exactitud de decimales que evite el `pago con error` "se va a volver inviable"; quedarían todas en pendiente y haría falta una persona aprobando manualmente miles de préstamos  [source/meetings/2026-07-16-demo-uat-cliente-perc.md](../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- Jose propone un "margen/delta" para la evaluación del pago, del orden de las centésimas (~3 lugares decimales, ~0,00X), configurable por variable de entorno; default de Quarks ajustable, "hasta que entendamos que está bien"  [source/meetings/2026-07-16-demo-uat-cliente-perc.md](../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- Marcos confirma que es factible agregarlo en la capa de negocio (antes de Big.js había un redondeo) sin perder la precisión absoluta de almacenamiento  [source/meetings/2026-07-16-demo-uat-cliente-perc.md](../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- Jose lo marca explícitamente como "un pequeño ajuste de requerimiento que ambos lados tienen que acordar": Quarks lo mide, PERC define qué diferencia es aceptable (decisión de negocio)  [source/meetings/2026-07-16-demo-uat-cliente-perc.md](../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- **Refinado 2026-07-20 (daily):** valor candidato = **~3 dígitos después de la coma**, configurable ("y después ya está"). PERC **rechazó la función alternativa "dar por pagada"** (marcar pagado con un clic, sin enviar el monto) **porque implicaría tener a un operativo** haciendo ese clic sobre miles de cuotas — justo lo que quieren evitar; por eso piden el threshold automático. Marcos siente que no supo explicar bien esa función en la demo.  [source/meetings/2026-07-20-daily-perc.md](../source/meetings/2026-07-20-daily-perc.md)

## Explicitly NOT doing
- No se toca la precisión de almacenamiento ni el cálculo: los montos siguen guardándose con precisión absoluta (Big.js, no punto flotante); el delta aplica solo a la evaluación "cuota pagada"  [source/meetings/2026-07-16-demo-uat-cliente-perc.md](../source/meetings/2026-07-16-demo-uat-cliente-perc.md)
- El threshold NO será configurable por el operador de BO en esta etapa (a diferencia del día de corte y los mails) — vive en variable de entorno  [source/meetings/2026-07-16-demo-uat-cliente-perc.md](../source/meetings/2026-07-16-demo-uat-cliente-perc.md)

## What would reverse this
Si PERC (negocio/compliance) define que cualquier diferencia de centavos debe resolverse manualmente (tolerancia = 0), o si la conciliación contra la caja del banco exige exactitud sin margen → se vuelve a igualdad exacta. Señal observable: definición de negocio de PERC sobre el valor del delta (incluido "0").

## Remaining ambiguities
- **Valor concreto del delta** sin definir. Jose sugirió el orden de ~centésimas / ~15 centavos / ~0,00X, pero es una decisión de negocio de PERC.
- ¿Delta absoluto (ej. ±$0,50) o porcentual (ej. ±0,1%)? En el call aparecieron ambos framings.
- Interacción con la conciliación contable contra la mutual (préstamo total vs. cobrado) — ver `flujo-credito.md` §Open questions (cuadre 2026-06-16), fuera de scope Quarks.

## For pending decisions only
- **Blocker impact:** medio — sin el delta, el volumen de descuadres operativos post-lanzamiento sería inmanejable manualmente. No bloquea el desarrollo actual (implementable en capa de negocio).
- **Deadline:** antes del UAT formal / go-live; a acordar en la reunión aparte Olivier × Seba.
- **Owner:** Olivier (lo lleva a Seba/PERC como ajuste de requerimiento cross-team).
- **Missing evidence:** valor de negocio del delta definido por PERC; forma (absoluto vs. %).

## Linked
- Feature: `../knowledge/product/features/flujo-credito.md` § Estados a nivel cuota
- Strategy: `../knowledge/strategy.md` § Tensions (watch: trabajo extra fuera de alcance)
- Stakeholders informed: `../stakeholders/sebastian.md`, `../stakeholders/jose-salgado.md`, `../stakeholders/marcos-perez.md`
