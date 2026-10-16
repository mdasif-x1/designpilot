# DesignPilot — Design Tokens & Layout Reference

Design systems must integrate seamlessly with existing codebases rather than imposing arbitrary external conventions. This guide provides rules for establishing semantic color tokens, typography scales, adaptive spacing systems, responsive grid layouts, and complete component states.

---

## 1. Respecting Existing Token Systems

Before introducing any new styles, inspect the project's existing configuration:
- **Tailwind CSS:** Inspect `tailwind.config.js` or `theme.extend`. Use existing utility classes and extend semantic tokens within the existing configuration.
- **CSS Custom Properties (Variables):** Inspect `index.css`, `globals.css`, or `:root` declarations. Reuse existing `--color-*` and `--space-*` variables.
- **Component Libraries (MUI, Chakra, Radix, Shadcn):** Leverage the library's built-in theme tokens. Do not bypass theme providers with inline raw values.

---

## 2. Semantic Color Architecture

A robust design system defines colors by **functional role**, not by physical hue names. This ensures dark mode compatibility and visual consistency.

### Standard Semantic Roles

| Token Role | Purpose | Contrast Expectation |
| :--- | :--- | :--- |
| `color-canvas-default` | Root page background | Baseline background surface |
| `color-surface-subtle` | Secondary cards, sidebars, table headers | Subtle distinction from canvas |
| `color-surface-elevated` | Modals, dropdown menus, popovers | Clear depth elevation (border or shadow) |
| `color-border-subtle` | Dividers, card boundaries, table grid lines | 3:1 contrast against adjacent surface |
| `color-border-focus` | Keyboard focus ring | Minimum 3:1 contrast against adjacent background |
| `color-text-primary` | Main reading text, high-level headings | Minimum 4.5:1 contrast (WCAG AA) |
| `color-text-muted` | Supporting captions, secondary metadata | Minimum 4.5:1 contrast for legible text |
| `color-action-primary` | Primary button fill, active tab indicator | High-contrast brand or accent color |
| `color-status-success` | Positive confirmations, completed steps | Distinct green hue with text label support |
| `color-status-warning` | Attention alerts, non-blocking notices | Distinct amber/orange hue |
| `color-status-danger` | Form validation errors, destructive actions | High-visibility red with text label support |

---

## 3. Typography & Hierarchy

### Modular Scale Principle
Establish a clear mathematical progression between text elements. If the project lacks a defined scale, use a standard 1.25 (Major Third) or 1.2 (Minor Third) scale:

```css
/* Example Fluid Type Scale (Desktop / Mobile adaptable) */
--font-size-xs:   0.75rem;   /* 12px - Captions, helper text */
--font-size-sm:   0.875rem;  /* 14px - UI labels, table data */
--font-size-base: 1rem;      /* 16px - Body text baseline */
--font-size-lg:   1.125rem;  /* 18px - Subheadings, card titles */
--font-size-xl:   1.25rem;   /* 20px - Section headings (H3) */
--font-size-2xl:  1.5rem;    /* 24px - Major section headers (H2) */
--font-size-3xl:  1.875rem;  /* 30px - Page title (H1) */
--font-size-4xl:  2.25rem;   /* 36px - Hero headline */
```

### Typographic Rules:
1. **Constrain Prose Width:** Long blocks of paragraph text should not exceed 65–80 characters per line (`max-width: 65ch`) to prevent reading fatigue.
2. **Line Height Proportions:** Use tighter line heights on large headings (`line-height: 1.1–1.25`) and generous line heights on body text (`line-height: 1.5–1.6`).
3. **Never Skip Heading Levels:** Structure documents logically (`H1` -> `H2` -> `H3`). Do not jump from `H1` directly to `H4` for visual convenience; style an `H2` with a smaller font class instead.

---

## 4. Spacing & Spatial Rhythm

### Adaptive Spacing Scales
Do not dogmatically force an 8px grid if the existing project uses a 4px, 6px, or fluid rem scale. Match and extend the host project's existing spatial rhythm:

```css
/* Standard 4px / 8px Baseline Scale */
--space-1: 0.25rem; /* 4px  - Compact icon gap */
--space-2: 0.5rem;  /* 8px  - Tight button padding, badge spacing */
--space-3: 0.75rem; /* 12px - Input field vertical padding */
--space-4: 1rem;    /* 16px - Standard component gap, card padding */
--space-6: 1.5rem;  /* 24px - Grid column gap, section padding */
--space-8: 2rem;    /* 32px - Major layout spacing */
--space-12: 3rem;   /* 48px - Page section divider spacing */
```

### Spatial Hygiene:
- **Avoid Arbitrary Values:** Never use random values like `margin-top: 19px` or `padding: 13px`. Use the nearest scale step.
- **Gap Over Margin:** When using CSS Grid or Flexbox, prefer `gap` over manual margins on child elements to prevent collapsed margin bugs.

---

## 5. Complete Component State Modeling

Every interactive element (buttons, form inputs, links, list items) must specify visual feedback for all relevant functional states:

```
┌─────────────────────────────────────────────────────────────┐
│ 1. Default:       Resting baseline affordance               │
│ 2. Hover:         Clear luminance or elevation change       │
│ 3. Focus-Visible: 2px outline with high-contrast offset     │
│ 4. Active:        Immediate pressed/tactile feedback        │
│ 5. Disabled:      Visually de-emphasized + aria-disabled    │
│ 6. Loading:       Non-blocking spinner or skeleton loader   │
│ 7. Empty / Error: Informative text + clear recovery action  │
└─────────────────────────────────────────────────────────────┘
```

### Context-Sensitive State Implementation:
- **Keyboard Focus (Crucial):** Never remove the focus ring (`outline: none`) without providing an explicit `:focus-visible` replacement. Use a high-contrast 2px solid ring with a 2px offset (`outline: 2px solid var(--color-border-focus); outline-offset: 2px;`).
- **Accessible Disabled States:** Do not use arbitrary 40% opacity if it renders text unreadable against the background. Combine a subtle luminance reduction with `cursor: not-allowed` and set `aria-disabled="true"` (prefer `aria-disabled` over hard `disabled` attribute where tooltip explanations are needed).
- **Interactive Affordance:** Non-button clickable elements (e.g., custom card links) must indicate clickability via cursor changes (`cursor: pointer`), border highlights, or subtle elevation shifts on hover.

---

## 6. Responsive Layouts & Fluid Containers

### Responsive Breakpoints
Adapt layouts smoothly across standard viewport boundaries:
- **Mobile Viewports (< 640px):** Single-column vertical stacking, full-width inputs, touch-friendly tap targets (minimum 44x44px), and collapsible off-canvas navigation.
- **Tablet Viewports (640px – 1024px):** Two-column split grids, adaptive sidebars, and fluid tables with horizontal scrolling containers where needed.
- **Desktop Viewports (> 1024px):** Multi-column dashboard layouts, persistent navigation bars, and constrained max-widths (`max-w-7xl` or `1280px`) to prevent stretched interfaces on ultra-wide monitors.

### Anti-Overflow Safeguards:
- Always set `box-sizing: border-box` globally.
- Ensure images and videos are responsive: `max-width: 100%; height: auto;`.
- Avoid hardcoded fixed pixel widths on container elements (use `max-width` instead of `width`).
