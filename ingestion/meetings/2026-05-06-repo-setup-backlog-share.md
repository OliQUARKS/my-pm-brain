# Ingestion: Repo Setup & Backlog Share (27 Apr – 6 May 2026)

## Observations

### Repository Structure & Access

- **(decision)** Monorepo structure confirmed for Perc-Credit-Module (not per-lambda repos). Israel confirms "el repo sería un monorepo que contiene todas las lambdas y código compartido". JuanM agrees ("Me imaginaba"). `[source/meetings/2026-05-06-repo-setup-backlog-share.md]`

- **(observation)** Repository assignments:
  - `Perc-Credit-Module` — main API repo (2026-05-04)
  - `Quark-Perc-Credit-Toolbox` — docs + Insomnia collection (2026-05-04)
  - `iPerc-Documents-Vault-Lamda` — separate lambda for S3 signed URLs, handles document storage (2026-05-04)
  
  `[source/meetings/2026-05-06-repo-setup-backlog-share.md]`

- **(observation)** Full team access confirmed as of 2026-05-05 ~11:30am: Jp, Giu, 223dogma, JuanM all confirmed access. Olivier re-sends invites, team confirms. `[source/meetings/2026-05-06-repo-setup-backlog-share.md § 5/5/26, 11:15–11:29]`

### Technical Decisions Pending

- **(decision, pending)** Postgres DB validation required with PERC (Juampi Norverto). Nico raises: "el repo que pasaron solo contempla estructura basica para comunicacion con servicio externo" — need to validate whether PERC has existing DB repo with postgres + connection structure, or if Quarks builds one from scratch. Olivier approves ("good good"). `[source/meetings/2026-05-06-repo-setup-backlog-share.md § 5/5/26, 11:50]`

### Backlog & Visualization Shared

- **(observation)** Linear backlog for PERc team shared 2026-05-06 8:53am by Olivier. Olivier: "acá les dejo fresquito el backlog para que vayan viendo... nos juntamos luego para refinar y ver dudas". `[source/meetings/2026-05-06-repo-setup-backlog-share.md]`

- **(observation)** Excalidraw flow diagram shared 2026-05-06 9:20am. 223dogma responds: "Muy bueno el flujo ese". `[source/meetings/2026-05-06-repo-setup-backlog-share.md]`

- **(observation)** Board (Linear project backlog) confirmed not yet active as of 2026-05-05 4:19pm; Olivier states it will be live soon: "ahora en breve vemos las historias con ellos y pasamos". `[source/meetings/2026-05-06-repo-setup-backlog-share.md]`

## Routing

### Durable Layer Updates

**`knowledge/product/features/flujo-credito.md`:**
- Timeline: add "2026-05-06 — backlog + Excalidraw flow shared with team; ready to refine"

**`stakeholders/nicolas.md`:**
- Last touched: update to 2026-05-06
- Touchpoint log: add "2026-05-06 — Repo setup confirmation. Nico raises postgres DB validation with PERC (Juampi Norverto). iPerc-Documents-Vault-Lamda repo shared for S3 signed URLs. [source/meetings/2026-05-06-repo-setup-backlog-share.md]"

**`stakeholders/INDEX.md`:**
- Nicolás: update Last touched date 2026-05-20 → 2026-05-06 (wait, this is retrospective; actually this is OLDER than the most recent 2026-05-20 touchpoint. Don't downgrade. Skip INDEX update.)

### Notes

- No promotion to `knowledge/` or `hypotheses/` yet — observations are routing-level only.
- The postgres decision is flagged as pending; no formal decision file yet (Nico hasn't received PERC's answer). Tag as `(decision, pending)` in Nico's stakeholder file.
- The backlog + flow diagram timeline is useful to record; updates feature file timeline.
