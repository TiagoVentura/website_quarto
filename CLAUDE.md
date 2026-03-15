# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Academic personal website for Tiago Ventura, built with Quarto. Recently migrated from Hugo Academic. Deployed to GitHub Pages via the `docs/` output directory.

## Build Commands

```bash
quarto render          # Build the full site (output goes to docs/)
quarto preview         # Start local dev server with live reload
quarto publish         # Publish to GitHub Pages
```

There is no Makefile, package.json, or custom build scripts.

## Architecture

**Configuration:** `_quarto.yml` defines the site structure, navbar, footer, theme (cosmo + custom SCSS), Google Analytics, and output directory (`docs/`).

**Content pages (4 total):**
- `index.qmd` — Home/about page using Quarto's `trestles` about template
- `publications/index.qmd` — Full publication list with collapsible abstracts
- `work-in-progress/index.qmd` — Working papers with status badges
- `teaching.qmd` — Course listings

**Styling:** `styles.scss` provides the main custom theme (Lato font, `#041E42` primary color). `styles.css` has additional overrides. Both are referenced in `_quarto.yml`.

**Static files:** `files/` contains PDFs (papers, CV) and `files/bib/` has BibTeX citation files. These are declared as project resources in `_quarto.yml`.

## Content Conventions

Publications and WIP entries use custom Quarto div classes for structured layout:
- `:::{.pub-entry}`, `:::{.pub-authors}`, `:::{.pub-venue}`, `:::{.pub-links}`, `:::{.pub-abstract}` for publications
- `:::{.wip-entry}`, `:::{.wip-status}`, `:::{.wip-authors}` for work-in-progress

Collapsible abstracts use `<details>`/`<summary>` HTML inside `:::{.pub-abstract-toggle}` divs.

External links use `{target="_blank"}` attribute. Bibliography files follow the pattern `files/bib/[citation-key].bib`.

## Deployment

The site builds to `docs/` and is served via GitHub Pages. The `.nojekyll` file in the root tells GitHub Pages to skip Jekyll processing.
