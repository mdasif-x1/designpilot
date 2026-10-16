# DesignPilot — Anti-Patterns & Cliché Prevention Guide

AI-generated interfaces often suffer from predictable, superficial styling trends that harm usability, legibility, and brand distinction. This reference identifies the most frequent UI anti-patterns, explains why they fail, and defines context-appropriate alternatives.

Visual techniques (such as gradients, cards, and glassmorphism) are not categorically prohibited; they are acceptable when they serve a demonstrable functional purpose.

---

## 1. Low Contrast & Inaccessible Text

### The Failure Mode
Using light gray text on white backgrounds, or dark slate text on black cards, to create a "subtle" or "sleek" aesthetic.

### Why It Fails
Violates WCAG 2.1 AA standards (minimum 4.5:1 contrast for body text; 3:1 for large text). Renders content unreadable for users with low vision, in bright ambient sunlight, or on low-quality displays.

### The Fix
Always calculate or verify contrast ratios against the actual computed background. Use semantic text tokens (`color-text-primary` and `color-text-muted`) that guarantee sufficient contrast in both light and dark themes.

---

## 2. Gratuitous Multi-Color Fluorescent Gradients

### The Failure Mode
Applying vibrant purple-to-cyan or pink-to-orange gradient fills to headlines, card borders, and page backgrounds on everyday utility interfaces.

### Why It Fails
- Gradient text frequently clips descenders (`g`, `y`, `p`) when using `-webkit-background-clip: text`.
- Multi-color borders distract the eye from data hierarchy.
- Imparts a generic, amateur "crypto/AI landing page" look to professional tools.

### When Gradients ARE Justified:
- Subtle monochromatic atmospheric lighting in a hero background (e.g., soft radial glow behind an editorial hero image).
- Gentle linear elevation gradient on primary buttons to provide depth.

---

## 3. Purposeless Glassmorphism

### The Failure Mode
Applying `backdrop-filter: blur(12px)` with semi-transparent white/black backgrounds across dense tables, dashboard cards, and form inputs.

### Why It Fails
- Text rendered on blurred backgrounds experiences contrast variations depending on what is scrolling underneath.
- Extreme performance penalty: multiple nested `backdrop-filter` layers trigger high GPU composite rendering overhead and battery drain.

### When Glassmorphism IS Justified:
- Sticky navigation headers or bottom navigation bars where seeing blurred page content scrolling beneath helps maintain spatial orientation.
- Modal backdrops or subtle toast overlays.

---

## 4. "Card-itis" (Repetitive 3-Card Grid Slop)

### The Failure Mode
Boxing every single piece of content into an identical 3-column card grid with uniform padding, rounded corners, and drop shadows, regardless of content relationship.

### Why It Fails
- Creates repetitive visual monotony.
- Flattens information hierarchy: primary metrics, secondary notes, and tertiary logs receive identical visual prominence.
- Wastes screen real estate with excessive container borders and margins.

### The Fix
Use varied layout structures: tabular lists for sequential data, asymmetric splits for featured content, key-value grids for specifications, and borderless sections separated by clean typographic whitespace.

---

## 5. Unstyled Form Controls & Stripped Focus Outlines

### The Failure Mode
Leaving HTML `<input>`, `<select>`, and `<textarea>` elements with browser-default styling, or stripping focus rings via `outline: none` without providing an alternative.

### Why It Fails
- Keyboard users navigating via <kbd>Tab</kbd> become completely blind to the currently active element.
- Default browser form styling looks disconnected from custom design systems.

### The Fix
Always provide explicit `:focus-visible` styles with a high-contrast 2px solid ring and offset. Style inputs consistently with custom design tokens for height, padding, border radius, and active states.

---

## 6. Missing Interaction & Async States

### The Failure Mode
Designing only the static "happy path" resting state, leaving buttons without hover feedback, lists without empty states, forms without validation errors, and async actions without loading indicators.

### Why It Fails
Users are left guessing whether a click registered, what went wrong during an error, or whether data is still loading.

### The Fix
Model all seven core interaction states (Default, Hover, Focus-Visible, Active, Disabled, Loading/Skeleton, Empty/Error) for every interactive feature.

---

## 7. Scope Creep & Unrequested Framework Rewrites

### The Failure Mode
Replacing an existing Tailwind CSS setup with custom CSS modules, introducing an unrequested icon library, or refactoring unaffected layout components during a minor UI fix.

### Why It Fails
Causes massive merge conflicts, bloats production bundle sizes, and breaks established developer workflows.

### The Fix
Strictly respect the existing repository stack, CSS architecture, and component libraries. Make changes proportionate to the prompt.

---

## 8. Fabricated Regulatory Assumptions & Insecure Client PII Storage

### The Failure Mode
Hardcoding regional identification formats (e.g., assuming US Social Security Numbers for generic public portals), promising specific agency turnaround SLAs (e.g., "processed within 3 business days"), or advising developers to store unencrypted applicant personal data in browser `localStorage`.

### Why It Fails
- Violates privacy regulations (GDPR, Privacy Act, HIPAA) and creates severe data breach liability on shared computers (libraries, schools, shared homes).
- Imposes fictitious legal or operational commitments that backend services or agencies cannot honor.
- Assumes specific national administrative systems when the product or user context may be international or local.

### The Fix
Parameterize identity and document requirements according to verified program rules. In design specifications and mock-data notes, label invented sample values as `[Illustrative Placeholder]`, while presenting natural, realistic placeholder copy in the UI itself without inventing real legal requirements, identifiers, or operational promises. Recommend encrypted server-side session stores for sensitive draft data with explicit public workstation warnings, and distinguish client UI safeguards from backend transaction guarantees.
