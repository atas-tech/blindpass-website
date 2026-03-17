# agent-Kryptos Website — Design Specification

> Maintenance guide and design specification for the agent-Kryptos landing page.

---

## 0. UI Design

This project uses Stitch for rapid design iterations and conceptual mockups.
- **Stitch Project ID**: `12997262989494330328`

---

## 1. Design System

### Color Palette

| Token | Value | Usage |
|-------|-------|-------|
| `--bg-primary` | `#060a14` | Page background |
| `--bg-secondary` | `#0c1222` | Alternating section backgrounds |
| `--bg-card` | `rgba(14, 22, 42, 0.6)` | Card backgrounds (glassmorphism) |
| `--text-primary` | `#f0f4ff` | Headings, primary text |
| `--text-secondary` | `#8892a8` | Body text, descriptions |
| `--text-muted` | `#5a6478` | Labels, captions |
| `--cyan` | `#00f5d4` | Primary accent (CTAs, highlights) |
| `--purple` | `#7b61ff` | Secondary accent (gradients) |
| `--danger` | `#ff4757` | Problem/warning elements |

### Typography

| Element | Font | Weight | Size |
|---------|------|--------|------|
| Headings | Inter | 700–900 | 32–58px (clamp) |
| Body | Inter | 400–500 | 14–18px |
| Code/Mono | JetBrains Mono | 400–600 | 12–14px |
| Labels | Inter | 600 | 12–13px, uppercase |

### Gradients

```css
/* Primary text gradient (cyan → purple) */
--gradient-text: linear-gradient(135deg, #00f5d4 0%, #7b61ff 100%);

/* Button gradient */
--gradient-btn: linear-gradient(135deg, #00f5d4 0%, #00b4d8 50%, #7b61ff 100%);
```

### Spacing

- Section padding: `120px` vertical (desktop), `80px` (mobile)
- Container max-width: `1200px`
- Card padding: `36px`
- Card border-radius: `20px`
- Grid gaps: `24px`

---

## 2. Component Catalog

### Cards
All cards use **glassmorphism**: translucent background with `backdrop-filter: blur(10px)`, subtle 1px border in `--border-color`, and hover lift (`translateY(-4px)`) with box shadow.

### Buttons
- **Primary** (`btn-primary`): Gradient fill, dark text, glow shadow on hover
- **Outline** (`btn-outline`): Transparent with border, fill on hover

### Hero
- **Mode toggle**: pill switch between `Human` and `Agent` views
- **Human view**: headline, supporting copy, CTA pair, trust stats
- **Agent view**: headline, supporting copy, terminal/JSON preview, security note, support cards, capability badges
- **Animated visual**: the existing particle background + shield/ring animation remains the persistent hero anchor across both views

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
| How It Works | `Implementation Plan.md` — Agent Skill + SPS flow |
| Architecture | `Implementation Plan.md` §2–5 (project structure) |
| Defense in Depth | `Brainstorm Secure Secret System.md` §5 |
| Features | `Brainstorm Secure Secret System.md` §3 |
| Get Started | `package.json` scripts + `SKILL.md` |

**When updating features or architecture in the core `agent-kryptos` repo (https://github.com/atas-tech/agent-kryptos), update the corresponding section here.**

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
| Hero mode toggle | Click / keyboard | 200ms | ease |
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
- Architecture cards: 0, 100ms, 200ms, 300ms
- Feature cards: 0, 100ms, 200ms, 300ms, 400ms, 500ms
- Defense layers: 0, 50ms, 100ms, ... 500ms

---

## 5. Responsive Breakpoints

| Breakpoint | Layout Changes |
|------------|---------------|
| `> 1024px` | Full desktop layout, 2-col hero with persistent animated visual |
| `768–1024px` | Single-col hero, toggle centered, agent terminal card stays readable |
| `< 768px` | Mobile: single-col everything, hamburger menu, reduced padding, stacked agent panel |
| `< 480px` | Extra compact: tighter padding, smaller code font |

---

## 6. SEO Checklist

- [x] Descriptive `<title>` tag
- [x] `<meta name="description">` with keyword-rich summary
- [x] Single `<h1>` (hero title)
- [x] Proper heading hierarchy (h1 → h2 → h3 → h4)
- [x] Semantic HTML5 (`<nav>`, `<section>`, `<footer>`)
- [x] `alt` attributes on images (SVG inline — covered by `aria-label` if needed)
- [x] Add `<link rel="icon">` favicon
- [ ] Add Open Graph / Twitter Card meta tags
- [ ] Add `sitemap.xml` and `robots.txt` for search engine crawling

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
