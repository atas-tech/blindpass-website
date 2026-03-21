# BlindPass Website — Design Specification

> Maintenance guide and design specification for the BlindPass landing page.

---

## 0. UI Design

This project uses Stitch for rapid design iterations and conceptual mockups.
- **Stitch Project ID**: `12997262989494330328`

---

## 1. Design System

The canonical design system is defined in [`DESIGN.md`](DESIGN.md). It follows the [Stitch DESIGN.md format](https://stitch.withgoogle.com/docs/design-md/overview/) and covers colors, typography, elevation, components, and design guardrails.

CSS implementation of these tokens lives in `:root` at the top of `style.css`.

**Do not duplicate design tokens here.** If a color, font, or component style needs to change, update `DESIGN.md` first and then sync `style.css`.

---

## 2. Component Catalog

### Cards
All cards use **glassmorphism**: translucent background with `backdrop-filter: blur(10px)`, subtle 1px border in `--border-color`, and hover lift (`translateY(-4px)`) with box shadow.

### Buttons
- **Primary** (`btn-primary`): Gradient fill, dark text, glow shadow on hover
- **Outline** (`btn-outline`): Transparent with border, fill on hover

### Hero
- **Unified message**: presents a single value proposition covering Human → Agent, Agent → Agent, and hosted workspace operations
- **Primary CTA**: hosted platform path
- **Secondary CTA**: docs or self-hosting path
- **Trust row**: compact badges for HPKE (RFC 9180), single-use retrieval, in-memory only, Open Source + Hosted
- **Animated visual**: the existing particle background + shield/ring animation remains the persistent hero anchor

### Tabbed Panels
- **How It Works**: switcher between `Human → Agent` and `Agent → Agent`
- **Platform**: switcher between `Dashboard`, `Policy & Approvals`, and `Deployment Options`
- **Behavior**: the first panel is visible by default without JS; JavaScript enhances the controls with ARIA state and panel toggling

### Section Headers
Each section follows the pattern:
1. **Label** — tiny uppercase tag with colored background (e.g., "THE PROBLEM")
2. **Title** — large heading with gradient text on key words
3. **Subtitle** — grey description, max 600px centered

### Navigation
- Fixed position, transparent by default
- On scroll (>50px): adds frosted glass backdrop + bottom border
- Mobile: full-screen overlay menu

---

## 3. Content Guide

### Maintaining Content Accuracy

The website content is sourced from these project files:

| Section | Source Document |
|---------|----------------|
| Hero tagline | Original brainstorm — tagline created during naming |
| Problem cards | `Brainstorm Secure Secret System.md` §1 |
| Use Cases | `README.md`, `Phase 2A - Agent to Agent Exchange.md`, `Phase 3A - Hosted Platform.md` |
| How It Works | `Brainstorm Secure Secret System.md`, `Phase 2A - Agent to Agent Exchange.md`, `Phase 2B - Production A2A.md` |
| Platform | `Phase 3A - Hosted Platform.md`, `Phase 3B - UI & Operations.md`, `guides/policy.md` |
| Defense in Depth | `Brainstorm Secure Secret System.md` §5 |
| Pricing / Comparison | `LANDING_PAGE_IMPROVEMENT_PLAN.md`, `README.md`, hosted phase docs |
| Final CTA | `README.md`, deployment docs, hosted service URLs |

**When updating features or architecture in the core `blindpass` repo (https://github.com/atas-tech/blindpass), update the corresponding section here.**

### Key Claims to Verify

These specific details must stay accurate:

- **"RFC 9180"** — HPKE standard reference
- **"X25519 + HKDF-SHA256 + ChaCha20-Poly1305"** — actual cipher suite (verify in `key-manager.ts`)
- **"3-minute TTL"** — current default (verify in `redis.ts`)
- **"11 layers"** — count the layers if any are added/removed
- **"Ed25519 JWT"** — gateway identity scheme (verify in `identity.ts`)
- **"Atomic GETDEL"** — Redis retrieval pattern (verify in `redis.ts`)

---

## 4. Animation Spec

| Animation | Trigger | Duration | Easing |
|-----------|---------|----------|--------|
| Particle background | Page load | Continuous | Linear |
| Tab / panel switch | Click / keyboard | 200ms | ease |
| Scroll fade-in | Intersection Observer (10% visible) | 700ms | ease-out |
| Card hover lift | Mouse hover | 200ms | ease |
| Shield rings | Page load | 10–20s per rotation | Linear |
| Shield core pulse | Page load | 3s cycle | ease-in-out |
| Data streams | Page load | 3s cycle | ease-in-out |
| Badge dot pulse | Page load | 2s cycle | ease-in-out |
| Nav link underline | Mouse hover | 200ms | ease |

### Staggered Grid Animations
Grid children use incremental `transition-delay`:
- Problem cards: 0, 100ms, 200ms, 300ms
- Use case cards: 0, 100ms, 200ms
- Flow cards: 0, 100ms, 200ms, 300ms
- Defense layers: 0, 50ms, 100ms, ... 500ms

---

## 5. Responsive Breakpoints

| Breakpoint | Layout Changes |
|------------|---------------|
| `> 1024px` | Full desktop layout, 2-col hero with persistent animated visual |
| `768–1024px` | Single-col hero, multi-card sections begin to collapse, dashboard/policy panels stack vertically |
| `< 768px` | Mobile: single-col sections, hamburger menu, stacked platform panels, comparison table becomes card-like rows |
| `< 480px` | Extra compact: tighter padding, smaller code font, reduced pill/button density |

---

## 6. SEO Checklist

- [x] Descriptive `<title>` tag
- [x] `<meta name="description">` with keyword-rich summary
- [x] Single `<h1>` (hero title)
- [x] Proper heading hierarchy (h1 → h2 → h3 → h4)
- [x] Semantic HTML5 (`<nav>`, `<section>`, `<footer>`)
- [x] `alt` attributes on images (SVG inline — covered by `aria-label` if needed)
- [x] Add `<link rel="icon">` favicon
- [x] Add Open Graph / Twitter Card meta tags
- [x] Add `sitemap.xml` and `robots.txt` for search engine crawling

---

## 7. Future Enhancements

- [x] Add favicon (`.svg`)
- [ ] Add Open Graph meta tags for social sharing
- [ ] Add dark/light mode toggle
- [ ] Add interactive sequence diagram (animated on scroll)
- [ ] Add testimonials / "Used by" logos section
- [ ] Add blog/changelog section
- [ ] Consider adding performance budget (Lighthouse CI)
- [ ] Add accessibility audit (WCAG 2.1 AA)
