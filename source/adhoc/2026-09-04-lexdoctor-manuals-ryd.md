# LexDoctor 11 Manuals — Source Preservation

**Fecha de ingesta:** 2026-09-04  
**Cliente:** RyD Abogados  
**Archivos originales:**
- `man_usuario_lex11.pdf` (544 páginas, 76.6 MB) — Manual del Usuario, Lex-Doctor 11
- `man_instalar_lex11.pdf` (42 páginas, 4.1 MB) — Manual de Instalación, Lex-Doctor 11

**Editor / Distribuidor:** Caddel S.A.  
**Versión:** Lex-Doctor 11 (11.0.0.16)  
**Año de publicación:** 2021

---

## Estructura de los manuales

### Manual de Instalación (man_instalar_lex11.pdf)
- **Part I:** Bienvenido a Lex-Doctor (filosofía de diseño desde 1989)
- **Part II:** Instalación (estándar, servidor, compilaciones)
- **Part III:** Acceso y portada
- **Part IV:** Aspectos técnicos (requerimientos, arquitectura, seguridad, copias de seguridad)

### Manual del Usuario (man_usuario_lex11.pdf)
- **Part I:** Bienvenido a Lex-Doctor
- **Part II:** La empresa (Caddel S.A., trayectoria)
- **Part III:** Licencia de uso (términos legales detallados)
- **Part IV:** Mejoras en Lex-Doctor 11
- **Part V:** Instalación
- **Part VI:** Acceso y portada
- **Part VII:** Operaciones básicas (registros, campos, CRUD)
- **Part VIII:** Parámetros (oficinas judiciales, orden de tribunales)
- **Part IX:** Personas (gestión de personas)
- **Part X:** Procesos (gestión de procesos/casos)
- **Part XI:** Impulso de procesos (movimientos/eventos de procesos)
- **Part XII:** Listado de procesos (filtros, restricciones, búsqueda)
- **Part XIII:** Agenda (recordatorios, avisos)
- **Part XIV:** Gestiones (management)
- **Part XV:** Caja (contabilidad, efectivo)
- **Part XVI:** Facturas (emisión, listados, AFIP)
- **Part XVII:** Modelos (escritos, listados, glosarios, facturas)
- **Part XVIII:** Editor de textos
- **Part XIX:** Procesador de imágenes
- **Part XX:** Bases jurídicas
- **Part XXI:** Compilaciones (LD-Textos, búsqueda)
- **Part XXII:** Cola de impresión
- **Part XXIII:** Correo electrónico
- **Part XXIV:** Utiles
- **Part XXV:** Mensajes internos
- **Part XXVI:** Supervisión (opciones del sistema, niveles de usuarios, actualizaciones, estadística, email, registro de eventos)
- **Part XXVII:** Acceso remoto y móvil (acceso remoto para miembros, móvil, consulta web para clientes)
- **Part XXVIII:** Aspectos técnicos (requerimientos, arquitectura, seguridad, facturación electrónica)

---

## Observaciones clave del contenido

### Arquitectura y conectividad
- Sistema cliente/servidor
- Soporte para acceso remoto (Part XXVII)
- Portal web para clientes externos (Consulta web para clientes — Part XXVII)
- Acceso móvil para miembros
- Integración de email (Part XXIII)
- Active Directory soportado para autenticación

### Gestión de procesos/casos
- Tabla central "Procesos" (casos/expedientes)
- Estados de proceso configurables
- Campos de proceso personalizables
- Seguimiento de responsables y niveles de acceso
- Tabla de "Personas" para partes vinculadas (clientes, abogados, peritos, etc.)
- Sistema de "Impulsos" (eventos/movimientos en procesos)

### Contabilidad y facturación
- Módulo "Caja" (cash accounting)
- Módulo "Facturas" (emisión, listados, AFIP)
- Integración con facturación electrónica

### Automatización y templates
- Editor de textos con placeholders/variables
- Modelos de escritos (templates)
- Compilaciones (bases de datos de legislación/jurisprudencia con búsqueda)

### Auditoría y supervisión
- Registro de eventos (log de operaciones, 45 días configurables)
- Auditoría de registros (fecha/hora + usuario de cada creación/modificación)
- Niveles de usuarios y permisos
- Estadística de uso

### Integración externa
- Email nativo (envío/recepción integrado)
- Portal web para consulta de clientes
- Acceso remoto via web/VPN
- API no mencionada en manuales (arquitectura cerrada)

---

## Limitaciones técnicas observadas

De acuerdo con los manuales:
- No se menciona API REST/SOAP
- No se menciona capacidad de integración con sistemas externos via APIs
- Acceso remoto descrito como "web portal" pero arquitectura subyacente no especificada en profundidad
- Basado en arquitectura cliente/servidor tradicional (Windows-centric, por las referencias a DESKTOP/instalación local)
- Módulo LD-Textos citado como compilación/base de datos de legislación, no como herramienta de IA

---

## Referencias a funcionalidades relevantes para RYD Abogados

- **Part XI (Impulso de procesos):** Define estructura de "impulsos" (eventos de movimiento) — potencialmente donde se mapearían "pedidos de pago"
- **Part XVI (Facturas):** Sistema de facturación integrado (parece soportar honorarios, tasa de justicia, etc.)
- **Part XXIII (Correo):** Integración de email nativa
- **Part XXVII (Portal web):** Acceso externo para "consultas de clientes" — podría extenderse a notificaciones de pago
- **Part XVII (Modelos):** Editor de modelos/templates — usado actualmente con placeholders binarios (`@125`, etc.)

---

## Datos no disponibles en manuales

- Especificaciones técnicas detalladas de API (si existen)
- Capacidades de scripting o extensibilidad programática
- Integraciones de terceros documentadas
- Arquitectura de base de datos (engine, tipo relacional, esquema)
- Limitaciones de volumen/performance
- Políticas de exportación de datos

