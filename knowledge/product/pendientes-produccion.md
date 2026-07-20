# Pendientes a producción — Flujo Crédito

> Checklist vivo del camino a producción del MVP. Derivado de [features/flujo-credito.md](./features/flujo-credito.md), las ingestas y las decisiones/tensiones abiertas. Detalle completo vive en la feature file y en cada decisión; esto es el tablero para tildar.
>
> **Última actualización:** 2026-07-20 (Olivier marcó 20 ítems como resueltos)
> **Marco de "terminado":** App (CTA + 3 opciones + firma unificada + desembolso) + Backoffice Watson + ciclo de cobro/liquidación Mantovana. Sin scope adicional contratado ([roadmap.md](./roadmap.md)).
> **Dueños:** `[Q]` Quarks · `[P]` PERC · `[M]` La Mantovana · `[Q+P]` ambos.
> **Encuadre (20/7):** los pendientes son mayormente **bugs/estabilización**, no features nuevas.

## 🔴 Camino crítico a la entrega (es una secuencia)
- [ ] **1. Cash out / desembolso real** `[Q]` — hoy la lógica corre pero no fondea. En curso (Marcos, ventana 9–18); agrega ~4 lambdas. **Primer eslabón: su PR debe pasar antes del refactor de lambdas.** 2ª cuenta habilitada (17/7) para probar.
- [ ] **2. Consolidación/refactor de lambdas (~65 → ~20)** `[Q + Gonzalo]` — no entra hasta pasar el PR de (1). Reescribe paths de front/Insomnia → **obliga a rehacer el UAT**. Causa confirmada (Nico): CI ~45 min + costo AWS serverless.
- [ ] **3. Entorno dev/stage estable → deploy del front a stage** `[P infra (Gonzalo) + Q]` — hoy al *estado ~demo* (Gonza subió; queda 1 PR chico); el refactor lo vuelve a mover. Falta: Marcos sube el front + Gonza deploya web apuntando a stage (recién ahí se testea sobre web, no solo Insomnia).
- [x] **4. Endpoints de "fondos" del lado PERC** `[P]` — ✅ **resuelto (Olivier, 2026-07-20).** La consulta de saldo de la recaudadora/CVU quedó cubierta.
- [ ] **5. UAT formal punta-a-punta (~130 escenarios)** `[Q+P]` — en dev estable, sin más cambios. **Es la entrega.** Enfoque nuevo: **UAT asistido por IA** (Pablo Folgar) desde el Excel de casos + Insomnia, verificando estado en DB; arranque acotado (una tabla por vez).
- [ ] **6. ⚠️ Biométrico/KYC dentro del flujo de préstamo** `[Q + AMFAYS]` — **comodín de plazo.** Caso de máxima = re-pedir biométrico en la solicitud + documentar + bajar al PDF → **modifica el front** + drop-off. Marcos cree que con TOTP alcanza. **Duda a evacuar con AMFAYS** — si es el caso de máxima, entra al camino crítico.

## 🟠 Desarrollo pendiente de Quarks
- [x] **7. Bug: préstamo pagado no libera al usuario** `[Q]` — ✅ **resuelto (Olivier, 2026-07-20).** El crédito `paid` ahora libera la `application` para pedir un 2º préstamo.
- [ ] **8. Implementar el threshold/delta de tolerancia** `[Q]` — en capa de negocio (env var). Dirección + valor candidato (~3 decimales) definidos; falta el valor de negocio de PERC (ver #18). Va como 3ª etapa (entre el PR de cash out y el refactor). Decisión: [2026-07-16-threshold-tolerancia-pago-cuota](../../decisions/2026-07-16-threshold-tolerancia-pago-cuota.md).
- [ ] **9. Pulir documentos** `[Q]` — storage-key + zip de hasta 25 reportes + descarga.
- [x] **10. Gaps de front (aprobados-con-comentario)** `[Q]` — ✅ **resuelto (Olivier, 2026-07-20)** (10a desglose de cuota user-side · 10b signo `deviation` · 10c pantalla resumen de importación · 10d strings/copiar en BO).
- [x] **11. Historia: cancelar la SOLICITUD antes del desembolso** `[Q]` — ✅ **resuelto (Olivier, 2026-07-20).** Desistimiento manual en ventana 24h cubierto.
- [x] **12. Crons** (envío + 2 de corte) `[Q]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [x] **13. Deuda de capital desagregada por cuota** `[Q]` — ✅ **resuelto (Olivier, 2026-07-20).** Habilita el cálculo de pago anticipado.
- [ ] **14. Nº SAEM/SAIN — generación + unicidad** `[Q]` — correlativo de 14 dígitos autogenerado por PERC. Seba duda del "random" (posible colisión) → debe ser **correlativo único**, no random. Definir generación + persistencia.
- [ ] **15. Importador de datos AMFAYS faltantes (RRHH → PERC)** `[Q construye / P alimenta]` — Quarks arma el importador; PERC/RRHH sube legajo, domicilio laboral, sueldo neto, antecedentes laborales. **Sueldo neto ⇒ actualización mensual de TODA la base** (no incremental) — costo operativo nuevo de PERC.

## 🟡 Definiciones / inputs pendientes de PERC
- [ ] **16. Número de legajo** `[P]` — ubicación conocida (está en el endpoint = nº de usuario). Falta OK formal de Fefe + el dato efectivo.
- [ ] **17. Set de campos obligatorios AMFAYS (compliance)** `[Q + AMFAYS]` — cerrar el ida-y-vuelta: PERC devuelve qué no tiene; AMFAYS valida con legales qué sacar. Pendiente: lugar de nacimiento, sensibles, alcance sujeto obligado. *(Ya corregido: filas 52-53 no obligatorias; motivo = "consumo" hardcode.)*
- [ ] **18. Valor del threshold/delta** `[P]` — decisión de negocio (habilita #8).
- [ ] **19. Campos del reporte de vuelta** (liquidaciones Mantovana) `[Q define / P confirma]`.
- [ ] **20. CBU larga del banco pagador** `[P riesgo + Q]` — ¿se captura además de la CVU corta? (criterio de riesgo) + formulario de autorización anexo.
- [ ] **21. Sueldo / antigüedad / presentismo por empleado** `[P]` — habilita tope 30% + elegibles. Tags on/off en Watson fuera de scope Q.
- [ ] **22. Integración Watson (Backoffice)** `[P]` — definición pendiente.
- [x] **23. Base del costo de cancelación anticipada (3%)** `[P]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [x] **24. IVA en cancelaciones** `[P]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [x] **25. ¿Mantovana regenera reportes por rango de fechas?** `[P/M]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [x] **26. Compliance BIND** `[P]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [x] **27. Empleados PJ** `[P]` — ✅ **resuelto (Olivier, 2026-07-20).** `person_type` J/F alcanza para docs/BO.
- [x] **28. Ida-y-vuelta completa Mantovana** `[Q+P]` — ✅ **resuelto (Olivier, 2026-07-20).** Casos OK/sobra/falta/ID-mal cubiertos.

## 🔵 Seguridad / técnico
- [ ] **29. TOTP security gap** `[Q]` — token válido puede llamar el endpoint de transferencia sin TOTP; revisión Nico/Joy.
- [x] **30. Restricciones de archivo HTML** `[Q → cyber]` — ✅ **resuelto (Olivier, 2026-07-20).** Tamaño/XSS/sanitización cubiertos.
- [x] **31. Pipeline CI/CD acordado** `[Q + Gonzalo]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [x] **32. JWT decodificado en evento Lambda HTTP** + cuenta sueldo en wallets `[Q]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [ ] **33. Protección de datos del documento AMFAYS** `[Q + P/AMFAYS]` — Quarks solo guarda la **referencia** (los datos viven del lado AMFAYS/PERC). Verificar que no queden datos sensibles (DNI/importe/cuota) en logs (check al final); dejar **registro fechado** (CYA). Ver [compliance/datos-personales/tratamiento-datos-amfays.md](../compliance/datos-personales/tratamiento-datos-amfays.md).

## ⚪ Decisiones / tensiones estratégicas abiertas
- [x] **34. Circuito de cancelaciones (scope creep)** `[Q→P]` — ✅ **resuelto (Olivier, 2026-07-20): BO con trazabilidad.** Registro-only, sin circuito de reporte a Mantovana → **no hay scope creep**. Ver [strategy.md § Tensions](../strategy.md).
- [x] **35. T&C 5 docs → 1** `[P]` — ✅ **resuelto (Olivier, 2026-07-20): es 1 solo documento.** Supersede la decisión de sábana → [2026-07-20-documento-unico-firma](../../decisions/2026-07-20-documento-unico-firma.md).
- [x] **36. Cancelación anticipada precalculada vs. on-demand** `[Q]` — ✅ **resuelto (Olivier, 2026-07-20): on-demand — Quarks calcula lo que el usuario debe pagar** (no se precalcula en el template).

## ◽ Watch / fuera de alcance (no gatean go-live)
- [ ] **37. Deploy del front Angular sandbox en infra** para negocio PERC `[Q+P]` — sin objeción; Nico Paez ↔ Gonzalo.
- [x] **38. Tab bar redesign** de la app (incorporar préstamos a la navegación) `[Q]` — ✅ **resuelto (Olivier, 2026-07-20).**
- [x] **39. Watch — features de cheques (Marcos Copello)** `[P]` — ✅ **cerrado (Olivier, 2026-07-20).** No avanza / fuera del MVP.

---

## ✅ Cerrado previamente (contexto)
- [x] **C1. Plazo → +1 sprint** decidido; arranque del refactor de lambdas antes del UAT. [2026-07-20-entrega-perc-mas-un-sprint](../../decisions/2026-07-20-entrega-perc-mas-un-sprint.md). *Residual: OK fino de fecha/alcance de Seba.*
- [x] **C2. ¿Dónde se cargan los ~20 campos AMFAYS?** → por origen: existentes vía accounts/Sherlock; faltantes mockeados/cableados + proveeduría real diferida a PERC; documento **desacoplado del MVP**. [2026-07-20-captura-datos-amfays](../../decisions/2026-07-20-captura-datos-amfays.md). *(Ejecución viva en #14, #15, #16, #17.)*
- [x] **C3. Causa de la re-arquitectura de lambdas** → confirmada por Nico (CI ~45 min + costo AWS serverless). *(Ejecución viva en #2.)*
- [x] **C4. Threshold — dirección y valor candidato** → ~3 decimales configurable en capa de negocio; rechazado el clic "dar por pagada". *(Implementación en #8; valor de negocio en #18.)*

---
**Sigue vivo (19 ítems):** camino crítico **#1 #2 #3 #5** en cadena + **#6 (biométrico) comodín**; desarrollo Q **#8 #9 #14 #15**; definiciones PERC **#16 #17 #18 #19 #20 #21 #22**; seguridad **#29 #33**; watch **#37**.
**Lo que realmente traba la entrega:** #1→#3→#5 (cash out → lambdas → entorno → UAT) + **#6 (biométrico)** según lo que responda AMFAYS.
