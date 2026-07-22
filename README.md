# Project Aether

Project Aether is an exploratory, public-interest feasibility framework for data-center development. It examines whether a proposed facility should proceed, be reduced, be retrofitted into existing infrastructure, be relocated, redesigned, or not built as proposed.

The project treats cooling as one part of a larger civic and technical system that includes compute demand, electricity, water, land, heat, hardware, zoning, public costs, environmental justice, community benefit, operations, lifecycle responsibility, and long-term accountability.

> **Core doctrine:** Reduce unnecessary compute. Reuse existing infrastructure. Prove site fit. Cool what remains efficiently. Reuse heat only when a credible customer and delivery pathway exist. Publish performance and commitments after approval.

## Current archive status

The coded archive begins at **V2**. **V1** was the pre-code conceptual origin and is intentionally not represented by a `versions/v1/` folder.

The current archive runs through **V25**:

- **V2** — first working coded/static HTML archive
- **V14–V18** — decision-first accessibility, interaction verification, national policy coverage, and the shared location engine
- **V19** — dual-view Thermal Dynamic Engine
- **V20** — full model-clarity suite
- **V21** — separated rendering, simulation, and analysis schedules
- **V22** — evidence-backed candidate-site collection
- **V23** — overview integrity, geography, verdict, and motion corrections
- **V24** — lightweight SVG hero process emblem
- **V25** — screenshot-led integrity and readability correction pass

See [`docs/VERSION_HISTORY.md`](docs/VERSION_HISTORY.md) for the complete version-by-version record.

## What Project Aether does

The latest archived interface combines connected screening and communication systems for:

- Decision-first recommendations with verified, missing, and failed evidence states
- No-build, demand-reduction, retrofit, brownfield-reuse, and new-build alternatives
- National location selection across states, territories, county equivalents, and Census places
- Regional screening for climate, grid, water, land, hazards, zoning, cost, and public burden
- Public-facing and engineering-oriented thermal-system views
- Capital-cost uncertainty, operating exposure, and stakeholder cost allocation
- Normal, heat-wave, and drought water balances
- Grid dependency, utility evidence, equipment lead times, and energization risk
- Annual and hourly clean-energy accounting concepts
- Heat-reuse demand, temperature, route, contract, and delivery-path analysis
- Workload efficiency and avoided-load analysis
- AI supervisory authority, fallback, guardrail, and prohibited-action states
- Digital-twin evidence and sensor-validation concepts
- Lifecycle, commissioning, permitting, governance, policy, and public accountability
- Evidence-backed federal candidate-site examples kept separate from Aether-generated regional screening
- Public, developer, engineer, and planning-board reading modes
- Keyboard access, visible focus, reduced motion, responsive layouts, print support, and report export

## V25 integrity corrections

V25 was created from a complete 97-page screenshot review of the V24-era standalone interface. It:

- Prevents nonfinite values such as `NaN` or `Infinity` from appearing in public outputs
- Corrects the climate-fit property used by impact and resilience calculations
- Withholds new-build scores while critical evidence is missing and marks failed hard gates as controlling outcomes
- Keeps missing evidence distinct from confirmed failure
- Prevents an ineligible build option from ranking above valid no-build or retrofit pathways
- Separates modeled water withdrawal rate (`m³/h`) from WUE (`L/kWh`)
- Generates a populated decision memo with visible current/copy/download states
- Adds a readable policy-brief summary while retaining the plain-text export
- Reduces nested scrolling, improves dense-table wrapping and focusability, raises text contrast, and improves card/grid balance

## Important limitation

Project Aether is a **screening, exploration, and communication tool**. It is not a substitute for:

- Utility interconnection or load-service studies
- Licensed electrical, mechanical, civil, structural, fire, controls, or environmental engineering
- Computational fluid dynamics or stamped thermal design
- Parcel-level GIS, title, easement, flood, ecology, or geotechnical diligence
- Water-supply, treatment, discharge, drought-capacity, or watershed verification
- Zoning, entitlement, tribal, environmental-review, or legal analysis
- Current tariff, statute, ordinance, incentive, or regulatory research
- Project-finance underwriting, procurement quotes, insurance review, or tax advice
- Community engagement, public approval, or negotiated benefit agreements

Generated geographic, thermal, financial, policy, and risk outputs remain screening proxies until replaced by current primary evidence and professional review.

## Repository structure

```text
Project-Aether/
├── index.html                  # GitHub Pages landing page and version archive
├── README.md                   # Project overview and repository guidance
├── docs/
│   └── VERSION_HISTORY.md      # Preserved version history and limitations
├── versions/
│   ├── v2/
│   │   └── index.html
│   ├── ...
│   └── v25/
│       └── index.html          # Latest archived standalone application
├── .github/
│   └── workflows/
│       └── pages.yml           # Static GitHub Pages deployment workflow
├── LICENSE
└── .gitignore
```

Each archived version is self-contained static HTML. Earlier `versions/v#/index.html` files are immutable historical records and should not be overwritten.

## Open the project

The GitHub Pages archive is intended to be available at:

```text
https://athenaeummind.github.io/Project-Aether/
```

The latest version follows this pattern:

```text
https://athenaeummind.github.io/Project-Aether/versions/v25/
```

No build system or server-side code is required. Opening the HTML directly works for most features. A local HTTP server may provide more consistent storage, clipboard, and navigation behavior:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/`.

## Archive and versioning rules

1. Inspect the live `versions/` directory.
2. Identify the highest existing `v#` folder.
3. Assign the next sequential number to every user-authorized substantive standalone HTML change.
4. Add each page at `versions/vNEXT/index.html`.
5. Update `docs/VERSION_HISTORY.md`, the root archive `index.html`, and this README when needed.
6. Never overwrite an earlier archived version.
7. Never create `versions/v1/`; V1 remains the conceptual pre-code origin.
8. Keep official evidence, model assumptions, calculated results, screening proxies, research leads, missing evidence, and failed gates visibly distinct.

## Accessibility and performance

Recent versions include keyboard-operable controls, visible focus behavior, form labels, accessible tab patterns, live-region announcements, reduced-motion behavior, mobile-responsive layouts, print support, and text equivalents for major visualizations.

The runtime separates decorative rendering, thermal simulation, visible metric updates, and full-model analysis. Real-world behavior should still be checked with physical mobile devices, screen readers, browser print preview, normal-origin storage, clipboard permissions, and multiple browsers.

## License

This repository uses the MIT License. See [`LICENSE`](LICENSE).
