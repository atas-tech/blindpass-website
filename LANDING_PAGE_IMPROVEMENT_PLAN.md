# Landing Page Improvement Plan

## Goal

Expand the landing page from a Phase 1/2 security story into a fuller product story that reflects the current `blindpass` scope:

- Human → Agent secret delivery
- Agent → Agent exchange
- Hosted workspace control plane

---

## Editorial Guardrails

- Market **shipped** capabilities as shipped.
- Market **planned / in-progress** capabilities only when clearly labeled `Planned`, `In Progress`, or `Roadmap`.
- Keep security language precise. Prefer concrete claims like `HPKE`, `single-use retrieval`, and `in-memory only` over vague claims like `unbreakable` or `production-ready`.
- Prefer one clear product hierarchy on-page: `Open Source Core` first, then `Hosted Platform`, instead of mixing roadmap items into the core story.
- If using screenshots or mocks, distinguish between `real UI` and `conceptual visual` so the page does not imply features are live when they are still planned.

---

## Resolved Product Decisions

- The landing page should serve **both** audiences: open-source adopters and hosted-product buyers.
- A public-facing hosted CTA should be present on the page.
- Pricing should appear on the landing page.
- `x402` should be treated as part of the product story, not hidden as a niche footnote.
- Use a **conceptual mock first** for the dashboard / hosted-product visual instead of waiting for a production screenshot.
- **Section Consolidation:** Create a single, robust **Platform** section using tabs/accordions to house `Dashboard`, `Policy & Approvals`, and `Deployment Options` to avoid page fatigue.
- **Navigation:** Maintain a flat top navigation limited to the core pillars (`Problem`, `Use Cases`, `Platform`, `Security`, `Pricing`, `Docs`).
- **Primary CTA & Terminal:** Keep the terminal snippet in the "Final CTA" section but add split paths directly below it (`Read Docs` → repo README, `Self-Host` → compose guide, `Explore Hosted` → waitlist/live dashboard).
- **SPIFFE Claim:** Rename Layer 08 to "Pluggable Identity (SPIFFE/SPIRE Ready)" to keep the "11 Layers" stat intact.
- **Hero Toggle:** Drop the Human/Agent toggle from the Hero. Present a unified message in the Hero and reserve the interactive toggle for the `How It Works` section.
- **x402 Display:** Display `x402` as an advanced capability card inside `Platform` and a single explanatory line in `Pricing`.

### Implications

- The page should clearly separate `Open Source Core` from `Hosted Platform`, but market both on the same page.
- CTA structure should support two real entry paths: open source docs / self-hosting and hosted exploration.
- Pricing should likely include both:
  - workspace pricing for hosted plans
  - machine-payment / x402 language as an advanced capability
- Mock visuals are acceptable in the first pass, but they should not imply that every depicted hosted screen is already live.

---

## Improvement Plan

### 1. Reposition the page around the full product surface · `code-only`

The current site still centers mostly on secret handoff. Update messaging to cover three pillars:

- `Human → Agent`
- `Agent → Agent`
- `Hosted workspace control plane`

The hero foundation already exists, but the current Human/Agent toggle should be removed from the hero and the interaction moved down into `How It Works`.

Reference:

- `/home/hvo/Projects/blindpass/README.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Brainstorm Secure Secret System.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3A - Hosted Platform.md`

---

### 2. Redesign the information architecture · `stitch`

Keep hero, problem, and security, but insert new sections for:

- `Use Cases`
- `Platform` (dashboard, policy, approvals, deployment)
- `Pricing`

These are entirely new sections with no existing layout pattern. Stitch is needed to nail down card/grid style, visual hierarchy, and how they interleave with existing sections.

> **⚠ Page-length risk** — the current page is already 7 sections. Adding 5+ new full-width sections pushes toward 12+. Consider whether some of these should collapse into tabs/accordions inside a single "Platform" section rather than all being separate scroll sections. Decide this in Stitch before coding.
>
> **Resolved direction** — `Hosted Dashboard`, `Policy & Approvals`, and `Deployment Options` belong inside one broader `Platform` section. `Pricing` remains separate.

Reference:

- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3B - UI & Operations.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3E - Hosted Hardening, Ecosystem & Launch.md`

---

### 3. Add a dedicated agent-to-agent section · `stitch`

> **Folded into §4 How It Works** — the section-by-section plan already places agent-to-agent as a second tab/toggle inside How It Works. This item stays as a content reference, but is not a standalone section.

Content to include in the agent-to-agent flow tab:

- requester agent
- fulfiller agent
- policy check
- approval path
- single-use retrieval

A sequence diagram or flow graphic would be ideal — design in Stitch first.

Reference:

- `/home/hvo/Projects/blindpass/docs/architecture/Brainstorm Secure Secret System.md`

---

### 4. Add a hosted operations section · `stitch`

> **Folded into §5 Platform** — the section-by-section plan consolidates dashboard, operations, and deployment into one Platform section. This item stays as a content reference.

Content to include inside the Platform section:

- agents
- members
- audit logs
- approvals
- billing
- quotas

Needs Stitch design to decide between dashboard screenshot mock, icon grid, or feature list layout.

Reference:

- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3A - Hosted Platform.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3B - UI & Operations.md`

---

### 5. Add a policy engine section · `stitch`

Explain the policy model as a key differentiator:

- secret registry
- trust rings
- allow / deny / pending approval
- tenant-scoped policy management
- versioned and audited policy changes

Trust rings and allow/deny/pending states are conceptually dense. A diagram or visual (concentric ring graphic, mini policy table) would land much better than text cards. Stitch is needed to explore visual treatments.

Reference:

- `/home/hvo/Projects/blindpass/docs/guides/policy.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3E - Hosted Hardening, Ecosystem & Launch.md`

---

### 6. Rewrite the CTA strategy · `code-only`

Replace the current generic `Get Started in 60 Seconds` block with clearer entry points:

- `Read Docs`
- `Self-Host`
- `Explore Hosted`

Because the page now serves both OSS and hosted audiences, the CTA area should explicitly split those paths rather than assuming one generic onboarding flow.

The existing `cta-row` layout can handle 3 buttons with minor CSS adjustment.

> **Decision resolved** — keep the current terminal block to preserve developer-first credibility, but add the three split path buttons below it.
>
> **Destination resolved**:
>
> - `Read Docs` → repo README or docs index
> - `Self-Host` → Docker Compose deployment guide
> - `Explore Hosted` → waitlist form or live dashboard

Reference:

- `/home/hvo/Projects/blindpass/README.md`

---

### 7. Tighten factual claims · `code-only`

Keep strong, defensible claims:

- `HPKE (RFC 9180)`
- `LLM blindness`
- `single-use retrieval`
- `in-memory only`

Avoid:

- presenting SPIFFE as the default identity model
- implying full production hardening is already complete
- overclaiming setup simplicity where the docs are still evolving

> **SPIFFE cascading change resolved** — Defense Layer 08 will be softened to "Pluggable identity (SPIFFE/SPIRE ready)". This keeps the hero stat "11 Security Layers" intact while remaining factually honest that custom JWTs are the default.

Reference:

- `/home/hvo/Projects/blindpass/docs/architecture/Brainstorm Secure Secret System.md`
- `/home/hvo/Projects/blindpass/docs/security/Security Audit.md`

---

### 8. Add proof surfaces · `stitch`

Make the page feel like a product site, not only a security concept page. Add:

- dashboard screenshot or mock
- simplified sequence diagram
- compact comparison: `Open Source Core` vs `Hosted Platform`

The comparison table and sequence diagram are new visual components that don't exist in the current design system. Design in Stitch first.

> **Resolved direction** — use a conceptual mock in the first pass. It should visually sell the hosted platform, but avoid depicting obviously unshipped or misleading states as if they are already live.

---

### 9. Add pricing section · `stitch`

Pricing is now an explicit part of the page strategy.

Recommended structure:

- hosted workspace pricing card(s)
- short comparison of `Free` vs `Standard`
- short note that advanced machine-payment flows can use `x402`

This section should stay simple. Avoid trying to explain every billing edge case on the landing page.

> **Content rule** — keep recurring hosted pricing and `x402` machine payments visually distinct so users do not confuse workspace subscription pricing with per-request autonomous payments.

---

### 10. Update navigation · `code-only`

Adding new sections means the nav links grow significantly. We will maintain a flat top navigation but limit the anchors to the core pillars:

- `Problem`
- `Use Cases`
- `Platform`
- `Security`
- `Pricing`
- `Docs`

This avoids the need for a complex dropdown menu and fits well on desktop and mobile.

---

## Discussion Points (Resolved)

1. **Page-length risk** — Resolved: Collapse new items (`Dashboard`, `Policy & Approvals`, `Deployment Options`) into tabs/accordions within a single "Platform" section.
2. **Navigation overflow** — Resolved: Keep flat anchor list limited to core pillars (`Problem`, `Use Cases`, `Platform`, `Security`, `Pricing`, `Docs`).
3. **SPIFFE cascade** — Resolved: Soften Layer 08 to "Pluggable Identity" to keep the 11-layer count.
4. **Pricing section placement** — Resolved: Keep `Pricing` as its own section, and put a note about `x402` inside it.
5. **Quick-start terminal decision** — Resolved: Keep the terminal snippet in the final CTA but update the buttons below it.
6. **Hero Toggle** — Resolved: Drop the toggle from the hero, using a unified message instead. Save the toggle for the "How It Works" section.

---

## Questions To Resolve Before Design

All strategic questions are now resolved:

1. The page should sell both the **open source project** and the **hosted product**.
2. A public-facing hosted CTA should be present.
3. `x402` should be visible as part of the product story (badge in `Platform`, note in `Pricing`).
4. Use a conceptual mock first for hosted visuals.
5. Pricing should appear on the page as its own section.
6. CTA destination types defined (`Read Docs` -> README/docs, `Self-Host` -> compose guide, `Explore Hosted` -> waitlist/dashboard); exact URLs still need wiring.
7. Quick-start terminal remains at the bottom, with split paths below it.
8. Hero presented with a unified message (no toggle).

---

## Proposed Landing Page Structure

This is the recommended first-pass structure for the rewrite of `index.html`.

### Recommended Section Order

1. Hero
2. Problem
3. Use Cases
4. How It Works
5. Platform
6. Security
7. Pricing
8. Open Source vs Hosted
9. Final CTA
10. Footer

This keeps the page focused while still covering both OSS and hosted audiences. It also avoids turning every new idea into a separate full-width section.

### Section-by-Section Plan

#### 1. Hero

Status:

- Keep the existing hero foundation
- Rewrite the copy
- Drop the Human / Agent toggle

Purpose:

- establish the core value proposition
- make it clear the product supports both open source and hosted usage
- present immediate paths for OSS and hosted visitors

Recommended content:

- headline centered on secure secret delivery for agents and teams
- subhead mentioning Human → Agent, Agent → Agent, and hosted workspace control
- primary CTA for hosted
- secondary CTA for docs or self-hosting
- compact trust row under hero:
  - `HPKE (RFC 9180)`
  - `Single-use retrieval`
  - `In-memory only`
  - `Open Source + Hosted`

Recommended note:

- do not overload the hero with too many roadmap items
- `x402` can appear as a small support badge, not the main headline

#### 2. Problem

Status:

- Keep the current section
- Tighten copy

Purpose:

- explain why agent secret handling is broken today
- build urgency before introducing the broader product surface

Recommended content:

- keep 3-4 problem cards
- tighten toward actual leakage vectors:
  - chat and prompt context
  - config/env sprawl
  - middleware/plaintext transit
  - missing expiry / uncontrolled reuse

Recommended edit:

- shorten card copy so the page moves faster into the solution and platform story

#### 3. Use Cases

Status:

- New section

Purpose:

- explain the three product modes in one glance

Recommended cards:

- `Human → Agent`
  - secure human handoff through browser encryption and one-time retrieval
- `Agent → Agent`
  - policy-checked exchange between requester and fulfiller agents
- `Hosted Teams`
  - operators manage agents, members, approvals, quotas, and billing

Recommended design:

- one 3-column card row on desktop
- each card has a short “best for” line

Why this matters:

- this is where the landing page stops being just a crypto explainer

#### 4. How It Works

Status:

- Keep the section
- Expand it from only Human → Agent into dual-flow storytelling

Purpose:

- make the mechanics concrete

Recommended structure:

- tabs or toggle inside the section:
  - `Human → Agent flow`
  - `Agent → Agent flow`

Human → Agent flow:

- request created
- secure link / confirmation step
- browser-side encryption
- single-use retrieval

Agent → Agent flow:

- requester asks SPS
- fulfiller is authorized by policy
- approval is checked if required
- ciphertext is submitted once
- requester retrieves once

Recommended note:

- keep diagrams simplified for marketing
- avoid pasting raw API routes into the page body

#### 5. Platform

Status:

- New consolidated section

Purpose:

- present the hosted product without scattering it across multiple sections

Recommended subsections inside one section:

- hosted dashboard mock
- operations capability list
- policy and approvals panel
- deployment options

Recommended content:

- dashboard mock labeled conceptual
- key ops bullets:
  - agent enrollment
  - member management
  - audit log
  - approvals inbox
  - billing and quotas
- policy area:
  - secret registry
  - trust rings
  - allow / deny / pending approval
  - audited policy changes
- deployment modes:
  - open source / self-hosted
  - hosted workspace platform

Recommended decision:

- fold `Hosted Dashboard`, `Policy & Approvals`, and `Deployment Options` together here
- do not split them into separate full-width sections in the first pass

#### 6. Security

Status:

- Keep current defense section
- simplify and correct claims

Purpose:

- preserve the security-first identity of the project

Recommended changes:

- keep layered defense framing
- reduce density if needed
- correct SPIFFE positioning:
  - default identity story should be SPS-trusted JWTs
  - SPIFFE should be optional / advanced, not default

Recommended structure:

- either keep 11 layers with corrected wording
- or reduce to a more readable top 6-8 layers if the section feels too long

Recommendation:

- if the full 11-layer stack stays, tighten each description to one short line

#### 7. Pricing

Status:

- New section

Purpose:

- give hosted visitors a concrete buying frame
- make `x402` visible without confusing it with workspace subscriptions

Recommended structure:

- `Free` hosted card
- `Standard` hosted card
- small side note or sub-block for `x402 machine payments`

Recommended content direction:

- hosted pricing is for workspace access and management
- `x402` is for advanced autonomous per-request payment flows

Important separation:

- recurring workspace pricing and per-request machine payments must not be presented as the same thing

#### 8. Open Source vs Hosted

Status:

- New section or lower-page comparison block

Purpose:

- help visitors self-select quickly

Recommended columns:

- `Open Source Core`
- `Hosted Platform`

Suggested comparison rows:

- deploy yourself
- browser encryption
- agent-to-agent exchange
- dashboard and admin UX
- billing and quotas
- policy management
- hosted onboarding

Recommended note:

- if the page becomes too long, this can collapse into a compact comparison card inside Pricing or Final CTA

Boundary with Pricing (§8):

- §8 Pricing owns **plan labels and price points** (Free vs Standard, x402 note)
- §9 Comparison owns **capability scope** (what each option includes)
- avoid repeating billing/quota details in both sections

#### 9. Final CTA

Status:

- Replace current quick-start section

Purpose:

- give both audiences a next step

Recommended structure:

- left: OSS path
  - `Read Docs`
  - `Self-Host`
- right: hosted path
  - `Explore Hosted`

Recommended content:

- remove the current “Get Started in 60 Seconds” framing unless the onboarding really supports that claim
- optional terminal snippet can remain only if it still helps the OSS story and does not dominate the section

Recommendation:

- prefer a split-path CTA over the current single terminal-led CTA block

#### 10. Footer

Status:

- Keep
- expand resource quality

Recommended links:

- docs
- core repo
- hosted product
- security / audit references
- deployment / self-hosting

### Mapping From Current Sections

Keep and rewrite:

- `Hero`
- `Problem`
- `How It Works`
- `Defense`
- `Footer`

Keep but repurpose:

- `Architecture` → fold into `Use Cases` or `Platform`
- `Features` → fold into `Platform` or comparison content
- `Get Started` → replace with `Final CTA`

Add net-new:

- `Use Cases`
- `Platform`
- `Pricing`
- `Open Source vs Hosted`

### Recommended Navigation Model

Keep the top nav short. Recommended anchors:

- `Problem`
- `Use Cases`
- `Platform`
- `Security`
- `Pricing`
- `Docs`

Skipped from nav (reachable by scrolling):

- `How It Works` — flows naturally from Use Cases; adding it crowds the bar without improving navigation
- policy / approvals content sits under Platform visually; giving it a nav slot implies it is a top-level product pillar
- `Open Source vs Hosted` — comparison content near the bottom; visitors reach it through Pricing or the final CTA

Notes:

- if nav starts to feel crowded, link `Docs` externally and keep only 5 on-page anchors

### Recommended Copy Hierarchy

Top-of-page hierarchy:

1. secure secret delivery for agents
2. support for both human and autonomous workflows
3. hosted control plane for teams

Lower-page hierarchy:

1. how the system works
2. how teams operate it
3. how policy and pricing fit

### Recommended Treatment For x402

`x402` should be visible, but not allowed to dominate the page.

Recommended placement:

- small badge or callout in hero support area
- one capability card inside `Platform` or `Pricing`
- one line in the comparison / pricing area explaining it as an advanced machine-payment path

Avoid:

- making the page look like a crypto product first
- merging `x402` language into the main hosted workspace pricing cards

---

## Suggested Execution Order

### High-Fidelity Design Package Status

The Stitch concept phase is now complete for the net-new product-story sections. The implementation plan should treat the local exports under `.stitch/designs/` as the current reference set:

1. `01-use-cases` → three-card product-mode section (`Human → Agent`, `Agent → Agent`, `Hosted Teams`)
2. `02-agent-to-agent` → sequence/flow visual for the `How It Works` agent-to-agent state
3. `03-dashboard` → conceptual hosted control-plane mock for the `Platform` section
4. `04-policy-engine` → trust-ring/policy visualization for the `Platform` section
5. `05-platform-options` → self-managed vs hosted deployment chooser for the `Platform` section
6. `06-pricing` → `Open Source Core` vs `Hosted Platform` pricing cards plus `x402` note
7. `07-comparison` → dense `Open Source Core` vs `Hosted Platform` capability matrix

Implementation note:

- These exported `.html` files are reference material, not production code to paste in directly. The repo is a hand-authored static site with its own tokens, spacing, and JavaScript conventions. Rebuild the concepts inside `index.html`, `style.css`, and `script.js` using the exports as visual/content guides.

### Phase 0 — Content Audit

1. Classify each current and proposed claim as `shipped`, `in progress`, or `planned`
2. ~~Decide the primary page audience: OSS adopters, hosted buyers, or both~~ → **resolved: both**
3. ~~Resolve the CTA destinations and whether hosted should be public-facing yet~~ → **resolved at the strategy level: hosted is public-facing and destination types are defined; exact URLs still need wiring during implementation**
4. ~~Decide whether pricing appears anywhere on-page~~ → **resolved: yes**

### Phase A — Stitch Design (complete)

> **Design system input** — Stitch should consume [`DESIGN.md`](DESIGN.md) as the design system source of truth. All new sections and components must follow the tokens, elevation rules, and Do's/Don'ts defined there.

Completed concept set:

1. Use Cases section layout (`01-use-cases`)
2. Agent-to-Agent flow / sequence visual (`02-agent-to-agent`)
3. Hosted Dashboard concept (`03-dashboard`)
4. Policy Engine / trust rings concept (`04-policy-engine`)
5. Deployment Options / Platform chooser (`05-platform-options`)
6. Pricing section (`06-pricing`)
7. OSS vs Hosted comparison component (`07-comparison`)

### Phase B — Information Architecture Refactor

1. Rewrite the top navigation to the resolved anchor model:
   - `Problem`
   - `Use Cases`
   - `Platform`
   - `Security`
   - `Pricing`
   - `Docs`
2. Rewrite the hero to a unified value proposition:
   - remove the current Human/Agent toggle from the hero
   - keep one shared headline/subhead
   - keep dual CTA logic for OSS + hosted audiences
   - preserve the existing trust/stat row, but retune the copy
3. Re-map the page structure in `index.html` to the new section order:
   - Hero
   - Problem
   - Use Cases
   - How It Works
   - Platform
   - Security
   - Pricing
   - Open Source vs Hosted
   - Final CTA
   - Footer
4. Remove or fold legacy sections once replacements are in place:
   - remove the old `Architecture` section after its useful ideas are absorbed into `Use Cases` / `Platform`
   - remove the old `Features` section after its useful ideas are absorbed into `Platform` / comparison
   - replace the current `Get Started` section with the new split-path final CTA

### Phase C — Section Implementation Plan

Implement in this order so the page works after each checkpoint and the largest structural risks are handled first.

#### C1. Hero + Nav + Problem

1. Update hero copy and buttons first because it affects page framing and nav CTA language.
2. Remove hero-mode markup that only exists to support the hero toggle.
3. Delete `initHeroMode()` and any CSS that only exists for hero tab state once the new hero is stable.
4. Tighten the `Problem` cards so the section leads faster into the new product surface.

#### C2. Use Cases + How It Works

1. Build a new `Use Cases` section from `01-use-cases`:
   - three cards
   - short “best for” labels
   - compact terminal/proof strip below the cards if it helps pacing
2. Keep `How It Works`, but convert it into a dual-flow section:
   - `Human → Agent`
   - `Agent → Agent`
3. Use `02-agent-to-agent` as the visual direction for the second flow state.
4. Add only the interaction needed to switch the flow content; avoid rebuilding the old hero toggle behavior one-for-one.

#### C3. Platform

1. Build one consolidated `Platform` section with internal tabs or segmented controls.
2. Use these three views inside that section:
   - `Dashboard` from `03-dashboard`
   - `Policy & Approvals` from `04-policy-engine`
   - `Deployment Options` from `05-platform-options`
3. Keep the dashboard explicitly labeled conceptual.
4. Keep the policy view focused on trust rings, policy states, and auditability rather than deep product copy.
5. Keep deployment options simple:
   - `Open Source / Self-Hosted`
   - `Hosted Workspace Platform`
6. Reuse one shared panel shell so all three views feel like one product surface instead of three unrelated sections.

#### C4. Pricing + Comparison + Final CTA

1. Build the standalone `Pricing` section from `06-pricing`.
2. Keep recurring hosted pricing distinct from `x402`:
   - pricing cards explain plans
   - a separate note/callout explains autonomous machine payments
3. Build the comparison grid from `07-comparison` as the lower-page decision aid.
4. Replace the final CTA with split paths:
   - `Read Docs`
   - `Self-Host`
   - `Explore Hosted`
5. Keep the terminal snippet only if it still supports the OSS story after the new pricing/comparison sections are in place.

### Phase D — Styling and Interaction Workstreams

#### HTML

1. Add new semantic section IDs for `use-cases`, `platform`, `pricing`, and `comparison`.
2. Keep anchor IDs stable and readable because the nav remains flat and mobile users need predictable jumps.
3. Use clear labels for conceptual UI blocks so planned hosted surfaces are not presented as shipped screenshots.

#### CSS

1. Extend the existing token system instead of introducing screen-specific inline styles from the Stitch exports.
2. Create reusable patterns for:
   - section headers
   - comparison tables
   - pricing cards
   - platform tab buttons
   - glass dashboard/policy panels
3. Verify the new dense sections at all required breakpoints:
   - `>1024`
   - `768-1024`
   - `<768`
4. Treat the comparison matrix as the highest mobile-risk component and design its stacked/mobile state early.

#### JavaScript

1. Remove the hero toggle logic after the hero rewrite.
2. Add only two net-new interaction systems:
   - `How It Works` flow switcher
   - `Platform` tab/segmented-control switcher
3. Keep both interactions progressively enhanced:
   - first state visible without JS
   - buttons/tabs update ARIA state when JS is available
4. Re-test the mobile nav after the nav link list changes.

### Phase E — Verification

1. Confirm the new section order does not create excessive page fatigue.
2. Check nav overflow and tap targets on mobile after adding the new anchors.
3. Verify that every CTA points to a real destination before deploy.
4. Re-check all product/security claims against the `blindpass` core docs before merging.
5. Confirm conceptual visuals are labeled in any place that could imply a live hosted UI.
6. Check that pricing and `x402` are visually separated enough to avoid billing confusion.
7. Update [`SPEC.md`](SPEC.md) and [`README.md`](README.md) if the public section map, CTA structure, or design token usage changes materially.

---

## Source Notes

Primary source documents reviewed:

- `/home/hvo/Projects/blindpass/README.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Brainstorm Secure Secret System.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3A - Hosted Platform.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3B - UI & Operations.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3D - Autonomous Payments & Crypto Billing.md`
- `/home/hvo/Projects/blindpass/docs/architecture/Phase 3E - Hosted Hardening, Ecosystem & Launch.md`
- `/home/hvo/Projects/blindpass/docs/guides/policy.md`
- `/home/hvo/Projects/blindpass/docs/security/Security Audit.md`
