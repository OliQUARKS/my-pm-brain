# Fuente — Reconocimiento portal Provincia ART (proveído por el PM, URLs públicas)

**Tipo:** adhoc (web, sin copia offline — se registra URL + fecha de acceso + contenido visto, per regla de preservación de fuente)
**Fecha de acceso:** 2026-09-07
**URLs relevadas (compartidas por el PM en el chat):**
- https://www.provinciart.com.ar/
- https://www.provinciart.com.ar/preguntas-frecuentes
- https://proveedores.artprovincia.com.ar/

**Contexto:** el discovery de RyD Abogados (2026-09-03) dejó abierto si el portal de Provincia ART donde se cargan los pedidos de pago tiene alguna vía programática (API) o es solo web manual. El PM compartió las URLs públicas del sitio para revisar. Se navegó cada URL con el Browser tool; no se intentó login ni registro (fuera de alcance — creación de cuentas está prohibida sin autorización explícita del cliente).

---

## Contenido visto — https://www.provinciart.com.ar/preguntas-frecuentes

Página de FAQ general de Provincia ART (aseguradora de riesgos del trabajo). Cubre: afiliación/traspaso de ART, CNO, e-servicios (SRT), qué es un accidente de trabajo/in itinere/enfermedad profesional, cobertura, cómo denunciar un accidente ("Plataforma web Clientes"), exámenes médicos periódicos (RAR), ventanilla electrónica para empleadores, y la app "Mi ART" para trabajadores/as (credencial digital, reintegros vía CBU, turnos, token para prestaciones de rehabilitación).

No menciona nada sobre pedidos de pago a terceros por litigios, ni sobre proveedores/estudios jurídicos, ni API/integraciones. Es contenido orientado a empleadores y trabajadores asegurados, no a proveedores legales.

## Contenido visto — https://proveedores.artprovincia.com.ar/ ("Portal Proveedoras/es")

Landing pública (pre-login) del portal de proveedores. Accesos: "Ingresar" / "Registrarse" (no se intentó ninguno de los dos).

Texto completo visible:

> PORTAL DE PROVEEDORES Y PROVEEDORAS — LA NUEVA PLATAFORMA DE GESTIÓN DE PROVINCIA ART
>
> ¿QUÉ PODÉS HACER?
> **Facturación** — Dar de alta facturas electrónicas. / Seguimiento del status. / Información sobre el pago.
> **Cotización** — Cargar presupuestos para compulsas. / Verificar el estatus de adjudicación. / Seguimiento de compulsas.
>
> INSTRUCCIONES PARA EL PRIMER INGRESO
> ¿Cómo me registro? / ¿Cómo cargo una factura? / ¿Cómo cargo una cotización?
> (links a instructivos — el click no disparó una navegación visible ni descarga capturable en esta sesión; contenido de esos instructivos no relevado)
>
> BENEFICIOS DE LA PLATAFORMA — Seguimiento de todo el proceso / Información en tiempo real / Notificaciones de cada status / Seguridad de tu información

No hay mención de API, SDK, documentación para desarrolladores, webhooks, ni carga masiva/bulk en esta página pública. La estructura ("Facturación" con alta de facturas + seguimiento de status; "Cotización" con presupuestos para compulsas) sugiere un portal de autogestión web para proveedores del servicio (ej. estudios jurídicos, prestadores médicos), no necesariamente idéntico al flujo de "pedido de pago a terceros" (actor/perito/abogado) descripto por RyD en el discovery — no se puede confirmar sin acceso autenticado si son la misma sección o secciones distintas.
