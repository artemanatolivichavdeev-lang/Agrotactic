# WORKFLOW — Antigravity → Tilda (TILDA-ONLY, Showcase Site + Lead Form)

**Note:** The website UI copy (labels, content, and CTAs) is in **Russian**.  
**Mode:** TILDA-ONLY — all working files live inside `/tilda/`. No `/src/`.

---

## 0) Project objective (1 paragraph)
Build a showcase website in a distinctive “industrial tactical / mission control” style (Hero + services + pricing + proof + contacts) and enable lead collection via a form.  
Development happens in Google Antigravity; publication happens in Tilda via **HEAD** and/or **T123**.

---

## 1) Roles & responsibilities
- Owner/Client: (Full name / company)
- Builder (you): design + content + HTML/CSS/JS + paste into Tilda
- AI assistant: generate variants, refactor, validate against checklists
- (optional) Dev/Integrations: webhook / CRM / Telegram

---

## 2) Platform constraints (Tilda rules)
### 2.1 Where the code runs (why Publish matters)
- **T123 (Embed HTML Code)** supports HTML + CSS (`<style>`) + JS (`<script>`).  
- In editor/preview the code may not execute; verify on the **published** page.
- To make T123 code operational, you must **Publish** the page.

Docs: https://help.tilda.cc/html

### 2.2 What is not allowed
- No PHP/server-side code inside the page.
- If server-side behavior is needed (form processing/integration), host it externally and use **Webhook**.

Docs: https://help.tilda.cc/forms/webhook

### 2.3 HEAD rules (global/shared code)
- Global for all pages: Site Settings → More → HTML code for the HEAD section
- Page-specific: Page Settings → Additional → HTML code for the HEAD section
- After changing HEAD: **republish all pages**

Docs: https://tilda.cc/en/answers/a/html-in-head-en/

---

## 3) Development principles (fast and structured)
### 3.1 Hero-first
1) Build only Hero first.
2) Iterate until it “feels right” (visual + responsive).
3) Only then assemble the remaining sections.

### 3.2 Reference-driven workflow
- Store all references in `/refs/` (screenshots, inspiration).
- For each iteration, record changes in `tilda/docs/CHANGELOG.md` (3–7 lines).

### 3.3 Simple tech stack (mandatory)
- HTML5 + CSS3 + JS (ES6+), no frameworks.
- Semantic HTML (`header/nav/section/h1-h3`).
- CSS variables for tokens (`:root`) — colors/typography/spacing.
- Layout via Grid/Flex.
- Responsive breakpoints: **375 / 768 / 1440**.

### 3.4 Style isolation (critical for Tilda)
To prevent custom CSS from breaking native Tilda blocks:
- Wrap custom sections inside `.x-site`
- Prefix classes with `x-...`
- Do not target global selectors without `.x-site`

---

## 4) Project structure (TILDA-ONLY)
Everything “working” lives here:

```
/refs/                              # reference images
/tilda/
  head/
    site-head.html                  # paste into Tilda HEAD
    page-home-head.html             # optional page-specific head
  t123/
    home/
      hero.html                     # paste into T123 (Hero)
      sections.html                 # optional other custom sections
  assets/
    img/                            # optimized images (upload to Tilda, then replace URLs)
    icons/                          # svg
  docs/
    WORKFLOW.md                     # this file copy (optional)
    COPY_TO_TILDA.md
    QA_CHECKLIST.md
    TILDA_ANCHORS.md
    CHANGELOG.md
  releases/
    2026-02-17_v0.1/
      site-head.html
      hero.html
```

**Rule:** no duplicate code outside `/tilda/`.

---

## 5) Design tokens (single style language)
Define tokens in `:root` (inside `site-head.html` OR inside each T123 snippet — choose one approach and stick to it):
- Colors: `--c-bg`, `--c-text`, `--c-accent`, `--c-muted`, ...
- Typography: `--ff-base`, `--fs-1..--fs-6`, `--lh-base`, `--fw-*`
- Spacing: `--sp-1..--sp-8`
- Radius: `--r-1..--r-4`
- Shadow: `--sh-1..--sh-3`

Rule: no random colors/sizes outside variables.

---

## 6) Iteration cycle
1) Update `/refs/` (if new references exist)
2) Change only one group per iteration:
   - grid/composition OR typography OR colors/accents OR effects
3) Validate:
   - 1440 desktop
   - 768 tablet
   - 375 mobile
4) Log changes in `tilda/docs/CHANGELOG.md`

---

## 7) Validation (before paste)
- If you need fast preview: use an external temp file **outside the project** (see `AGENTS.md`).
- Otherwise validate directly on the **published** Tilda page.

---

## 8) Paste into Tilda (standard protocol)
Use `tilda/docs/COPY_TO_TILDA.md` as the exact paste order:
- HEAD: paste `tilda/head/site-head.html` → then **republish all pages**
- T123: paste `tilda/t123/home/hero.html` → then **publish the page**

---

## 9) Lead form (2 modes)
### 9.1 No-code (recommended)
Use standard Tilda form blocks and set recipients (email/CRM/table).

### 9.2 Integration (Webhook)
Enable Webhook and receive POST payload on your server endpoint.

Docs: https://help.tilda.cc/forms/webhook

---

## 10) Definition of Done
### 10.1 Hero done if
- visual matches intended style
- responsive 375/768/1440 without breaks
- CTA links work (anchors)
- no console errors on published page

### 10.2 Launch ready if
- form delivers leads (3 test submissions)
- HEAD republish done after changes
- `QA_CHECKLIST.md` passed
