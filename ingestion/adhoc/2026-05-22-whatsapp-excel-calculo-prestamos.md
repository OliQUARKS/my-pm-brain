# Ingestion: WhatsApp comentarios Excel calculo prestamos — 2026-05-22

- Source: [source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md](../../source/adhoc/2026-05-22-whatsapp-excel-calculo-prestamos.md)
- Participantes: Olivier Luce, Sebastián Cárdenas, Federico Fernández
- Hora: 16:04–16:22
- Feature: flujo-credito

---

## Observations

1. **(decision) Seguro de vida capitalizado al inicio.** Seba confirma: "está sumado todo al principio en la primer pestaña suma al capital." La columna G de la tabla de amortización está vacía porque el seguro ya está incluido en el monto prestado como `Capital × Seguro%`. No es un cargo mensual. (stakeholder-verbal, Seba, 2026-05-22)

2. **(decision) Mora = costo en el capital inicial.** Seba confirma: "la mora se calcula como un costo en el capital inicial." Es un componente del monto prestado, no una penalidad por cuota atrasada. Fede cuestionó si tenía sentido ("pero si no hay mora técnicamente") — Seba confirmó que es intencional. (stakeholder-verbal, Seba, 2026-05-22)

3. **(observation) IVA en cancelación anticipada — pendiente hasta el lunes 2026-05-26.** Seba reconoce el punto ("ahí veo lo de la cancelacion") pero difiere el detalle. Confirma que "las variables son las mismas" — el flag de IVA configurable del Excel aplica. (stakeholder-verbal, Seba, 2026-05-22)

4. **(open question) Cancelación anticipada: ¿precalculada en template o calculada on-demand?** Seba pregunta. Olivier devuelve la pregunta. Sin respuesta. Tema del último sprint. (stakeholder-verbal, Seba + Olivier, 2026-05-22)

---

## Routing

- `knowledge/product/features/flujo-credito.md` — cerradas OQ seguro de vida + monto prestado; actualizado §Cuota methodology con fórmula y confirmaciones; nueva OQ cancelación anticipada timing
- `stakeholders/sebastian.md` — touchpoint 16:10
- `stakeholders/federico.md` — touchpoint 16:21
