# Tabla de UAT PERC Flujo Crédito — Acceso Rápido

**Generada:** 2026-07-06 | **Scope:** Sprint 1–4 (MVP)

---

## Archivos

### 1. `uat-perc-flujo-credito.csv` (15 KB)
**Archivo principal de UAT — importable a Google Sheets**

**Estructura:**
- 50 casos de prueba (PER-001 a PER-050)
- 10 columnas funcionales
- Encoding UTF-8, separador coma
- 100% Gherkin en español

**Columnas:**
1. Épica (9 áreas)
2. ID Historia
3. Nombre Historia
4. Nombre Escenario
5. Escenario (Dado/Cuando/Entonces)
6. Validación
7. Resultado Esperado
8. **Resultado Obtenido** ← QA llena
9. **Status** ← QA llena
10. **Asignación** ← QA llena

**Cómo importar:**
```
1. Abre https://sheets.google.com
2. Nuevo → Importar
3. Sube uat-perc-flujo-credito.csv
4. Elige "Reemplazar hoja"
5. Listo: tabla compartible
```

---

### 2. `UAT-PERC-Flujo-Credito-ENTREGA.md` (8.4 KB)
**Guía completa con instrucciones y referencia**

**Secciones:**
- Resumen ejecutivo
- Épicas & distribución
- Estructura de columnas
- Campos pre-llenados vs. vacíos
- Bloqueos & dependencias
- Notas de ingeniería
- Próximos pasos

---

## Distribución Rápida

| Épica | # Casos | Rango |
|-------|---------|-------|
| Solicitud de Crédito | 4 | PER-001–004 |
| Desembolso | 4 | PER-005–008 |
| Reportes | 6 | PER-009–014 |
| Imputación | 6 | PER-015–020 |
| Estados | 3 | PER-021–023 |
| Cancelación | 4 | PER-024–027 |
| Cálculos | 7 | PER-028–034 |
| Documentos | 4 | PER-035–038 |
| Operativa | 12 | PER-039–050 |

---

## Casos Críticos

⚠️ **Bloqueantes (requieren dependencias PERC):**
- **PER-005–007:** Desembolso (requiere endpoint `/funds/balance`)
- **PER-037:** TOTP security (requiere validación Joy)
- **PER-035, PER-048:** Documentos HTML (pendiente compliance)

✓ **Pueden ejecutarse con mocks:**
- Usar stubs/fixtures para fondos
- Usar TOTP dummy para pruebas
- Usar plantillas HTML ejemplo

---

## Flujo UAT Típico

1. **QA abre Google Sheet** con CSV importado
2. **Para cada fila:**
   - Lee columna "Escenario (Gherkin)"
   - Ejecuta en sistema
   - Registra "Resultado Obtenido"
   - Marca "Status" (✓ / ✗ / ⏳)
   - Ingresa "Asignación" (tu nombre)
3. **Al terminar:**
   - `=COUNTIF(Status, "Aprobado") / 50 * 100%` → tasa cobertura
   - Exporta hallazgos
   - Genera reporte

---

## Validación Interna

✓ 50 casos únicos  
✓ 100% Gherkin español  
✓ 9 épicas cubiertas  
✓ UTF-8 verificado  
✓ CSV parseado correctamente  

---

## Preguntas Frecuentes

**P: ¿Puedo modificar el CSV directamente?**  
R: Sí. Pero mejor importa a Google Sheets para colaboración en tiempo real.

**P: ¿Puedo agregar más columnas?**  
R: Sí. Google Sheets permite columnas adicionales (ej: Severidad, Componente, Links a tickets).

**P: ¿Qué hago si el caso está bloqueado?**  
R: Marca Status = "Bloqueado" en Resultado Obtenido; documenta la dependencia pendiente.

**P: ¿Cómo genero un reporte final?**  
R: Usa fórmulas COUNTIF en Google Sheets:
   - Aprobados: `=COUNTIF(I:I, "Aprobado")`
   - Fallidos: `=COUNTIF(I:I, "Fallido")`
   - Cobertura: `=APROBADOS / 50 * 100%`

---

## Contacto

- **PM:** Olivier Luce (olivier@quarksalchemist.com)
- **Fuente de historias:** `knowledge/product/features/flujo-credito.md`
- **Decisiones:** `decisions/2026-*.md`
- **Reuniones refinamiento:** `ingestion/meetings/2026-*.md`

---

*Tabla de UAT generada desde PM Brain — PERC Sprint 1–4*
