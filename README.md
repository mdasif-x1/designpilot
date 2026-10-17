# DesignPilot

> Context-aware UI/UX design guidance for Google Antigravity.

DesignPilot is an open, lightweight, zero-dependency plugin that guides AI coding agents through an intentional, evidence-based design workflow before writing interface code. Instead of producing generic AI templates (unmotivated gradients, repetitive card grids, and low-contrast text), DesignPilot tailors design decisions to your project's specific domain, existing styling conventions, interactive states, and accessibility requirements.

---

## Quick Install

To use DesignPilot in any project, install it as a workspace-local plugin:

1. **Open your target project** as the root workspace in Google Antigravity.
2. **Install into `.agents/plugins/designpilot`** at your project root:

   **Option A: Clone directly (Recommended for GitHub users)**
   Ensure `.agents/plugins/designpilot` does not already exist or is empty, then run from your project root:
   ```bash
   git clone https://github.com/mdasif-x1/designpilot.git .agents/plugins/designpilot
   ```

   **Option B: Copy from an existing local copy**
   If you already downloaded or cloned DesignPilot locally, copy its contents into your project (replace `<source-path>` with the directory containing DesignPilot):

   *Windows (PowerShell):*
   ```powershell
   if (!(Test-Path ".agents\plugins\designpilot")) { New-Item -ItemType Directory -Force -Path ".agents\plugins\designpilot" }
   Copy-Item -Recurse -Force -Path "<source-path>\*" -Destination ".agents\plugins\designpilot"
   ```

   *macOS / Linux:*
   ```bash
   mkdir -p .agents/plugins/designpilot
   cp -R /path/to/designpilot/* .agents/plugins/designpilot/
   ```

3. **Confirm directory structure:**
   Ensure the destination directory contains:
   - `.agents/plugins/designpilot/plugin.json`
   - `.agents/plugins/designpilot/skills/designpilot/SKILL.md`

   *(Avoid extra nesting such as `.agents/plugins/designpilot/designpilot/`)*.

4. **Verify activation:**
   Inspect the active skills and plugins in Antigravity, or ask in the chat panel:
   > *"What design skills or plugins are currently available?"*

   If the plugin files were added while Antigravity was already open, reload the IDE window so workspace customizations are re-indexed.

> **Verification status:** Workspace-local placement (`.agents/plugins/designpilot/`) is the **tested and verified** installation route. Global user-profile installation (`~/.gemini/config/plugins/designpilot`) is documented in Antigravity architecture references but remains **unverified** in this environment.

---

## Start Using DesignPilot

Once installed in your workspace, DesignPilot activates automatically whenever you request UI/UX design, component styling, or frontend review in Antigravity.

Open your project workspace and try prompts such as:

- **B2B SaaS / Operational Dashboard:**
  > *"Design a user management and role assignment table using our existing Tailwind tokens, including full keyboard and loading states."*

- **Developer Tools / Documentation:**
  > *"Propose a responsive sidebar navigation and code block component for our developer documentation site."*

- **E-Commerce / Catalog:**
  > *"Create an accessible product filter bar and pricing summary that matches our current CSS custom properties."*

- **UI/UX Audit & Review:**
  > *"Audit our checkout form against WCAG 2.1 AA contrast requirements and interactive state completeness using DesignPilot."*

---

## What It Does

DesignPilot provides structured design intelligence across six core areas:

- **Context-First Discovery:** Inspects package dependencies, existing stylesheets, component libraries, and design tokens before proposing or editing interface code.
- **Five Domain Archetypes:** Adapts layout density, typography, and visual hierarchy to the project's specific archetype:
  1. *Developer Tools & Technical Documentation* (high density, monospaced data, persistent navigation)
  2. *B2B SaaS & Operational Dashboards* (data density, scannable tables, state indicators)
  3. *E-Commerce & Marketing Catalogs* (visual clarity, conversion hierarchy, trust signals)
  4. *Portfolios & Editorial Showcases* (expressive typography, generous whitespace, visual rhythm)
  5. *Institutional & Public-Service Portals* (maximum clarity, plain language, resilient contrast)
- **Design-System & Token Respect:** Adheres to your project's existing styling conventions (Tailwind CSS, CSS Modules, styled-components, or plain CSS variables) without forcing unrequested rewrites.
- **Seven-State Modeling:** Ensures interactive elements specify default, hover, focus-visible, active, disabled, loading, and empty/error states.
- **Responsive Layout Guidance:** Provides token-driven breakpoint strategies for mobile, tablet, and desktop views.
- **Evidence-Based Review Rubric:** Audits interfaces across seven quality pillars (context fit, layout hierarchy, color/contrast, typography, state completeness, responsive behavior, and accessibility).

---

## How It Works

DesignPilot operates as a pure prompt-driven skill loaded on demand by Antigravity. It requires no background processes or external network services.

The plugin consists of a central orchestrator and four modular reference documents:

- **`skills/designpilot/SKILL.md`:** The primary skill definition guiding the agent through a six-stage workflow (Context Discovery &rarr; Visual Direction &rarr; Tokens & Layout &rarr; State Modeling &rarr; Review & Rubric &rarr; Delivery).
- **`references/archetypes.md`:** Deep-dive heuristics, layout principles, and anti-patterns for each of the five domain archetypes.
- **`references/tokens-and-layout.md`:** Systematic token scales for spacing, typography, colors, elevation, and layout structures.
- **`references/anti-patterns.md`:** Concrete catalog of generic AI design flaws to actively avoid (such as decorative low-contrast pills, unmotivated gradients, and floating unlabeled cards).
- **`references/review-rubric.md`:** A structured scoring rubric and checklist based on WCAG 2.1 AA standards for pre-commit design audits.

---

## Scope and Limitations

To maintain clear and realistic expectations, understand the scope of DesignPilot's guidance:

- **Design Guidance vs. Runtime Execution:** DesignPilot guides design decisions, layout structures, and static code generation. It does not replace live browser rendering tests, automated unit/E2E test suites, or physical screen-reader verification.
- **Installation Routes:** Workspace-local installation (`.agents/plugins/designpilot`) is fully verified. Global installation via `~/.gemini/config/plugins/` is supported by Antigravity's architecture but has not been independently validated in this test suite.
- **No Command-Line Interface:** DesignPilot does not provide an `agy` CLI command, npm package, or one-click marketplace installer. Installation is accomplished by placing the plugin directory into the project workspace.
- **Zero Runtime Overhead:** DesignPilot contains no compiled binaries, background daemons, or telemetry collection. It executes purely within the Antigravity agent context.

---

## License & Repository

- **License:** Free and open-source software under the [MIT License](LICENSE) (Copyright &copy; 2026 MD Asif).
- **Repository:** [https://github.com/mdasif-x1/designpilot.git](https://github.com/mdasif-x1/designpilot.git)
- **Issues & Contributions:** Bug reports, documentation improvements, and archetype suggestions are welcome via GitHub issues and pull requests.
