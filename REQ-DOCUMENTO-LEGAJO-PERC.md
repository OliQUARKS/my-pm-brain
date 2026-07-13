# Requerimiento — Documento / Legajo de Préstamo (Flujo Crédito PERC)

> **Estado:** borrador para revisión de Olivier antes de enviar a Seba (PERC).
> **Origen:** call del 2026-07-08 (Olivier / Marcos Perez / Sebastián Cárdenas).
> **Documento base:** `Legajo Prestamo v1 (2).docx` — legajo de préstamo de **AMFAYS** (Asociación Mutual de las Fuerzas Armadas y de Seguridad), 9 formularios cuya plantilla está aprobada por una entidad regulada por la **Superintendencia de Seguros**.
> **Objetivo:** que PERC tome tres decisiones (formato, campos mínimos, origen de los datos) para poder cerrar la carga del documento en el flujo y no bloquear el UAT.

---

## 1. Qué necesitamos que PERC defina (resumen ejecutivo)

Para poder implementar la generación del documento en el flujo de crédito, PERC debe cerrar **tres decisiones** y **dos endpoints**:

**Decisiones**
1. **Formato.** ¿Se puede reemplazar el formato "imprimir-y-llenar" (tablas + cuadraditos + campos manuscritos) por **HTML plano con variables** `{{campo}}`? Esto depende de si la Superintendencia de Seguros aprueba el **contenido** de los formularios o también su **formato/layout**. → *Seba a confirmar con la mutual/legales.*
2. **Campos mínimos.** ¿Cuáles son los **datos mínimos obligatorios** para otorgar el préstamo? El legajo trae muchos campos que la mutual usa para cualquier trámite y que no hace falta completar (ver §3, columna categoría).
3. **Origen de los datos que hoy no tenemos.** Para los campos que NO devuelve el endpoint `mi cuenta` y que NO son datos del préstamo, hay tres caminos posibles: **(a)** ampliar el endpoint de cuenta para que los devuelva; **(b)** un formulario de data-entry del usuario — **fuera de scope, no se diseñó**; **(c)** una alternativa que proponga PERC.

**Endpoints (Quarks pide a PERC)**
4. **Endpoint de saldo/fondos** de la cuenta recaudadora. El actual "obtener CVU" solo dice **si hay o no dinero** (booleano), no **cuánto**. Para validar fondos contra el monto a desembolsar necesitamos el saldo, o un endpoint **consulta-y-reserva / consulta-y-desembolsa** en una sola llamada (evita la race condition entre consultar y transferir).
5. **Endpoint de cash out** completo. El que se pasó **pide variables que no están en el Insomnia**, por lo que hoy no se puede probar. Necesitamos el contrato completo.

---

## 2. Alcance documental — ¿cuáles de los 9 formularios aplican al MVP?

El .docx contiene 9 formularios de la mutual. **A confirmar con PERC/legales cuáles entran realmente en el flujo de firma del préstamo** (varios parecen ajenos al crédito). Propuesta de clasificación inicial:

| Código | Formulario | ¿Aplica al préstamo? (propuesta) |
|---|---|---|
| A237 | **Solicitud de S.A.E.M.** (el préstamo) | ✅ Núcleo — sí |
| A172 | Resumen TYC SAEM (Com. A 7199 BCRA) | ✅ Sí — resumen obligatorio de tasas/condiciones |
| A116 | Pagaré a la vista | ✅ Sí — título ejecutivo de la deuda |
| A169 | Instrucción irrevocable para desembolso | ✅ Sí — instrucción de liquidación |
| A118 | Constancia de liquidación y recibo de pago | ✅ Sí — recibo del desembolso |
| A152 | Autorización de débito de haberes | ✅ Sí — autoriza la retención mensual |
| A143 | DDJJ PEP / UIF (Res. 99/2023 + 35/2023) | ⚠️ A confirmar — antilavado; ¿lo exige el flujo digital o ya lo cubre PERC como empleador? |
| A104 | Solicitud de Socio AMFAYS | ⚠️ A confirmar — ¿el empleado se hace socio de la mutual en el flujo? Trae datos familiares/subsidio de carga manual. |
| A136 | Solicitud de Servicios Sociales | ❌ Propuesta: **fuera** — óptica/farmacia/turismo/subsidios, ajeno al préstamo |

> **Nota:** esto también toca la definición pendiente de **"5 documentos → 1"** (legales evaluaba unificar los T&C). Conviene cerrar en el mismo movimiento **cuántos y cuáles** documentos se persisten/firman en el MVP.

---

## 3. Inventario de campos y de dónde sale cada uno

**Leyenda de categorías**

- **[EP]** — Disponible hoy en el endpoint `mi cuenta` (dato del usuario logueado).
- **[EP?]** — Dato del usuario que **hoy NO devuelve** `mi cuenta` → habría que **ampliar el endpoint** (o definir otro origen). Es el corazón de la decisión #3.
- **[PR]** — **Dato del préstamo** — lo completa el sistema/BO desde el template del crédito y el cálculo de cuotas.
- **[MX]** — **Carga manual → FUERA DE SCOPE.** No hay formulario de data-entry; estos campos quedan sin completar salvo que PERC defina otra vía.
- **[SY]** — **Sistema / firma** — lo genera el flujo (Nº de operación, fecha, firma electrónica).

### 3.1 Datos personales del solicitante

| Campo | Categoría | Notas |
|---|---|---|
| Apellido y Nombres | [EP?] | Usuario logueado — **confirmar que `mi cuenta` lo devuelve** |
| Tipo y Nº de Documento (DNI) | [EP?] | Ídem — confirmar |
| CUIL / CUIT | [EP?] | Ídem — confirmar |
| Fecha de Nacimiento | [EP?] | Seba: "todo lo demás no está" → probable gap |
| Nacionalidad | [EP?] | Probable gap |
| Estado Civil | [EP?] | Probable gap |
| Sexo / Género | [EP?] | Probable gap (aparece en A136/A143) |
| Lugar de Nacimiento | [MX] | Solo en A143 (DDJJ PEP) — evaluar si A143 aplica |
| Domicilio (calle, número, piso, dpto) | [EP?] | Probable gap |
| Código Postal | **[EP]** | Confirmado por Seba |
| Localidad | **[EP]** | Confirmado por Seba |
| Provincia | [EP?] | Confirmar |
| Teléfono Particular / Celular | [EP?] | Probable gap |
| Mail / correo electrónico | [EP?] | Probable gap |
| Propietario de Vehículo (Sí/No) | [MX] | A104 — opción manual, fuera de scope |
| Propietario de Inmueble (Sí/No) | [MX] | A104 — opción manual, fuera de scope |
| Condición frente a IVA + CUIT | [MX] | A104/A143 — manual, fuera de scope |

### 3.2 Antecedentes laborales

| Campo | Categoría | Notas |
|---|---|---|
| Empleador actual | [PR]/[SY] | Constante = la empresa del Grupo PERC (dato fijo del template) |
| CUIT del empleador | [PR]/[SY] | Constante del empleador |
| **Antigüedad** | **[EP]** | Confirmado por Seba |
| **Legajo Nro.** | **[EP]** | Confirmado por Seba (además, Quarks lo levanta/guarda — ver ciclo Mantovana) |
| Actividad / Profesión | [EP?] | Confirmar / probable gap |
| Cargo / Categoría / Sección | [EP?] | Probable gap |
| Domicilio laboral (calle/CP/loc/prov) | [SY] | Constante del empleador |
| Teléfono e interno laboral | [SY] | Constante del empleador |
| **Sueldo Mensual** | [EP?] | **Necesario** — habilita el tope legal del 30%. Entra con la elegibilidad; hoy es un gap conocido. |
| Empleado PJ (flag) | **[EP]** | Confirmado que `mi cuenta` trae PJ (persiste la brecha de entendimiento sobre cómo se usa) |

### 3.3 Datos bancarios

| Campo | Categoría | Notas |
|---|---|---|
| CBU / CVU (cuenta sueldo) | [EP?] | Debe salir de las wallets del usuario (`get account`); el desembolso va **siempre a cuenta sueldo** |
| Banco Pagador de Haberes | [EP?] | Confirmar si se deriva del CBU o falta |
| Sucursal | [EP?] | Probable gap |

### 3.4 Datos del préstamo (los completa el sistema/BO)

| Campo | Categoría | Notas |
|---|---|---|
| Nº de S.A.E.M. / operación | [SY] | Genera el sistema |
| Monto solicitado ($ y en letras) | [PR] | Input del BO en el template (capital solicitado) |
| Cantidad de cuotas | [PR] | Del template/plan elegido |
| Valor de cuota mensual ($ y en letras) | [PR] | Cálculo Sistema Francés |
| Mes de inicio / fecha 1ª cuota | [PR]/[SY] | Según fecha de desembolso |
| Interés compensatorio anual (%) | [PR] | Del template del crédito |
| TNA / TEM / TEA | [PR] | Del cálculo |
| CFT (CFTNA / CFTEA) | [PR] | Del cálculo |
| Monto total a reintegrar | [PR] | Del cálculo |
| Comisión de precancelación (%) | [PR] | Del template (config por tipo de préstamo) |
| Destino de los fondos | [PR]/[MX] | Si es obligatorio declararlo, definir si es fijo o manual |

### 3.5 Carga manual → FUERA DE SCOPE

| Bloque | Formulario | Categoría |
|---|---|---|
| Datos familiares (parentesco/nombre/doc/fec.nac) | A104 | [MX] |
| Datos del beneficiario del subsidio | A104 | [MX] |
| Servicios sociales y subsidios (óptica, farmacia, turismo, hogar, salud) | A136 | [MX] |
| DDJJ PEP (Sí/No, cargo, jerarquía, vigencia) | A143 | [MX] |
| Sujeto Obligado UIF (Sí/No) | A143 | [MX] |
| Volumen de ingresos / facturación anual | A143 | [MX] |
| Motivo de elección del servicio/producto | A143 | [MX] |

> **Consecuencia de scope:** si alguno de estos campos resulta **obligatorio** para la validez legal del préstamo, se abre una definición nueva (no hay data-entry en el MVP). Por eso la decisión #3 es bloqueante: hay que saber **qué campos obligatorios caen en [MX]**.

### 3.6 Firma / cierre

| Campo | Categoría | Notas |
|---|---|---|
| Firma del solicitante (`#FIRMA#`) | [SY] | Firma electrónica del flujo (modelo tipo iniciales/TOTP — pendiente validación legal de compliance) |
| Aclaración / DNI al pie | [EP?] | Se deriva de datos personales |
| Fecha | [SY] | Fecha del acto |
| VºBº Promotor / campos internos de la mutual | [MX] | Uso interno AMFAYS — probablemente no aplica al flujo digital |

---

## 4. Lo que Quarks necesita de PERC para desbloquear

1. **Confirmar el contrato de `mi cuenta`** — lista exacta de campos que devuelve hoy (validar/ampliar la tabla §3 marcada [EP?]).
2. **Decidir formato** — HTML plano con variables (sí/no), según lo que apruebe la Superintendencia (contenido vs. formato).
3. **Decidir el origen** de los campos [EP?] y qué se hace con los [MX] obligatorios (ampliar endpoint vs. valor por defecto vs. quitar del documento).
4. **Definir el set final de formularios** del MVP (§2) — cerrar junto con la definición "5 docs → 1".
5. **Entregar** el endpoint de saldo/fondos y el contrato completo de cash out.

## 5. Cronograma (acordado en el call)

- **Jue–vie 9–10 jul:** PERC no trabaja; Job (reviewer) de licencia hasta el lunes. Quarks manda PRs → quedan en cola; Quarks avanza el happy path asumiendo aprobación.
- **Lunes 13 jul:**
  - **Best case:** PRs aprobados + documentos definidos + endpoint de fondos → **sale el UAT** con margen para correcciones.
  - **Worst case:** sin documentos y/o sin endpoint de fondos → **se mueve la reunión / el UAT**.
