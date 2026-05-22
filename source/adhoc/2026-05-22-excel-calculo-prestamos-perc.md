# Excel: CALCULO DE PRESTAMOS PERC — Seba, 2026-05-22

## Metadata
- Recibido: 2026-05-22 15:44 (WhatsApp, Sebastián Cárdenas → Olivier)
- Archivo original: CALCULO DE PRESTAMOS PERC 22-05-2026.xlsx
- Sheets: Premisas | Tabla Amortización | Cancelación Anticipada | Amort. Cancelación | Resumen Ejecutivo
- Propósito: Definir la metodología de cálculo de cuotas y cancelación anticipada del flujo crédito PERC.

---

## Sheet 1 — Premisas

**Título:** MODELO DE PRÉSTAMO BANCARIO – TABLA DE AMORTIZACIÓN FRANCESA
**Convención:** Sistema Francés (cuota fija) | Moneda: ARS

### 1. Parámetros principales del préstamo (INPUT)

| Parámetro | Valor | Notas |
|---|---|---|
| Monto solicitado y a depositar (capital) | 1,000,000 | Monto neto que recibe el cliente |
| Monto prestado | 1,075,000 | Base de la tabla de amortización |
| TNA (Tasa Nominal Anual) | 0.89 | Base 30/365; decimal (0.89 = 89%) |
| Cantidad de cuotas (meses) | 24 | Sistema francés – cuotas mensuales iguales |
| Día de pago | 10 | Día del mes en que vence cada cuota |
| Impuesto de Sellos (%) | 0.012 | 1.0%–1.2% sobre capital; configurable |
| Mora | 0.03 | — |
| Seguro % | 0.03 | — |
| Gasto administrativo mensual | 500 | Comisión fija mensual; configurable |
| IVA sobre intereses (%) | 0.21 | 21% s/ intereses |
| Penalidad cancel. anticipada (%) | 0.03 | % s/ capital restante + intereses no devengados |
| Gastos de otorgamiento | 3,000 | Comisión única al inicio; configurable |

**Leyenda de colores:**
- Texto azul / fondo amarillo = INPUT configurable
- Fondo gris = fórmula derivada (no editar)
- Texto verde = vínculo entre hojas

### 2. Tasas y montos derivados (calculados automáticamente)

| Parámetro | Valor | Fórmula |
|---|---|---|
| Tasa sin IVA (mensual) | 0.07417 | TNA / 12 |
| Tasa mensual (TEM) con IVA | 0.08974 | (TNA/12) × (1 + IVA) |
| Tasa efectiva anual (TEA) | 1.35972 | (1 + TEM)^12 − 1 |
| Cuota pura (capital + interés) | 110,522.60 | PMT(TEM_conIVA, n, −Monto_prestado) |
| Impuesto de sellos ($) | 12,900 | Monto_prestado × 1.2% |
| Gastos de otorgamiento ($) | 3,000 | — |
| Total Crédito | 1,090,900 | Monto_prestado + Sellos + Otorgamiento |
| Total a pagar (sin cancelación) | 2,668,442.29 | Cuota_total × n + Sellos + Otorgamiento |
| Costo financiero total ($) | 1,593,442.29 | Total pagado − capital solicitado |
| CFT (aproximado c/ IVA, anual) | 1.0769 | TNA × (1 + IVA) — aprox. regulatoria |

---

## Sheet 2 — Tabla Amortización

**Título:** TABLA DE AMORTIZACIÓN – SISTEMA FRANCÉS

**Columnas:** N° Cuota | Fecha Vencimiento | Saldo Inicial | Interés Bruto | IVA s/Interés |
Amortización Capital | Seguro de Vida | Gasto Adm. | Cuota Total | Saldo Final |
Capital Acum. Pagado | Interés Acum. Pagado | Flujo Neto Banco

**Fórmulas por fila:**
- Interés Bruto = Saldo Inicial × (TNA/12)
- IVA s/Interés = Interés Bruto × 0.21
- Amortización Capital = Cuota pura − Interés Bruto − IVA s/Interés
- Seguro de Vida = Saldo Inicial × Seguro% — **columna presente pero = 0 en todas las cuotas de este ejemplo**
- Cuota Total = Interés Bruto + IVA s/Interés + Amortización Capital + Seguro de Vida + Gasto Adm.

**Primeras 8 cuotas (ejemplo: Capital_prestado = 1,075,000 | TNA = 89% | n = 24):**

| N° | Saldo Inicial | Interés Bruto | IVA s/Int. | Amortización | Seguro | Gasto Adm. | Cuota Total | Saldo Final |
|---|---|---|---|---|---|---|---|---|
| 1 | 1,075,000.00 | 79,729.17 | 16,743.13 | 14,050.30 | 0 | 500 | 111,022.60 | 1,060,949.70 |
| 2 | 1,060,949.70 | 78,687.10 | 16,524.29 | 15,311.20 | 0 | 500 | 111,022.60 | 1,045,638.50 |
| 3 | 1,045,638.50 | 77,551.52 | 16,285.82 | 16,685.25 | 0 | 500 | 111,022.60 | 1,028,953.24 |
| 4 | 1,028,953.24 | 76,314.03 | 16,025.95 | 18,182.62 | 0 | 500 | 111,022.60 | 1,010,770.62 |
| 5 | 1,010,770.62 | 74,965.49 | 15,742.75 | 19,814.36 | 0 | 500 | 111,022.60 | 990,956.27 |
| 6 | 990,956.27 | 73,495.92 | 15,434.14 | 21,592.53 | 0 | 500 | 111,022.60 | 969,363.74 |
| 7 | 969,363.74 | 71,894.48 | 15,097.84 | 23,530.28 | 0 | 500 | 111,022.60 | 945,833.46 |
| 8 | 945,833.46 | 70,149.32 | 14,731.36 | 25,641.92 | 0 | 500 | 111,022.60 | 920,191.54 |

**TOTALES (24 cuotas):**

| Componente | Total |
|---|---|
| Interés Bruto | 1,303,753.96 |
| IVA s/Interés | 273,788.33 |
| Amortización Capital | 1,075,000.00 |
| Seguro de Vida | **0** (parámetro 3% en Premisas, columna presente, pero vacía en este ejemplo) |
| Gasto Adm. | 12,000 (500 × 24) |
| Cuota Total acumulada | 2,664,542.29 |

---

## Sheet 3 — Cancelación Anticipada

**Título:** CANCELACIÓN ANTICIPADA – REGLAS CONFIGURABLES

### Parámetros de cancelación (configurables)

| Parámetro | Valor | Explicación |
|---|---|---|
| Cuota de cancelación (N°) | 12 | En qué cuota se cancela |
| % s/intereses futuros | 0.05 (5%) | Penalidad sobre intereses no devengados |
| Comisión cancelación (%) | 0.03 (3%) | % adicional sobre capital restante |
| ¿Aplica IVA a penalidad? | **1 (= Sí)** | Flag configurable: 1 = Sí, 0 = No |
| Tipo de préstamo | Personal | Personal / Hipotecario / Prendario |

### Cálculo detallado (ejemplo: cancelación en cuota 12 de 24)

| Parámetro | Valor | Fórmula |
|---|---|---|
| Capital restante | 792,452.94 | Saldo final cuota 12 |
| Cuotas restantes | 12 | 24 − 12 |
| Intereses futuros brutos | 441,172.07 | Suma intereses cuotas 13–24 |
| Penalidad por intereses futuros | 22,058.60 | Int. futuros × 5% |
| Comisión sobre capital restante | 23,773.59 | Capital restante × 3% |
| Subtotal antes de IVA | 838,285.13 | Capital + Penalidad + Comisión |
| IVA sobre penalidades | 9,624.76 | (Penalidad + Comisión) × 21% |
| **TOTAL A PAGAR PARA CANCELAR** | **847,909.89** | Incluye capital + penalidades + IVA |
| Ahorro vs. seguir pagando | 484,361.26 | Cuotas futuras − monto cancelación |

**Nota del Excel:** Todos los % de penalidad son configurables en B5:B8. El modelo recalcula automáticamente.

### Referencia: reglas por tipo de préstamo

| Tipo | % Int. Futuros | Comisión | Observación |
|---|---|---|---|
| Personal | 3%–10% | 2%–5% | Definida contractualmente |
| Hipotecario | 0%–3% | 0%–1% | Regulado BCRA |
| Prendario | 5% | 3% | Estándar de mercado |
| Tarjeta/Créd. | N/A | 0% | Sin penalidad por ley |

---

## Sheet 5 — Resumen Ejecutivo

| Parámetro | Valor |
|---|---|
| **Datos del préstamo** | |
| Monto solicitado (base amortización) | 1,075,000 |
| Impuesto de sellos | 12,900 |
| Gastos de otorgamiento | 3,000 |
| Total desembolso inicial | 1,090,900 |
| **Condiciones** | |
| TNA | 0.89 |
| TEM | 0.08974 |
| TEA | 1.35972 |
| CFT aprox. c/ IVA | 1.0769 |
| N° de cuotas | 24 |
| Cuota pura mensual | 110,522.60 |
| **Costo total** | |
| Total a pagar | 2,668,442.29 |
| Costo financiero total | 1,593,442.29 |
| **Cancelación anticipada (cuota 12)** | |
| Capital restante | 792,452.94 |
| Total a pagar para cancelar | 847,909.89 |
| Ahorro estimado | 484,361.26 |
