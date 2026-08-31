# CLAUDE.md

## Project
Personal website for Guo Zi Qiang Robin, served via GitHub Pages at `ziqiangg.github.io`.
Plain HTML/CSS. No build step, no framework, no package manager, no dependencies.

## Structure
- Pages source: `docs/` folder on `main` branch.
- One folder per page, each with its own `index.html` (→ clean URLs like `/about/`).
- Shared assets in `docs/assets/{css,img}/`.
- Root `docs/index.html` = homepage.

## Rules
- Do not introduce a build step, bundler, or framework unless explicitly asked.
- Do not commit secrets, API keys, or analytics tokens directly in HTML/JS — this repo is fully public.
- Keep HTML semantic; every page needs a `<title>`, meta description, and viewport meta tag.
- Reuse `docs/assets/css/style.css` across pages — don't create per-page stylesheets.
- Commit messages: short, imperative (`add projects page`, not `Added Projects Page`).

## Workflow
- Local preview steps: see `SKILLS.md`.
- Push to `main` to deploy — no CI needed.

## Design discipline (before calling any page "done")
- Screenshot the page (chrome-devtools MCP) at desktop and mobile widths before saying a page is finished. Don't rely on markup alone.
- Avoid default AI-generated look: no unstyled system fonts, no purple/violet gradient hero, no generic centered-card layout unless deliberately chosen.
- Pick one distinctive element (typography, accent color, one signature layout choice) and keep everything else quiet around it.
- Responsive down to mobile width, visible keyboard focus states, respect `prefers-reduced-motion`.
- Self-critique against the screenshot before presenting: does this look templated, or intentional?
