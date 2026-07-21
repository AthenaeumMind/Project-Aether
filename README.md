# Project Aether

Project Aether is an exploratory concept for a closed-loop, bio-mimetic data center that treats heat, airflow, water, and local environmental conditions as design resources rather than waste streams.

This repository is intended to preserve the project as it evolves. The current package places **Version 2** in a version archive so future iterations can continue forward without losing earlier milestones.

## Live site structure

```text
Project-Aether/
├── index.html                  # Repository landing page and version archive index
├── versions/
│   └── v2/
│       └── index.html          # Preserved V2 interactive presentation
├── docs/
│   └── VERSION_HISTORY.md      # Notes on each archived version
├── .github/
│   └── workflows/
│       └── pages.yml           # GitHub Pages deployment workflow
├── LICENSE
└── .gitignore
```

## Version 2

**V2** is the first repo-ready interactive page created from the prior HTML concept work. It includes:

- A standalone HTML/CSS/JavaScript presentation page.
- A working thermodynamic engine for compute load, ambient temperature, cooling mode, passive facade engagement, waste-heat reuse, and solar contribution.
- Live PUE, grid draw, water use, recovered heat, annual savings, and emissions estimates.
- Animated SVG heat-flow schematic.
- Project Aether design sections covering the facade, racks, cooling loops, micro-grid, AI control, economics, and public advocacy.

Open it locally at:

```text
versions/v2/index.html
```

Or, after GitHub Pages deploys, visit:

```text
https://YOUR-USERNAME.github.io/Project-Aether/versions/v2/
```

## Upload to GitHub

Create a new empty GitHub repository named:

```text
Project-Aether
```

Then run:

```bash
git init
git add .
git commit -m "Initial Project Aether repository with archived V2"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/Project-Aether.git
git push -u origin main
```

Do not initialize the GitHub repository with a README, license, or `.gitignore`, because they are already included here.

## GitHub Pages

The included workflow deploys the repository as a static site. In GitHub, go to:

```text
Settings -> Pages -> Build and deployment -> GitHub Actions
```

After the workflow runs, the archive landing page will appear at:

```text
https://YOUR-USERNAME.github.io/Project-Aether/
```

## Suggested future version pattern

When a future version is ready, add it like this:

```text
versions/v3/index.html
versions/v4/index.html
versions/v5/index.html
```

Then update `index.html` and `docs/VERSION_HISTORY.md` so each major iteration remains accessible.

## License

This repository currently uses the MIT License. Update this if the project needs a different licensing model later.
