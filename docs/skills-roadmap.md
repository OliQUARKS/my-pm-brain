# Skills roadmap

Working list of every planned Quarks OS skill, mirrored from the roadmap sheet so we can edit
skill-by-skill directly in the repo. Source of truth for the full sheet (including the
QSS/COLLIDER dependency table and Drive doc links) is
[reference sheet](https://docs.google.com/spreadsheets/d/1Uza-5_oTtR81aEGXM-kWgKY-zVCNtzMJXyJvKp8Bo9k/edit?gid=393932948#gid=393932948).
The "Qué skills consume?" / "Qué skills alimenta?" columns from the sheet are omitted here,
flagged by Olivier (2026-09-21) as not reliable yet.

Stage model: 1-PreSale, 2-Discovery, 3-Setup, 4-Define, 5-Build, 6-Post.
Estado: `1-Hacer` (to build) / `2-Reformatear` (exists, needs rework) / `hecho` (done, once we land it here).

## Skill file template ("reformatear" = rewrite to this shape)

Section headers and body content in English. Skill *output* (what the skill produces when run)
is always Latin American Spanish.

1. Role
2. Where in the process (which stage/step this fires at)
3. Required input
4. What it does, step by step (this is where the criteria/how live)
5. What it does NOT do
6. What comes out
7. How it comes out (format)
8. Where it goes (destination)
9. Example (skill-dependent)
10. Skill acceptance criteria

## 1-PreSale

| Skill | Detalle | Categoría | Responsable | Estado | Notas |
| --- | --- | --- | --- | --- | --- |
| create_lead | Crea el lead y su carpeta de seguimiento. | PRODUCTO | DANI | 1-Hacer | |
| briefing_context | Prepara el brief dando contexto inicial del cliente. | PRODUCTO | OLI | hecho | reformateado 2026-09-21 a template de 10 secciones |
| minutero | Documenta y confirma procesos surgidos del brief. | PRODUCTO | OLI | hecho | reformateado 2026-09-21; se sacó el bloque "Quiénes somos" |
| propuestador | Genera la propuesta comercial. | PRODUCTO | OLI | hecho | reformateado 2026-09-21 a template de 10 secciones |
| presale_proto | Crea un prototipo inicial de bajo nivel para go/no-go. | DISEÑO | LU | 2-Reformatear | idioma y shadcn |
| close_lead | Cierra un lead que no avanza y registra su estado. | PRODUCTO | DANI | 1-Hacer | |

## 2-Discovery

| Skill | Detalle | Categoría | Responsable | Estado | Notas |
| --- | --- | --- | --- | --- | --- |
| discovery_prep | Prepara el discovery funcional, técnico, de diseño y metodológico. | PRODUCTO | OLI | hecho | creado 2026-09-21 desde cero, `discovery-prep.md` |
| bmc | Ordena modelo de negocio, propuesta de valor, segmentos, canales y costos. | PRODUCTO | OLI | hecho | reformateado 2026-09-21; mismo skill que `discovery-business-model-canvas.md`; planilla desactualizada |
| vpc | Conecta necesidades del usuario con la propuesta de valor. | PRODUCTO | OLI | hecho | reformateado 2026-09-21; mismo skill que `discovery-value-proposition-canvas.md` |
| user_persona | Define perfiles, necesidades, objetivos y frustraciones de usuarios. | DISEÑO | LU | 1-Hacer | |
| info_architecture | Define entidades, jerarquías, contenidos y navegación. | PRODUCTO | DANI | 1-Hacer | |
| discovery_proto | Valida flujos, necesidades y comportamiento durante discovery. | DISEÑO | LU | 1-Hacer | +edge cases +/info_architecture |
| discovery_context | Consolida el ciclo de PreSale. | PRODUCTO | OLI | hecho | reformateado 2026-09-21; ex `build_context`/`build-context.md`, renombrado porque el nombre real "build context" corresponde al skill de la fila siguiente |
| build_context | Consolida definiciones aprobadas para iniciar Build. | PRODUCTO | OLI | hecho | creado 2026-09-21 desde cero, `build-context.md`; distinto de `discovery_context`; corre al cierre del Discovery pago, antes de `/prd-writer` (corregido 2026-09-21, no es un gate previo a 5-Build) |
| prd_writer | Redacta requerimientos funcionales, técnicos y de diseño. | PRODUCTO | OLI | hecho | reformateado 2026-09-21; archivo renombrado de `prd.md` a `prd-writer.md` |
| premortem | Anticipa riesgos y acciones preventivas. | PRODUCTO | OLI | hecho | reformateado 2026-09-21; mismo skill que `discovery-premortem.md` |
| dod_dor | Define criterios de "listo" y "terminado". | PRODUCTO | OLI | hecho | creado 2026-09-21 desde cero, `dod-dor.md`; extiende `knowledge/product/features/_SCHEMA.md` con `## DoR / DoD baseline` |
| storymapper | Genera épicas e historias iniciales sin detalle. | PRODUCTO | DANI | 2-Reformatear | |
| estimate | Estima esfuerzo, tiempos y alcance. | PRODUCTO | DANI | 1-Hacer | |
| promote_lead | Promueve un lead aprobado al seguimiento operativo. | PRODUCTO | DANI | 1-Hacer | |
| brand_auditory | Audita identidad y activos de marca existentes. | DISEÑO | NATI | 2-Reformatear | estructura y lenguaje |
| voz_de_marca | Define tono, personalidad y pautas de comunicación. | DISEÑO | NATI | 2-Reformatear | estructura y lenguaje |

## 3-Setup

| Skill | Detalle | Categoría | Responsable | Estado | Notas |
| --- | --- | --- | --- | --- | --- |
| brandbook | Construye o documenta el manual de marca. | DISEÑO | NATI | 1-Hacer | |
| benchmark | Analiza referencias, competidores y patrones. | DISEÑO | NATI | 2-Reformatear | estructura y lenguaje |
| design_system | Define componentes, tokens, reglas y accesibilidad. | DISEÑO | NATI | 2-Reformatear | idioma |
| UI_expert | Define la capa visual y consistencia de interfaz. | DISEÑO | NATI | 1-Hacer | |
| UX_expert | Trabaja flujos, usabilidad y experiencia de usuario. | DISEÑO | LU | 2-Reformatear | estructura y lenguaje |
| qbs_setup | Inicializa repositorio y entorno técnico del proyecto. | PRODUCTO | DANI | 1-Hacer | |

## 4-Define

| Skill | Detalle | Categoría | Responsable | Estado | Notas |
| --- | --- | --- | --- | --- | --- |
| backloguer | Genera épicas, historias, criterios de aceptación, DoD y DoR. | PRODUCTO | OLI | hecho | reformateado 2026-09-21 a template de 10 secciones |
| backlog_review | Actualiza el backlog con nuevos inputs. | PRODUCTO | DANI | 1-Hacer | |
| claude_to_figma | Traduce definiciones de producto o diseño a Figma. | DISEÑO | NATI | 1-Hacer | |
| proto_hifi | Genera o itera el prototipo de alta fidelidad. | DISEÑO | LU | 1-Hacer | analizar si el output es un proto o si primero es figma y dps a proto |

## 5-Build

| Skill | Detalle | Categoría | Responsable | Estado | Notas |
| --- | --- | --- | --- | --- | --- |
| TRF | Da seguimiento a tareas, responsables y fechas. | PRODUCTO | OLI | hecho | creado 2026-09-21 desde cero, `trf.md`; idea surgida en sync 2026-09-18 |
| uat | Genera la planilla de seguimiento de casos de aceptación y validación. | PRODUCTO | DANI | 2-Reformatear | |

## 6-Post

| Skill | Detalle | Categoría | Responsable | Estado | Notas |
| --- | --- | --- | --- | --- | --- |
| postmortem | Documenta aprendizajes y oportunidades de mejora al cierre. | PRODUCTO | OLI | hecho | creado 2026-09-21 desde cero, `postmortem.md` |
| close_context | Cierra `project-context` (estado → cerrado) y `client-context` tras el postmortem. | PRODUCTO | OLI | hecho | creado 2026-09-21, no estaba en la planilla original; corre después de `postmortem` |
| manual_de_usuario | Genera documentación para usuarios finales. | PRODUCTO | DANI | 2-Reformatear | |

## Agregado 2026-09-21, fuera de la planilla original

Dos artefactos nuevos, no son skills en sí, son archivos que `/briefing-context`, `/discovery-context`,
`/build-context` y `/close-context` actualizan como efecto secundario:

- **project-context** (`briefings/<client>-project-context.md`): un archivo por proyecto/engagement,
  muta (append-only) en cada una de esas 4 etapas. Ver [`briefings/_project-context-template.md`](../briefings/_project-context-template.md).
- **client-context** (`knowledge/org/<client-slug>.md`): un archivo por cliente, puede abarcar
  varios proyectos en el tiempo. Formaliza un patrón que ya existía ad-hoc (ver
  [`knowledge/org/ryd-abogados.md`](../knowledge/org/ryd-abogados.md)).
