# Nota de respaldo — Prototipo Frigorífico Merlo

**Artifact (link compartible):** https://claude.ai/code/artifact/4bc2ca1a-a1c0-4250-a0a4-51aa3e662dda
**Fuente versionada:** [`2026-07-frigorifico-merlo-prototipo.html`](./2026-07-frigorifico-merlo-prototipo.html)
**Deriva de:** [build-context](./2026-07-frigorifico-merlo-build-context.md) · [doc de flujos del cliente](../source/adhoc/2026-07-frigorifico-merlo-doc-flujos-ventas.md)
**Corre en:** etapa 4 del [ciclo](./_ciclo-preventa.md), en paralelo a `/propuestador`.

## Qué se prototipó (camino feliz del MVP)

El flujo de **ventas no facturadas** (order-to-cash de la despostada), que es el foco del build-context, en 4 pantallas navegables:

1. **Pedidos del día** — pedidos entrados (WhatsApp/presencial) ya interpretados en una lista digital, con línea A/B y **estado de cuenta corriente inline** para priorizar (al día / debe / Contado). Incluye "ver mensaje original" → interpretado.
2. **Programa de despostada** — se arma solo desde los pedidos confirmados, por corte y línea; lo que baja a cámara.
3. **Romaneo y venta** — el corazón del valor: al "traer pesos de las etiquetas", los kg llegan desde la balanza, la venta se arma sola (depósito por línea, precio de lista, importe calculado) — **sin re-tipeo manual**.
4. **Cierre y control** — cuadre automático contra el **Diario de Cajas**; dos alertas de discrepancia detectadas al instante (peso 16,8 vs 18,7 kg; caja premium sin marca "A" en depósito equivocado), con acción de corrección.

## Formato y branding

- **Backoffice de escritorio** (no mobile): el dolor y los usuarios están en administración (Nacho / Matías / Andrés). Responsive + theme-aware (claro/oscuro).
- **Branding nivel 2 (sin manual):** paleta derivada del mundo del cliente — bordó/carne como marca, y las dos líneas reales como acentos (**Criadores Pampeanos** = ámbar/premium, **Merlo** = gris azulado/estándar). Tipografía: serif de sistema para el wordmark, sans de sistema para la UI (CSP bloquea webfonts).

## Simulado / ilustrativo (honestidad de factibilidad)

- **Ingreso por WhatsApp:** se muestra la lista ya interpretada y el "mensaje original", pero **la integración viva con WhatsApp no está resuelta** (vía/costos de Meta) — es el gran abierto técnico. En el proto está como ejemplo, no como integración real.
- **Datos de ejemplo evidentes:** clientes, cortes, kg y precios son inventados (chip "Prototipo · datos de ejemplo"). Precios por kg son ilustrativos.
- El resto del flujo (romaneo→venta, depósitos por línea, cuadre por Diario de Cajas) se apoya en el proceso real documentado y en el **precedente interno**: en preventas la Palm ya asocia corte↔cliente automáticamente.

## Gaps que el cliente debe confirmar

- **Assets de marca oficiales:** logo (SVG/PNG) y tipografías — el wordmark actual es aproximado.
- **Vía de integración de WhatsApp** (define si el paso 1 se puede automatizar como se muestra).
- **Alcance de la API a medida** sobre MySQL (con el programador) para leer/escribir ventas, stock y cuenta corriente.
- Confirmar lista de cortes/depósitos y nombres exactos si se quiere fidelidad total.

## Regla de oro

Cara al cliente: sin montos del deal, sin stakeholders internos, sin competidores, sin activos internos. Los controles de negocio (stock, crédito, línea) se manifiestan en la UX (badges, estado de cuenta, alertas), no como checklist interno.
