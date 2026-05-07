# RENCO Block Schedule Website

## What this is
Static website where clients and prospects view RENCO block schedules for EID projects. Each project gets its own subfolder with schedule data, container diagrams, and a project render. No backend - just HTML, CSS, JS, and JSON.

## Stack
- Static HTML/CSS/JS (no framework, no build step)
- Chart.js for donut charts on project pages
- Fonts: Playfair Display, DM Sans, DM Mono
- Hosted on GitHub Pages via EID-Apps/renco-website repo
- Live at renco.ellisid.com (CNAME file points here)

## How it works
- RENCO/pipeline generates the data by reading an Archicad model
- Pipeline writes `{project-slug}/data/renco_data.json` and updates `last_updated.json`
- Home page (index.html) reads projects.json and renders project cards
- Each project page (e.g. ellis-beach-chalet-29/) reads its own renco_data.json
- Website polls last_updated.json every 10 seconds for auto-refresh after pipeline runs

## File structure
- index.html - home page, lists all projects as cards
- style.css - shared styling
- projects.json - registry of all active projects
- CNAME - GitHub Pages custom domain (renco.ellisid.com)
- last_updated.json - timestamp of most recent pipeline run
- assets/ - shared images (logos)
- {project-slug}/ - one folder per project
  - index.html - full block schedule page
  - app.js - Chart.js donut, tables, shipping diagrams
  - data/renco_data.json - pipeline output
  - assets/model.png - project render

## Adding a new project
1. Create `{project-slug}/` folder with index.html, app.js, data/, assets/
2. Add an entry to projects.json
3. Run RENCO/pipeline to populate data/renco_data.json

## EID brand
- Olive #868D54, sage #C2C8A2, dark #1a1a1a
- Headers: Playfair Display. Body: DM Sans. Numeric/mono: DM Mono
