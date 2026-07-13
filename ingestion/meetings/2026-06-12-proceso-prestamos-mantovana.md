# Síntesis — Call PERC × La Mantovana × Quarks (Proceso de Préstamos)
**Fecha:** 2026-06-12
**Source:** [source/meetings/2026-06-12-proceso-prestamos-mantovana.md](../../source/meetings/2026-06-12-proceso-prestamos-mantovana.md)
**Tipo:** definición operativa del ida y vuelta — primera vez con La Mantovana (Isis + Nico López) en la mesa.

Esta reunión cierra varias preguntas que el refinamiento interno del 9/6 ([ingestion/meetings/2026-06-09-sprint4-refinement-perc.md](2026-06-09-sprint4-refinement-perc.md)) había dejado abiertas, porque trajo a la operación de liquidación de La Mantovana (Isis dirige el CSC) que tiene la palabra final sobre formato, timing y casuísticas.

---

## Definiciones cerradas (decision / stakeholder-verbal)

1. **El reporte de novedades lleva SOLO la cuota del mes, no el préstamo total.** (decision) Se descartó mandar el total y que Finegans lo divida, por riesgo de redondeo/desfase y porque pronto-pago/cancelación obligarían a un "método pronto pago" en Finegans. La Mantovana liquida una "liquidación de préstamo" + un "descuento mensual" separados, así no se les desfasa la cuenta corriente. (stakeholder-verbal, Isis + Seba + Nico López + Nico Ortiz, 2026-06-12)

2. **Fecha de envío de la ida = día 20** (apertura de liquidaciones de La Mantovana). Debe ser un **valor configurable del ambiente**. Préstamos otorgados después del corte entran al ciclo siguiente (primera cuota a ~33 días). (stakeholder-verbal, Isis + Seba, 2026-06-12) — ya alineado con Marcos previamente.

3. **Finegans resuelve por número de LEGAJO, no por CUIL/DNI.** (observation, Isis + Juan Pablo, 2026-06-12) El archivo de subida masiva de La Mantovana usa: **número de legajo, número de concepto, nombre, importe, fecha (desde 1° hasta último día del mes)**. Isis ya envió por mail el modelo del importador a Seba.
   - **Implicancia técnica:** Quarks necesita el legajo para comunicárselo a Finegans → o La Mantovana da acceso a la base de legajos, o se guarda el legajo en el usuario (Sherlock) vía tarea asincrónica al hacer la importación masiva. (interpretation) **Sin cerrar cuál de las dos.**

4. **Medio de envío = mail.** A Isis con copia a Nicolás López; ellos lo distribuyen internamente. (Drive quedó descartado como canal primario.) (stakeholder-verbal, Isis, 2026-06-12)

5. **La vuelta (archivo de liquidaciones) llega el 4º día hábil del mes**, que es cuando se hace el pago de haberes (puede correr 1–2 días). Misma casilla, mismo medio (mail). Los campos del reporte de vuelta los define Quarks y La Mantovana los arma en Finegans. (stakeholder-verbal, Isis + Nico López, 2026-06-12)

6. **Conciliación = manual**, macheando cuota enviada vs. descontada por legajo. Los errores caen a un **panel/front en Watson** donde un backoffice de Perk los corrige a mano. (stakeholder-verbal, Seba, 2026-06-12)

7. **Tope legal de descuento: la cuota no puede superar el 30% del sueldo percibido.** (observation/industry-knowledge, Nico Ortiz, 2026-06-12) → Quarks necesita el **sueldo de cada empleado** para calcular el máximo prestable. Dato que entra junto con antigüedad/presentismo en la elegibilidad.

8. **Arrepentimiento (10 días) requiere que el cliente TENGA los fondos.** (decision) Arrepentirse = devolver el producto (el monto). Si no tiene fondos no puede arrepentirse. Operativamente: TED que retira los fondos del CBU del empleado de vuelta al CBU recaudador. Confirmado con Marcos. Es distinto de la cancelación anticipada. (stakeholder-verbal, Seba, 2026-06-12)

9. **Ajustes/correcciones → mes siguiente, en archivo separado con DOS conceptos** ("ajuste de préstamo" y "préstamo"), para que no se mezclen en el recibo y aparezcan como dos ítems en Finegans. (stakeholder-verbal, Nico López + Juan Pablo, 2026-06-12)
   - **Excepción crítica:** si fue **error de débito** (se le cobró a quien NO correspondía), NO se ajusta al mes siguiente — la corrección debe ser **inmediata del lado de Perk** (rollback/TED), porque se le tocó el sueldo a alguien que no correspondía. (stakeholder-verbal, Nico Ortiz, 2026-06-12)

10. **Reclamos → los direcciona la billetera (PERC/mutual), no La Mantovana.** El cliente tomó el préstamo a través de PERC y autorizó a La Mantovana solo el débito (cuenta por cuenta y orden). Hace falta un circuito de derivación rápido. (stakeholder-verbal, Seba + Nico Ortiz, 2026-06-12)

---

## Fuera del scope de Quarks (aclarado por Seba, reafirmado por el grupo)

- **Elegibilidad / segmentación de quién recibe préstamo.** Métricas iniciales: **antigüedad + presentismo**. Proceso **manual** en la primera etapa (matriz de riesgo manual, revisión cada ~15 días); automatización futura. El scope de Quarks es: input de datos → output que genera préstamos y calcula cuotas. (stakeholder-verbal, Seba + Juan Pablo + Nico Ortiz, 2026-06-12)
- **Prender/apagar tags** (habilitación de usuarios) se hace en **Watson**, no en el desarrollo de Quarks. Quarks solo maneja templates de crédito; el crédito y el usuario no se manipulan desde acá. (observation, Nico Paez, 2026-06-12) — Quarks sí necesita en su BO una forma de prender/apagar masivo de templates (desarrollo interno).
- **Consultas recurrentes a Finegans** (altas/bajas/embargos) para refrescar elegibles: manual por ahora, no automatizado. (stakeholder-verbal, Seba, 2026-06-12)

---

## Open questions que quedan (need PM/Seba judgment)

1. **Casuística border — cancelación entre el día 20 (ya reporté la cuota) y el pago de haberes.** ¿Cómo se manda la cancelación: columna/pestaña en el mismo archivo, segundo archivo, o update de la novedad en Finegans? **Seba se lo llevó para un refinamiento interno de Perk** (preguntas legales + técnicas + producto). Probablemente proceso manual (Excel/update en Finegans), no construible por Quarks por falta de acceso a APIs de Finegans → fuera de scope. (stakeholder-verbal, Seba, 2026-06-12)
2. **Legajo: ¿Quarks lo trae en la importación masiva o La Mantovana da acceso a la base?** Sin confirmar (Seba lo confirma).
3. **Ventana de toma de préstamo** (ej. habilitar hasta el día 10 para que los 10 días de arrepentimiento caigan en un mes sin descuento ejecutado). Operativo vía tags; a sumar en la experiencia de usuario. Sin cerrar.
4. **Campos exactos del reporte de vuelta** — Quarks los debe definir y pasar a La Mantovana.

---

## Contradicción / cambio a vigilar — NO resolver acá

**Los términos y condiciones podrían pasar de 5 documentos a 1 solo archivo unificado.** (observation, Seba, 2026-06-12: *"que antes eran cinco y desde legales nos están dejando de que sea un solo archivo con todos los términos y condiciones. Voy a consultar si sigue siendo uno, pero idealmente es uno."*)

- Esto **tensiona** la decisión [decisions/2026-05-20-sabana-no-persiste.md](../../decisions/2026-05-20-sabana-no-persiste.md), cuyo modelo era: sábana de render al usuario + **5 documentos individuales persistidos** para compliance.
- **No se resuelve en esta ingesta.** Seba dijo "voy a consultar". Es un cambio *propuesto por legales*, todavía no confirmado. Cuando se confirme, hay que revisar si el modelo de firma (TOTP → persistir N docs) cambia a 1 doc.
- La decisión original sigue válida como artefacto (esa definición fue correcta al 20/5); lo que puede cambiar es el *número de documentos persistidos*, no el principio de persistencia para compliance.

**Documentación legal en el primer envío:** Nico López pide que en el **primer descuento de cada empleado** viaje adjunto el legajo firmado (constancia de aceptación) + el **acuerdo marco** entre empresas. Seba aclara que el acuerdo marco "no viaja por crédito" (es macro, relación contractual aparte). Los T&C/contratos sí están referenciados en el desarrollo. (stakeholder-verbal, Nico López + Seba, 2026-06-12)

---

## Ruteo propuesto (durable — requiere OK del PM, propose-and-wait)

- **3 stakeholders nuevos:** `isis-rondon` (La Mantovana, liquidación/CSC), `nicolas-lopez` (La Mantovana, Gerente RRHH), `nicolas-ortiz` (PERC, gestión préstamos/mutual) + filas en `stakeholders/INDEX.md` + entrada en maintenance log (cambio estructural).
- **`knowledge/product/features/flujo-credito.md`:** resolver/actualizar open questions con las definiciones 1–10; agregar dependencia "archivo importador de Finegans (recibido 12/6)"; agregar el tope 30% como regla; nota de scope (elegibilidad fuera de Quarks).
- **Decisión nueva candidata:** "Reporte de novedades = solo cuota del mes" (def. #1) y "Arrepentimiento requiere fondos" (def. #8) — ambas tienen confirmación de Marcos / acuerdo multilateral.
- **Tensión a registrar (no resolver):** unificación T&C 5→1 vs. decisión sábana/5 docs.
