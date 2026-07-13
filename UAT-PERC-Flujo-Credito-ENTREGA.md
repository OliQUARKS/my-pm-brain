# Tabla de UAT — PERC Flujo Crédito
**Generado:** 2026-07-06  
**Scope:** Sprint 1–4 (MVP completo)  
**Archivo CSV:** `uat-perc-flujo-credito.csv`

---

## Resumen Ejecutivo

**50 casos de UAT completamente funcionales** listos para importar a Google Sheets.

| Métrica | Valor |
|---------|-------|
| **Total casos de prueba** | 50 |
| **Historias cubiertas** | 50 (sin subtareas) |
| **Escenarios Gherkin (Español)** | 100% |
| **Épicas/Áreas funcionales** | 9 |
| **Encoding** | UTF-8 |
| **Separador** | Coma (,) |

---

## Épicas & Distribución

| Épica | # Casos | Descripción |
|-------|---------|-------------|
| **Solicitud de Crédito** | 4 | Creación, firma con TOTP, expiración automática |
| **Desembolso** | 4 | Desembolso inmediato, retry, timeout 24h, vista BO |
| **Reportes** | 6 | Generación Excel, importación La Mantovana, histórico filtrable |
| **Imputación** | 6 | Regla FIFO 4+1, estados de pago (Parcial/Error/Sobrepago), carga manual |
| **Estados** | 3 | Transiciones válidas (PENDIENTE→OTORGADO→PAGADO) |
| **Cancelación** | 4 | Arrepentimiento, precancelación, desistimiento pre-desembolso |
| **Cálculos** | 7 | Cuenta sueldo, tope 30%, cuota francesa, seguro, mora, legajo |
| **Documentos** | 4 | HTML dinámico, Sábana PDF, TOTP obligatorio, firma auditable |
| **Operativa** | 12 | Máquina de estados, audit trail, FIFO, validación formato, identificación cuenta sueldo |

**Total: 50 casos**

---

## Estructura de Columnas

| Columna | Descripción | Estado |
|---------|---|---|
| **Épica** | Área funcional (categoría) | ✓ Pre-llenado |
| **ID Historia** | Identificador único (PER-001 a PER-050) | ✓ Pre-llenado |
| **Nombre Historia** | Título de la historia | ✓ Pre-llenado |
| **Nombre Escenario** | Identificador del escenario dentro historia | ✓ Pre-llenado |
| **Escenario (Gherkin)** | Dado/Cuando/Entonces en español | ✓ Pre-llenado |
| **Validación** | Qué verifica QA durante ejecución | ✓ Pre-llenado (mayoría) |
| **Resultado Esperado** | Outcome correcto del escenario | ✓ Pre-llenado |
| **Resultado Obtenido** | QA llena durante testing | ⚪ Vacío (a llenar) |
| **Status** | Aprobado / Fallido / Bloqueado / Pendiente | ⚪ Vacío (a llenar) |
| **Asignación** | Nombre QA responsable | ⚪ Vacío (a llenar) |

---

## Campos Pre-llenados

### Épica
9 áreas funcionales del Flujo Crédito:
- Solicitud de Crédito
- Desembolso
- Reportes
- Imputación
- Estados
- Cancelación
- Cálculos
- Documentos
- Operativa

### ID Historia
Identificadores únicos: **PER-001** a **PER-050** (correlativo, ordenado por épica)

### Nombre Historia
Título descriptivo, ej:
- "Crear solicitud de crédito"
- "Desembolso a cuenta sueldo"
- "Generar archivo novedades para La Mantovana"
- "Estado de pago: PAGO PARCIAL"

### Nombre Escenario
Variante dentro de la historia, ej:
- "Con opción válida"
- "Múltiples solicitudes simultáneas"
- "Desembolso inmediato con fondos"
- "Monto < cuota; genera error"

### Escenario (Gherkin)
**Formato:** `Dado que [precondición] | Cuando [acción] | Entonces [resultado]`  
**Idioma:** Español  
**Ejemplo:**
```
Dado que usuario está autenticado en APP | 
Cuando selecciona una de las 3 opciones de preaprobadas | 
Entonces se crea solicitud en estado EN CURSO sin registro en BD
```

### Validación
Qué verifica QA. Ejemplos:
- "La solicitud se muestra en la sesión del usuario con monto y plazo seleccionado"
- "Sistema registra imputación con timestamp; cuota avanza en estado de pago"
- "Error muestra: fila exacta | campo faltante | solución sugerida; requiere reintentar"

### Resultado Esperado
Outcome correcto. Ejemplos:
- "Documento se marca como FIRMADO con timestamp; estado pasa a PENDIENTE"
- "Solicitud es inaccesible; usuario debe reiniciar flujo"
- "PDF generado contiene: nombre correcto | monto solicitado | términos dinámicos; sin placeholders"

---

## Columnas Vacías para QA

### Resultado Obtenido
**Qué hace QA:** Durante ejecución, documenta lo que realmente ocurre en el sistema.

Formatos aceptados:
- ✓ "PASS: Solicitud creada correctamente"
- ✗ "FAIL: Sistema rechazó con error 500"
- ⏳ "BLOQUEADO: Endpoint /funds/balance no disponible"
- 📝 "PARCIAL: Funciona en Chrome, falla en Safari"

### Status
Marca el resultado final. Opciones recomendadas:
- ✓ **Aprobado** - Funciona exactamente como esperado
- ✗ **Fallido** - Comportamiento incorrecto; requiere corrección
- ⏳ **Bloqueado** - No se puede ejecutar (dependencia faltante)
- ⏸️ **Pendiente** - No ejecutado aún
- 🔄 **Requiere retest** - Fallido en sprint anterior, se reintenta

### Asignación
Nombre de persona QA responsable de ese caso.  
Ejemplo: "Juan (QA)" o "Maria Lopez"

---

## Cómo Usar (Flujo Típico)

### 1. Importar a Google Sheets
```
1. Abre https://sheets.google.com
2. Nuevo archivo > Importar
3. Carga uat-perc-flujo-credito.csv
4. Formato: Fila 1 = encabezados, datos desde fila 2
5. Elige Reemplazar hoja
6. Listo: tabla compartible
```

### 2. QA Ejecuta Casos
Para cada fila:
1. Lee columna **Escenario (Gherkin)** → entiende precondición
2. Lee columna **Validación** → sabe qué verificar
3. Ejecuta acciones en sistema
4. Compara "Resultado Obtenido" vs "Resultado Esperado"
5. Llena columnas:
   - **Resultado Obtenido** = qué pasó realmente
   - **Status** = ✓ / ✗ / ⏳
   - **Asignación** = tu nombre (auto-fill si es repetido)

### 3. Generación de Reportes
Al finalizar UAT:
```
=COUNTIF(Status, "Aprobado")     → Total aprobados
=COUNTIF(Status, "Fallido")       → Total fallidos
=COUNTIF(Status, "Bloqueado")     → Total bloqueados
Tasa de cobertura = Aprobados / Total × 100%
```

---

## Bloqueos & Dependencias Identificadas

| Bloqueante | Impacto | Casos | Estado |
|---|---|---|---|
| **Endpoint `/funds/balance`** (PERC) | Desembolso, retry, timeout | PER-005 a PER-007, PER-043 | Solicitado 2026-06-17 |
| **Confirmación legajo (Fefe)** | OK formal sobre quién lo levanta | PER-033 | Pendiente |
| **Definición entorno + CI/CD** | Infraestructura pre-UAT | Todos | En progreso |
| **Validación TOTP security** | Bypass de autenticación | PER-037 | Abierto (Joy) |
| **Plantillas HTML compliance** | Documentos dinámicos | PER-035, PER-048 | En compliance |

**Notas:** Los casos bloqueantes pueden ejecutarse con mocks/stubs; revalidar post-resolución.

---

## Notas de Ingeniería

### Gherkin es Guía, no Prescripción
QA puede adaptar pasos exactos según:
- Entorno (dev/stage/prod)
- Navegador/dispositivo
- Datos de prueba disponibles

### Casos 24–27 (Cancelación)
Validan **registro**, no **ejecución de TED** (transfer). La Mantovana ejecuta transferencias; Quarks solo registra.

### Casos 47–48 (Elegibilidad/Sueldo)
Datos vienen de PERC; Quarks valida que existan, no recalcula criterios.

### Audit Trail (Case 40)
- Implementado por Nico en backend
- QA verifica: consultando BD directamente O a través de UI BO si está expuesta

### Estados de Pago (Cases 15–20)
Máquina de 4 estados:
- **PAGADA** — Monto = Cuota exactamente
- **PAGO PARCIAL** — Monto < Cuota
- **PAGO CON ERROR** — Imputación inválida
- **SOBREPAGO** — Monto > Cuota

---

## Validación Interna

✓ **50 casos únicos**, sin duplicación  
✓ **100% Gherkin en español**, formato Dado/Cuando/Entonces  
✓ **Cobertura de épicas:** todas representadas  
✓ **Encoding UTF-8:** importable a cualquier plataforma  
✓ **Columnas pre-llenadas:** Épica, ID, Nombre, Escenario, Validación, Resultado Esperado  
✓ **Columnas vacías para QA:** Resultado Obtenido, Status, Asignación  

---

## Próximos Pasos

1. **Importar a Google Sheets** → compartir con equipo QA
2. **Validar con Seba/Nico:** ¿50 casos cubren todos los AC?
3. **Mapear PER-001–050 a Linear IDs** si existe backlog en Linear
4. **Configurar filtros en Sheets:**
   - Por Épica (dropdown)
   - Por Status (condicionales coloreadas)
   - Por Asignación (filtro avanzado)
5. **Ejecutar UAT** → recolectar hallazgos
6. **Generar reporte final:** tasa cobertura + bugs encontrados

---

## Contacto & Soporte

- **PM:** Olivier Luce (olivier@quarksalchemist.com)
- **Tech Lead QA:** [A definir]
- **Fuente de historias:** `/Users/olivierluce/projects/my-pm-brain/knowledge/product/features/flujo-credito.md`
- **Decisiones relacionadas:** `decisions/2026-*.md`

---

*Tabla generada desde PM Brain — PERC Flujo Crédito Sprint 1–4 (MVP)*

**Archivo:** `uat-perc-flujo-credito.csv` (UTF-8, 50 casos)  
**Última actualización:** 2026-07-06
