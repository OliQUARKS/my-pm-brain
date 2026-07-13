# Decision: El reporte de novedades a La Mantovana lleva solo la cuota del mes, no el préstamo total

## Status
decided

## Date
2026-06-12

## Context
En el ida y vuelta con La Mantovana, PERC debe informar mensualmente qué descontar por nómina. La pregunta era si enviar el **préstamo total** (y que Finegans lo divida en cuotas) o **solo la cuota del mes en curso**. La decisión afecta la generación del archivo de novedades, la conciliación y el manejo de cancelaciones/pronto-pago (Sprint 4).

## Options considered
1. Enviar el monto total del préstamo y que Finegans lo divida por la cantidad de cuotas.
2. Enviar únicamente la cuota a descontar de ese mes (agnóstico del resto del préstamo).
3. Crear el "concepto de préstamo" dentro de Finegans con el total y la cantidad de cuotas.

## Decision
Opción 2 — el archivo de novedades lleva **solo la cuota del mes en curso**, mes a mes. El control del saldo y del préstamo total queda del lado de PERC/mutual.

## Why
Si Finegans divide el total, las variaciones de redondeo pueden no conciliar perfectamente; además, pronto-pago y cancelación anticipada obligarían a implementar un "método pronto pago" para reescribir el plan en Finegans. Enviar solo la cuota del mes mantiene la cuenta corriente de La Mantovana sin desfase y deja toda la dinámica de cancelación/precancelación del lado de PERC, donde ya vive.

## Evidence
- Seba advirtió que enviar el total arriesga la conciliación por redondeo y que pronto-pago/cancelación obligarían a un método extra en Finegans  `(stakeholder-verbal, Sebastián, 2026-06-12)`
- Isis y Nico López confirmaron que operativamente liquidan una "liquidación de préstamo" + un "descuento mensual" separados; si liquidaran por el importe total nunca coincidiría con el neto por los intereses  [../source/meetings/2026-06-12-proceso-prestamos-mantovana.md](../source/meetings/2026-06-12-proceso-prestamos-mantovana.md)
- Nico Ortiz: el control del préstamo total lo lleva PERC; enviar solo la novedad mes a mes evita comprometer contablemente a La Mantovana  `(stakeholder-verbal, Nico Ortiz, 2026-06-12)`

## Explicitly NOT doing
- No enviar el monto total del préstamo ni delegar la división de cuotas a Finegans  `(stakeholder-verbal, Sebastián + Isis, 2026-06-12)`

## What would reverse this
La Mantovana/Finegans cambia su operatoria y exige el total del préstamo por adelantado, o el volumen de ajustes manuales mensuales (correcciones, pronto-pago) se vuelve inmanejable y conviene que Finegans administre el plan completo.

## Remaining ambiguities
- Casuística border: cancelación informada después del día 20 pero antes del pago de haberes — ¿cómo se comunica la baja de esa cuota ya reportada? Seba se lo llevó a un refinamiento interno de Perk (legal + técnico + producto).
- ¿Quarks trae el número de legajo en la importación masiva o La Mantovana da acceso a la base de legajos? Sin cerrar.
