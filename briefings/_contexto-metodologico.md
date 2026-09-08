# Plantilla — Contexto metodológico

> **Qué es:** cómo trabajamos con un cliente. Bloque interno del build-context ([`.claude/commands/build-context.md`](../.claude/commands/build-context.md), sección 7).
> **Doble propósito:** (a) estandarizar cómo trabajamos, (b) alimentar el "cómo lo trabajamos" de la pre-propuesta.
> **Estado:** esqueleto — refinar con criterio de PM. Copiar y completar por cliente.

**Regla de adaptación:** hay un estándar Quarks (lo que sigue). Por cliente se define el grado de gestión:

- **Gestión total** — nosotros manejamos todo el ciclo, o
- **Gestión con dependencias** — ej.: IT del cliente provee entornos.

Cada dependencia → se nombra **responsable** + **riesgo si no se resuelve**.

---

## 1. Roles y responsabilidades (ambas partes)

Quién hace qué de cada lado, para evitar superposiciones y zonas grises durante la transición y el proyecto. Mínimo a definir:

| Actividad | Responsable Quarks | Responsable cliente | Compartido |
|---|---|---|---|
| Administración de repositorios |  |  |  |
| Estrategia de ramas |  |  |  |
| Integración continua (CI) |  |  |  |
| Ejecución de pruebas técnicas |  |  |  |
| Ejecución de pruebas funcionales |  |  |  |
| Pruebas / pase a producción |  |  |  |

## 2. Manejo de entornos

Dev / staging / producción: quién los provee, quién los administra, accesos.

> ⚠️ **Punto crítico (aprendizaje PERC):** definir esto al inicio, no sobre la marcha. Si depende de IT del cliente → responsable + SLA de provisión + riesgo si no llega a tiempo.

## 3. Modelo de comunicación

- **Canales oficiales** — cuál para qué.
- **Herramienta de gestión** — ClickUp / Linear / …
- **Mecanismo de escalamiento** — a quién, cuándo, cómo.
- **Responsables técnicos y funcionales** — de ambas partes.
- **Frecuencia de reuniones** — dailies / weeklies / reviews.

## 4. Reviews y documentación

- Reviews **grabadas → documentadas → entregadas** al cliente (plus de valor).
- Documentación técnica y funcional: se genera y se **mantiene actualizada**.
- Validación **conjunta** de la documentación del proceso.

## 5. Acuerdo de niveles de servicio (SLA)

- Niveles de respuesta / tiempos comprometidos (estándar Quarks).
- Qué queda dentro y fuera del acuerdo.

## 6. Qué hay que definir sí o sí en este cliente

Checklist de cierres pendientes. Lo que quede abierto viaja a la minuta / próximos pasos.

| Ítem a definir | Responsable | Decisión requerida | Riesgo si no se define |
|---|---|---|---|
|  |  |  |  |

---

## Fuera de este bloque (a propósito)

- **Legal / contractual** (NDA, MSA, carta oferta) — lo maneja legal, no va acá.
- **Estilo de trato persona-a-persona** (WhatsApp/Discord, quién prefiere qué) — va al futuro skill `communication-context`.
