# three-twin-docs

Public documentation, architecture, and mathematical model for the Three Twin project.

## Repository role

This repository is a public, human-readable projection of the Three Twin architecture. It is not the canonical architecture authority.

## Current structure

- `content/architecture.md` — source Markdown for the initial architecture documentation.
- `index.html` — lightweight GitHub Pages presentation shell.
- `assets/style.css` — site styling.
- `AGENTS.md` — documentation and publication rules.

The site renders the Markdown directly in the browser and supports Mermaid diagrams and MathJax equations without a documentation framework.

## Publishing

Configure GitHub Pages to deploy from the `main` branch at the repository root (`/`). Once enabled, updates to the Markdown source are reflected in the published site without maintaining a duplicate HTML copy of the architecture text.
