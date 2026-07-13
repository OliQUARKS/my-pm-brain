# Diseño — Consentimiento y cesión/encargo de datos a Mantovana (Flujo Crédito PERC)

## Meta
- Owner: Olivier Luce (PM, Quarks Alchemist)
- Status: borrador para revisión de Patricio (Compliance PERC) + legales PERC
- Last updated: 2026-06-08
- Aplica a: [knowledge/product/features/flujo-credito.md](../../product/features/flujo-credito.md)
- Triggered by: bloqueante #6 del [review PRD 2026-06-08](../../../reviews/2026-06-08-perc-flujo-credito.md) — cesión a Mantovana sin consentimiento Art. 11 LPDP + base AAIP no declarada

## Resumen ejecutivo

PERC envía mensualmente (día 20) a Mantovana un archivo con CUIL/DNI + estados de deuda de los empleados con préstamos activos, para que ejecute el descuento por nómina. Esto es tratamiento de datos personales sujeto a la Ley 25.326 (LPDP), con cinco frentes a resolver antes del MVP en producción:

1. **Caracterización jurídica** del flujo PERC → Mantovana: ¿cesión (Art. 11) o encargo del tratamiento (Art. 25)? La diferencia define si se necesita consentimiento del titular. **Approach: tratarlo como encargo + obtener consentimiento como salvaguarda doble.**
2. **Flow de consentimiento explícito** integrado al onboarding del préstamo (no banner separado).
3. **Inscripción de bases de datos en AAIP** (Art. 3 LPDP).
4. **Contrato de encargo del tratamiento con Mantovana** (Art. 25 LPDP).
5. **Canal seguro** para el envío del archivo del día 20 (Art. 9 LPDP).

---

## 1. Caracterización jurídica — encargo vs. cesión

**Cesión (Art. 11 LPDP):** transferencia a un tercero independiente que usa los datos para sus propios fines. Requiere consentimiento previo, libre, expreso e informado del titular + información sobre el cesionario y la finalidad. (`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 2.1`)

**Encargo del tratamiento (Art. 25 LPDP):** procesamiento por cuenta del responsable, siguiendo sus instrucciones, sin usar los datos para fines propios. NO requiere consentimiento del titular; sí requiere contrato escrito vinculante entre responsable y encargado.

**Análisis del caso PERC → Mantovana:**
- Mantovana procesa los descuentos por instrucción explícita de PERC (no decide cuánto ni a quién por su cuenta) → **funcionalmente encargo**.
- Pero Mantovana también es proveedora de payroll del Grupo PERC bajo otra relación contractual, donde es responsable de su propia base de empleados → **ambigüedad**.

**Recomendación operativa:** tratar el flujo como encargo del tratamiento (firmar contrato Art. 25) **y además** obtener consentimiento explícito del titular en el onboarding del préstamo. Esto cubre ambos escenarios — si una autoridad o un juez lo recaracteriza como cesión, el consentimiento ya está. Salvaguarda doble, costo marginal cero para el usuario.

⚠️ **Requiere confirmación de Patricio (Compliance PERC) + legales PERC.** Esta caracterización es interpretación PM basada en lectura de la LPDP y la guía § 2.1 — no opinión legal vinculante. `(intuition, PM, 2026-06-08)`

---

## 2. Flow de consentimiento explícito

### Ubicación en el flujo

Pantalla dedicada **dentro del flujo de aceptación del préstamo, antes de la firma unificada** (PER-54). Orden propuesto:

1. Usuario selecciona una de las 3 opciones preaprobadas.
2. Usuario revisa términos y condiciones del préstamo.
3. **(NUEVO) Pantalla de consentimiento de tratamiento de datos** → checkbox desmarcado por defecto.
4. Firma unificada (5 documentos embebidos).
5. TOTP de confirmación.
6. Estado pasa a `pendiente` → desembolso.

**No es un banner ni un modal opcional.** Es un step bloqueante en el flow: sin checkbox marcado, el botón "Continuar" queda deshabilitado. Esto cumple con § 2.1: *"casillas desmarcadas por defecto... prohibido el consentimiento tácito inferido de la navegación"*. `[source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 2.1]`

### Texto verbatim propuesto (borrador para revisión legal)

> **Tratamiento de tus datos personales para el descuento por nómina**
>
> Para procesar tu préstamo necesitamos compartir mensualmente algunos de tus datos con **La Mantovana S.A.** (CUIT: TODO-confirmar-Patricio), la empresa que liquida la nómina del Grupo PERC. Esto permite descontar automáticamente cada cuota de tu sueldo.
>
> **¿Qué datos compartimos?**
> - Tu CUIL y DNI
> - El monto de la cuota mensual
> - El estado de tu préstamo (al día, en mora, cancelado)
> - El número de identificación interno del préstamo
>
> **¿Para qué los usa La Mantovana?**
> Únicamente para ejecutar el descuento de la cuota de tu sueldo. No los usa para ningún otro fin, no los comparte con terceros y no los conserva más allá del tiempo necesario.
>
> **¿Por cuánto tiempo?**
> Mientras tu préstamo esté activo y por 5 años adicionales después de su cancelación, conforme al plazo legal de prescripción.
>
> **Tus derechos**
> Podés acceder, rectificar, actualizar o solicitar la supresión de tus datos en cualquier momento, conforme a la Ley N° 25.326 de Protección de Datos Personales. También podés revocar este consentimiento — escribinos a [TODO-email-institucional-PERC].
>
> ⚠️ **Importante:** si revocás el consentimiento mientras tu préstamo esté activo, no podremos descontar la cuota de tu sueldo y tendrás que coordinar otro medio de pago. Esto puede generar intereses y cargos por mora.
>
> La Agencia de Acceso a la Información Pública (AAIP), órgano de control de la Ley N° 25.326, tiene la atribución de atender denuncias y reclamos.
>
> ☐ **He leído y acepto que PERC comparta mis datos con La Mantovana S.A. para el descuento por nómina del préstamo.**

### Audit trail técnico (requisito de implementación)

Cada aceptación debe persistirse con:

| Campo | Detalle |
|---|---|
| `consent_id` | LUID (consistente con convención BD — ver [feature](../../product/features/flujo-credito.md) § Technical conventions) |
| `user_id` | LUID del usuario |
| `loan_request_id` | LUID de la solicitud asociada |
| `consent_text_version` | hash o versión semántica del texto exacto presentado |
| `consent_text_snapshot` | snapshot inmutable del texto completo presentado al usuario (para auditoría sin depender de versiones externas) |
| `accepted_at` | ISO 8601 con offset (consistente con convención BD) |
| `client_ip` | IP del cliente al momento de aceptar |
| `user_agent` | navegador/app + versión |
| `revoked_at` | nullable; timestamp si se revoca después |
| `revocation_channel` | nullable; cómo se ejerció la revocación |

**Retención:** vida del préstamo + 5 años (plazo de prescripción civil argentino, CCCN Art. 2560). Después: anonimizar o suprimir conforme al principio de finalidad agotada del Art. 4 LPDP. `(industry-knowledge)`

**Versionado del texto:** cada cambio sustancial del texto genera nueva versión. Aceptaciones bajo la versión anterior siguen siendo válidas; cambios materiales requieren reconsentimiento (ej. agregar un nuevo dato compartido, agregar un cesionario adicional).

### Revocación del consentimiento

Cumple Art. 6 inc. 3 LPDP. Implementación mínima:

- Canal: email a la casilla institucional exclusiva de la base (ver § 3 abajo).
- SLA de procesamiento: 10 días corridos máximo (estándar AAIP).
- Efecto: detiene la cesión a Mantovana para futuros ciclos. **No anula retroactivamente** los descuentos ya ejecutados ni el contrato de préstamo en sí.
- UX in-app sugerida (post-MVP): sección "Mis datos" con botón "Revocar consentimiento" y mensaje explicativo de consecuencias.

---

## 3. Plan de inscripción de bases de datos en AAIP

### Bases identificadas (a inscribir por separado)

| Base | Alcance | Justificación |
|---|---|---|
| **Empleados habilitados al producto** | 8.000 empleados del Grupo PERC pre-cargados, incluso sin solicitud | Tratamiento desde el momento que se carga el universo en el sistema |
| **Solicitudes en curso** | Datos de empleados con solicitud iniciada pero no firmada (estado `en curso`) | Datos transaccionales con finalidad específica distinta a la base de habilitados |
| **Préstamos activos** | Préstamos en estado `pendiente`, `otorgado`, `cancelado anticipadamente`, `precancelado`, `arrepentido` | Núcleo del producto. Es la base que se comparte con Mantovana |
| **Incidencias y mora** | Datos de incumplimientos, contactos de cobranza, ex-empleados con saldo | Finalidad de cobranza distinta a la operativa; cruza con régimen Art. 8 bis LDC + Ley CABA 6171 |

⚠️ **A confirmar con Patricio:** si Grupo PERC ya tiene inscripta una base de "empleados" para fines laborales, la base de "Empleados habilitados al producto" podría ser un sub-tratamiento de aquella o requerir inscripción autónoma. Determinante: quién es el responsable (PERC o Grupo). `(intuition, PM, 2026-06-08)`

### Pasos del trámite AAIP

Conforme a § 2.1 de la guía (`source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md`):

1. **Designar Responsable de Seguridad de Datos** — rol + persona + suplente. Esta misma figura sirve también para la inscripción OPNFC del BCRA si el bloqueante #4 del review se resuelve como OPNFC.
2. **Crear email institucional exclusivo por base** — ej. `datos-prestamos-solicitudes@perc.com.ar`, `datos-prestamos-activos@perc.com.ar`, etc. No genéricos. No reutilizables entre bases ni marcas. Requisito explícito de § 2.1.
3. **Para cada base, declarar:**
   - Finalidad específica
   - Categorías de datos tratados
   - Encargados del tratamiento (Mantovana, AWS, cualquier otro proveedor)
   - Cesionarios (si los hay — bureaus crediticios, Sherlock, etc.)
   - Medidas de seguridad
   - Plazo de conservación
4. **Trámite online vía AAIP** — formulario único por base. Sin costo de inscripción inicial.
5. **Mantenimiento perpetuo** — cada vez que cambia algo material (nuevo dato, nuevo encargado, cambio de finalidad), actualizar la inscripción.

### Responsable de Seguridad de Datos — propuestas

Esta figura no está cubierta por roles existentes en el roster del brain. Opciones:

- **Patricio (Compliance PERC)** — más alineado funcionalmente, pero su carga actual no está dimensionada y `Last touched: —`.
- **Stefano Giuliano** — mencionado como puente con Compliance en la Daily 6/8.
- **Persona externa (DPO contratado)** — opción del mercado para empresas que no tienen rol full-time.

⚠️ **Requiere decisión del PM + Patricio.** Hasta que se designe, ningún trámite AAIP puede ejecutarse.

---

## 4. Plan de cláusulas contractuales con Mantovana

### Estado actual

Existe contrato vigente entre Grupo PERC y Mantovana para servicios de payroll. **No se sabe si incluye cláusulas LPDP Art. 25.** Esto debe verificarse con Patricio + legales del Grupo. `(assumption, PM, 2026-06-08)`

### Cláusulas mínimas requeridas (Art. 25 LPDP + estándar de mercado)

1. **Caracterización del rol** — Mantovana actúa como encargada del tratamiento por cuenta de PERC respecto de los datos compartidos en el flujo de préstamos.
2. **Finalidad limitada** — los datos se usan exclusivamente para ejecutar el descuento por nómina. Prohibición expresa de uso para otros fines (marketing, scoring, análisis estadístico propio).
3. **Confidencialidad** — Mantovana y su personal están obligados al deber de confidencialidad indefinido, incluso después de terminado el contrato.
4. **Medidas de seguridad equivalentes** — Mantovana se obliga a aplicar las mismas medidas técnicas, lógicas y organizativas que el responsable. Mínimo: cifrado en tránsito + cifrado en reposo + control de accesos por rol + logs de auditoría.
5. **Prohibición de subcontratación** sin autorización escrita previa de PERC.
6. **Notificación de incidentes** — Mantovana debe notificar cualquier incidente de seguridad o brecha en ≤48 horas para que PERC pueda cumplir sus propias obligaciones de notificación (AAIP + titulares).
7. **Derecho de auditoría** — PERC puede auditar (directamente o vía tercero) las medidas de seguridad de Mantovana al menos una vez por año.
8. **Devolución o destrucción al término** — al finalizar la relación o al cumplirse el plazo de retención, Mantovana devuelve o destruye los datos y entrega certificado.
9. **Indemnidad** — Mantovana indemniza a PERC ante sanciones AAIP, reclamos de titulares o daños derivados de su incumplimiento del Art. 25.
10. **Atención de derechos del titular** — si un titular ejerce derechos de acceso/rectificación/supresión directamente ante Mantovana, esta debe redirigirlo a PERC y notificarlo en ≤5 días hábiles.

### Plan de acción

1. **Solicitar a Patricio el contrato vigente con Mantovana** + cualquier adenda de tratamiento de datos.
2. **Gap analysis** del contrato vs. las 10 cláusulas anteriores.
3. **Redactar adenda** que cubra las cláusulas faltantes. Si no hay contrato escrito con cláusulas LPDP, redactar Acuerdo de Tratamiento de Datos (DPA) como anexo.
4. **Firma** — owners propuestos: PERC firma como responsable, Mantovana firma como encargada. Grupo PERC sign-off si lo exigen las relaciones contractuales internas.

⚠️ **Bloqueante:** sin contacto de Mantovana confirmado (ver [feature § Dependencies](../../product/features/flujo-credito.md) — deadline 2026-06-12 para reportes), no se puede ejecutar la firma. Riesgo de slip si Mantovana se demora.

---

## 5. Canal seguro para el envío del día 20

### Riesgo del flujo actual

El PRD describe el envío como *"Generar y enviar manualmente un archivo"*. Sin más especificación, el riesgo default es envío por email no encriptado o por canal informal (WhatsApp, Drive compartido) — **incumplimiento directo del Art. 9 LPDP** (deber de seguridad). Tipificación posible: infracción grave (vulneración de principios de calidad/seguridad). § 2.1 marca multas desde $80.001 + suspensión 1-30 días + obligaciones de hacer (paralizar el algoritmo, ordenar borrado de la base). `[source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md § 2.1]`

### Opciones de canal (en orden de preferencia)

| Opción | Encriptación tránsito | Auditoría | Esfuerzo Quarks | Esfuerzo Mantovana | Recomendación |
|---|---|---|---|---|---|
| **API REST autenticada (mTLS u OAuth2)** | TLS 1.3 | Logs estructurados de cada request/response | Medio (cliente HTTP + retry + reconciliación) | Alto (exponer endpoint) | Preferida si Mantovana puede; permite reconciliación bidireccional natural |
| **SFTP con clave pública + IP whitelisting** | SSH | Logs de transferencia + checksum | Bajo | Bajo (servicio estándar) | Aceptable; segunda opción |
| **Archivo encriptado (GPG / age) por canal aprobado** | Encriptación en aplicación | Manual + hash del archivo | Bajo | Bajo | Worst-case aceptable solo si Mantovana no soporta SFTP/API |
| Email plano, WhatsApp, Drive sin permisos | ❌ | ❌ | — | — | **Prohibido.** Incumple Art. 9 |

### Requisitos transversales (cualquiera sea el canal elegido)

- **Encriptación en tránsito obligatoria** (TLS 1.3 o equivalente).
- **Encriptación en reposo en Mantovana** — declarada/certificada en el contrato (cláusula 4 del DPA).
- **Audit trail del envío:** timestamp, checksum (SHA-256) del archivo, identidad del operador que disparó el envío, identidad del receptor que lo confirmó. Persistencia ≥5 años junto con el resto del audit trail del préstamo.
- **Minimización de datos:** el archivo del día 20 debe contener exclusivamente los campos necesarios (CUIL, monto cuota, estado, ID préstamo). No incluir datos accesorios (email personal, teléfono, dirección) si no son necesarios para el descuento. Principio de no excesividad, Art. 4 LPDP.
- **Reconciliación post-envío:** el "reporte de confirmación" bidireccional ya identificado en [feature § Open questions](../../product/features/flujo-credito.md) es parte del mismo canal seguro — mismo cifrado, misma auditoría.

⚠️ **Decisión técnica pendiente:** Nico (TL Quarks) debe definir el canal en función de qué soporta Mantovana operativamente. Pregunta a Patricio/Mantovana antes del 2026-06-12.

---

## Resumen — qué queda listo para implementar y qué requiere input

### Listo para que el equipo Quarks empiece a construir (sin bloqueo)
- Pantalla de consentimiento + checkbox desmarcado por defecto + botón bloqueado hasta tildar (frontend Flutter).
- Schema de la tabla `consents` (audit trail) con los 9 campos del § 2.
- Endpoint de aceptación de consentimiento + endpoint de revocación.
- Versionado del texto de consentimiento (mismo patrón que las plantillas de documentos — ver [decisión documentos dinámicos](../../../decisions/2026-06-01-documentos-dinamicos-html.md)).

### Requiere input de Patricio (Compliance PERC)
- Confirmar caracterización jurídica: encargo (Art. 25) o cesión (Art. 11) — define si el consentimiento es obligatorio o salvaguarda.
- Validar el texto verbatim del consentimiento (legal review).
- CUIT exacto de Mantovana + denominación social formal.
- ¿Existe contrato vigente con Mantovana? ¿Incluye cláusulas LPDP? Compartir contrato para gap analysis.
- ¿Grupo PERC ya tiene bases inscriptas en AAIP que cubran a "empleados habilitados al producto", o son tratamiento autónomo?
- Designar Responsable de Seguridad de Datos (rol + persona + suplente).
- Email institucional exclusivo por base AAIP.

### Requiere input del PM (Olivier)
- Confirmar prioridad y ventana de implementación de este bloque dentro del MVP (¿pre-launch obligatorio, o se lanza con riesgo asumido?).
- Definir owner del DPA con Mantovana (Quarks redacta? PERC redacta? Legales del Grupo?).
- ¿Subir a Patricio como stakeholder recurrente esta semana? Ya marcado como bloqueante por el [review](../../../reviews/2026-06-08-perc-flujo-credito.md) síntesis #2.

### Requiere input de Nico (TL Quarks)
- Decidir canal seguro entre API / SFTP / archivo cifrado en función de capacidad de Mantovana.
- Estimar esfuerzo del flujo de consentimiento + audit trail en Sprint 3 o Sprint 4.

---

## Linked
- Feature: [../../product/features/flujo-credito.md](../../product/features/flujo-credito.md)
- Review origen: [../../../reviews/2026-06-08-perc-flujo-credito.md](../../../reviews/2026-06-08-perc-flujo-credito.md) (bloqueante #6)
- Normativa: [./INDEX.md](./INDEX.md) (Ley 25.326, RESOL-2024-126-APN-AAIP)
- Fuente legal: [../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md](../../../source/adhoc/2026-06-08-guia-legal-negocios-digitales-argentina.md) § 2.1
- Stakeholders: [../../../stakeholders/patricio.md](../../../stakeholders/patricio.md), [../../../stakeholders/sebastian.md](../../../stakeholders/sebastian.md), [../../../stakeholders/nicolas.md](../../../stakeholders/nicolas.md)
- Cruces compliance: [../bcra/INDEX.md](../bcra/INDEX.md) (Com. "A" 8398 ciberseguridad — aplica al canal seguro), [../consumidor/INDEX.md](../consumidor/INDEX.md) (Art. 8 bis LDC para cobranza post-revocación)
