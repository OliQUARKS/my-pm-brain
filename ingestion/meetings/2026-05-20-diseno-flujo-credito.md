# Ingestion — Diseño Flujo Crédito y Ajustes de Saldo

- **Source:** [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md)
- **Date:** 2026-05-20
- **Shape:** meeting
- **Participants:** Olivier (PM), Nati Fasanello (UX/UI, Quarks), Lucía Guyet (UX/UI, Quarks), Federico Fernandez (COO, Quarks), Johan Zambrano (Dev Frontend, PERC), Sebastián Cárdenas (PO, PERC). Marcos Copello — no asistió.

---

## Observations

### Scope decision — todos los flujos de cancelación son manuales
Arrepentimiento, cancelación anticipada y precancelación (pendiente de desembolso) resuelven igual: el usuario envía un mail pre-completado por la app. No hay firma digital ni flujo end-to-end digital para cancelaciones. Decisión acordada explícitamente en la reunión por Seba + Federico + PM. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### TOTP — terminología confirmada
Johan corrigió "OTP" → "TOTP" en el flujo para mantener consistencia con los demás flujos. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Desembolso a cuenta sueldo — confirmado legalmente
Seba: "Sí, sí, legalmente es así." Solo la cuenta sueldo recibe el préstamo, sin alternativas. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Success screen: sin "total a pagar"
En la pantalla de confirmación/éxito se muestra cuotas + cuota mensual + CFT. "Total a pagar" explícitamente eliminado. Federico: "Yo no le pondría el total a pagar. Haría como si el tipo acá compró un producto, tres cuotas de ochenta, listo." (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Onboarding carousel confirmado
Opción 1 elegida: carousel de 3 slides, sin auto-timer, avance por swipe o botón "continuar". Fondo blanco. Federico + PM confirmaron. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### La Mantovana desbloqueada — Johan encontró los templates
Johan encontró los templates Excel (importación + exportación) con un contacto técnico de La Mantovana. Reunión con "Isis" (contacto técnico de La Mantovana) agendada para 2026-05-21. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Tab bar redesign pendiente
El tab bar actual tiene 3 ítems (QR, perfil, home). Incorporar préstamos requiere rediseño de navegación. No resuelto en la reunión. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Animaciones — Lottie
Johan sugirió usar Lottie para animaciones del banner. El equipo de UX (Nati/Lucía) arma el spec de animación para pasarle a Johan. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Banner/mascota (Franky) — decisión diferida a Marcos
Tres variantes de Franky presentadas. Nati envía screenshot A/B/C a Marcos para que elija. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Open ask — template de mail de cancelación para Johan
Johan pidió que se le pase el formato/template del mail de cancelación para que el front pueda pre-completarlo. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Arrepentimiento — días corridos vs hábiles, pendiente verificar
En la reunión se mencionó "diez días corridos" pero nadie confirmó con certeza. Requiere verificación con Seba. (assumption, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))

### Cuota mensual — dato más importante a destacar
Acuerdo en la reunión: la cuota mensual es el dato que más le importa al usuario ("cuánto me sacan del sueldo por mes"). Resaltar sobre el monto total. Federico + PM coincidieron. (observation, [source/meetings/2026-05-20-diseno-flujo-credito.md](../../source/meetings/2026-05-20-diseno-flujo-credito.md))
