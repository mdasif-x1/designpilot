---
name: designpilot
description: Context-aware UI/UX design intelligence for Google Antigravity. Activates to guide project discovery, visual direction, design system tokens, responsive layout, interactive states, and accessibility auditing.
---

# DesignPilot — Context-Aware UI/UX Design Intelligence

DesignPilot guides agents through an intentional, evidence-based UI/UX design workflow before implementing interface code. Rather than enforcing a monolithic visual template or applying generic AI tropes (such as unmotivated gradients, repetitive cards, or arbitrary glassmorphism), DesignPilot tailors design decisions to the project's domain, target audience, technical stack, and accessibility standards.

---

## The 6-Stage Cognitive Workflow

When tasked with designing, implementing, or reviewing user interfaces, follow these six sequential stages:

```
┌────────────────────────────────────────────────────────┐
│ Stage 1: Contextual Discovery & Stack Audit            │
└──────────────────────────┬─────────────────────────────┘
                           ▼
┌────────────────────────────────────────────────────────┐
│ Stage 2: Intentional Direction & Rationale             │
└──────────────────────────┬─────────────────────────────┘
                           ▼
┌────────────────────────────────────────────────────────┐
│ Stage 3: Visual System & State Architecture            │
└──────────────────────────┬─────────────────────────────┘
                           ▼
┌────────────────────────────────────────────────────────┐
│ Stage 4: Proportionate Implementation Guidance         │
└──────────────────────────┬─────────────────────────────┘
                           ▼
┌────────────────────────────────────────────────────────┐
│ Stage 5: Defect Sweep & Self-Audit                     │
└──────────────────────────┬─────────────────────────────┘
                           ▼
┌────────────────────────────────────────────────────────┐
│ Stage 6: Honest Verification Declaration               │
└────────────────────────────────────────────────────────┘
```

---

### Stage 1: Contextual Discovery & Stack Audit
Before proposing or writing UI code, inspect the target project's files, configuration, and stylesheets to establish ground truth:
1. **Inspect Target Workspace Evidence:** Check the project's actual directories, routes, components, configuration files, and package manifests (`package.json`, etc.) before asking the user to repeat information already present.
2. **Identify the Project Category:** Determine whether the application is a Developer Tool, B2B SaaS Dashboard, E-Commerce Catalog, Portfolio Showcase, or Institutional Portal based on genuine project evidence. Never treat DesignPilot's own plugin or reference files as evidence of the target application's domain or stack.
3. **Inspect Existing Tech Stack & Tokens:** Identify active styling systems (Tailwind CSS, CSS custom properties, CSS Modules, Vanilla CSS, component libraries). Never overwrite an existing design token system without explicit authorization.
4. **Handling Missing or Ambiguous Context:**
   - If the project is empty, inaccessible, or materially ambiguous, ask at most two focused clarifying questions about missing information that would directly alter the design or technical implementation.
   - If the user explicitly requests a hypothetical concept or provides sufficient prompt context for a proposal, proceed with clearly labeled assumptions rather than unnecessarily blocking.
   - Never invent frameworks, brand guidelines, target personas, business rules, or legal mandates and present them as established facts.

---

### Stage 2: Intentional Direction & Contextual Rationale
Formulate a clear visual strategy grounded in user goals and verified requirements:
1. **Explain the Rationale:** Provide a concise explanation of why the proposed visual tone, hierarchy, and density suit this specific product and audience.
2. **Preserve Established Identity:** If existing brand colors, logos, or styles are present in the project, preserve them as primary accents.
3. **Avoid Trend-Driven Decoration:** Do not add decorative styling (e.g., multi-color neon glows, floating blur spheres) unless it directly reinforces the product's identity or usability.
4. **Distinguish Facts from Assumptions:** Clearly separate confirmed project facts, working assumptions, and illustrative examples. Label invented data points as `[Illustrative Placeholder]` in design specifications, audit notes, and mock-data documentation—not in production-facing interface copy. Example UI copy should use natural, realistic placeholder content appropriate to the confirmed product context, while never inventing real legal requirements, identifiers, eligibility rules, or operational promises.

---

### Stage 3: Visual System & State Architecture
Consult the bundled reference guides to establish cohesive design foundations:
1. **Domain Guidance:** Inspect [references/archetypes.md](references/archetypes.md) for detailed layout structures, information density recommendations, and user journey patterns specific to your detected category.
2. **Design Tokens & Spacing:** Inspect [references/tokens-and-layout.md](references/tokens-and-layout.md) to define semantic color roles (`canvas`, `surface`, `border`, `text-primary`, `text-muted`, `accent`, `status`), typography hierarchy, and spacing scales that integrate with the existing codebase.
3. **Privacy, Security & Regulatory Guardrails:**
   - Never silently assume jurisdiction-specific identifiers (e.g., SSN, National Insurance), eligibility rules, agency SLAs, retention windows, or backend response schemas.
   - Minimize sensitive data collection. Never recommend storing sensitive personal information (PII) in unencrypted browser client storage (`localStorage` or `sessionStorage`), especially on shared or public workstations. Recommend server-side encrypted storage with session timeouts or explicit public computer warnings.
   - Distinguish client-side interface safeguards (e.g., submit button debouncing, input masking, client validation) from guarantees requiring backend enforcement (e.g., transactional idempotency, persistent storage). Do not claim a transaction succeeded or a draft was securely saved until authoritative confirmation is returned.
4. **Interactive State Modeling:** Explicitly model all functionally relevant states:
   - **Default:** Resting visual affordance.
   - **Hover:** Clear luminance or elevation feedback.
   - **Focus-Visible:** High-contrast 2px outline for keyboard accessibility (never use `outline: none` without a visible alternative).
   - **Active / Pressed:** Tactile confirmation (e.g., subtle scale or inset feedback).
   - **Disabled:** Visually de-emphasized with `cursor: not-allowed` and `aria-disabled="true"` while maintaining legible contrast.
   - **Loading / In-Progress:** Non-blocking skeleton loader or status indicator during asynchronous requests; disable duplicate submissions.
   - **Empty / Error:** Clear descriptive guidance with an actionable recovery path.
   - **Confirmation / Recovery:** Distinct confirmation only upon verified success; non-destructive failure alerts that preserve user input for retry.

---

### Stage 4: Proportionate Implementation Guidance
1. **Scope Discipline:** Make modifications proportionate to the user's explicit request. Do not refactor unrelated components or perform unrequested directory reorganizations.
2. **Semantic Structure:** Use appropriate HTML5 semantic landmarks (`<main>`, `<nav>`, `<header>`, `<footer>`, `<section>`, `<article>`, `<button>`, `<input>`) where they improve assistive technology access.
3. **Token Reuse:** Use existing CSS classes or variables rather than hardcoding arbitrary pixel values (e.g., use `var(--space-md)` or Tailwind `p-4`, not `padding: 17px`).

---

### Stage 5: Defect Sweep & Self-Audit
Before delivering the interface, audit the implementation against common pitfalls:
1. **Anti-Patterns Check:** Inspect [references/anti-patterns.md](references/anti-patterns.md) to sweep for forbidden AI tropes (e.g., low-contrast gray text on dark cards, universal 3-card grids, unstyled native forms, or decorative gradient text).
2. **Review Rubric:** Inspect [references/review-rubric.md](references/review-rubric.md) to evaluate the interface across the 7 Quality Pillars:
   - Pillar 1: Purpose & Audience Fit
   - Pillar 2: Information Hierarchy
   - Pillar 3: Visual Coherence
   - Pillar 4: Component & State Completeness
   - Pillar 5: Responsive Adaptation (Mobile 375px, Tablet 768px, Desktop 1280px)
   - Pillar 6: Accessibility (WCAG 2.1 AA text contrast >= 4.5:1, keyboard tab flow)
   - Pillar 7: Stack & Convention Respect

---

### Stage 6: Honest Verification Declaration
Conclude every UI task by reporting an evidence-based verification summary. Strictly separate verified facts, static reasoning, and unverified assumptions:
1. **Evidence-Based Evaluation Rules:**
   - A conceptual design plan is not proof that an implementation works.
   - A source code review is not proof of rendered visual or interactive behavior.
   - Reading or citing this skill is not proof of successful execution in all contexts.
   - Always report **Executed Checks** and **Proposed / Unexecuted Checks** in separate sections.
   - Use explicit statuses: `PASS`, `FAIL`, or `INCONCLUSIVE` based on observable evidence.
   - When a browser, DOM runtime, or testing tool is unavailable, explicitly report the check as `NOT RUN` with the specific environment limitation. Never fabricate or imply test execution.
2. **Standard Verification Levels:**
   - **Level 1 (Static Code Review):** Inspected syntax, semantic markup, and token alignment in source files.
   - **Level 2 (Headless DOM / Computed Inspection):** Inspected computed styles, element hierarchy, or accessibility attributes in a DOM environment.
   - **Level 3 (Interactive & Visual Testing):** Tested clicks, keyboard tab cycles, and captured screenshots via live browser tooling.
3. **Disclosure of Unverified Assumptions & Remaining Risks:** Explicitly list any responsive breakpoint, assistive technology, or interaction that was not tested directly.

---

## Platform Operation & Resource Access Protocol

### 1. Antigravity Customization Architecture
DesignPilot operates within Antigravity's progressive-disclosure customization model:
- **Observed Plugin Discovery:** In the tested workspace, the plugin was discovered in the host registry via `plugin.json` in `.agents/plugins/designpilot/`.
- **Observed Skill Availability:** The `designpilot` skill was listed by the host in its active skill registry.
- **Observed File Accessibility:** During acceptance testing, the agent was able to retrieve and read `SKILL.md` and supporting references on demand using file-reading tools (`view_file`).
- **Workflow & Environment Boundary:** Distinguish host-provided platform capabilities from DesignPilot's own workflow instructions. The agent applies the 6-stage cognitive workflow within its conversation context, while code modifications and verification tests occur via available workspace tools.
- **Evidence-Bounded Platform Scope:** These observations establish discovery, registration, and file accessibility in the tested environment. They do not establish every internal platform mechanism or guarantee behavior across all environments. Do not invent an invocation API or claim that one exists, and do not assert that an internal platform mechanism does not exist unless authoritative platform documentation establishes that fact.

### 2. Bundled Reference Documents
The four supporting documents in `references/` contain specialized reference material:
- [references/archetypes.md](references/archetypes.md): Detailed heuristics for 5 application archetypes.
- [references/tokens-and-layout.md](references/tokens-and-layout.md): Comprehensive token scales, responsive layouts, and contrast rules.
- [references/anti-patterns.md](references/anti-patterns.md): Concrete negative constraints and cliché avoidance.
- [references/review-rubric.md](references/review-rubric.md): 7-pillar quality rubric and WCAG 2.1 AA checklists.

### Tool Access & Fallback Instruction:
Inspect these references on demand using available file-reading tools. If environment permissions prevent reading reference files, **do not pretend to have read them**. State:
> *"Notice: Could not load `references/<file>.md` due to local environment file access restrictions. Proceeding using baseline design principles."*
