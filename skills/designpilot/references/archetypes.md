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

### Intra-Archetype Context Discrimination
Tailor recommendations when evidence confirms the specific audience expertise and reading goals:
- **Expert API / CLI Reference & Quick Lookup:**
  - *IA & Density:* High density; three-column layout (symbol navigation tree, documentation/examples, sticky on-page TOC); minimal prose explanation; high screen real estate for syntax signatures and return types.
  - *Navigation & Search:* Fast keyboard search (`Cmd+K` / `Ctrl+K`) with symbol-type filters (methods, classes, errors); anchor links on every symbol for direct sharing.
  - *Primary Interactions:* Immediate one-click snippet copying with visual badge feedback; interactive parameter expanders; language/framework syntax tabs.
  - *Typography & Visuals:* Monospace code with high glyph distinction; restrained syntax highlighting; subdued chrome.
  - *States:* Fast copy status feedback (`Copy` -> `Copied!` -> `Error`); empty search states with suggested fuzzy search terms; explicit deprecation badges (`[Deprecated: v2.4]`).
  - *Accessibility & Devices:* Desktop-prioritized; full keyboard navigation across code blocks; high-contrast focus rings; responsive horizontal code wrapping.
- **Beginner Learning, Onboarding & Step-by-Step Tutorials:**
  - *IA & Density:* Medium density; linear progressive disclosure; numbered procedural steps; explanatory callouts preceding code snippets.
  - *Navigation & Search:* Sequential Next/Previous step navigation; prerequisite checklists; clear breadcrumbs; table of contents reflecting learning progression.
  - *Primary Interactions:* Collapsible concept explainers; copyable setup commands; inline verification checks (e.g., "Expected terminal output").
  - *Typography & Visuals:* Generous body typography (16px base, 1.5 line height); structured callout cards for tips and caveats.
  - *States:* Step completion indicators (`Step 2 of 5 [✓ Completed]`); contextual troubleshooting hints for common beginner mistakes.
  - *Accessibility & Devices:* Screen-reader friendly step announcements; fully responsive across mobile and tablet viewports for dual-screen learning.

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

### Intra-Archetype Context Discrimination
Tailor recommendations based on task frequency and user operational familiarity:
- **Operational Monitoring & Dense Analytical Workflows:**
  - *IA & Density:* High density; multi-pane dashboard; compact tables with sticky headers; customizable metric widgets; zero decorative padding.
  - *Navigation & Search:* Collapsible multi-level sidebar; global query bar with filter pills; saved view presets.
  - *Primary Interactions:* Multi-column sorting; inline row selection; bulk action toolbars; fast keyboard shortcuts for triage.
  - *Typography & Visuals:* Tabular figures for alignment; strict semantic alert hues; high data-ink ratio.
  - *States:* Non-blocking skeleton loaders during metric polling; inline retry for failed widget queries; modal confirmation on destructive batch actions.
  - *Accessibility & Devices:* Desktop workstation focused (>=1280px); keyboard-accessible data grids with `aria-sort`; accessible horizontal table scroll containers.
- **Guided Workflows for Occasional or Non-Technical Operators:**
  - *IA & Density:* Medium density; focused single-task wizard or card layout; generous spacing; contextual helper text below form fields.
  - *Navigation & Search:* Clear progress bar; simple "Back" and "Continue" actions; breadcrumbs indicating current step.
  - *Primary Interactions:* Form inputs with inline validation on blur; summary review screen before final commitment; undo options where safe.
  - *Typography & Visuals:* Friendly, legible sans-serif; distinct primary action button; clear descriptive field labels without dense operational jargon.
  - *States:* Clear inline field error messaging with actionable guidance; non-destructive failure alerts that preserve inputs; celebratory confirmation on completion.
  - *Accessibility & Devices:* High-contrast form controls; touch-friendly interactive targets (>=44x44px); responsive across laptops and tablets.

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

### Intra-Archetype Context Discrimination
Tailor catalog presentation and purchasing flows to the transaction scale and buyer intent:
- **Luxury or Boutique Consumer Shopping:**
  - *IA & Density:* Low to medium density; generous whitespace; prominent editorial photography and lifestyle imagery; storytelling narrative sections.
  - *Navigation & Search:* Minimalist category navigation; curated collection filters; visual swatch filters.
  - *Primary Interactions:* High-resolution zoomable image gallery; single-item variant selectors; slide-over cart drawer with purchase summary.
  - *Typography & Visuals:* Refined editorial serif or high-character sans-serif; subtle luxury palette; high contrast on primary checkout actions.
  - *States:* Subtle hover scale on product cards; visible selected boundary on color/size swatches; "Sold Out" state with optional waitlist prompt; elegant non-intrusive cart feedback.
  - *Accessibility & Devices:* Descriptive alt text for imagery; keyboard-navigable variant carousels; responsive mobile-first shopping experience.
- **High-Volume B2B Wholesale & Industrial Procurement:**
  - *IA & Density:* High density; tabular catalog with thumbnail, part/SKU number, technical specifications, availability, and tiered pricing.
  - *Navigation & Search:* Parametric faceted search (by dimension, tolerance, material, SKU); quick-order entry pad.
  - *Primary Interactions:* Direct numeric quantity inputs per row; bulk "Add Selected to Order" actions; quote request workflows; reorder from past purchase lists.
  - *Typography & Visuals:* Compact neutral sans-serif; tabular numbers for prices and quantities; utilitarian layout prioritizing scannability over emotive imagery.
  - *States:* Real-time stock availability indicators (`[In Stock: 2,400]`, `[Backorder: 2 Weeks]`); minimum order quantity validation warnings; sticky order subtotal summary.
  - *Accessibility & Devices:* Full keyboard table traversal; accessible labels on dynamic quantity inputs; desktop-oriented with horizontal scroll wrappers.

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

### Intra-Archetype Context Discrimination
Tailor presentation to the creator's discipline and the evaluator's criteria:
- **Visual & Editorial Creative Showcase:**
  - *IA & Density:* Low density; asymmetrical layouts; full-bleed media and video presentations; narrative case-study pacing.
  - *Navigation & Search:* Minimalist header; filter by creative medium (Branding, Motion, Art Direction); smooth anchor scrolling.
  - *Primary Interactions:* Fluid lightbox previews; cursor hover effects indicating interactive media; direct social/email contact links.
  - *Typography & Visuals:* Distinctive display typography reflecting creative voice; curated palette; high contrast prose.
  - *States:* Graceful media skeletons during image load; subtle hover elevation; non-destructive contact form validation.
  - *Accessibility & Devices:* Respect `prefers-reduced-motion` for transitions; accessible image descriptions; fully fluid responsive layouts.
- **Technical & Engineering Case-Study Portfolio:**
  - *IA & Density:* Medium density; structured problem/solution/impact case-study hierarchy; embedded architecture diagrams and code excerpts.
  - *Navigation & Search:* Tagged project indexing (e.g., Systems, Distributed Architecture, Frontend); sticky reading navigation for long case studies.
  - *Primary Interactions:* Interactive before/after performance comparison sliders; deep-linkable section headings; links to live deployments and GitHub repositories.
  - *Typography & Visuals:* Clean technical sans-serif paired with monospace for code snippets; restrained neutral palette with functional accents.
  - *States:* Clear distinction between external repo links and internal case studies; fast-loading static fallback diagrams.
  - *Accessibility & Devices:* High-contrast diagrams with text summaries; structured semantic headings (`H1` -> `H2` -> `H3`); readable across phone and desktop viewports.

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

### Intra-Archetype Context Discrimination
Tailor recommendations based on whether the workflow is citizen-facing or internal administration:
- **Public-Facing Citizen / Student / Customer Services:**
  - *IA & Density:* Medium density; plain-language task groups; single-column form layouts; linear step-by-step wizard.
  - *Navigation & Search:* Direct task search ("Apply for Assistance"); hierarchical breadcrumbs; skip-to-content links; no hover-only menus.
  - *Primary Interactions:* Plain-language input fields; accessible date pickers; clear draft-saving indicators; non-destructive validation error recovery.
  - *Typography & Visuals:* High-legibility system typography (>=16px); 7:1 contrast on reading text; authoritative, calming color palette.
  - *States:* Prominent accessible error summaries linking to invalid fields; server-verified submission confirmations; warnings on shared public devices against unencrypted storage of PII.
  - *Accessibility & Devices:* WCAG 2.1 AA/AAA compliance; 100% keyboard navigable; mobile-first and shared library terminal friendly.
- **Internal Administrative & Case-Processing Workflows:**
  - *IA & Density:* High density; split-pane case review layout (applicant data on left, adjudication/checklist panel on right); dense queue tables.
  - *Navigation & Search:* Case queue filters by priority, status, and assignment; rapid case ID search; persistent module tabs.
  - *Primary Interactions:* Case status update selectors; document verification checkboxes; audit log notes; batch status changes.
  - *Typography & Visuals:* Functional, compact sans-serif; tabular timestamps and case reference numbers; explicit text status badges (`[Pending Review]`, `[Approved]`, `[Flagged]`).
  - *States:* Modal confirmation for irreversible decisions (e.g., denial, penalty); record lock indicators when another caseworker is editing; automatic server-side draft preservation.
  - *Accessibility & Devices:* Keyboard navigation shortcuts for case review; high contrast indicators; desktop workstation optimized (dual-monitor and 1080p+ layouts).

---

## 6. Context-Sensitive Adaptation Rules
1. **Conceptual Scaffolding, Not Mandatory Templates:** Do not force every listed archetype variant into every recommendation. Do not infer sensitive attributes, business rules, purchasing behaviour, organizational objectives, or user personas without evidence. Use these intra-archetype distinctions as conceptual scaffolding to ensure recommendations materially reflect confirmed project context rather than generic templates.
2. **Preventing Unsupported Feature Invention & Distinguishing Proposals:** Specialized capabilities described in the examples above (such as quote-request workflows, record-lock indicators, batch operational actions, automated server-side draft saving, or before/after comparison controls) and newly recommended UI elements are illustrative possibilities, NOT default requirements.
   - Distinguish existing content and capabilities from newly proposed UI enhancements.
   - When recommending a new code example, banner, modal, interaction, or content block not found in the inspected project, identify it as proposed (e.g., `[Proposed UI Enhancement]`).
   - Never refer to a proposed element or feature as though it already exists.
   - Recommend a specialized feature or content element as an existing capability only when supported by relevant implementation, active configuration, API schemas/contracts, or explicit user-confirmed requirements.
   - If corroborating evidence is missing from the repository, label the capability explicitly as an optional proposal requiring product and backend validation (`[Proposed Feature — Requires Backend / API Validation]`).
   - Never invent backend endpoints, permissions, persistence guarantees, concurrency behaviors, record-locking semantics, or operational business rules and present them as established facts.
