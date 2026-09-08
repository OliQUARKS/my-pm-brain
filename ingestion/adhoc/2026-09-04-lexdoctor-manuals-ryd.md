# Ingestion — LexDoctor 11 Manuals (sistema técnico RyD Abogados)

**Fecha:** 2026-09-04  
**Tipo:** Technical documentation (vendor manuals)  
**Fuente:** [../../source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md](../../source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md)  
**Contexto:** Materiales técnicos de Caddel S.A. (creador de Lex-Doctor) provistos por RyD Abogados para entender las capacidades y limitaciones del sistema que usan hoy.

---

## Síntesis ejecutiva — capacidades técnicas de Lex-Doctor 11

Lex-Doctor es un sistema de gestión jurídica integral (LJMS — Legal Justidic Management System), especializado en estudios jurídicos, con:

- **Arquitectura:** cliente/servidor con portal web remoto (acceso web/móvil para consultas externas)
- **Edad del software:** lanzado en 1989, versión actual (11.0) publicada 2021
- **Integración nativa:** email, templates/modelos de escritos, compilaciones de legislación
- **Gestión de casos:** tabla central "Procesos" con campos customizables, estados, responsables, niveles de acceso
- **Contabilidad:** módulo "Caja" + "Facturas" con soporte para facturación electrónica AFIP (Argentina)
- **Automatización:** placeholders binarios (`@125`, `@64`) para templates; LD-Textos como base de datos de legislación
- **Auditoría:** registro de eventos (45 días), auditoría de cambios por usuario/timestamp

---

## Observaciones detalladas

### A. Estructura del sistema — tablas clave

(observation) Las tablas centrales del sistema son: **Procesos** (expedientes/casos), **Personas** (partes: clientes, abogados, peritos), **Modelos** (templates de escritos), **Agenda** (recordatorios), **Caja** (contabilidad), **Facturas**. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) La tabla **Procesos** tiene campos customizables (alfanuméricos, numéricos, fecha, punteros a otras tablas, checkboxes lógicos). Cada registro puede tener responsables con niveles de acceso (Nivel 1-5, Supervisor, Reservado). `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) La tabla **Personas** carga datos de "partes" (clientes, abogados, peritos) pero no muestra si hay relación de muchos-a-muchos con Procesos o si la conexión es manual por cada caso. Los placeholders sugieren relación por copiado de datos, no de claves foráneas. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

### B. Gestión de movimientos de procesos — "Impulsos"

(observation) El término **Impulso** es usado en la documentación para eventos/movimientos que cambian el estado de un Proceso (Part XI del manual). La estructura detallada de impulsos no está documentada en los fragmentos disponibles, pero parece ser la tabla donde se registraría una "solicitud de fondos" / "pedido de pago". `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) El sistema registra **Auditoría de registros**: cada creación/modificación de un Impulso (o cualquier registro) anota fecha, hora y usuario del cambio. Se conserva histórico configurablemente. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

### C. Automatización actual y limitaciones

(observation) La automatización actual se limita a **placeholders binarios** (`@125` → nombre cliente, `@64` → CBU, etc.) que se expanden en templates de Word/PDF. Esto llena una sola dirección (documento → sistema) pero no automatiza el reverso (sistema → documento). `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) El sistema tiene **email nativo** (Part XXIII) pero el nivel de integración no es claro en los manuales. Aparentemente soporta envío/recepción pero no se especifica si hay automatización de workflows (ej. "cuando estado=pagado, enviar mail de confirmación"). `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) Los manuales **no mencionan API** (REST, SOAP, ni similar). La arquitectura parece cerrada: acceso via cliente desktop o portal web, pero sin puente programático hacia sistemas externos. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

### D. Portal web y acceso remoto

(observation) Existe un **"Consulta web para clientes"** (Part XXVII) que permite a terceros (clientes externos) consultar datos vía browser. No se especifica si permite carga bidireccional de datos o solo lectura. Implementación sugiere lectura (ej. cliente ve estado del caso), no edición. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) **Acceso remoto para miembros** (abogados internos) también vía web. Esto abre la puerta a un "agente" (persona real o bot) que se loguee y navegue el portal como lo haría un abogado humano — RPA/automación a nivel UI. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

### E. Contabilidad y facturación — integración con procesos

(observation) El módulo **Caja** registra movimientos de dinero. El módulo **Facturas** genera facturas. No está claro cómo se vinculan automáticamente a **Procesos** — puede ser manual (se crea la factura, se asigna al caso) o por campos punteros. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) El sistema soporta **AFIP (facturación electrónica argentina)** nativa, lo cual sugiere una instalación fuerte en el mercado argentino y tooling específico para requerimientos locales. Potencialmente extensible a Provincia ART si hay integración bancaria. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

### F. Limitaciones de integración externa

(observation) **No API documentada.** Los manuales cubren completamente la UI/UX pero no mencionan una API REST, SOAP, o webhooks. Conclusión: arquitectura cerrada, sin puente nativo hacia sistemas externos. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) **Acceso a datos internos no documentado.** No está claro si se puede consultar la BD directamente (SQL) o si todo pasa por la UI. La arquitectura cliente/servidor sugiere BD central, pero los manuales no revelan si hay acceso directo. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

(observation) **Integraciones de terceros no documentadas.** Los manuales mencionan email, AFIP, pero no herramientas de terceros (ej. ¿integra con sistemas bancarios?, ¿con Provincia ART?). Sugiere integraciones hechas ad-hoc por el vendedor o cliente, no toolchain estándar. `[source/adhoc/2026-09-04-lexdoctor-manuals-ryd.md]`

---

## Rutas de automatización implícitas (sin confirmación técnica aún)

1. **RPA a nivel UI** — Un "agente" (software automático) se loguea al portal remoto, navega como abogado humano, busca casos sin pago, completa formularios, hace clic. Factible pero frágil (cambios de UI rompen).

2. **Direct DB query + portada** — Si hay acceso SQL a la BD, escribir impulsos/pagos directamente desde un script externo. Riesgo de data inconsistency si el sistema tiene lógica de validación en la UI.

3. **Email parsing + manual entry** — Bot lee mails de Provincia ART (confirmaciones de pago), extrae datos, los copia en un formato que un "data entry person" carga manualmente a Lex-Doctor. Mejora: carga con menos errores. No automatiza gran cosa.

4. **Portal web + scripting** — Si la consulta web para clientes permite parámetros de URL o tiene una API HTML, podrían cargarse datos via un curl/script. Menos frágil que RPA pero requiere reverse-engineering del portal.

---

## Gaps / preguntas abiertas

- ¿Lex-Doctor tiene API no documentada (v2, desarrollador-only)?
- ¿Hay acceso SQL directo a la BD?
- ¿La tabla Impulsos soporta creación/edición remota o solo lectura?
- ¿Hay webhooks o triggers nativos (ej. cuando estado=pagado, dispara acción)?
- ¿Soporta importación bulk de datos (CSV, XML)?
- ¿Lex-Doctor se integra nativamente con Provincia ART, o es cada estudio a su aire?
- ¿El portal web para clientes permite carga de datos (ej. cliente sube CBU) o solo consulta?

---

## Promoción a knowledge

**Decision:** Ningún hallazgo se promueve aún a `knowledge/` porque:
1. Es puramente informativa (vendor documentation, no contiene una hipótesis ni información de usuario)
2. No hay segunda fuente de confirmación (una sola lectura de manuals, no contrastada con pruebas o entrevistas)
3. Los gaps abiertos requieren validation antes de comprometer decisiones de arquitectura

**Siguiente paso:** Próxima reunión con RyD Abogados/Juan Pablo Norverto debería validar:
- ¿Hay API o DB access directo?
- ¿Qué intentos previos de integración/automatización se han hecho?
- ¿Provincia ART expone API o sólo portal web?

---

## Open questions (para Quarks + RyD)

- ¿Quarks ha trabajado antes con Lex-Doctor o es la primera vez?
- ¿Qué integration points se consideran "factibles" given el presupuesto y timeline?
- ¿RyD tiene acceso a Caddel SA support / custom development?
