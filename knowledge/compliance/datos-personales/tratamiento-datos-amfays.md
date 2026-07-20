# Tratamiento de datos — AMFAYS como tercero (Flujo Crédito PERC)

## Meta
- Owner: Olivier Luce (PM, Quarks Alchemist)
- Status: borrador / frente abierto — no discutido a fondo con AMFAYS ni con compliance PERC
- Last updated: 2026-07-20
- Aplica a: [knowledge/product/features/flujo-credito.md](../../product/features/flujo-credito.md) § Documento / campos AMFAYS
- Triggered by: daily PERC 2026-07-20 — Pablo Folgar levanta la protección de datos del documento AMFAYS ([ingestion/meetings/2026-07-20-daily-perc.md](../../../ingestion/meetings/2026-07-20-daily-perc.md))

## Por qué existe este archivo

El diseño de consentimiento/cesión existente ([diseno-consentimiento-mantovana.md](./diseno-consentimiento-mantovana.md)) cubre el flujo **PERC → Mantovana** (descuento por nómina). **AMFAYS** — la mutual que provee el instrumento ([knowledge/org/amfays.md](../../org/amfays.md)) — es un **tercero distinto** que entra en el tratamiento de datos con el documento de la ayuda económica, y **no está cubierto** por ese diseño. Este archivo abre ese frente.

## 1. Hechos (daily 2026-07-20)

- **(observation)** El documento AMFAYS pide datos que hoy PERC no captura (propiedad de inmueble/auto, familiares, CBU de la empresa, etc.) + KYC biométrico + firma. Se relevó campo-por-campo el 2026-07-17 ([ingesta](../../../ingestion/meetings/2026-07-17-call-amfays-documento-prestamo.md)).
- **(observation, arquitectura)** **Quarks NO guarda los datos del documento — solo guarda la referencia** al documento, que está **almacenado del lado de AMFAYS/PERC**. — Marcos + Nico Paez, [source](../../../source/meetings/2026-07-20-daily-perc.md).
- **(observation)** El request que arma el documento **sí lleva la cuenta de la persona**; va por **HTTPS** (segurizado en tránsito). El foco de riesgo es que **datos sensibles (DNI/importe/cuota) NO queden persistidos en logs**.
- **(interpretation, Marcos)** Alternativa de diseño para minimizar exposición: que **el documento lo arme AMFAYS/PERC**, de modo que "no viaje toda esa data" por Quarks.

## 2. Riesgo / caracterización (a validar — NO opinión legal vinculante)

- **(assumption, PM)** Al sumar AMFAYS, hay una **posible cesión/encargo adicional** de datos personales (LPDP Ley 25.326, Art. 11 cesión / Art. 25 encargo) hacia la mutual. Igual que con Mantovana, conviene la salvaguarda doble: **contrato de encargo + consentimiento explícito** del titular en el flujo del préstamo. Requiere confirmación de **Patricio (compliance PERC) + legales PERC + legales AMFAYS**.
- **(assumption, PM)** Datos **sensibles** en juego (PEP/sujeto obligado, biometría del onboarding) → el tratamiento sin encriptación adecuada es infracción "muy grave" bajo [RESOL-2024-126-APN-AAIP](./INDEX.md). La biometría/prueba de vida ya se captura en el **onboarding de la billetera**; AMFAYS **auditará** ese proceso de validación de identidad (no impone el suyo).

## 3. Acción de gobernanza (recomendación de Pablo Folgar, 2026-07-20)

- **(decision operativa, en principio)** Dejar un **registro documentado y fechado** de que Quarks **planteó la protección de datos el 2026-07-20** y de las medidas que propuso (no persistir datos sensibles en logs; solo guardar la referencia; sugerir que el documento lo arme AMFAYS/PERC). Objetivo: que la responsabilidad del tratamiento quede del lado de PERC/AMFAYS y Quarks pueda **acreditar diligencia** a futuro. — (stakeholder-verbal, Pablo Folgar, 2026-07-20)

## 4. Pendientes

- [ ] **Check técnico:** verificar que no queden datos sensibles (DNI/importe/cuota) en logs; agregar un check al final del flujo. `[Q]`
- [ ] **Caracterización jurídica AMFAYS** (cesión vs. encargo) + consentimiento/contrato. `[P compliance + AMFAYS + Q]`
- [ ] **Decidir dónde se arma el documento** (Quarks con HTML pelado + variables, o AMFAYS/PERC) — impacta qué data viaja por Quarks. Ver [flujo-credito § Documento / campos AMFAYS](../../product/features/flujo-credito.md). `[Q + AMFAYS]`
- [ ] **Registro CYA fechado** — dejar por escrito lo planteado el 20/7 (mail/documento). `[Q → Olivier]`
