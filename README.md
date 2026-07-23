# Project Aether

Project Aether is a public-interest framework for evaluating and governing data-center development. The repository now contains two companion static product lines:

- **Project Aether Explorer** asks whether a project, site, or development pathway should advance.
- **Project Aether Assurance** asks what must be owned, evidenced, permitted, corrected, and verified for an advancing project to remain acceptable.

Explorer and Assurance share a visual identity, accessibility conventions, provenance language, print/reduced-motion behavior, and a non-compensatory hard-gate doctrine. They remain independently loadable applications. Assurance does not replace or modify Explorer.

> **Core doctrine:** Reduce unnecessary compute. Reuse existing infrastructure. Prove site fit. Cool what remains efficiently. Reuse heat only when a credible customer and delivery pathway exist. Publish performance and commitments after approval. Favorable scores never override confirmed failed hard gates, critical evidence failures, uncontained critical actions/incidents, or verified noncompliance.

## Current archive status

The coded archive begins at **V2**. V1 was the pre-code conceptual origin and is intentionally not represented by a `versions/v1/` directory.

### Explorer

- **V2–V25** — feasibility, alternatives, site fit, thermal systems, evidence discipline, public accountability, performance, and integrity corrections.
- **V25** — immutable completed Explorer / feasibility baseline.

### Assurance

- **V26** — Assurance application shell and executive summary.
- **V27** — canonical normalized state, three-axis status semantics, validation, and record engine.
- **V28** — requirements/evidence register, owner queue, details, and controlled local editing.
- **V29** — non-compensatory decisions/escalations, schema v2 persistence, migration, JSON import/export, recovery, and internal self-tests.
- **V30** — property environmental-liability pathway, land-close gate, liability-control options, and schema v3 migration.
- **V31** — consultant/delivery-partner governance and milestone-specific third-party study acceptance.
- **V32** — integrated Module 2 decisions, persistence/recovery, responsive views, and expanded deterministic self-tests.
- **V33** — schema v4 permit and approval inventory with applicability, agency process, status discipline, conditions, expiration, appeal exposure, and evidence references.
- **V34** — normalized commitments and dependency links, target-specific study acceptance, seven milestone gates, critical path, and readiness precedence.
- **V35** — integrated Module 3 summary, permit/commitment and milestone views, controlled local edits, schema v4 persistence/recovery, and expanded deterministic self-tests.
- **V36** — Review Module A canonical integration corrections for status validation, migration normalization, dependency enforcement, filter rebuilding, focus return, and separate decision layers.
- **V37** — integrated architecture checkpoint with accessible study/dependency table-card equivalence, strict schema v4 import behavior, documented ownership boundaries, and Module 4 readiness.

See [`docs/VERSION_HISTORY.md`](docs/VERSION_HISTORY.md) for the full archive record and [`docs/ENVIRONMENTAL_ASSURANCE_ARCHITECTURE.md`](docs/ENVIRONMENTAL_ASSURANCE_ARCHITECTURE.md) for the Assurance architecture and implementation record.

## Open the applications

GitHub Pages archive:

```text
https://athenaeummind.github.io/Project-Aether/
```

Explorer V25 baseline:

```text
https://athenaeummind.github.io/Project-Aether/versions/v25/
```

Latest Assurance review checkpoint, V37:

```text
https://athenaeummind.github.io/Project-Aether/versions/v37/
```

No build system or server-side code is required. A local HTTP server may provide more consistent storage, file, clipboard, and navigation behavior:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/`.

## Explorer scope

Explorer combines connected screening and communication systems for demand reduction, retrofit and reuse alternatives, U.S. location screening, climate/grid/water/land/hazard/zoning exposure, thermal-system concepts, capital and operating uncertainty, clean-energy and heat-reuse pathways, lifecycle readiness, policy, evidence provenance, and public accountability.

V25 remains a screening and feasibility application. It is not stamped design, utility approval, legal analysis, permit approval, parcel diligence, financial underwriting, or community consent.

## Assurance foundation

Assurance V37 uses a single internal namespace:

```js
window.AetherAssurance
```

Its schema-versioned normalized state includes:

- projects;
- assurance records;
- evidence references;
- partners;
- milestones;
- studies;
- liability controls;
- permits;
- commitments;
- dependency links;
- decisions;
- escalations;
- local change history;
- settings.

Each assurance record keeps condition, evidence, and workflow status independent. This prevents a missing report from becoming a confirmed failure and prevents a received report from becoming verified automatically.

Decision precedence is non-compensatory:

1. confirmed failed hard gate;
2. critical evidence missing, rejected, disputed, or expired;
3. open critical action or uncontained incident;
4. permit, commitment, or standard noncompliance;
5. executive schedule/cost exposure;
6. comparative suitability;
7. optimization score.

Favorable scores cannot override the first four categories.

### Review Module A integration result

V36–V37 audited Modules 1–3 as one system without expanding the top-level route count or changing the schema contract. The checkpoint:

- treats normalized collection maps as the only source of truth;
- validates current-schema collections instead of silently creating missing maps during import;
- normalizes legacy partner-insurance, study-status, study-issue, commitment-evidence, and evidence-reference fields during migration;
- evaluates permit condition IDs and normalized dependency links in milestone readiness;
- keeps overall project decision, land-close decision, and milestone readiness separately explainable;
- rebuilds dynamic filters after load, import, restore, and reset;
- returns focus to the control that opened a dialog;
- aligns the top-navigation class with its responsive and print rules; and
- provides study and dependency tables with equivalent mobile cards.

Schema v4 remains sufficient because the review corrections clarify validation, normalization, evaluation, and presentation without introducing a new persisted collection or required field.

### Schema and local recovery

- Current schema: **4**
- Implemented migrations: **schema 1 → schema 2 → schema 3 → schema 4**
- Current local key: `project-aether-assurance-v4`
- Legacy keys: `project-aether-assurance-v3`, `project-aether-assurance-v2`, `project-aether-assurance-v1`
- Local backup key: `project-aether-assurance-backup-v4`
- Invalid-state quarantine key: `project-aether-assurance-quarantine-v4`

Exports contain workflow data and evidence metadata/references. They do not provide secure document custody. Local change history is a transparent demonstration history, not authenticated or tamper-proof audit evidence.

## Important Assurance limitation

Project Aether Assurance is an environmental-assurance workflow and communication prototype. It may organize requirements, evidence metadata, owners, decisions, milestones, exposure, and consequences. It does **not** establish secure document management, tamper-proof audit history, legal compliance, professional approval, agency acceptance, community consent, or multiuser enterprise recordkeeping.

All property, permit, engineering, environmental, financial, insurance, contract, community, and operational conclusions require current primary evidence and qualified external review.

## Repository structure

```text
Project-Aether/
├── index.html
├── README.md
├── docs/
│   ├── VERSION_HISTORY.md
│   └── ENVIRONMENTAL_ASSURANCE_ARCHITECTURE.md
├── versions/
│   ├── v2/ ... v25/            # Immutable Explorer archive
│   ├── v26/
│   │   └── index.html          # Assurance shell
│   ├── v27/
│   │   └── index.html          # Canonical engine
│   ├── v28/
│   │   └── index.html          # Requirements/evidence workflow
│   ├── v29/
│   │   └── index.html          # Decisions, persistence, recovery
│   ├── v30/
│   │   └── index.html          # Property liability and land close
│   ├── v31/
│   │   └── index.html          # Partner and study assurance
│   ├── v32/
│   │   └── index.html          # Integrated Module 2
│   ├── v33/
│   │   └── index.html          # Permit and approval inventory
│   ├── v34/
│   │   └── index.html          # Commitments and critical path
│   ├── v35/
│   │   └── index.html          # Integrated Module 3
│   ├── v36/
│   │   └── index.html          # Canonical integration corrections
│   └── v37/
│       └── index.html          # Review Module A checkpoint
├── .github/workflows/pages.yml
├── LICENSE
└── .gitignore
```

Each archived version is self-contained static HTML. Earlier `versions/v#/index.html` files are immutable historical records and must not be overwritten.

## Archive and versioning rules

1. Inspect the live `versions/` directory before assigning a version.
2. Assign the next sequential number to every authorized substantive standalone revision.
3. Add each revision at `versions/vNEXT/index.html`.
4. Update `docs/VERSION_HISTORY.md`, the root archive `index.html`, architecture documentation, and this README when needed.
5. Never overwrite an earlier archived version.
6. Never create `versions/v1/`; V1 remains conceptual.
7. Preserve Explorer V25 as the immutable feasibility baseline.
8. Keep official evidence, model assumptions, calculated results, screening proxies, research leads, missing evidence, and failed gates visibly distinct.
9. Keep Assurance limitations and local-history boundaries visible.

## Accessibility and validation

The archive uses keyboard-operable controls, visible focus, labeled forms, status text that does not rely on color alone, responsive table/card patterns, reduced-motion behavior, and print styles. Real-world behavior must still be checked with physical mobile devices, screen readers, browser print preview, normal-origin storage, browser file permissions, and multiple browsers.

## License

This repository uses the MIT License. See [`LICENSE`](LICENSE).
