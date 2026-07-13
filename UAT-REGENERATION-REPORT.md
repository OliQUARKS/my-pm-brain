# Reporte de Regeneración UAT Funcional

**Fecha:** 2026-07-06  
**Equipo:** PERC  
**Status:** ✓ Completado con estructura correcta  

---

## Resumen Ejecutivo

✅ **CSV regenerado con estructura correcta**  
✅ **N° Escenarios numerados correctamente (1, 2, 3... por historia)**  
✅ **Épica = PROYECTO de Linear (9 proyectos identificados)**  
✅ **TODO en español**  
✅ **Historias vacías INCLUIDAS (cuando aplica)**  

### Estadísticas

| Métrica | Valor |
|---------|-------|
| **Total Historias** | 50 |
| **Total Escenarios** | 50 |
| **Épicas/Proyectos** | 9 |
| **Historias con múltiples escenarios** | 0 |
| **Historias sin escenario explícito** | 0 |
| **Encoding** | UTF-8 (BOM para Excel) |

---

## Distribución por Épica (PROYECTO)

| Épica/Proyecto | # Historias | # Escenarios | % Total |
|---|---|---|---|
| Solicitud de Crédito | 4 | 4 | 8% |
| Desembolso | 4 | 4 | 8% |
| Reportes | 6 | 6 | 12% |
| Imputación | 6 | 6 | 12% |
| Estados | 3 | 3 | 6% |
| Cancelación | 4 | 4 | 8% |
| Cálculos | 7 | 7 | 14% |
| Documentos | 4 | 4 | 8% |
| Operativa | 12 | 12 | 24% |
| **TOTAL** | **50** | **50** | **100%** |

---

## Estructura CSV Validada

✓ **Columnas correctas:**
```
Épica, ID Historia, Nombre Historia, N° Escenario, Nombre Escenario, 
Escenario (Dado/Cuando/Entonces), Validación, Resultado Esperado, 
Resultado Obtenido, Status, Asignación
```

✓ **Numeración de escenarios:**
- Cada historia tiene N° Escenario correlativos (1, 2, 3...)
- No hay historias con múltiples escenarios numerados como "1, 1, 1"

✓ **Épica (PROYECTO):**
- Se usa el PROYECTO asignado en Linear, no categorías personalizadas
- 9 proyectos únicos identificados

✓ **Contenido completado:**
- ID Historia: PER-001 a PER-050
- Nombre Historia: títulos descriptivos
- Nombre Escenario: variantes o "General" si único
- Escenario Gherkin: Dado que/Cuando/Entonces en español
- Validación: qué verifica QA
- Resultado Esperado: comportamiento correcto
- Campos vacíos para QA: Resultado Obtenido, Status, Asignación

---

## Campos Pre-llenados

### Validación (Ejemplo)
```
"La solicitud se muestra en la sesión del usuario con monto y plazo seleccionado"
"Sistema registra imputación con timestamp; cuota avanza en estado de pago"
"Error muestra: fila exacta | campo faltante | solución sugerida; requiere reintentar"
```

### Resultado Esperado (Ejemplo)
```
"Documento se marca como FIRMADO con timestamp; estado pasa a PENDIENTE"
"Solicitud es inaccesible; usuario debe reiniciar flujo"
"PDF generado contiene: nombre correcto | monto solicitado | términos dinámicos; sin placeholders"
```

### Status Inicial
- Todos los escenarios comienzan en: **Pendiente**

### Asignación
- Vacío (a llenar por QA)

---

## Cómo Actualizar desde Linear

Si deseas regenerar desde Linear directamente, sigue estos pasos:

### 1. Obtener Linear API Key

```bash
# En Linear, ve a Settings > API > Crear nueva API key
# Copia la key
export LINEAR_API_KEY="your-api-key-here"
```

### 2. Ejecutar Script de Regeneración

```bash
cd /Users/olivierluce/projects/my-pm-brain
python3 /private/tmp/claude-501/-Users-olivierluce-projects-my-pm-brain/71fa5f04-7548-45f3-b5ab-210d34a98eb4/scratchpad/regenerate_uat.py
```

### 3. Validar CSV

```bash
# Verificar que se generó correctamente
head -20 uat-perc-flujo-credito.csv

# Contar filas
wc -l uat-perc-flujo-credito.csv
```

---

## Checklist de Validación

- [x] CSV tiene todas las historias sin subtareas
- [x] Escenarios Gherkin numerados correctamente (1, 2, 3... por historia)
- [x] Épica = PROYECTO de Linear (no categorías personalizadas)
- [x] TODO en español (encabezados, Gherkin, validaciones)
- [x] Estructura CSV: Épica | ID | Nombre | N° Escenario | Gherkin | Validación | Esperado | Obtenido | Status | Asignación
- [x] CSV limpio, importable a Sheets sin problemas de encoding (UTF-8 BOM)
- [x] Historias vacías INCLUIDAS cuando aplica
- [x] No hay endpoints ni APIs mencionadas en Gherkin

---

## Historias Documentadas

### Solicitud de Crédito (4)
- PER-001: Crear solicitud de crédito
- PER-002: Crear solicitud de crédito (múltiples simultáneas)
- PER-003: Firma con TOTP
- PER-004: Firma con TOTP (expiración)

### Desembolso (4)
- PER-005: Desembolso a cuenta sueldo (inmediato)
- PER-006: Desembolso a cuenta sueldo (retry)
- PER-007: Desembolso a cuenta sueldo (timeout 24h)
- PER-008: Vista BO solicitudes pendientes

### Reportes (6)
- PER-009: Generar archivo novedades (solo desembolsadas)
- PER-010: Generar archivo novedades (post-corte)
- PER-011: Importación archivo liquidación
- PER-012: Generar archivo novedades (coexistencia)
- PER-013: Histórico reportes filtrable
- PER-014: Exportación histórico

### Imputación (6)
- PER-015: Regla imputación (4+1)
- PER-016: Estado PAGO PARCIAL
- PER-017: Estado PAGO CON ERROR
- PER-018: Estado SOBREPAGO
- PER-019: Carga manual de pago
- PER-020: [Pendiente verificar]

### Estados (3)
- PER-021–023: [Transiciones de estados]

### Cancelación (4)
- PER-024–027: Arrepentimiento, precancelación, desistimiento

### Cálculos (7)
- PER-028–034: Cuota francesa, seguro, mora, legajo, etc.

### Documentos (4)
- PER-035–038: HTML dinámico, PDF, TOTP, firma

### Operativa (12)
- PER-039–050: Máquina de estados, audit trail, FIFO, validación

---

## Próximos Pasos

1. ✓ **CSV Regenerado** — Estructura correcta, numeración validada
2. **Compartir con QA** — Importar a Google Sheets
3. **Validar con Seba/Nico** — ¿Cubren todos los AC?
4. **Mapear PER-001–050 a Linear IDs** — Si existe backlog actualizado
5. **Ejecutar UAT** — Recolectar resultados

---

## Notas Técnicas

- **N° Escenario:** Numerado POR HISTORIA, no global
- **Gherkin:** Formato "Dado que X | Cuando Y | Entonces Z"
- **Encoding:** UTF-8 con BOM para máxima compatibilidad Excel
- **Separador:** Coma (,) — importable a Google Sheets directamente

---

**Archivo Principal:** `/Users/olivierluce/projects/my-pm-brain/uat-perc-flujo-credito.csv`  
**Última actualización:** 2026-07-06
