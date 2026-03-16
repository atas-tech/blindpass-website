# Contributing to agent-Kryptos Website

Thank you for your interest in contributing! This is a simple static site, so getting started is straightforward.

## Development Setup

```bash
git clone https://github.com/atas-tech/agent-kryptos-website.git
cd agent-kryptos-website
python3 -m http.server 8080
# Open http://localhost:8080
```

No build tools, no dependencies, no frameworks. Just HTML, CSS, and JS.

## Guidelines

### Design Consistency
- Read `SPEC.md` before making visual changes — it documents the full design system
- Use CSS custom properties from `:root` (don't hardcode colors)
- Follow the glassmorphism card pattern for new components
- Keep the dark theme consistent

### Code Style
- **HTML**: Semantic elements, unique IDs for interactive elements
- **CSS**: BEM-ish naming, grouped by section with clear comment headers
- **JS**: Vanilla only, no frameworks or build tools

### Content Updates
- Keep technical claims accurate — see SPEC.md §3 "Key Claims to Verify"
- Reference source documents in the core `agent-kryptos` repo (https://github.com/atas-tech/agent-kryptos)

### Adding a New Section
1. Add HTML to `index.html` following the existing section pattern
2. Add styles to `style.css` in a new clearly commented block
3. Add `data-animate` to elements that should fade in on scroll
4. Update `SPEC.md` with any new design tokens or patterns
5. Update `README.md` section table

## Pull Request Process
1. Keep PRs focused and small
2. Test on mobile viewport before submitting
3. Verify no console errors
4. Include a screenshot if it's a visual change
