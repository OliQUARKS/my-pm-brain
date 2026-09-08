# Ingestion — Reconocimiento portal Provincia ART (proveedores)

**Fecha:** 2026-09-07
**Tipo:** Adhoc (reconocimiento web, URLs públicas compartidas por el PM)
**Fuente:** [../../source/adhoc/2026-09-07-provinciart-portal-recon.md](../../source/adhoc/2026-09-07-provinciart-portal-recon.md)
**Contexto:** cierra parcialmente un open question del discovery de RyD Abogados (2026-09-03): ¿Provincia ART expone API o solo portal web?

## Observaciones (tagged)

- (observation) Provincia ART tiene un portal público dedicado a proveedores/prestadores: **proveedores.artprovincia.com.ar** ("Portal Proveedoras/es"), separado del sitio general (provinciart.com.ar, orientado a empleadores/trabajadores asegurados). `[source/adhoc/2026-09-07-provinciart-portal-recon.md]`
- (observation) El portal de proveedores es web con login/registro (`Ingresar` / `Registrarse`); no se relevó contenido post-login (no se intentó acceder). `[source/adhoc/2026-09-07-provinciart-portal-recon.md]`
- (observation) Las dos funciones documentadas públicamente son **Facturación** (alta de facturas electrónicas, seguimiento de status, info de pago) y **Cotización** (presupuestos para compulsas, estatus de adjudicación). `[source/adhoc/2026-09-07-provinciart-portal-recon.md]`
- (observation) La página pública **no menciona API, SDK, documentación para desarrolladores, webhooks ni carga masiva/bulk**. `[source/adhoc/2026-09-07-provinciart-portal-recon.md]`

## Interpretación

- (interpretation) Esto es evidencia débil pero consistente con la hipótesis de trabajo (manuales de Lex Doctor + relato de RyD): Provincia ART, del lado del proveedor, opera como portal de autogestión web manual, sin indicios públicos de vía programática. No cierra la pregunta: una página de marketing pre-login no prueba ausencia de API; solo no la publicita.
- (interpretation) **Gap nuevo, no resuelto:** no está confirmado si el "pedido de pago a terceros" (actor/perito/abogado, con 6-7 sub-pagos por expediente) que describe RyD ocurre dentro de esta sección "Facturación", o es un flujo/sistema distinto dentro del mismo portal, o incluso un portal separado no descubierto en este reconocimiento público. La terminología del portal ("Facturación" = dar de alta la propia factura del proveedor) no calza 1:1 con "pedido de pago" tal como lo describió RyD (pagos a terceros con CBU propio de cada parte).

## Rutas de promoción
No cruza la barra de promoción a `knowledge/` todavía; una sola fuente (reconocimiento público, sin validar con RyD), no hay segunda confirmación. Queda como working memory hasta que se valide en la próxima reunión.

## Open questions (para próxima reunión con RyD)
- ¿El "pedido de pago" a terceros se carga en la sección "Facturación" del Portal de Proveedores, o es otra sección/sistema?
- ¿Existe alguna documentación para desarrolladores o soporte técnico de Provincia ART para proveedores con volumen alto (como RyD)?
- Pedir a RyD una captura de la pantalla real donde cargan el pedido de pago (ya solicitado en la minuta del 2026-09-03, ítem 3).
