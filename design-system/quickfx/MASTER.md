# QuickFX — Design System Master File

> **LOGIC:** When building a specific page, first check `design-system/quickfx/pages/[page-name].md`.
> If that file exists, its rules **override** this Master file.
> If not, strictly follow the rules below.

---

**Project:** QuickFX
**Product:** Premiere Pro plugin — keyboard-triggered search popup for finding and applying effects
**Category:** Developer Tool / IDE × Creative Tool / Video Editor
**Audience:** Professional video editors, YouTubers, motion designers
**Brand Personality:** Fast, precise, professional but not corporate — "pro tool that respects your time"
**Stack:** HTML + Tailwind CSS
**Generated:** 2026-03-19

---

## 1. Brand Identity

### Voice & Tone
- **Do:** Direct, confident, technical but approachable. Short sentences. Active voice.
- **Don't:** Corporate jargon, hype language, exclamation marks, "revolutionary"
- **Examples:**
  - Good: "Find any effect in under a second."
  - Good: "Type. Select. Apply. Done."
  - Bad: "Revolutionize your editing workflow!!!"
  - Bad: "QuickFX leverages cutting-edge AI to synergize..."

### Brand Metaphors
- Command palette (VS Code Cmd+K, Spotlight, Raycast)
- Keyboard-first interaction
- Lightning speed, zero friction
- "The search bar your timeline deserves"

---

## 2. Page Pattern

**Pattern:** Product / Single Tool Landing (NOT marketplace)

**Hero Strategy:** Demo-led hero — show the search popup in action (screenshot or video). The product IS the hero. No abstract illustrations.

**Section Order:**
1. **Hero** — Headline + animated demo/video of the popup in use
2. **Speed Proof** — "Find any effect in <1s" with keystroke animation or stat
3. **How It Works** — 3-step: Trigger → Search → Apply (keyboard shortcut visual)
4. **Feature Grid** — 4-6 key capabilities (fuzzy search, categories, favorites, etc.)
5. **Social Proof** — Testimonials from editors / YouTubers (keep tight, 2-3 max)
6. **Pricing / CTA** — Single clear action: Download / Buy / Try Free
7. **Footer** — Minimal: links, support, socials

**CTA Strategy:**
- Primary CTA in hero: "Download Free" or "Try QuickFX"
- Sticky CTA on scroll (subtle top bar, not obstructive)
- No "Book a Demo" — this is a self-serve tool

---

## 3. Color System

### Core Palette

| Role | Hex | Tailwind | Usage |
|------|-----|----------|-------|
| **Electric Blue** (Primary) | `#0066FF` | `blue-600` custom | Brand color, primary buttons, links, active states |
| **Blue Glow** | `#3388FF` | `blue-500` custom | Hover states, subtle highlights, icon accents |
| **Blue Wash** | `#0066FF12` | `blue-600/7` | Faint backgrounds, tag fills, subtle tints |
| **Deep Navy** (Surface) | `#0A0E1A` | Custom | Page background (dark mode primary) |
| **Slate Dark** (Card Surface) | `#111827` | `gray-900` | Card backgrounds, elevated surfaces |
| **Slate Mid** (Borders) | `#1F2937` | `gray-800` | Borders, dividers, subtle separators |
| **Cool Gray** (Muted Text) | `#9CA3AF` | `gray-400` | Secondary text, captions, placeholders |
| **Off-White** (Primary Text) | `#F1F5F9` | `slate-100` | Headings, primary body text |
| **Pure White** (Emphasis) | `#FFFFFF` | `white` | High-emphasis text, active items |
| **Success Green** | `#22C55E` | `green-500` | "Applied" confirmations, success states |
| **Warning Amber** | `#F59E0B` | `amber-500` | Alerts, upgrade prompts |
| **Error Red** | `#EF4444` | `red-500` | Error states, destructive actions |

### Color Rules
- **Dark mode is the ONLY mode.** No light mode. Video editors work in dark environments. Premiere Pro is dark. This tool lives inside that context.
- **Electric Blue is accent, not flood.** Use it for interactive elements, focus rings, and highlights — never as large background fills.
- **Text hierarchy through opacity/shade, not color.** White → slate-100 → gray-400 → gray-500 for 4-level hierarchy.
- **Glow is earned.** Reserve blue glow effects for the hero and the search input demo. Don't glow everything.

### Tailwind Custom Config (reference only — do not implement yet)

```
colors: {
  quickfx: {
    blue: '#0066FF',
    'blue-glow': '#3388FF',
    'blue-wash': '#0066FF12',
    navy: '#0A0E1A',
  }
}
```

---

## 4. Typography

### Font Pairing

| Role | Font | Weight | Fallback |
|------|------|--------|----------|
| **Headlines** | **Inter** | 700 (Bold), 600 (Semi) | `system-ui, -apple-system, sans-serif` |
| **Body** | **Inter** | 400 (Regular), 500 (Medium) | `system-ui, -apple-system, sans-serif` |
| **Code / Keyboard / UI Elements** | **JetBrains Mono** | 400, 500 | `'SF Mono', 'Fira Code', monospace` |

### Why This Pairing
- **Inter** — The "developer's sans-serif." Neutral, highly legible, designed for screens. Used by Linear, Vercel, Raycast. Communicates precision without being cold.
- **JetBrains Mono** — For keyboard shortcuts (`Ctrl+Space`), effect names in the search demo, and any code/technical UI. Reinforces the developer-tool DNA.
- NOT using a display/creative font. QuickFX is a tool, not a brand lifestyle. The typography should disappear and let the product speak.

### Type Scale (Tailwind classes)

| Element | Size | Class | Weight | Line Height |
|---------|------|-------|--------|-------------|
| Hero Headline | 48-64px | `text-5xl md:text-6xl` | `font-bold` | `leading-tight` (1.1) |
| Section Headline | 32-40px | `text-3xl md:text-4xl` | `font-bold` | `leading-tight` (1.2) |
| Sub-headline | 20-24px | `text-xl md:text-2xl` | `font-semibold` | `leading-snug` (1.3) |
| Body Large | 18px | `text-lg` | `font-normal` | `leading-relaxed` (1.6) |
| Body | 16px | `text-base` | `font-normal` | `leading-relaxed` (1.6) |
| Caption / Small | 14px | `text-sm` | `font-medium` | `leading-normal` (1.5) |
| Keyboard Shortcut | 13-14px | `text-sm font-mono` | `font-medium` | — |
| Micro Label | 12px | `text-xs` | `font-medium` | `leading-normal` |

### Typography Rules
- Max line length: `max-w-2xl` (42rem / ~65 characters) for readability
- Hero headline max: `max-w-3xl`
- Keyboard shortcuts always in `font-mono` with a subtle `bg-gray-800 px-1.5 py-0.5 rounded` badge treatment
- Numbers in stats/metrics use `tabular-nums` (Tailwind: `tabular-nums` or `font-variant-numeric: tabular-nums`)

### Google Fonts Import
```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap');
```

---

## 5. Spacing System

Use Tailwind's default 4px base scale. Key spacing tokens:

| Usage | Tailwind | Value |
|-------|----------|-------|
| Tight element gaps | `gap-1` to `gap-2` | 4-8px |
| Icon-to-text | `gap-2` | 8px |
| Button padding | `px-5 py-2.5` or `px-6 py-3` | 20-24px × 10-12px |
| Card internal | `p-6` | 24px |
| Section padding (mobile) | `py-16 px-4` | 64px × 16px |
| Section padding (desktop) | `py-24 px-8` | 96px × 32px |
| Between sections | `space-y-24` to `space-y-32` | 96-128px |
| Container max-width | `max-w-6xl mx-auto` | 1152px |

---

## 6. Effects & Visual Language

### Shadows (Dark Mode Adapted)

| Level | Tailwind / CSS | Usage |
|-------|---------------|-------|
| Subtle | `shadow-sm` + dark override: `0 1px 3px rgba(0,0,0,0.4)` | Default cards |
| Medium | `shadow-md` override: `0 4px 12px rgba(0,0,0,0.5)` | Elevated cards, dropdowns |
| Popup | `shadow-xl` override: `0 12px 40px rgba(0,0,0,0.6)` | The search popup demo |
| Blue Glow | `shadow-[0_0_20px_rgba(0,102,255,0.3)]` | Search input focus, hero CTA |

### Border Radius

| Element | Tailwind | Value |
|---------|----------|-------|
| Buttons | `rounded-lg` | 8px |
| Cards | `rounded-xl` | 12px |
| Search popup | `rounded-2xl` | 16px |
| Tags / badges | `rounded-md` | 6px |
| Avatars | `rounded-full` | 50% |

### Borders
- Default: `border border-gray-800` (subtle, low contrast)
- Hover: `border-gray-700`
- Focus / Active: `border-blue-500` with `ring-2 ring-blue-500/20`
- No thick borders. 1px only. This is a precision tool.

### Glow & Light Effects
- **Search input glow:** `shadow-[0_0_30px_rgba(0,102,255,0.15)]` on the demo popup — suggests the input is alive and ready
- **Gradient accent line:** A thin (`h-px` or `h-0.5`) horizontal gradient (`from-transparent via-blue-500 to-transparent`) as a section divider
- **Subtle radial glow:** Behind the hero, a large soft radial gradient (`radial-gradient(ellipse at center, rgba(0,102,255,0.08) 0%, transparent 70%)`) to draw attention without overwhelming
- **No neon. No hard glow. No animated rainbow borders.** The glow should feel like moonlight, not a nightclub.

### Motion & Animation

| Interaction | Duration | Easing | Effect |
|-------------|----------|--------|--------|
| Button hover | 150ms | `ease-out` | Slight brightness increase, subtle lift (`translateY(-1px)`) |
| Card hover | 200ms | `ease-out` | Border brightens to `gray-700`, subtle shadow increase |
| Focus ring | 150ms | `ease-out` | `ring-2 ring-blue-500/30` fade in |
| Page section reveal | 400ms | `ease-out` | `opacity-0 → 1`, `translateY(8px) → 0`. Subtle. |
| Search popup demo (hero) | 300ms | `cubic-bezier(0.16, 1, 0.3, 1)` | Scale from 0.97 → 1, opacity 0 → 1. Snappy spring. |
| Keystroke animation | 80ms per key | `ease-out` | Keys light up sequentially — suggests speed |

### Motion Rules
- **Fast transitions only.** Nothing over 400ms. This product is about speed — the UI must reflect that.
- **No bounce. No elastic. No playful wobble.** Use `ease-out` or a fast spring curve. The motion should feel decisive.
- **Scroll animations: max 1 per section.** Fade-up on enter is fine. Don't animate every element.
- **Respect `prefers-reduced-motion`.** Disable all non-essential animation.

---

## 7. Component Guidelines

### Buttons

| Type | Style | Usage |
|------|-------|-------|
| Primary | `bg-blue-600 hover:bg-blue-500 text-white rounded-lg px-6 py-3 font-semibold` | Main CTA: "Download", "Try Free" |
| Secondary | `bg-gray-800 hover:bg-gray-700 text-gray-100 rounded-lg px-6 py-3 font-medium border border-gray-700` | Secondary actions |
| Ghost | `text-gray-400 hover:text-white font-medium` | Nav links, tertiary actions |
| Keyboard CTA | Primary button with a `kbd` badge showing the shortcut | Hero CTA with shortcut hint |

### Cards (Feature Cards)
- `bg-gray-900 border border-gray-800 rounded-xl p-6`
- Icon top-left in `text-blue-500`
- Title in `text-white font-semibold`
- Description in `text-gray-400 text-sm`
- No hover lift on feature cards (they're informational, not interactive)

### The Search Popup (Demo Component)
This is the HERO of the entire landing page. Treat it as the centerpiece.
- Dark container: `bg-gray-900 rounded-2xl border border-gray-800 shadow-2xl`
- Search input row: `bg-gray-800 rounded-xl` with blue focus glow
- Results list: Clean rows with `hover:bg-gray-800` highlight
- Effect names in `font-mono text-sm`
- Category tags in `text-xs bg-blue-500/10 text-blue-400 rounded-md px-2 py-0.5`
- The popup should look like it belongs inside Premiere Pro's UI

### Keyboard Shortcut Badges
- `font-mono text-xs bg-gray-800 text-gray-300 border border-gray-700 rounded px-1.5 py-0.5`
- Example: `Ctrl` + `Space`
- Always monospace. Always the badge treatment. These are a signature design element.

### Icons
- **Library:** Lucide icons (consistent stroke width, clean geometry)
- **Size:** 20px for inline, 24px for feature cards, 16px for compact UI
- **Color:** `text-gray-400` default, `text-blue-500` for accent/active
- **NO emoji icons. Ever.**

---

## 8. Imagery & Media

- **Hero:** Animated demo (video or CSS animation) of the search popup in action. NOT a static screenshot if avoidable.
- **Screenshots:** Always in a dark Premiere Pro-like frame. Show the popup in context on a real timeline.
- **Illustrations:** None. This is a tool, not a lifestyle brand. Use the product itself as the visual.
- **Backgrounds:** Dark gradients, subtle grid/dot patterns at low opacity (`opacity-[0.03]`), or nothing. No stock photos.
- **Video:** If using video, autoplay muted with no controls visible. Loop the demo.

---

## 9. Anti-Patterns — Do NOT Use

### Visual
- ❌ **Light mode** — Editors work in dark UIs. A light landing page would feel disconnected from the product.
- ❌ **Gradient text on everything** — One gradient headline max (hero). The rest is solid color.
- ❌ **Neon glow overload** — Subtle glow on 1-2 elements. Not a cyberpunk aesthetic.
- ❌ **Glassmorphism cards** — Too trendy, too fragile in dark mode. Use solid dark surfaces.
- ❌ **Abstract 3D illustrations** — They say nothing about the product. Show the actual product.
- ❌ **Emoji as icons** — Always SVG. Emojis render differently across systems and look unprofessional.
- ❌ **Decorative animations** — Every animation must convey speed or demonstrate the product.

### Typographic
- ❌ **Display/script fonts** — No Lobster, no Playfair, no "creative" fonts. This is a precision tool.
- ❌ **ALL CAPS body text** — Headings can be caps sparingly. Body text never.
- ❌ **Thin font weights (300)** — Poor readability on dark backgrounds. Minimum 400 for body.

### Layout
- ❌ **Long-scroll storytelling** — Keep it tight. 5-7 sections max. Editors are busy.
- ❌ **Multi-column feature grids > 4 columns** — 2-3 columns max. Breathe.
- ❌ **Sticky sidebars** — Single-column flow. This is a product page, not a dashboard.
- ❌ **Pop-up modals for CTAs** — No "subscribe to newsletter" popups. Respect the user.

### Interaction
- ❌ **Slow transitions (>400ms)** — Contradicts the brand promise of speed.
- ❌ **Hover-dependent info** — All info visible by default. Hover enhances, never reveals.
- ❌ **Scroll-jacking** — Never override native scroll. Video editors are power users — don't fight their muscle memory.
- ❌ **Autoplay audio** — Instant close. Never.

### Copy
- ❌ **"Revolutionary" / "Game-changing" / "Next-gen"** — Empty hype. Be specific.
- ❌ **Feature walls** — Don't list 20 features. Highlight 4-6, link to docs for the rest.
- ❌ **Exclamation marks** — Confidence doesn't shout.

---

## 10. Accessibility Requirements

- **Contrast:** All text meets WCAG AA (4.5:1 for normal text, 3:1 for large text)
- **Focus:** Visible `ring-2 ring-blue-500/40 ring-offset-2 ring-offset-gray-900` on all interactive elements
- **Keyboard nav:** Full tab-order support. Test without a mouse.
- **Motion:** Wrap all animations in `@media (prefers-reduced-motion: no-preference)`
- **Alt text:** All product screenshots have descriptive alt text
- **Semantic HTML:** Proper heading hierarchy (h1 → h2 → h3), landmarks, button vs link distinction
- **Color independence:** Never convey meaning through color alone. Use icons + text alongside.

---

## 11. Responsive Breakpoints

| Breakpoint | Tailwind | Layout |
|------------|----------|--------|
| Mobile | Default (< 640px) | Single column, stacked sections, full-width CTA |
| Tablet | `sm:` (640px) | 2-column feature grid |
| Small Desktop | `md:` (768px) | Side-by-side hero layout |
| Desktop | `lg:` (1024px) | Full layout, max-width container |
| Wide | `xl:` (1280px) | Expanded spacing, larger type |

**Container:** `max-w-6xl mx-auto px-4 sm:px-6 lg:px-8`

---

## 12. File & Asset Conventions

- Icons: Inline SVG or Lucide React components
- Images: WebP format, lazy-loaded below the fold
- Fonts: Google Fonts via `<link>` in `<head>` (preconnect to fonts.googleapis.com)
- CSS: Tailwind utility classes. No custom CSS files unless absolutely necessary.
- No CSS-in-JS. No styled-components. Pure Tailwind.

---

## Pre-Delivery Checklist

Before delivering any UI code, verify:

- [ ] Dark mode only — no light backgrounds leaking through
- [ ] Electric blue used as accent only, not as background fill
- [ ] All text passes WCAG AA contrast on dark surfaces
- [ ] `cursor-pointer` on all clickable elements
- [ ] Hover/focus states on all interactive elements (150-300ms transitions)
- [ ] `prefers-reduced-motion` respected for all animations
- [ ] No emojis as icons — SVG only (Lucide)
- [ ] Keyboard shortcuts displayed in `font-mono` badge treatment
- [ ] Hero shows the actual product (search popup), not abstract art
- [ ] Responsive: tested at 375px, 768px, 1024px, 1440px
- [ ] No horizontal scroll on mobile
- [ ] No scroll-jacking or autoplay audio
- [ ] Heading hierarchy: h1 → h2 → h3 (no skips)
- [ ] All images have alt text
- [ ] Page loads fast — fonts swapped, images lazy-loaded
