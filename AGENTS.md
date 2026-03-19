# Repository Guidelines

## Project Structure & Module Organization
This repository is a static single-page site with no build system.

- `index.html`: page structure and content sections.
- `style.css`: design tokens, layout, components, and responsive rules.
- `script.js`: UI behavior (particles, scroll animations, mobile nav).
- `README.md`, `SPEC.md`, `CONTRIBUTING.md`: product, design, and contribution docs.
- `.github/workflows/deploy.yml`: GitHub Pages deployment workflow.

If you add images or other media, place them under an `assets/` directory and use relative paths.

## Build, Test, and Development Commands
- `python3 -m http.server 8080`: run a local static server.
- `npx serve .`: alternative local server.
- `open http://localhost:8080` (or browser equivalent): preview changes.

There is no compile or bundling step; deploy output is the repository root.

## Coding Style & Naming Conventions
- Use semantic HTML (`<section>`, `<nav>`, `<footer>`) and keep IDs unique.
- Follow existing naming style: kebab-case classes/IDs (for example, `hero-title`, `mobile-menu-btn`).
- Reuse CSS variables from `:root`; avoid hardcoded colors when a token exists.
- Keep sectioned comment headers in CSS/JS for readability.
- Preserve current indentation conventions by file: HTML/CSS use 2 spaces, JS uses 4 spaces.
- Use vanilla JavaScript only; do not introduce frameworks or build tooling without prior discussion.

## Testing Guidelines
No automated test framework is configured. Validate changes manually before opening a PR:

- Check desktop and mobile layouts (`>1024`, `768-1024`, `<768`).
- Verify animations and mobile menu interactions.
- Confirm no browser console errors.
- Re-check factual/security claims against the core `blindpass` project when editing content.

## Commit & Pull Request Guidelines
- Follow the existing commit style: `type: summary` (examples: `fix: ...`, `deploy: ...`, `test: ...`).
- Keep commits and PRs focused on one logical change.
- PRs should include: clear description, linked issue (if any), and screenshots for visual updates.
- Update `README.md`/`SPEC.md` when structure, design tokens, or user-facing content changes.
