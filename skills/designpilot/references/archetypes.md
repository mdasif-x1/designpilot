# DesignPilot — Application Archetypes Guide

Different product categories demand fundamentally different design heuristics. Applying a consumer landing page aesthetic to an operational dashboard or developer CLI results in visual noise and degraded usability.

This reference provides context-specific guidance across five core application archetypes. Use these guidelines as conceptual scaffolding, not rigid visual templates.

---

## 1. Developer Tools & Documentation Portals

### Context & Audience
- **Target Users:** Software engineers, DevOps specialists, system administrators, and technical contributors.
- **Primary Need:** Fast access to accurate syntax, copyable command snippets, predictable navigation, and high code legibility without distracting marketing decoration.

### Layout & Information Density
- **Density:** High. Prioritize screen real estate for technical content and code examples.
- **Structure:** Multi-column layout with a persistent left navigation sidebar (grouped hierarchically), a central reading column with constrained line length (65–80 characters for text), and an optional right-hand sticky table of contents (On This Page).
- **Header:** Lightweight and utility-oriented: breadcrumbs, version selector, and global keyboard-accessible search (`Cmd+K` / `Ctrl+K`).

### Typography & Color Strategy
- **Typography:** Clean, highly legible sans-serif for UI chrome and prose (e.g., Inter, system-ui). Monospace with distinct glyph differentiation (distinguishing `0`/`O`, `1`/`l`/`I`) for inline code and syntax blocks.
- **Palette:** Neutral slate or graphite canvas. High-contrast foreground text. Semantic syntax highlighting colors with subdued saturation to prevent eye fatigue during extended reading sessions.

### Key Interaction Priorities
- **One-Click Snippet Copying:** Every code block must feature an accessible copy button with clear feedback ("Copied!").
- **Deep Linking:** Headings should feature anchor links on hover to facilitate technical sharing.
- **Low Motion:** Avoid slow scroll-triggered animations or floating decorative objects that delay information retrieval.

---

## 2. B2B SaaS & Operational Dashboards

### Context & Audience
- **Target Users:** Operations managers, analysts, customer support leads, and enterprise specialists.
- **Primary Need:** Monitoring metrics, identifying anomalies, executing repetitive workflows, and processing dense tabular data with minimum cognitive friction.

### Layout & Information Density
- **Density:** High to Medium. Every square pixel must serve an operational purpose.
- **Structure:** Collapsible left navigation bar for system modules. Top app bar for user profiles, notifications, and workspace switching. The main canvas should feature a modular grid of data widgets, metric cards, and filterable tables.
- **Card Usage:** Use container cards strictly to isolate distinct operational widgets (e.g., Key Metrics vs. Recent Transactions). Avoid nesting cards within cards.

### Typography & Color Strategy
- **Typography:** Compact, neutral sans-serif. Use tabular (monospaced) numerals for financial figures, metrics, and timestamps to ensure vertical alignment in tables.
- **Palette:** Subdued surface tones (e.g., light neutral gray or deep charcoal) that allow status indicators to stand out. Semantic alert colors (green for success, amber for warning, red for critical error) must be reserved exclusively for system status.

### Key Interaction Priorities
- **Tabular Data Ergonomics:** Support column sorting, sticky table headers on scroll, inline search/filter bars, and pagination controls.
- **Status Badges:** Use explicit text labels alongside colors (never color alone) to convey status (e.g., `[✓ Active]`, `[⚠ Degraded]`).
- **Modal Confirmation:** Destructive operations (e.g., account deletion, revoking credentials) must require explicit modal confirmation.

---

## 3. E-Commerce & Transactional Catalogs

### Context & Audience
- **Target Users:** Consumers, retail buyers, and B2B procurement agents making transactional purchasing decisions.
- **Primary Need:** Clear product photography, transparent pricing, straightforward variant selection, and a frictionless path to checkout.

### Layout & Information Density
- **Density:** Medium. Ample breathing room to highlight imagery and product specifications.
- **Structure:**
  - **Catalog View:** Responsive grid of product cards with consistent aspect ratios, clear titles, pricing, and ratings.
  - **Product Detail View (PDP):** Two-column split on desktop (gallery on the left, sticky purchasing panel with title, price, variants, and Add to Cart on the right).
- **Navigation:** Prominent category navigation, visual search, cart status indicator, and clear breadcrumbs.

### Typography & Color Strategy
- **Typography:** Polished, brand-appropriate typography (modern sans-serif or refined serif for headings; highly legible sans-serif for prices and descriptions).
- **Palette:** Clean, neutral background (often pure white or soft off-white) to prevent clashing with product imagery. High-contrast accent color reserved strictly for primary purchasing actions (Add to Cart, Checkout).

### Key Interaction Priorities
- **Mobile Tap Targets:** Buttons, variant swatches, and cart toggles must meet minimum 44x44px touch target guidelines.
- **Immediate State Feedback:** Instant visual confirmation when an item is added to the cart (e.g., sliding cart drawer or badge animation).
- **Variant Selection:** Clear active visual boundary around selected sizes or colors; disable out-of-stock options with transparent tooltips.

---

## 4. Portfolio & Editorial Showcases

### Context & Audience
- **Target Users:** Clients, recruiters, curators, design peers, and hiring managers evaluating craft and creative direction.
- **Primary Need:** Engaging visual storytelling, distinct brand personality, immersive media presentation, and an effortless way to review past case studies and contact the creator.

### Layout & Information Density
- **Density:** Low to Medium. Generous whitespace to frame creative work and establish rhythm.
- **Structure:** Asymmetrical or editorial grid layouts. Hero section introducing identity and creative focus, followed by featured project case studies with high-fidelity visual assets, process breakdowns, and contact mechanisms.
- **Navigation:** Minimalist, unobtrusive header that recedes during scrolling to keep the focus on the portfolio pieces.

### Typography & Color Strategy
- **Typography:** Expressive, characterful typography pairings (e.g., distinctive display serif paired with a geometric sans-serif). Generous line height and careful typographic scale.
- **Palette:** Curated, deliberate color palette reflecting the individual's or studio's unique aesthetic. High contrast between text and background to maintain readability across long project case studies.

### Key Interaction Priorities
- **Media Optimization:** Responsive image and video presentation with subtle hover scaling or caption reveals.
- **Smooth Page Transitions:** Subtle, fluid micro-interactions that communicate polish without causing motion sickness.
- **Accessible Contact Path:** Always provide direct, frictionless contact links (email, LinkedIn, GitHub) alongside any contact form.

---

## 5. Institutional & Public-Service Portals

### Context & Audience
- **Target Users:** Citizens, civil servants, students, patients, and community members of diverse ages, abilities, digital literacy levels, and network speeds.
- **Primary Need:** Finding critical public services, legal documentation, application forms, or health records with zero barriers and maximum clarity.

### Layout & Information Density
- **Density:** Medium. Predictable, logical grouping of services with plain-language navigation.
- **Structure:** Single or two-column reading layouts with clear visual headings. Prominent task-oriented search (e.g., "Find property records", "Renew driver's license"). Step-by-step progress indicators for multi-page official forms.
- **Breadcrumbs:** Mandatory hierarchical breadcrumbs on every interior page to prevent disorientation.

### Typography & Color Strategy
- **Typography:** Highly legible, universally available system fonts or robust web fonts (e.g., Public Sans, Roboto, Segoe UI). Strong contrast and generous font sizes (minimum 16px body text).
- **Palette:** Authoritative, trustworthy palette (e.g., navy blue, slate, clean white). High-contrast ratios that exceed baseline WCAG requirements (aiming for 7:1 contrast on core reading surfaces).

### Key Interaction Priorities
- **Extreme Accessibility:** Strict conformance with WCAG 2.1 AA standards: robust keyboard navigation, visible focus indicators, skip-to-content links, and clear form field error summaries.
- **No Complex Hover Dependencies:** All menus and navigation paths must be accessible via direct click or keyboard activation; avoid hover-only dropdowns.
- **Low-Bandwidth Resilience:** Interface must function cleanly even if images or custom web fonts fail to load.
- **Data Minimization & Public Device Privacy:** Collect only data essential to the service. Never recommend storing sensitive personal information (PII) in unencrypted browser storage (`localStorage`), particularly given frequent usage on public library or shared family computers. Recommend server-side encrypted sessions and display clear warnings on shared devices.
- **Configurable Identifiers & Parameterized SLAs:** Never hardcode regional identity formats (e.g., US SSN) or fabricate agency turnaround SLAs. Use generic parameterized identifiers (`[Program Reference / Identifier]`), label mock examples as `[Illustrative Placeholder]` in specifications and documentation (while using realistic, natural placeholder content in user-facing UI copy without inventing legal requirements), and parameterize agency status updates according to actual program agreements.
- **Explicit Submission Boundaries:** Distinguish client-side UI submission states from authoritative backend receipt. Never indicate that an application was accepted until verified confirmation is returned. In the event of network failure, preserve entered form data non-destructively so users can retry without retyping.
