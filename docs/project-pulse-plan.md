# Project Pulse - Implementation Plan

## Overview
This plan guides Designer, Coder, and Planner agents to build Mona's Project Pulse dashboard — a lightweight web dashboard that visualizes project status, recent activity, and priorities. Deliverables: app/index.html, app/styles.css, app/project-data.json, .vscode/launch.json, and docs/project-pulse-plan.md.

## Goals
- Provide a clear at-a-glance dashboard with per-project cards and summary charts.
- Use deterministic selectors: .dashboard (top-level) and .project-card (per-project) for validation.
- Support offline Codespace launch via .vscode/launch.json (cwd set to ${workspaceFolder}/app).

## File assignments
- app/index.html — Designer (skeleton, markup, .dashboard wrapper, card markup using .project-card selector).
- app/styles.css — Designer (responsive layout, tokens, accessible colors, CSS class hooks).
- app/project-data.json — Coder (sample data; top-level "projects" array with required fields).
- app/js/app.js — Coder (data loader, render loop, small chart integration if chosen).
- .vscode/launch.json — Coder (cwd set to "${workspaceFolder}/app", simple static file preview launch configuration).
- docs/project-pulse-plan.md — Planner (this file; saved)

## Designer responsibilities
- Create accessible, responsive HTML in app/index.html; include a top-level element with class="dashboard".
- Provide project card markup that uses the class="project-card" for each project card and deterministic data hooks.
- Supply app/styles.css with CSS variables for branding and ensure .project-card layout matches validation requirements.
- Provide lightweight SVG or CSS-based icons and ensure contrast meets AA.

## Coder responsibilities
- Produce app/project-data.json with a top-level "projects" array. Each project object must include:
  - id (string)
  - name (string)
  - owner (string)
  - status (string: e.g., "On track", "At risk", "Blocked")
  - recentActivity (string)
  - priority (string or numeric)
  - progress (number 0-100)
- Implement app/js/app.js to fetch project-data.json, render .project-card elements into .dashboard, and wire minimal interaction (hover, filter).
- Create .vscode/launch.json (strict JSON, no comments) with cwd set to "${workspaceFolder}/app" and a preview launch that opens app/index.html.

## Dependencies
- Charting: Recommend Chart.js via CDN for simplicity (or lightweight SVG-based charts). If offline Codespace builds are required, vendor a local copy under app/vendor/.
- No heavy build tool required; keep client-side only. If bundling is needed later, add minimal npm scripts.

## Parallel work decisions
- Phase 0: Coder creates .vscode/launch.json and app/project-data.json (sample data) — no Designer overlap.
- Phase 1: Designer builds app/index.html and app/styles.css (uses deterministic selectors). These tasks can run in parallel with Coder implementing app/js/app.js because designers only modify markup/style files and coder only reads them to implement JS.
- Ensure merge strategy: do not modify the same file concurrently; use feature branches if simultaneous edits are needed.

## Validation expectations
- app/index.html contains a top-level element with class="dashboard".
- Each rendered project uses class="project-card".
- app/project-data.json is valid JSON and includes a non-empty "projects" array with at least three sample projects.
- .vscode/launch.json is valid JSON and sets cwd to "${workspaceFolder}/app".
- Basic interaction: loading the page in Codespace preview shows project cards and at least one chart or progress indicator.

## Phases and timeline (suggested)
- Phase 0 (Day 0): Coder — create .vscode/launch.json and app/project-data.json sample.
- Phase 1 (Day 1): Designer — app/index.html & app/styles.css skeleton; Coder — app/js/app.js basic renderer.
- Phase 2 (Day 2): Integration — Chart integration, accessibility pass, polish.
- Phase 3 (Day 3): Validation, tests, and documentation.

## Acceptance criteria
- All required files exist in the repository.
- Dashboard renders in Codespace preview with .dashboard and .project-card selectors present.
- Sample data loads and displays at least three project cards with progress indicators.

## Notes & open decisions
- Confirm chart library (Chart.js recommended) and whether to vendor for offline use.
- Confirm exact project-data.json schema variants (dates, IDs) if integrations are required.

---

Save this file exactly at docs/project-pulse-plan.md.
