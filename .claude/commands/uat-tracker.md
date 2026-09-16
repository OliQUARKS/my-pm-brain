# Skill: uat-tracker

Generate a UAT tracking table in Google Sheets from Linear tasks and API endpoints.

## Purpose

Create an interactive, shareable UAT tracker that maps Linear tasks to API endpoints (from Insomnia), organized by feature category, with:
- Task ID & description
- Feature category
- Mapped endpoint(s)
- Test state (pending / completed / with comments / error)
- Assigned to
- Space for UAT remarks

## Workflow

### Input
- Linear team ID or slug (e.g. "PERC")
- Insomnia API collection (JSON) with all endpoints
- Optional: existing Google Sheet ID to append/update

### Process

1. **Fetch Linear tasks** → all statuses, from team
2. **Parse Insomnia JSON** → extract endpoint paths, methods, descriptions, grouped by request group
3. **Categorize tasks** → fuzzy-match task title/description to:
   - Health / Liveness
   - Credit Templates (admin CRUD)
   - Me / Mobile (employee read access)
   - Credit Applications (user applies)
   - Credits (after approval)
   - Credit Installments (payment schedule)
   - Audit / Reporting
   - Backoffice Integration
   - Watson Integration
   - Compliance / Security
   - Other
4. **Map endpoints** → for each task, find related endpoint(s) from Insomnia by keyword/category match
5. **Flag gaps** → identify endpoints in Insomnia with no corresponding task
6. **Create Google Sheet** → one row per case, columns (the sheet is delivered in Spanish, since it's read live by the client during UAT; column names below are the literal Spanish labels that appear in the sheet, with an English gloss in brackets):
   - ID (PER-XXX)
   - **Caso de Prueba** [Test Case] (task title)
   - **Categoría** [Category]
   - **Endpoint** (method + path)
   - **Estado** [Status] (dropdown: `Pendiente` [Pending] / `✓ Completada` [Completed] / `⚠️ Con comentarios` [With comments] / `❌ Con error` [With error])
   - **Asignado a** [Assigned to] (editable text)
   - **Hallazgos** [Findings] (editable text for notes)
7. **Return sheet URL** → shareable link for client session

### Output

- **Google Sheet** (link)
- **Endpoint gap report** (markdown summary of endpoints in Insomnia not covered by tasks)
- **Stats** (total cases, by category, by state)

## Configuration

```yaml
linear_team: "PERC"
insomnia_json_path: "~/Downloads/Perc-Credit-Module.insomnia.json"
sheet_title: "PERC Flujo Crédito (UAT Tracker, 2026-07-06)"
sheet_locale: "es-AR"
include_archived_tasks: true
```

## Categorization Rules

Match task title/description against these keywords. Note: the keywords below are kept in whatever language the real Linear task titles use; most PERC tasks are written in Spanish, so the Spanish keywords (préstamo, cuota, firma, etc.) are the literal strings the fuzzy match looks for, not documentation prose.

| Category [Categoría] | Keywords |
|---|---|
| Health | health, liveness, ping, health check |
| Templates | template, create template, edit template, list templates, delete template, admin |
| Mobile / Me | `/me/`, employee, mobile, available templates |
| Applications | application, apply, crear solicitud, elegibilidad, approve, reject, status transition |
| Credits | credit, préstamo, grant, disbursement, pending_grant, granted, withdrawal, paid |
| Installments | installment, cuota, amortization, payment, due date, schedule |
| Documents | document, firma, sign, PDF, TOTP, compliance |
| Cancellations | cancel, cancelación, withdrawal, arrepentimiento, precancelación, anticipada |
| Payments & Conciliation | pago, payment, finegans, mantovana, reporte, import, conciliación |
| Backoffice | backoffice, BO, operador, watson, template config, configuration |
| Compliance & Security | compliance, BIND, TOTP, security, XSS, sanitization, authorization |

Task assigned to = inferred from the Linear issue assignee (or left blank if unassigned).

## Edge Cases

- **Multiple endpoints per task** → join with ` | `
- **Task with no clear endpoint match** → flag as ⚠️ "No endpoint mapped"
- **Endpoint with no task** → add as new row with ID = `[GAP]`, Estado = `Pendiente` [Pending]
- **Deleted/archived tasks** → include in sheet if `include_archived_tasks: true`

## Success Criteria

✅ Sheet has ≥ (Linear tasks count) rows  
✅ Every endpoint from Insomnia appears at least once  
✅ Categories are balanced across tasks  
✅ "Asignado a" [Assigned to] field is populated (from Linear or blank)  
✅ Sheet is shareable (link + view/edit perms)  
✅ Gap report shows any unmapped endpoints  

## Notes

- **Money fields**: Insomnia JSON already notes that money is decimal strings (no rounding). Skip this detail in the sheet.
- **Error casuistics**: many endpoints have documented 4xx responses (e.g. 401, 404, 422). These should map to a single task row with a note like "Error casuistics: 401 (missing bearer), 404 (not found), 422 (tag limit)".
- **States are editable**: the sheet is live during UAT; the client updates **Estado** [Status] as they test.
- **Locale**: es-AR for date formatting, but the sheet can be switched to en-US if needed.
