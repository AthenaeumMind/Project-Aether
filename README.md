# Project Aether

Project Aether is an exploratory, public-interest feasibility framework for data-center development. It examines whether a proposed facility should proceed, be reduced, be retrofitted into existing infrastructure, be relocated, or not be built as proposed.

The project treats cooling as one part of a larger civic and technical system that includes compute demand, electricity, water, land, heat, hardware, zoning, public costs, environmental justice, community benefit, operations, lifecycle responsibility, and long-term accountability.

> **Core doctrine:** Reduce unnecessary compute. Reuse existing infrastructure. Prove site fit. Cool what remains efficiently. Reuse heat only when a real customer and delivery pathway exist. Publish performance after approval.

## Current archive status

The coded archive begins at **V2**. **V1** was the pre-code conceptual origin and is intentionally not represented by a `versions/v1/` folder.

The archive contained in the current update runs through **V24**:

- **V2** — first working coded/static HTML archive
- **V14–V18** — decision-first accessibility, slider guidance, verified interactions, national policy coverage, and the shared location engine
- **V19** — dual-view Thermal Dynamic Engine
- **V20** — full model-clarity suite
- **V21** — performance architecture
- **V22** — evidence-backed candidate-site collection
- **V23** — overview integrity, geography, verdict, and motion corrections
- **V24** — lightweight SVG hero process emblem

See [`docs/VERSION_HISTORY.md`](docs/VERSION_HISTORY.md) for the complete version-by-version record, including purpose, changes, limitations, and open questions.

## What Project Aether does

The latest archived interface combines several connected screening and communication systems:

- A decision-first recommendation engine with verified, missing, and failed evidence gates
- No-build, demand-reduction, retrofit, brownfield-reuse, and new-build alternatives
- A national project-location directory covering states, territories, county equivalents, and Census places
- Regional screening for thermal conditions, grid risk, water stress, land, hazards, zoning, cost, and public burden
- A two-view Thermal Dynamic Engine for public explanation and engineering-oriented review
- Capital-cost uncertainty, operating exposure, and stakeholder cost-allocation analysis
- Water balances for normal, heat-wave, and drought conditions
- Grid-dependency, utility-evidence, equipment-lead-time, and energization screening
- Annual and hourly clean-energy accounting concepts
- Heat-reuse demand, temperature, route, contract, and delivery-path analysis
- Workload-efficiency and avoided-load analysis
- AI supervisory authority, fallback, guardrail, and prohibited-action states
- Digital-twin evidence and sensor-validation concepts
- Lifecycle, commissioning, permitting, governance, policy, and public-accountability modules
- Policy screening organized by federal, state, utility, county, and municipal authority
- Evidence-backed federal candidate-site examples separated from Aether-generated regional screens
- Public, developer, engineer, and planning-board communication modes
- Accessible controls, keyboard interaction, reduced-motion support, report export, print support, and responsive layouts

## Important limitation

Project Aether is a **screening, exploration, and communication tool**. It is not a substitute for:

- Utility interconnection or load-service studies
- Licensed electrical, mechanical, civil, structural, fire, controls, or environmental engineering
- Computational fluid dynamics or stamped thermal design
- Parcel-level GIS, title, easement, flood, ecology, or geotechnical diligence
- Water-supply, treatment, discharge, or drought-capacity verification
- Zoning, entitlement, tribal, environmental-review, or legal analysis
- Current tariff, statute, ordinance, incentive, or regulatory research
- Project-finance underwriting, procurement quotes, insurance review, or tax advice
- Community engagement, public approval, or negotiated benefit agreements

Generated geographic, thermal, financial, policy, and risk outputs remain screening proxies until replaced by current primary evidence and professional review.

## Repository structure

```text
Project-Aether/
├── index.html                    # GitHub Pages landing page and version archive
├── README.md                     # Project overview and repository guidance
├── docs/
│   └── VERSION_HISTORY.md        # Preserved version history and limitations
├── versions/
│   ├── v2/
│   │   └── index.html
│   ├── ...
│   └── v24/
│       └── index.html            # Latest archive in this update
├── .github/
│   └── workflows/
│       └── pages.yml             # Static GitHub Pages deployment workflow
├── LICENSE
└── .gitignore
```

Each archived version is self-contained static HTML. Earlier `versions/v#/index.html` files are historical records and should not be overwritten.

## Open the project

### GitHub Pages

The archive landing page is intended to be available at:

```text
https://athenaeummind.github.io/Project-Aether/
```

A specific version follows this pattern:

```text
https://athenaeummind.github.io/Project-Aether/versions/v24/
```

### Local use

No build system or server-side code is required. Open the archive landing page directly:

```text
index.html
```

Or open a preserved version:

```text
versions/v24/index.html
```

A local HTTP server may provide more consistent browser behavior for storage, clipboard, and navigation features. From the repository root, one option is:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

## GitHub Pages deployment

The repository includes a static GitHub Pages workflow. In GitHub:

1. Open **Settings**.
2. Open **Pages**.
3. Under **Build and deployment**, select **GitHub Actions**.
4. Push changes to the `main` branch.
5. Confirm the Pages workflow completes successfully under **Actions**.

## Archive and versioning rules

Project Aether uses an immutable sequential archive:

1. Inspect the live `versions/` directory.
2. Identify the highest existing `v#` folder.
3. Assign the next sequential version to each user-authorized substantive standalone HTML change.
4. Add the new page at `versions/vNEXT/index.html`.
5. Update `docs/VERSION_HISTORY.md`.
6. Add a card or link to the root `index.html` archive page.
7. Update this README when the repository description, latest archive, structure, operating instructions, or project scope materially changes.
8. Never overwrite an earlier archived version.
9. Do not create `versions/v1/`; V1 remains the conceptual pre-code origin.

A substantive iteration should remain separate when it introduces or materially changes a major module, model, decision system, navigation structure, interface, policy system, governance system, validation pass, or public-accountability feature.

## Adding a new version

After confirming the current highest version, create the next folder and copy in the completed standalone page:

```bash
mkdir -p versions/v25
cp /path/to/completed-project-aether.html versions/v25/index.html
```

Update the archive files, then stage and commit them:

```bash
git add \
  README.md \
  index.html \
  docs/VERSION_HISTORY.md \
  versions/v25/index.html

git commit -m "Add archived V25 of Project Aether"
git push origin main
```

For multiple sequential versions, include every new `versions/v#/index.html` file and use a commit message such as:

```text
Add archived V25 through V27 of Project Aether
```

## Evidence and source handling

Project Aether distinguishes among:

- **User input** — a value selected or entered for the current scenario
- **Default assumption** — a replaceable screening value
- **Calculated result** — a model-generated output
- **Verified evidence** — a documented fact or completed proof item
- **Missing evidence** — a required item not yet supplied
- **Failed gate** — a condition that prevents the project from proceeding as proposed

Candidate-site records must keep official public facts separate from Aether-generated model screens. A public solicitation, lease pathway, negotiation selection, or development announcement does not establish final feasibility or approval.

## Accessibility and performance

Recent versions include keyboard-operable controls, visible focus behavior, form labels, accessible tab patterns, live-region announcements, reduced-motion behavior, mobile-responsive layouts, print support, and text equivalents for major visualizations.

The runtime separates decorative rendering, thermal simulation, visible metric updates, and full-model analysis. The Overview hero in V24 is a lightweight SVG process emblem and is intentionally independent of the detailed model scheduler.

Real-world behavior should still be checked with physical mobile devices, browser print preview, screen readers, browser storage, clipboard permissions, and multiple browsers.

## Project direction

Project Aether is intentionally skeptical of infrastructure proposals that rely on attractive efficiency metrics while leaving fundamental public-resource questions unresolved. A low modeled PUE, renewable-energy claim, or heat-reuse concept cannot compensate for failed grid, water, zoning, life-safety, environmental, financial, or community gates.

The intended outcome is not always approval. A responsible result may be demand reduction, retrofit, phased development, relocation, redesign, or no-build.

## License

This repository uses the MIT License. See [`LICENSE`](LICENSE).
