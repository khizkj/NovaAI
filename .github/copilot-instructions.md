## Purpose
Provide targeted instructions so an AI coding agent can be immediately productive in this repository.

Keep guidance brief and actionable (20–50 lines). Reference concrete files and examples found in the codebase.

---

### Big picture (what this repo is)
- Static marketing site built with plain HTML/CSS/vanilla JS. Primary pages: `index.html` and `services.html` in the repository root.
- No backend, package.json, or build step detected. Styling uses Tailwind via CDN and custom CSS blocks inside each HTML file.

### Key files to read first
- `index.html` — main entry. Contains hero, features, nav, footer and inline scripts. Examples:
  - `pages` JS object contains demo HTML for other pages (lines where navigation is simulated).
  - Theme state is stored in `localStorage` under key `theme` and toggled by adding/removing the `dark` class on `<html>`.
- `services.html` — service detail page. Mirrors patterns used in `index.html` (Tailwind CDN, AOS animations).

### Developer workflow & quick run
- No build step: open `index.html` in a browser to preview. On Windows PowerShell you can run:
  - `start .\index.html` (opens default browser)
- Recommended for iterative editing: use VS Code Live Server extension for auto-reload.

### Conventions & patterns (project-specific)
- Visual system: Tailwind CDN + handcrafted CSS in <style> blocks. Keep small visual tweaks inline unless introducing a build tool.
- Dark theme: toggled by toggling `html.classList` value `dark`. Persisted in `localStorage` under `theme` — preserve this logic when refactoring.
- Navigation: `navigateTo(page)` in `index.html` currently shows a demo alert and stores theme; real multi-page routing is done by separate HTML files (e.g., `services.html`). Don't assume a SPA router.
- Animation: AOS library is used (AOS.init). Keep AOS data attributes when adding new sections.
- Reusable UI tokens: classes like `glass`, `feature-card`, `service-card`, and `btn-primary` are used across files — prefer to reuse these exact class names for consistent look.

### Integration & external dependencies
- External CDNs used (no lockfiles):
  - Tailwind CDN: `https://cdn.tailwindcss.com`
  - AOS CSS/JS: `https://cdnjs.cloudflare.com/ajax/libs/aos/2.3.4/...`
- Because assets are CDN-hosted, changes to design tokens should avoid assuming a local Tailwind build unless a build system is added.

### What an agent should do / avoid
- Do: Make minimal, local edits to HTML/CSS/JS. Use existing class names and data attributes (AOS) to maintain visuals and animations.
- Do: Preserve `localStorage` theme behavior and the mobile menu toggle (elements `#mobileMenuBtn`, `#mobileMenu`).
- Avoid: Adding a build system or changing CDNs without an explicit task from maintainers — this repo is intentionally simple and static.

### If merging with an existing `.github/copilot-instructions.md`
- Preserve any custom human-written sections. Update or add the sections: "Key files to read first", "Developer workflow", and "Conventions & patterns" with the exact notes above.

---

If anything here is unclear or you want more detail (e.g., proposal to add a build step, split CSS into files, or add tests), tell me which area to expand and I will update the file.
