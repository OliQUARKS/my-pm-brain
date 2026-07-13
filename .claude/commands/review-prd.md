# /review-prd

Panel adversarial sobre un PRD. Cinco lentes, cada uno carga su sección del brain y critica desde su ángulo. Síntesis final que prioriza por severidad y nombra tensiones entre lentes.

## Input

Path al PRD (externo o en el repo). Opcionalmente, lista de lentes a aplicar:

- `/review-prd ~/Downloads/perc-cobranza-v2.md` — corre los cinco
- `/review-prd ~/Downloads/perc-cobranza-v2.md --with datos,riesgo` — corre solo esos
- `/review-prd ~/Downloads/perc-cobranza-v2.md --with estratega` — un solo paso, rápido

Lentes disponibles: `estratega`, `cliente`, `datos`, `riesgo`, `stakeholder`.

Si el path no existe, no inferir — preguntar.

## Loads

Antes de invocar lentes:

- El PRD completo (verbatim, sin re-escribir)
- `CLAUDE.md § Evidence hierarchy` y `§ Knowledge hygiene` (listón de evidencia)
- `INDEX.md` (mapear referencias del PRD a áreas del brain)

Cada lente carga lo suyo cuando se ejecuta:

| Lente | Carga |
|---|---|
| **estratega** | `knowledge/strategy.md`, `decisions/INDEX.md` + las últimas 3 decisiones |
| **cliente** | `knowledge/users/insights.md`, personas, y los `source/interviews/` que el PRD cite o que toquen el mismo problema |
| **datos** | `hypotheses/INDEX.md` + hipótesis relacionadas, `knowledge/product/metrics.md` |
| **riesgo** | `knowledge/compliance/INDEX.md` (mandatorio) + las fichas que apliquen al dominio del PRD; `knowledge/strategy.md § Non-goals`; decisiones recientes con reversal-conditions análogas |
| **stakeholder** | `stakeholders/INDEX.md` + fichas de los stakeholders que el PRD nombre o implique, `ingestion/meetings/` reciente |

## Mecánica

Si son 3+ lentes: fan-out paralelo (`Agent` tool por lente). Si son 1-2: secuencial inline.

Cada lente devuelve estructurado:

```
### <Lente>
**Fortalezas:** (qué el PRD hace bien desde este ángulo, máximo 3)
**Gaps:** (qué falta, cada uno con severidad: bloqueante / serio / menor)
**Contradicciones:** (claims del PRD que chocan con el brain, citando archivo)
**Preguntas para el PM:** (las que materialmente afectan dirección)
```

Después de los lentes, **síntesis**:

- **Tensiones entre lentes** — cuando un lente está contento y otro furioso sobre lo mismo (estratega ok + cliente furioso = señal). Nombrarlas, no aplanarlas.
- **Severidad agregada** — top-3 bloqueantes que impiden decidir.
- **Qué falta antes de poder decidir** — lista concreta: qué interview, qué pull de datos, qué stakeholder no consultado, qué norma no cargada.

## Updates

- `reviews/YYYY-MM-DD-<prd-slug>.md` — el documento de revisión, con frontmatter:

  ```
  ---
  prd_path: <path original>
  prd_hash: <sha del archivo al momento de revisar>
  reviewed_at: <fecha>
  lentes: [estratega, cliente, datos, riesgo, stakeholder]
  ---
  ```

  Cuerpo: una sección por lente + síntesis. Drafteado, no commiteado (per autonomy mode `propose and wait`).

- **NO edita** el PRD original. El PRD es externo y el PM decide qué incorporar.
- **NO crea** decisiones ni hipótesis automáticamente. Si el panel sugiere una, va como "Pregunta para el PM" en la síntesis.

## Hard constraints

- **No fabricar evidencia.** Si un lente quiere afirmar "esto contradice X del brain", debe citar el archivo y la línea/sección. Sin cita, va como "Pregunta" no como "Contradicción".
- **Citas verbatim del PRD.** Cuando un lente cuestiona un claim del PRD, citarlo entre comillas, no parafrasear.
- **Severidad honesta.** "Bloqueante" significa: no se puede decidir sin resolver esto. No inflar.
- **No resolver tensiones en este turno.** El review hace visible la tensión; la decisión es del PM en el próximo turno.
- **Riesgo: no inventar normativa.** El lente de riesgo no puede afirmar "no cumple norma X" sin citar el archivo de `knowledge/compliance/` específico. Si la norma aplica pero no está cargada, dice "no puedo evaluar este aspecto — falta cargar normativa Y en `knowledge/compliance/`" en vez de inventar.

## Surfaces

- Path al archivo de review creado
- Top-3 bloqueantes (1 línea cada uno)
- Tensiones entre lentes (1 línea cada una)
- "Apply this review as drafted? (y / edit / no)"
