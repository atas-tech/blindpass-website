# Design System: BlindPass
**Project ID:** 12997262989494330328

## 1. Visual Theme & Atmosphere
A deep dark-mode, developer-centric interface for a cryptographic secret delivery platform. The aesthetic is futuristic yet clean — high-contrast text on near-black surfaces, frosted glass panels floating above a slowly moving particle field, and neon cyan/purple accents that evoke a secure terminal environment. The product must communicate robust cryptography (RFC 9180 HPKE, in-memory only, single-use retrieval) while feeling alive through micro-animations, hover glows, and pulsing status indicators.

## 2. Color Palette & Roles
- **Neon Cyan** (#00f5d4) - Used for primary actions, active states, hover borders, status indicators, and the dominant brand accent. Use sparingly for maximum impact.
- **Neon Purple** (#7b61ff) - Used as a supporting accent for gradients alongside primary, decorative highlights, and badge variants.
- **Deep Space Black** (#060a14) - Used for the main page background behind the particle canvas.
- **Dark Navy** (#0c1222) - Used for alternating full-width sections for visual rhythm.
- **Translucent Deep Blue-Black** (rgba(14, 22, 42, 0.6)) - Used for all glassmorphic panels and card surfaces.
- **Off-White** (#f0f4ff) - Used for all headings, primary text, and high-contrast foreground content.
- **Cool Grey** (#8892a8) - Used for body text, long descriptions, and secondary copy.
- **Slate Grey** (#5a6478) - Used for small labels, terminal headers, timestamps, and subtle borders.
- **Bright Red** (#ff4757) - Used for destructive actions, problem cards, and warning states.
- **Subtle Bright Blue** (rgba(100, 200, 255, 0.08)) - Used for default card and panel borders at rest.

## 3. Typography Rules
- **Headline Font**: Inter (Weights 700-900). High impact, geometric clarity.
- **Body Font**: Inter (Weights 400-500, 14-18px). Readable, clean sans-serif.
- **Code Font**: JetBrains Mono. Used wherever code appears: terminal blocks, JSON previews, capability badges, and inline snippets. Gives a "built by engineers" feel.
- **Label Font**: Inter (Weight 600, 12-13px). Uppercase with wide letter tracking (3px) to create clear section markers.

## 4. Component Stylings
* **Section Headers:** (A tiny uppercase label tag with primary-tinted background, large bold heading with gradient text on key words for emphasis, centered subtitle in secondary text color, constrained to 600px max width).
* **Cards/Containers (Glassmorphism):** (Generously rounded corners at 20px, translucent deep blue-black background with backdrop blur. Thin subtle blue tinted border at rest. On hover, cards lift up via `translateY(-4px)` with intensified drop shadow and border shifts toward primary cyan).
* **Buttons:** (Primary variant is filled with a linear gradient from neon cyan to neon purple, text is dark space black for a cutout effect, glowing drop shadow. Outline variant has a transparent background with thin border and backdrop blur. Both lift up and intensify glow on hover).
* **Navigation Bar:** (Fixed top bar, transparent by default. On scroll >50px, becomes a frosted glass bar with a bottom border constraint).
* **Terminal / Code Blocks:** (Mocked terminal windows with macOS window dots and body text in JetBrains Mono. Syntax highlighting uses cyan for prompts, blue for commands, green for strings).
* **Pricing Cards:** (Side-by-side comparison cards for 'Free' vs. 'Standard'. Includes distinct badges and notes for `x402` machine payments to avoid confusing recurring billing with per-request autonomous paths).
* **Comparison Grids:** (Compact grids contrasting 'Open Source Core' versus 'Hosted Platform' capabilities. Kept dense with subtle borders and icon indicators).
* **Flow/Sequence Diagrams:** (Networked nodes connected by pulsing or dashed lines over a glassmorphism panel. Simple, non-technical visual summaries of Agent-to-Agent logic).
* **Platform Tabs/Accordions:** (Stackable or tabbed panels used to group Dashboard, Policy, and Deployment Views without endlessly expanding the page vertically).
* **Conceptual Dashboard Mocks:** (Frosted glass panels simulating deployed UI within the platform sections, clearly communicating a modern hosted control plane).
* **Policy Trust Rings:** (Concentric circles or network structures communicating allow/deny blocks and trust ring concepts).

## 5. Layout Principles
- **Elevation via Blur:** Uses frosted glass (glassmorphism) over traditional drop shadows at rest. Shadow is only introduced significantly on hover interactions to pull elements toward the viewer.
- **Section Alignment:** Every content section is centered horizontally with max-width container boundaries and uses generous vertical padding (`120px`) spacing.
- **No Flat SaaS Design:** Everything should feel layered, glowing, and futuristic, cleanly partitioned with thin lines and blurs rather than flat opaque grey boxes.
- **Focus Restraint:** Restrict the use of the primary cyan color to a single, most important action per screen or critical status pulses to maintain hierarchy.
- **Dark Mode Purity:** Maintain extremely high contrast (WCAG AA) with white and off-white headers over the deep space background. Avoid more than two intense accent colors per view.
