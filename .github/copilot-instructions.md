# vellabs.github.io Copilot Instructions

## Project Overview
This is a **static marketing website** for the vellabs open-source community. It's a pure HTML/CSS site with no backend, no build process, and no framework—designed for simplicity, performance, and direct customization.

**Key Files:**
- [index.html](../index.html) - Single-page layout with hero, about, features, contribute, community, contact, and footer sections
- [styles.css](../styles.css) - Complete styling (~770 lines) using CSS Grid, Flexbox, gradients, and CSS custom properties
- [README.md](../README.md) - Comprehensive setup and customization guide

## Architecture & Design System

### Layout Pattern: Container-Based Responsive Grid
All sections use this pattern:
```html
<section class="section-name">
  <div class="container">
    <!-- Content in grid or flex -->
  </div>
</section>
```
- `.container` has `max-width: 1200px` with `0 20px` padding
- Sections use `padding: 80-100px 0` for vertical rhythm
- Grids use `grid-template-columns: repeat(auto-fit, minmax(X, 1fr))` for responsive behavior

### Color System (CSS Variables)
Located at `:root` in [styles.css](../styles.css#L8-L18):
- `--primary: #6366f1` (indigo) - Primary brand color used in buttons, gradients, icons
- `--secondary: #ec4899` (pink) - Accent color in gradients and highlights
- `--dark: #1f2937` - Text color
- `--light: #f9fafb` - Section backgrounds
- Always use these variables instead of hardcoding colors

### Typography
- Body: `'Inter', sans-serif` (weights: 400, 500, 600, 700)
- Code: `'JetBrains Mono', monospace` - Used only in `.code-block` sections
- Link to [Google Fonts](https://fonts.googleapis.com) at top of [index.html](../index.html#L8-L11)

### Button Styles
Three variants:
- `.btn.btn-primary` - Gradient background, white text, lift on hover
- `.btn.btn-secondary` - Transparent with border, inverts on hover
- `.btn-small` - Compact version for community channels

## Common Patterns & Development Conventions

### Adding New Sections
1. Create `<section class="section-name">` with `.container` inside
2. Style with `padding: 80px 0` and optional light background
3. Use semantic heading (`<h2>`) that inherits center-aligned styling
4. Follow grid/flex layout patterns from existing sections (hero, features, contribute)

### Card Components
Reusable card pattern used in about, features, community sections:
```css
.card {
  background: white;
  padding: 30-40px;
  border-radius: var(--border-radius);  /* 12px */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  transition: var(--transition);  /* all 0.3s ease */
  border: 1px solid var(--gray-light);
}
.card:hover {
  transform: translateY(-10px);  /* Lift effect */
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
}
```

### Smooth Scrolling & Navigation
- `html { scroll-behavior: smooth }` enables smooth anchor scrolling
- Navbar is sticky (`position: sticky; top: 0`) with backdrop blur
- All section IDs match nav links: `#about`, `#contribute`, `#community`, `#contact`

## Customization Points

### Update Community Branding
- **Name**: Search `vellabs` in [index.html](../index.html) - appears in title, nav logo, multiple headings, footer
- **Logo Icon**: Change `.logo-icon` content (currently `◎`) - consider emoji or SVG
- **Colors**: Modify CSS variables at `:root` to rebrand from indigo/pink

### Update Social/Contact Links
These are placeholders pointing to `#`:
- Discord, Twitter, GitHub, Email in [index.html](../index.html#L240-L270)
- Replace `href="#"` with actual community URLs
- Footer social links also need updates

### Content Updates
All marketing copy is in semantic HTML—modify directly in [index.html](../index.html). Key sections:
- Hero pitch (lines ~30-40)
- About mission cards (lines ~50-75)
- Feature items (lines ~90+)
- Contribution steps and types (lines ~160+)
- Community channels (lines ~190+)

## Deployment & Testing

### Local Testing
Three methods documented in [README.md](../README.md#L47-L66):
```bash
# Preferred: Python HTTP server (no dependencies)
python -m http.server 8000

# Or: Node.js
npx http-server

# Or: macOS direct open
open index.html
```

### GitHub Pages Deployment
This repo is configured for GitHub Pages (`.github.io` domain structure). On push to main:
- Static files serve automatically
- No build process needed
- Works immediately at repository URL

## Key Decisions & Why

**No Framework/Build Process**: This is intentional—simplicity + performance + zero dependencies
**Single HTML File**: Easier to customize branding, faster load, all context visible at once
**CSS Grid + Flexbox**: Modern browser support (>95%), responsive without media queries where possible
**Smooth Transitions**: Subtle animations (0.3s ease) throughout—consistent via `--transition` variable

## Common Tasks

**Add a new feature to "Why Choose vellabs?"**
→ Add `.feature-item` div to [styles.css](../styles.css#L240) features-grid section with `h4` and `p`

**Change button styling globally**
→ Modify `.btn-primary`, `.btn-secondary`, or `.btn-small` classes in [styles.css](../styles.css#L108-L160)

**Adjust spacing/padding for sections**
→ Modify section `padding` values and `.container` max-width/padding in [styles.css](../styles.css)

**Update responsive breakpoints**
→ Search `@media` in [styles.css](../styles.css) (sections at bottom)—currently optimized for mobile-first
