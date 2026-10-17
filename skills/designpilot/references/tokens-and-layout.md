# DesignPilot — Design Tokens & Layout Reference

Design systems must integrate seamlessly with existing codebases rather than imposing arbitrary external conventions. This guide provides rules for establishing semantic color tokens, typography scales, adaptive spacing systems, responsive grid layouts, and complete component states.

---

## 1. Respecting Existing Token Systems

Before introducing any new styles, inspect the project's existing configuration:
- **Tailwind CSS:** Inspect `tailwind.config.js` or `theme.extend`. Use existing utility classes and extend semantic tokens within the existing configuration.
- **CSS Custom Properties (Variables):** Inspect `index.css`, `globals.css`, or `:root` declarations. Reuse existing `--color-*` and `--space-*` variables.
- **Component Libraries (MUI, Chakra, Radix, Shadcn):** Leverage the library's built-in theme tokens. Do not bypass theme providers with inline raw values.

### Component & Design-System Integrity
1. **Inspect Supported Props & Conventions:** When an existing component is present, inspect its supported props, variant APIs, and styling conventions before recommending or writing implementation code.
2. **Prevent Variant & Utility Conflicts:** Do not combine a semantic component variant (e.g., `variant="destructive"` or `variant="outline"`) with conflicting utility classes (such as overriding color, background, or padding classes) unless the project's styling mechanism explicitly supports that pattern.
3. **Transparent Token & Variant Gaps:** If a needed semantic variant or token is absent, explain the gap and offer a compatible proposal; do not silently expand the design system or claim the extension already exists.
4. **Proportionate, Compatible Additions:** Do not mandate a new danger token or component variant when a smaller compatible option is supported by existing conventions.

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

## 6. Contextual Responsive Layouts & Device Adaptation

### Target Device Environment Discovery
Before prescribing layout breakpoints or mobile adaptation rules, inspect project evidence to determine the actual target deployment environment:
- **Public Responsive Web Application:** Broad public reach across smartphones, tablets, laptops, and ultra-wide desktops.
- **Mobile-First Application:** Primarily designed for touchscreens, handheld portrait usage, and constrained bandwidth.
- **Desktop-Oriented Professional Tool:** Power-user tool optimized for dense mouse/keyboard interaction, multi-column layouts, and wide monitors.
- **Internal Workstation Application:** Mission-specific enterprise software deployed on standardized desktop/laptop hardware.
- **Kiosk, Shared Device, or Constrained Embedded Interface:** Fixed display resolutions, touch-only or specialized inputs, and public physical security considerations (when explicitly evidenced).

### Contextual Adaptation Rules:
1. **Conventions Are Evidence, Not Law:** Existing media queries in stylesheets indicate historical conventions, not necessarily the complete intended supported device range. Check explicit requirements, target personas, input methods, content width, and deployment constraints.
2. **Preserve Working Conventions:** Preserve existing responsive behavior and grid systems unless a justified, requested change demands modification.
3. **Flexible Test Viewports:** Treat 375px (mobile), 768px (tablet), and 1280px (desktop) as useful verification viewports when relevant, not universal design laws.
4. **Desktop Tools Do Not Require Mobile-First Redesigns:** A desktop-oriented operations dashboard or developer CLI viewer must not be forced into a mobile-first stacked layout. Focus on desktop ergonomics (dense data display, keyboard shortcuts) while ensuring graceful reflow and preventing horizontal breakage down to smaller desktop or laptop windows (e.g., 1024px or 1280px), in accordance with WCAG 1.4.10 (Reflow).
5. **Breakpoints Do Not Equal Responsiveness:** A public web application cannot be declared responsive merely because CSS `@media` rules exist; inspect whether content overflows, navigation collapses cleanly, and forms remain usable across viewports.
6. **Context-Sensitive Interactive Target Sizing:**
   - While baseline WCAG 2.1 AA does not mandate a specific minimum touch-target dimension (WCAG 2.1 Criterion 2.5.5 Target Size is Level AAA, recommending 44x44px), providing generous target sizes (>=44x44px) serves as strong ergonomic design guidance on touchscreen interfaces and mobile viewports to prevent mis-taps.
   - For desktop workstation interfaces operated primarily via mouse and keyboard, interactive elements (such as compact data-table action icons) do not require artificial touch padding, but must maintain clear visual spacing, unambiguous pointer affordance, and high-contrast visible keyboard focus indicators (`:focus-visible`).
   - Never use desktop context to excuse cramped, overlapping controls, missing focus outlines, or keyboard inaccessibility.
7. **Accessibility Distinct from Preference:** Distinguish mandatory accessibility constraints (e.g., 400% zoom reflow, keyboard focusability, minimum contrast) from elective aesthetic layout preferences.
8. **Handling Unknown Device Context:** When the target device context is unevidenced and materially alters the layout architecture, ask a focused clarifying question (subject to the two-question budget) or explicitly declare the assumed device target.

### Anti-Overflow Safeguards:
- Always set `box-sizing: border-box` globally.
- Ensure media elements are fluid: `max-width: 100%; height: auto;`.
- Avoid hardcoded fixed pixel widths on container elements (use `max-width` instead of `width`).
- Use horizontal scroll wrappers (`overflow-x: auto`) around wide data tables to protect surrounding layouts on narrower viewports.
