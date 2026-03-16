# agent-Kryptos Website

> *"Some secrets are meant to stay hidden. Even from the agents that use them."*

The official landing page for **[agent-Kryptos](https://github.com/tuthan/agent-kryptos)** — a zero-knowledge secret provisioning system for AI agents.

![agent-Kryptos Preview](https://img.shields.io/badge/status-live-00f5d4?style=flat-square)


---

## Overview

This is a static, single-page marketing website that introduces agent-Kryptos to the world. It communicates the core value proposition, architecture, security model, and how to get started.

The hero now supports two audience views:
- **Human** — operator-first messaging and onboarding
- **Agent** — API/runtime-oriented messaging with a request/response preview plus support highlights for agent-to-agent provisioning, x402 payments, and OpenClaw

### Sections

| # | Section | Purpose |
|---|---------|---------|
| 1 | **Hero** | Human/agent toggle, CTAs, animated shield visual |
| 2 | **Problem** | Why current secret handling in AI agents is broken |
| 3 | **How It Works** | 5-step flow from keypair generation to secret retrieval |
| 4 | **Architecture** | Component cards (SPS Server, Browser UI, Agent Skill, Gateway) |
| 5 | **Defense in Depth** | 11 security layers with threat neutralization mapping |
| 6 | **Features** | Key capabilities grid (HPKE, LLM Blindness, Ephemeral Keys, etc.) |
| 7 | **Get Started** | Terminal code snippet with install/run commands |
| 8 | **Footer** | Navigation links, license, open-source badge |

---

## Quick Start

No build tools required — this is a static site.

```bash
# Clone
git clone https://github.com/tuthan/agent-kryptos-website.git
cd agent-kryptos-website

# Serve locally
python3 -m http.server 8080
# or
npx serve .

# Open http://localhost:8080
```

---

## Project Structure

```
agent-kryptos-website/
├── index.html          # Complete single-page landing
├── style.css           # Design system & responsive styles
├── script.js           # Particles, hero toggle, scroll animations, mobile menu
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

- **[agent-Kryptos Core](https://github.com/tuthan/agent-kryptos)** — The actual SPS system (server, agent skill, gateway)

---

## Open Source

This project is open source.

