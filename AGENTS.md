# AGENTS.md — TILDA-ONLY MODE (Agrotactic)

**IMPORTANT:** This project is **Tilda-only**.  
Single Source of Truth = files inside `/tilda/` only.  
No parallel `/src/`, no “local prototype” inside the repo, no duplicate copies.

The website UI copy (labels, content, CTAs) must be in **Russian**.

---

## 0) Allowed workspace (hard constraint)
You may create/modify files **ONLY** under:

- `tilda/` (everything: code, assets, docs, releases)
- `refs/` (reference images only, read-only unless explicitly asked)

**Never** create or modify any other folders (`src/`, `pages/`, `dist/`, `build/`, etc).

---

## 1) Core objective
Build a **showcase site** (Hero + sections + contacts + lead form) and publish it to **Tilda** via:

- **HEAD** (global or per page)
- **T123** (Embed HTML Code)

---

## 2) Tilda platform rules (must be respected)
- **T123 supports** HTML + CSS (inside `<style>`) + JS (inside `<script>`). No PHP on page.
- In editor/preview, code may appear as text and may not execute; verify on the **published** page.
- After changing **HEAD** code, you must **republish all pages**.

Docs:
- Embed HTML (T123): https://help.tilda.cc/html
- Code in HEAD + republish: https://tilda.cc/en/answers/a/html-in-head-en/
- Webhook forms: https://help.tilda.cc/forms/webhook
- Custom scripts tips: https://help.tilda.cc/tips/javascript

---

## 3) Hard engineering rules
- Stack: **plain HTML5 + CSS3 + JS (ES6+)**; no React/Vue/Bootstrap.
- JS: vanilla only (do not assume jQuery).
- Style isolation is mandatory:
  - wrap custom content in `.x-site`
  - prefix all classes with `x-...`
  - do not target global selectors (`body`, `h1`, `a`) without `.x-site` prefix
- Must be responsive at **375 / 768 / 1440** widths.

---

## 4) File contract (what must exist)
### 4.1 What we paste into Tilda
- `tilda/head/site-head.html` — paste into Tilda **HEAD** (site-wide or page-level)
- `tilda/t123/home/hero.html` — paste into **T123** (Hero section)

Optional (if/when needed):
- `tilda/t123/home/sections.html` — other custom sections
- `tilda/head/page-*.html` — page-specific HEAD code

### 4.2 Release snapshots (mandatory)
After each successful publish, create a snapshot folder:

`/tilda/releases/2026-02-17_vX/`
- `site-head.html`
- `hero.html`
- (any other pasted snippets for that release)

---

## 5) Output / delivery contract (when generating code)
When asked to build/update a section, return:
1) The updated file contents for the relevant `tilda/...` file(s)
2) A short copy/paste instruction: where to paste in Tilda + what to republish
3) A mini DoD checklist (6–10 items)

Do not ask for approval unless explicitly requested.

---

## 6) Preview rule (avoid dual versions)
If a local preview is needed, create it **outside the project folder**, e.g.:

`C:\Users\Gideon\Downloads\Antigravity\_preview\temp.html`

Never store preview pages inside the repository.
