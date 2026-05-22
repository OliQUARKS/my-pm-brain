# Ingestion — Ajustes Cards de Saldo PERC

- **Date:** 2026-05-06
- **Participants:** Olivier, Natalia Fasanello, Lucía Guyet, Sebastián Cárdenas, Marcos Copello
- **Source:** [../../source/meetings/2026-05-06-ajustes-cards-de-saldo.md](../../source/meetings/2026-05-06-ajustes-cards-de-saldo.md)
- **Feature:** Cards de Saldo (balance display — distinto de flujo crédito)
- **Context:** Pre-kickoff Quarks–PERC (kickoff oficial = 2026-05-20). UX review de diseño de la pantalla de saldo.

---

## Decisión de diseño — Cards de Saldo: opción 1 seleccionada

**(decision, pre-kickoff)** Las tres opciones presentadas (card-scroll, flotante sin card, tab) se votaron. Olivier, Marcos y Seba eligieron opción 1: cards con swipe horizontal + puntitos de indicación + toggle para ver saldo total en pesos o dólares. La opción 2 (flotante) fue descartada por Lu y Nati (flecha confusa, mucha flecha). La opción 3 (tab) quedó como segunda opción de Marcos.

Ajustes acordados para opción 1:
- Chip/badge en el título de la card (no texto plano) — cortar "remunerada" si es largo
- Botones de enviar/recibir con border-radius reducido (menos redondos, tipo micrófono Meet)
- Toggle del total en pesos/dólares: saldo total consolidado en una moneda (no dos totales separados)
- Color de card por moneda: leve tinte (Seba: "va a quedar medio cocolich" — pendiente validar en producción)

(stakeholder-verbal, Marcos Copello + Olivier Luce, 2026-05-06) — [source/meetings/2026-05-06-ajustes-cards-de-saldo.md](../../source/meetings/2026-05-06-ajustes-cards-de-saldo.md)

## Cuenta remunerada — cutoff 7pm

**(observation)** Marcos confirma: la cuenta remunerada paga intereses sobre el saldo que esté al cierre del día. El cutoff es las 7pm: si la plata entra antes de las 7pm, se remunera ese día; si entra después, recién al día siguiente. Un retiro solicitado después de las 7pm sale a las 7am del día siguiente.

Relevante para flujo crédito: si el desembolso llega a la cuenta sueldo/remunerada después de las 7pm, el usuario no gana intereses ese día.

(stakeholder-verbal, Marcos Copello, 2026-05-06) — [source/meetings/2026-05-06-ajustes-cards-de-saldo.md](../../source/meetings/2026-05-06-ajustes-cards-de-saldo.md)

## Documentos con variables — evidencia pre-kickoff

**(observation, pre-kickoff)** Seba menciona que recibirá "los cinco documentos en un solo documento" con variables marcadas para autocompletar, y que Nico lo convertirá a HTML + rellenará variables + imprimirá como PDF. Esto confirma que la intención original (antes del kickoff formal) era documentos dinámicos con variables. Relevante para la open question de documentos dinámicos vs. estáticos en flujo crédito.

(stakeholder-verbal, Sebastián Cárdenas, 2026-05-06) — [source/meetings/2026-05-06-ajustes-cards-de-saldo.md](../../source/meetings/2026-05-06-ajustes-cards-de-saldo.md)

## Acciones en cards — todas las cuentas tienen enviar/recibir

**(observation)** Marcos confirma que todas las cuentas (pesos, dólares, remunerada, recaudadora) pueden enviar y recibir. Los botones de acción se mantienen fijos debajo del carrusel de cards — no cambian por card porque las acciones son iguales para todas. Cuando el usuario está en una card específica, "enviar" presupone esa cuenta como origen.

(stakeholder-verbal, Marcos Copello, 2026-05-06) — [source/meetings/2026-05-06-ajustes-cards-de-saldo.md](../../source/meetings/2026-05-06-ajustes-cards-de-saldo.md)

## Routing

- Sin promoción durable (feature diferente — cards de saldo, no flujo crédito; meeting aislada pre-kickoff)
- Nota para flujo crédito: remunerada 7pm cutoff es contexto relevante para el desembolso (no bloquea, pero es una expectativa del usuario a documentar)
