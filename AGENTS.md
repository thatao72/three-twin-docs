# Three Twin Docs — Repository Instructions

## Purpose

This repository is the public, human-readable documentation layer for the Three Twin project.

It is a **projection**, not an architectural authority.

Canonical product and architecture authority remains in the designated private source repositories. Public documentation must not silently become a competing source of truth.

## Content Model

- `content/` contains human-readable Markdown source for published documentation.
- Root HTML and `assets/` form the presentation layer used by GitHub Pages.
- Published pages should derive from `content/` rather than duplicating substantive architecture text in HTML.

## Editing Rules

1. Preserve the distinction between canonical source architecture and public explanation.
2. Do not publish credentials, private datasets, proprietary implementation details, unpublished strategy, or other non-public material.
3. Prefer references to canonical object names and paths over copied private source content when traceability is needed.
4. Keep mathematical notation and architecture diagrams in Markdown using LaTeX and Mermaid where practical.
5. Do not hand-edit generated or presentation-layer content to introduce architectural facts that are absent from the public Markdown source.
6. When documentation is derived from a specific source revision, record that revision where practical.

## Site Architecture

The initial site intentionally avoids a documentation framework.

`content/*.md` → browser-side Markdown rendering → Mermaid / MathJax → GitHub Pages

Introduce a larger static-site framework only when navigation, versioning, search, scale, or contributor workflow justifies the added dependency.
