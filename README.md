# DesignPilot

> Context-aware UI/UX design intelligence for Google Antigravity.

DesignPilot is an open, lightweight, zero-dependency plugin for Google Antigravity. It guides AI coding agents through an intentional, evidence-based design process before writing interface code. Instead of producing generic AI templates (such as unmotivated gradients, repetitive card grids, and low-contrast text), DesignPilot tailors design decisions to your project's specific domain, audience, existing styling conventions, and accessibility needs.

---

## Key Features

- **Context-Aware Discovery:** Inspects your project dependencies, existing stylesheets, and component architecture before recommending or changing styles.
- **Domain Archetypes:** Applies tailored design heuristics across 5 core categories:
  - Developer Tools & Documentation Portals
  - B2B SaaS & Operational Dashboards
  - E-Commerce Catalogs & Product Pages
  - Portfolio & Editorial Showcases
  - Institutional & Public-Service Portals
- **Stack & Token Respect:** Seamlessly adapts to your existing design tokens (Tailwind CSS, CSS variables, CSS Modules, or component libraries) without unrequested rewrites.
- **Comprehensive State Modeling:** Ensures interactive elements specify default, hover, focus-visible, active, disabled, loading, and error states.
- **Evidence-Based Auditing:** Uses a 7-pillar quality rubric and WCAG 2.1 AA accessibility checklists, reporting verification levels honestly.
- **Zero Runtime Dependencies:** Pure static plugin with no background daemons, external API calls, or telemetry.

---

## Installation & Setup

Antigravity supports loading customizations and plugins from your workspace root or user configuration profile.

> **Pre-Release Evaluation Notice:** DesignPilot is currently in pre-release audit. The public GitHub repository will become active upon official release. For evaluation, use direct local folder placement as described below.

---

### Route 1: Workspace Installation (Verified & Recommended)

Install DesignPilot directly into your project's `.agents/plugins/designpilot` directory. This ensures the plugin is available to any agent session operating within that repository.

> **Workspace Scope Requirement:** Open the root directory of your target project as the active workspace in Antigravity. Workspace plugins are discovered from `.agents/plugins/` relative to the current workspace root.

#### Option A: Direct Local Copy (Pre-Release Evaluation)

Copy the canonical `designpilot` directory into your project's `.agents/plugins/` folder:

**Windows (PowerShell):**
```powershell
# From the root of your target project:
if (!(Test-Path ".agents\plugins\designpilot")) { New-Item -ItemType Directory -Force -Path ".agents\plugins\designpilot" }
Copy-Item -Recurse -Force -Path "C:\Dev\DesignPilot\*" -Destination ".agents\plugins\designpilot"
```

**macOS / Linux:**
```bash
# From the root of your target project:
mkdir -p .agents/plugins/designpilot
cp -R /path/to/DesignPilot/* .agents/plugins/designpilot/
```

#### Option B: Git Clone / Submodule (Post-Release)

Once published to GitHub, direct repository cloning into the workspace will be supported:

```bash
# Post-release workspace clone:
git clone https://github.com/mdasif-x1/designpilot.git .agents/plugins/designpilot
# Or as a Git submodule:
git submodule add https://github.com/mdasif-x1/designpilot.git .agents/plugins/designpilot
```

---

### Route 2: Global User Installation (Documented Location)

Antigravity documentation identifies `~/.gemini/config/` as the machine-local global customization root. Plugins can be placed in `~/.gemini/config/plugins/designpilot` to make them available across workspaces.

*(Note: While `.agents/plugins/` workspace discovery has been verified in local test suites, global nested plugin discovery is based on documented customization roots and has not been independently verified in this test environment).*

**Windows (PowerShell):**
```powershell
$globalPluginDir = "$HOME\.gemini\config\plugins\designpilot"
if (!(Test-Path $globalPluginDir)) { New-Item -ItemType Directory -Force -Path $globalPluginDir }
Copy-Item -Recurse -Force -Path "C:\Dev\DesignPilot\*" -Destination $globalPluginDir
```

**macOS / Linux:**
```bash
mkdir -p ~/.gemini/config/plugins/designpilot
cp -R /path/to/DesignPilot/* ~/.gemini/config/plugins/designpilot/
```

---

## Verifying Plugin Activation

Placing plugin files on disk makes them eligible for discovery. To verify that Antigravity has recognized DesignPilot in the active session:

1. **Check Skills & Customizations View:**

   In Antigravity, open the **Skills & Customizations** view in the sidebar to inspect active plugins, skills, and rules.

2. **Session Verification Prompt:**

   In your Antigravity chat panel, prompt:
   > *"What design plugins or skills are currently available?"*

3. **Expected Confirmation:**

   The agent confirms that the `designpilot` skill is loaded, summarizing its ability to guide project discovery, visual direction, design system tokens, responsive layouts, interactive states, and accessibility audits.

---

## How to Use DesignPilot

Once installed, DesignPilot is recognized by Antigravity's skill registry. The agent retrieves `SKILL.md` on demand when UI design, styling, or frontend reviews are requested, following the 6-stage cognitive workflow within the conversation.

### Example Prompts:
- **Dashboard Feature:**

  *"Design a user management and role assignment table for our B2B SaaS platform using our existing Tailwind tokens."*

- **Developer Documentation:**

  *"Propose a layout structure and code snippet component for our developer documentation site."*

- **Frontend Review:**

  *"Audit our checkout page for responsive behavior, keyboard accessibility, and state completeness using DesignPilot."*

---

## Updating & Uninstallation

### Updating
- **Workspace (Local Copy):** Replace the contents of `.agents/plugins/designpilot` with the updated release files.
- **Workspace (Post-Release Git):** Run `git pull` inside `.agents/plugins/designpilot`.
- **Global:** Replace the contents of `~/.gemini/config/plugins/designpilot` with the updated files.

### Uninstallation
- **Workspace:** Delete only the `.agents/plugins/designpilot` directory.

  > **Caution:** Do not delete the parent `.agents/` folder or other plugins/rules located within `.agents/plugins/`.

- **Global:** Delete only the `~/.gemini/config/plugins/designpilot` directory.

  > **Caution:** Do not delete the parent `~/.gemini/config/` directory or other global configuration files.

- **Recovery from Incomplete Installation:** Delete the `designpilot` directory and re-copy the clean files into place.

---

## Troubleshooting

- **Target Workspace Root:** Plugins located in `.agents/plugins/` are discovered relative to the active workspace root. If your editor is opened to a parent or subfolder, close and reopen the editor directly at your project root.
- **Directory Nesting Check:** Ensure `plugin.json` resides directly at `.agents/plugins/designpilot/plugin.json` (avoid accidental nesting such as `.agents/plugins/designpilot/designpilot/`).
- **Reloading the Window:** If plugin files were copied while the IDE was open, reload the window (`Developer: Reload Window` in VS Code / Antigravity IDE) to force a re-index of customizations.
- **Reference Access Fallback:** If local environment permissions restrict reading supporting files in `references/`, DesignPilot's built-in fallback protocol will notify you and proceed using baseline design principles without failing silently.

---

## Marketplace Status

The Google Antigravity Marketplace (`antigravity-plugins-official`) is a curated plugin registry maintained by Google. DesignPilot v1 is distributed openly via GitHub. Official Marketplace submission is planned for a subsequent release cycle.

---

## License & Contributing

DesignPilot is free and open-source software licensed under the [MIT License](LICENSE). Contributions, bug reports, and archetype feedback are welcome via GitHub issues and pull requests.
