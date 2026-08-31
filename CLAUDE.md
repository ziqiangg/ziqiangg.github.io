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
- Never let color alone carry a meaning (WCAG 1.4.1) — selection state especially: use a native checked/unchecked control (checkbox) or an icon/text change, not just a color/opacity shift on a button.

## Domain color palette (docs/ssp/ section)
The 26 SSP control domains (17 cybersecurity + 9 Digital Service Standards) each get a `--domain-<CODE>` custom property in `docs/assets/css/style.css` (light values in `:root`, dark values in the `prefers-color-scheme: dark` block, same pattern as `--pico-primary`).
- Colors are the **dataviz skill's validated 8-hue categorical theme** (blue, orange, aqua, yellow, magenta, green, violet, red — see the skill's `references/palette.md`), round-robin assigned across the 26 domains in `docs/assets/data/domains.json` order. Validated with `scripts/validate_palette.js` against this site's actual light (`#ffffff`) and dark (`#13171f`) backgrounds — all hard gates pass; 3 light-mode hues (aqua/yellow/magenta) sit below 3:1 contrast by design, which is why the mitigation below is load-bearing, not optional.
- **8 hues cannot give 26 pairwise-distinct colors** — the validator caps reliably distinguishable categorical series at 8 (confirmed: no ordering of a full 8-hue set clears the all-pairs CVD floor, so a 26-color set can't either). Color here is a **supplementary scanning aid, never a unique identifier** — every colored swatch/badge always sits directly next to its 2-letter code, and everywhere but the space-constrained control-card badge, next to the full domain name too. Don't extend this to "give every domain a truly unique color" — it isn't achievable accessibly; add domains to the existing round-robin instead.
- To change the palette: substitute the dataviz skill's `references/palette.md` categorical values (or your own, run through `scripts/validate_palette.js` first) and regenerate the round-robin assignment — don't hand-pick replacement hex values.
