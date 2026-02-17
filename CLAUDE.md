# CLAUDE.md — Agrotactic

## Project Overview

Agrotactic is a **corporate showcase website** for an agricultural operations platform targeting enterprise agro-holdings. The site is designed as a "proof-driven" tool to help enterprise buyers progress through internal procurement/pilot approval. It is published on the **Tilda** platform.

- **Language:** All UI copy is in **Russian**. Code comments may be in English.
- **Current version:** v0.1 (2026-02-17)
- **Mode:** TILDA-ONLY — the single source of truth is `/tilda/`

---

## Tech Stack

- **HTML5 + CSS3 + Vanilla JavaScript (ES6+)** — no frameworks, no build system
- **No npm/node/package.json** — this is not a Node.js project
- **Fonts:** Inter (UI) + JetBrains Mono (monospace/data) via Google Fonts
- **Platform:** Tilda website builder (publication channel only)
- **No database, no backend API** — purely frontend, stateless

---

## Project Structure

```
/
├── CLAUDE.md              # This file
├── AGENTS.md              # Hard engineering constraints (MUST READ)
├── README.md              # Project overview (Russian)
├── WORKFLOW.md            # Development workflow
├── CHANGELOG.md           # Version history
├── COPY_TO_TILDA.md       # Paste-to-Tilda instructions
├── QA_CHECKLIST.md        # Pre-launch QA checklist
├── refs/                  # Reference images (read-only inspiration assets)
└── tilda/                 # *** SINGLE SOURCE OF TRUTH ***
    ├── head/
    │   └── site-head.html         # Global HEAD code (fonts)
    ├── t123/
    │   └── home/
    │       ├── home.html          # Main page (~1459 lines, all 12 sections)
    │       └── hero.html          # Stub (unused, content merged into home.html)
    ├── docs/
    │   ├── WORKFLOW.md
    │   ├── COPY_TO_TILDA.md
    │   ├── QA_CHECKLIST.md
    │   ├── TILDA_ANCHORS.md       # Placeholder-to-real Tilda ID mapping
    │   ├── TODO.md                # Post-deployment checklist
    │   └── CHANGELOG.md
    └── releases/
        └── 2026-02-17_v0.1/      # Snapshot of shipped code
            ├── site-head.html
            └── home.html
```

---

## Hard Constraints (from AGENTS.md)

These rules are **mandatory** and must never be violated:

1. **Workspace:** Only create/modify files under `/tilda/` and `/refs/`. Never create `/src/`, `/build/`, `/dist/`, `/pages/`, or any other top-level directories.
2. **No duplicate versions:** Never maintain a second copy of code outside `/tilda/`.
3. **CSS isolation:** All custom content must be wrapped in `<section class="x-site">`. All CSS classes must use the `x-` prefix. Never use global selectors (`body`, `h1`, `a`) without `.x-site` scoping.
4. **Vanilla JS only:** No jQuery, React, Vue, Bootstrap, or any other framework/library.
5. **Responsive:** Must work at **375px**, **768px**, and **1440px** widths.
6. **Russian UI:** All user-facing copy must be in Russian.
7. **HEAD changes:** After modifying `tilda/head/site-head.html`, all Tilda pages must be republished.
8. **T123 verification:** Code in T123 blocks does NOT execute in Tilda's editor preview — it must be verified on the **published** page.
9. **No preview files in repo:** If a local preview is needed, create it outside the project directory.

---

## CSS Architecture

### Scoping
- All custom markup lives inside `<section class="x-site">...</section>`
- Every CSS class uses the `x-` prefix (e.g., `.x-header`, `.x-btn--primary`, `.x-card`)
- CSS is scoped via `<style>` tags within T123 blocks

### Design Tokens (CSS Custom Properties)
Defined in `:root` / `.x-site`:
- **Colors:** `--c-bg`, `--c-text`, `--c-accent`, `--c-muted`, etc.
- **Typography:** `--ff-base`, `--fs-1` through `--fs-6`, `--lh-base`, `--fw-*`
- **Spacing:** `--sp-1` through `--sp-8`
- **Radius:** `--r-1` through `--r-4`
- **Shadows:** `--sh-1` through `--sh-3`

### Key Components
| Component | Class | Description |
|-----------|-------|-------------|
| Header | `.x-header` | Sticky header with blur, collapses to burger on mobile |
| Hero | `.x-hero` | 2-column layout with role-based tab switcher |
| Tabs | `.x-tabs`, `.x-tab` | Role switcher (3 roles) |
| Accordion | `.x-accordion`, `.x-acc-item` | Expandable panels |
| Stepper | `.x-stepper`, `.x-step` | A2/A3/A4 autonomy levels (clickable) |
| Cards | `.x-card` | Content card grids |
| Drawer | `.x-drawer` | Side panel for Trust Pack / Procurement Pack |
| Buttons | `.x-btn--primary/secondary/tertiary` | Three button variants |
| Self-check | `.x-selfcheck` | Interactive checkbox quiz |
| Layout | `.x-wrap` | Centered container (max-width: 1200px) |
| Sections | `.x-section` | Full-width section blocks |

### Responsive Breakpoints
- **Mobile:** 375px
- **Tablet:** 768px
- **Desktop:** 1440px

Use `clamp()` for scalable font sizes. No mobile-first CSS methodology — use explicit breakpoints.

---

## JavaScript Patterns

- **State management:** DOM-based only — `classList.add/remove/toggle`, ARIA attributes
- **No centralized store** — state is local to components (active tab, open drawer, etc.)
- **Event handling:** `addEventListener` on document or specific elements
- **Interactive behaviors:** sticky header (scroll), burger menu, tabs, accordion, drawer (overlay + Escape key + focus trap), hotspots (hover/tap), self-check quiz

---

## Navigation & Routing

- **No client-side router** — single page with anchor-based navigation
- **Internal anchors** (within T123 code): `#x-model`, `#x-platform`, `#x-integrations`, `#x-pilot`, `#x-autonomy`, `#x-command`, `#x-compliance`, `#x-security`, `#x-procurement`
- **Tilda block anchors** (placeholder): `#recFORM`, `#recCONTACTS` — must be replaced with real Tilda block IDs after publishing
- Smooth scroll via native browser anchor behavior

---

## Page Sections (S0-S12)

The home page (`tilda/t123/home/home.html`) contains 12 sections in this order:

1. **S0 — Header:** Sticky nav with burger menu on mobile
2. **S1 — Hero:** Role switcher tabs, hotspots, trust badges, CTA buttons
3. **S2 — Operational Model:** 5-node control circuit (accordion)
4. **S3 — Platform Architecture:** 4-layer diagram (cards)
5. **S4 — Autonomy Ladder:** A2 -> A3 -> A4 stepper (clickable)
6. **S5 — Command Center:** Dispatch scenarios
7. **S6 — Integrations:** ERP/1C, telematics, IoT, BI, REST API + self-check quiz
8. **S7 — Compliance:** Audit trail, "Mercury" system
9. **S8 — Security:** Data protection, Trust Pack
10. **S9 — Pilot Program:** 6-8 weeks, KPIs, acceptance criteria
11. **S10 — Procurement Pack:** Document drawer (One-pager, Pilot Blueprint, etc.)
12. **S11 — Final CTA + Contacts**

---

## Development Workflow

### No Build System
There is no build step. The workflow is:
1. **Edit** files directly in `/tilda/`
2. **Copy** code to Tilda (HEAD or T123 block)
3. **Publish** the page in Tilda
4. **Verify** on the published public URL (not editor preview)
5. **Snapshot** working code to `/tilda/releases/YYYY-MM-DD_vX/`

### Hero-First Principle
When building new features, start with the Hero section. Perfect it before moving to other sections.

### Iteration Cycle
1. Update `/refs/` if new references exist
2. Change only one group per iteration: layout OR typography OR colors OR effects
3. Validate at 1440px, 768px, 375px
4. Log changes in `tilda/docs/CHANGELOG.md`

### Release Protocol
After each successful publish:
1. Copy final artifacts to `/tilda/releases/YYYY-MM-DD_vX/`
2. Update `tilda/docs/CHANGELOG.md`

---

## Testing & QA

**No automated tests.** All testing is manual per `QA_CHECKLIST.md`:

- **Tilda specifics:** Pages published, HEAD republished if changed, T123 blocks inserted
- **SEO:** Title, meta description, charset, viewport, favicon
- **Content:** All copy in Russian, no placeholders
- **Lead form:** 3 test submissions, success state, delivery confirmation
- **Responsive:** 375px, 768px, 1440px — no overflow, readable text, tappable buttons
- **Performance:** Optimized images, minimal font weights, no heavy libraries
- **JS sanity:** No console errors on published page, scoped CSS/JS
- **Accessibility:** One H1, logical headings, alt text, sufficient contrast, keyboard navigation
- **Links:** No broken links, external links work

---

## Outstanding Tasks (v0.1 Post-Deployment)

- Replace placeholder Tilda anchor IDs (`#recFORM`, `#recCONTACTS`) with real block IDs
- Upload PDF documents to Tilda and update download links in the drawer
- Configure and test lead form (3 test submissions)
- Set up meta title/description and analytics
- Run full QA checklist before final launch

---

## Key Files to Know

| File | Purpose |
|------|---------|
| `AGENTS.md` | Hard constraints — read before any code changes |
| `tilda/t123/home/home.html` | Main page code (all sections, ~1459 lines) |
| `tilda/head/site-head.html` | Global HEAD (Google Fonts) |
| `tilda/docs/TILDA_ANCHORS.md` | Placeholder-to-real Tilda ID mapping |
| `tilda/docs/CHANGELOG.md` | Version history |
| `tilda/docs/TODO.md` | Post-deployment checklist |
| `QA_CHECKLIST.md` | Pre-launch QA verification |
| `COPY_TO_TILDA.md` | Step-by-step paste instructions |

---

## Common Pitfalls

1. **Creating files outside `/tilda/`** — Everything must live under `/tilda/`. No exceptions.
2. **Using global CSS selectors** — Always scope under `.x-site` and use `x-` prefixed classes.
3. **Forgetting to republish after HEAD changes** — Tilda requires "Publish all pages" when HEAD code changes.
4. **Testing in Tilda editor preview** — T123 code only executes on the published page.
5. **Using `javascript:void(0)` for downloads** — These are placeholders; real PDF URLs need to be substituted after Tilda upload.
6. **Adding npm/build tooling** — This project intentionally has zero build dependencies.
7. **Writing UI copy in English** — All user-facing text must be in Russian.
