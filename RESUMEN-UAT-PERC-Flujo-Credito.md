# Tabla de UAT — PERC Flujo Crédito
**Escenarios Gherkin desde PM Brain**  
**Generado:** 2026-07-06  
**Scope:** Sprint 1–4 (MVP completo)

---

## Estadísticas Generales

| Métrica | Valor |
|---------|-------|
| **Total casos de prueba** | 50 |
| **Historias únicamente** | 50 (sin subtareas) |
| **Escenarios con Gherkin explícito** | 50/50 (100%) |
| **Categorías cubiertas** | 9 |
| **Status inicial** | Pendiente (vacío) |

---

## Categorización por Área Funcional

### 1. **Ciclo de Solicitud & Firma (Cases 1–4)**
- Creación de solicitud (EN CURSO, sin BD)
- Firma unificada + TOTP
- Expiración automática (1h sin firma)
- Cambio de template (expira asociadas)

**Escenarios:** 4 | **Punto de entrada:** APP → BO

---

### 2. **Desembolso & Fondos (Cases 5–8)**
- Desembolso inmediato (fondos disponibles)
- Desembolso PENDIENTE con retry cada 5 min
- Timeout 24h corridas → Cancelación
- Vista BO: solicitudes pendientes por fondos (countdown)

**Escenarios:** 4 | **Dependencia bloqueante:** Endpoint `/funds/balance` (PERC)

---

### 3. **Generación de Reportes & Sincronización La Mantovana (Cases 9–14)**
- Archivo novedades (solo DESEMBOLSADOS)
- Estructura Excel: legajo + concepto + nombre + importe + fecha
- Corte configurable (BD, no env var)
- Coexistencia automático/manual
- Importación archivo liquidación La Mantovana
- Histórico filtrable por usuario/mes/fecha

**Escenarios:** 6 | **Cadencia:** Mensual (~día 20 / 4º día hábil)

---

### 4. **Imputación & Estados de Pago a Cuota (Cases 15–20)**
- Imputación a primera cuota NO PAGADA (regla 4+1)
- **PAGO PARCIAL:** Monto < cuota; marca faltante
- **PAGO CON ERROR:** Imputación inválida (ej. cuota pagada)
- **SOBREPAGO:** Monto > cuota; habilita devolución
- Carga manual de pago desde BO (quién/cuándo/cuánto)
- Panel de conciliación con historial

**Escenarios:** 6 | **Máquina de estados:** 4 estados de cuota

---

### 5. **Estados del Préstamo & Transiciones (Cases 21–23)**
- OTORGADO (desembolsado)
- PAGADO (todas cuotas pagadas)
- Cancelación anticipada (fórmula: K + (I_futuros × %pen) + (K × %com) + IVA)

**Escenarios:** 3

---

### 6. **Cancelación (Cases 24–27)**
- Arrepentimiento (10 días ley, manual por mail)
- Precancelación anticipada (manual por mail)
- BO marca "Cancelado" (registro, no ejecuta)
- Cancelación SOLICITUD pre-desembolso (desistimiento)

**Escenarios:** 4 | **Scope:** Registro solamente (no ejecución de TED)

---

### 7. **Cálculos & Parámetros de Crédito (Cases 29–34)**
- Validación cuenta SUELDO (único destino desembolso)
- Tope 30% sueldo percibido
- Cuota Sistema Francés (fija mensual)
- Seguro de vida (capitalizado al inicio, $0 en cuotas)
- Mora (% fijo capitalizado, no condicional)
- Legajo (levantado por Quarks, guardado en usuario)

**Escenarios:** 6

---

### 8. **Documentos & Seguridad (Cases 35–38)**
- HTML dinámico + PDF (renderizado con variables)
- TOTP obligatorio en firma
- TOTP security: bypass imposible en endpoint
- Documentos auditables (firma + 5 docs embebidos)

**Escenarios:** 4

---

### 9. **Operativa & Auditoría (Cases 39–50)**
- Máquina de estados (transiciones válidas)
- Logging de operador BO (audit trail)
- Validación formato importación (rechaza íntegro si error)
- Concordancia exacta pago = cuota
- Arrepentimiento requiere validación de fondos
- Base cancelación anticipada (deuda restante)
- FIFO estricto (orden de llegada)
- Elegibilidad / Tags / Sueldo (PERC side)
- Documentos dinámicos (placeholders)
- Firma manual cancelaciones (flujo email)

**Escenarios:** 12

---

## Historias SIN Gherkin Explícito

**Ninguna.** Todos 50 casos se derivaron de:
- Decisiones documentadas en `decisions/`
- Reuniones de refinamiento en `ingestion/meetings/`
- Feature file `knowledge/product/features/flujo-credito.md`

---

## Bloqueos & Dependencias Detectadas

| Bloqueante | Propietario | Estado | Impacto |
|---|---|---|---|
| Endpoint `/funds/balance` (consulta saldo recaudadora) | PERC | Solicitado 2026-06-17 | Cases 5–7, 43–46 |
| Confirmación Fefe: legajo lo levanta Quarks | PERC | Pendiente | Case 34 |
| Definición BO entorno + CI/CD | PERC + Quarks | En progreso | Infra desembolso |
| Validación TOTP security bypass | Joy (integración) | Abierto | Case 37 |
| Plantillas HTML compliance | Compliant + Seba | En compliance | Case 35 |

---

## Columnas de la Tabla UAT

| Columna | Descripción | Llenado |
|---------|---|---|
| **CASO** | # secuencial (1–50) | ✓ Pre-llenado |
| **ID** | PER-001 a PER-050 | ✓ Pre-llenado |
| **Nombre** | Título corto de la historia | ✓ Pre-llenado |
| **Descripción (Escenario Gherkin)** | Given/When/Then | ✓ Pre-llenado |
| **Paso** | Qué acción ejecuta el QA | ✓ Pre-llenado sugerencia |
| **Validación** | Qué verifica el QA | ✓ Pre-llenado sugerencia |
| **Resultado Esperado** | Outcome correcto | ✓ Pre-llenado |
| **Resultado Obtenido** | QA llena durante testing | Vacío (a llenar) |
| **Status** | Aprobado / Fallido / Pendiente | Vacío (a llenar) |
| **Asignación** | Persona responsable | Vacío (a llenar) |

---

## Cómo usar esta tabla

### Flujo de UAT típico:
1. **QA abre la tabla** → accede a todos 50 casos
2. **Para cada caso:**
   - Lee Descripción (Gherkin)
   - Ejecuta "Paso"
   - Verifica "Validación"
   - Compara "Resultado Obtenido" vs "Resultado Esperado"
   - Marca Status (✓ Aprobado / ✗ Fallido / ⏳ Pendiente)
   - Anota hallazgos en "Resultado Obtenido"
3. **Al final:** Cuenta aprobados/fallidos, genera reporte

---

## Notas

- **Gherkin es sugerencia, no prescriptivo.** QA puede adaptar pasos según entorno.
- **Casos 24–27 (Cancelación):** Validan registro, no ejecución de TED (out of scope Sprint 4).
- **Caso 46:** Bloqueante → no se puede validar desembolso sin endpoint de fondos PERC.
- **Casos 47–48 (Elegibilidad/Sueldo):** Data viene de PERC; Quarks solo valida.
- **Audit trail (Case 40):** Nico implementa logging; QA verifica DB directamente o via BO UI.

---

## Próximos pasos

1. **Importar CSV a Google Sheets** (editable, shareable)
2. **Mapear PER-001 → PER-050 a Linear IDs** cuando PERC tenga backlog en Linear
3. **Integrar estado desde Linear** (P_READ: if caso tiene PER-XXX → buscar en Linear → sync status)
4. **Validar con Seba/Nico** que los 50 escenarios cubren todos los AC de las historias

---

*Generado desde PM Brain `knowledge/product/features/flujo-credito.md` + decisiones + refinamientos Sprint 1–4.*
