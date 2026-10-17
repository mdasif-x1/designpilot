# DesignPilot — Quality Evaluation Rubric & Review Guide

This guide establishes the objective quality standards for auditing user interfaces generated or modified by AI coding agents. Every design should be reviewed against seven core pillars before delivery.

---

## The 7 Quality Pillars

### Pillar 1: Purpose & Audience Fit
- **Evaluation:** Does the visual density, typography character, and tone match the specific application archetype (Developer Tool, B2B SaaS, E-Commerce, Portfolio, Institutional)?
- **Pass:** Visual hierarchy and density directly reflect the user persona's core tasks.
- **Fail:** Applying an inappropriate generic consumer template to an enterprise or technical tool.

### Pillar 2: Information Hierarchy & Scannability
- **Evaluation:** Can a user scan the interface and identify the primary action or primary metric within 3 seconds?
- **Pass:** Clear visual dominance for primary actions; logical heading hierarchy (`H1` -> `H2` -> `H3`); supporting details visually subordinate.
- **Fail:** Competing high-contrast buttons; inverted heading levels; visual clutter with equal weight given to all items.

### Pillar 3: Visual Coherence & Token Discipline
- **Evaluation:** Are spacing, typography, and color tokens consistent throughout the layout?
- **Pass:** Strict adherence to semantic color tokens and defined spacing increments (e.g., matching the project's scale).
- **Fail:** Arbitrary inline pixel margins (`margin-top: 17px`), clashing font sizes, unmotivated decorative neon borders.

### Pillar 4: Component & Interaction State Completeness
- **Evaluation:** Are all applicable interaction states accounted for?
- **Pass:** Visible hover, focus-visible, active, disabled, loading, and error states on interactive elements where functionally relevant.
- **Fail:** Missing focus outlines, unstyled native inputs, links without hover affordance, unhandled empty or error states.

### Pillar 5: Responsive Adaptation & Device Context
- **Evaluation:** Does the interface adapt appropriately to its confirmed target deployment environment without content clipping, horizontal overflow, or broken interactions?
- **Pass (Public Responsive Web):** Fluid reorganization across relevant mobile, tablet, and desktop viewports (using 375px, 768px, and 1280px as useful test viewports when appropriate, without assuming every product must support every width); touch targets meet touch guidelines on touchscreens.
- **Pass (Desktop / Workstation Tools):** Ergonomic utilization of wide screens; content reflow and readable containment without horizontal page breaking at standard laptop widths (e.g., 1024px or 1280px); keyboard navigability preserved. An interface is not penalized solely because it does not transform into a stacked 375px mobile view.
- **Pass (Mobile-First / Kiosk):** Layout optimized for confirmed handheld or fixed touch viewports without desktop bloat.
- **Fail:** Unintended horizontal scrollbars at supported sizes; clipped text or overlapping controls; inaccessible touch targets or broken keyboard focus; using device context as an excuse for poor reflow, clipped data, or genuine accessibility failures.
- *Notice:* Clearly distinguish static source inspection of CSS rules from empirically verified rendering. Static code review cannot prove that an interface renders without layout breakage.

### Pillar 6: Accessibility (WCAG 2.1 AA Checklist)
- **Evaluation:** Does the interface respect baseline web accessibility standards?
- **Checklist:**
  - [ ] **Contrast:** Minimum 4.5:1 contrast ratio for normal text; 3:1 for large text (>= 18pt / 24px) and essential UI icons against their background.
  - [ ] **Keyboard Flow:** All interactive elements can be reached and activated using <kbd>Tab</kbd>, <kbd>Enter</kbd>, and <kbd>Space</kbd>.
  - [ ] **Focus Rings:** Distinct, high-contrast 2px focus indicators visible on keyboard navigation.
  - [ ] **Form Labels:** Every input has an associated `<label>` or explicit `aria-label`.
  - [ ] **Color Independence:** Status and errors are communicated through text labels or icons in addition to color.
- *Notice:* Passing an automated checklist provides necessary baseline assurance, but does not substitute for testing with real assistive technology or diverse users.

### Pillar 7: Stack & Convention Respect
- **Evaluation:** Did the agent respect the project's existing build system, CSS framework, component libraries, and design-system conventions?
- **Pass:** Reuses existing Tailwind utility patterns, CSS custom properties, or component library conventions without unrequested rewrites; inspects existing component props before recommending implementation; avoids combining semantic variants with conflicting utility classes; transparently explains token/variant gaps instead of silently inventing them; chooses smaller compatible options over mandating new danger tokens or variants.
- **Fail:** Introducing an unrequested external framework, swapping CSS solutions, or creating redundant inline styling systems; combining semantic variants with clashing utility classes; silently expanding design tokens without disclosure; mandating redundant danger tokens or component variants when existing conventions suffice.

---

## Verification Levels & Honest Reporting Contract

AI agents must report the exact level of verification achieved for each task. Never claim an interface was visually inspected or interaction-tested unless that specific action was genuinely performed.

### Core Verification Principles:
1. **Plans Are Not Proof:** A conceptual design proposal is not proof that an implementation functions or meets accessibility standards.
2. **Static Code Is Not Rendered Behavior:** Static inspection of source markup cannot verify computed layout rendering, sub-pixel alignment, or assistive technology compatibility.
3. **Skill Reading Is Not Execution:** Ingesting this skill into conversation context does not guarantee absence of bugs; compliance must be verified against actual output.
4. **Separation of Executed vs. Proposed Checks:** Always group checks into **Executed Checks** (supported by observable tool output) and **Proposed / Unexecuted Checks**.
5. **Rigorous Status Labeling:**
   - **`PASS`:** Supported by concrete, observable evidence from executed inspection or tests.
   - **`FAIL`:** Concrete evidence of a defect, regression, or unmet requirement.
   - **`INCONCLUSIVE`:** Evidence is incomplete, ambiguous, or unverifiable in the current session.
   - **`NOT RUN`:** Required tool, browser, or runtime was unavailable. Always report the exact limitation. Never fabricate or imply completion.
6. **Feature & Content Attribution:** Distinguish existing content and capabilities from newly proposed UI enhancements. When recommending a new code example, banner, modal, interaction, or content block not found in the inspected project, identify it as proposed. Never refer to a proposed element as though it already exists.
7. **Avoid Unsupported Specificity:** Do not present unverified durations, timeouts, thresholds, API behavior, or business rules as established project requirements. Numeric values may be suggested as illustrative defaults when useful, but label them as proposals and explain that project conventions or requirements should determine the final value.
8. **Evidence Clarity:** Make the distinction between observed facts, inferences, and proposals explicit wherever confusion is reasonably likely. Prefer concise section labels or targeted inline tags over mechanically tagging every sentence. Ensure the distinction works for both audits and new-design recommendations without making normal output verbose or repetitive.

### Level 1: Static Code Inspection
- **Definition:** The agent reviewed source markup, CSS rules, component props, and token declarations using file reading tools.
- **Report Example:** *"Verified via static code inspection: Semantic HTML tags (`<main>`, `<nav>`) used; Tailwind classes match existing token scale; heading hierarchy strictly ordered H1-H3."*

### Level 2: Headless DOM & Computed Style Inspection
- **Definition:** The agent rendered the component or page in a headless runtime environment and inspected computed styles, accessibility attributes, or DOM tree structures.
- **Report Example:** *"Verified via DOM inspection: Computed text color `#1f2937` against background `#ffffff` achieves 12.6:1 contrast; all form controls possess linked `<label>` elements."*

### Level 3: Interactive & Visual Testing
- **Definition:** The agent used browser automation tools to capture screenshots, record session video, or simulate user clicks, keyboard tab cycles, and viewport resizes.
- **Report Example:** *"Verified via live browser testing: Captured visual screenshot at 375px and 1280px viewports; confirmed zero horizontal overflow; verified keyboard tab focus rings on all form inputs."*

### Mandatory Reporting Rule:
If an interface was only verified at Level 1, explicitly disclose any unverified visual aspects:
> *"Notice: Responsive behavior and interactive focus rings were verified via static CSS inspection; live visual rendering was not tested in a browser."*
