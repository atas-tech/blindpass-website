# BlindPass Website

> *"Some secrets are meant to stay hidden. Even from the agents that use them."*

The official landing page for **[BlindPass](https://github.com/atas-tech/blindpass)** — secure secret delivery for humans, agents, and hosted teams.

![BlindPass Preview](https://img.shields.io/badge/status-live-00f5d4?style=flat-square)


---

## Overview

This is a static, single-page marketing website that introduces the full BlindPass product story. It now covers Human → Agent handoff, Agent → Agent exchange, hosted workspace operations, pricing, and deployment choices in a single landing page.

### Sections

| # | Section | Purpose |
|---|---------|---------|
| 1 | **Hero** | Unified value proposition, dual OSS/hosted CTAs, animated shield visual |
| 2 | **Problem** | Why current secret handling in AI agents is broken |
| 3 | **Use Cases** | Human → Agent, Agent → Agent, and Hosted Teams product modes |
| 4 | **How It Works** | Switchable human handoff and agent exchange flows |
| 5 | **Platform** | Consolidated dashboard, policy engine, and deployment options |
| 6 | **Security** | 11 security layers with threat neutralization mapping |
| 7 | **Pricing** | Open Source Core vs Hosted Platform plan cards plus x402 note |
| 8 | **Comparison** | Capability matrix for self-managed vs hosted evaluation |
| 9 | **Final CTA** | Terminal proof plus split docs / self-host / hosted paths |
| 10 | **Footer** | Resource links and product navigation |

---

## Quick Start

No build tools required — this is a static site.

```bash
# Clone
git clone https://github.com/atas-tech/blindpass-website.git
cd blindpass-website

# Serve locally
python3 -m http.server 8080
# or
npx serve .

# Open http://localhost:8080
```

---

## Project Structure

```
blindpass-website/
├── index.html          # Complete single-page landing
├── style.css           # Design system & responsive styles
├── script.js           # Particles, tabbed panels, scroll animations, mobile menu
├── README.md           # This file
├── SPEC.md             # Design specification & maintenance guide
├── CONTRIBUTING.md     # Contribution guidelines

└── .gitignore
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Structure | Semantic HTML5 |
| Styling | Vanilla CSS (custom properties, glassmorphism, gradients) |
| Interactivity | Vanilla JavaScript (Intersection Observer, Canvas API) |
| Typography | [Inter](https://fonts.google.com/specimen/Inter) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts |
| Build | None — zero dependencies, no bundler |

---

## Deployment

This is a static site that can be deployed anywhere:

- **GitHub Pages**: Push to `main` branch, enable Pages in repo settings
- **Netlify**: Connect repo, zero config needed
- **Vercel**: Import project, auto-detects static site
- **Cloudflare Pages**: Connect repo, build command: (none), output: `/`

---

## Related

- **[BlindPass Core](https://github.com/atas-tech/blindpass)** — The actual SPS system (server, agent skill, gateway)

---

## Open Source

This project is open source.
