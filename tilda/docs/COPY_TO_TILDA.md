# COPY_TO_TILDA — TILDA-ONLY (HEAD vs T123) Cheat Sheet

**Goal:** paste code into Tilda quickly and correctly, with **one source of truth** (only `/tilda/`).

---

## 0) Core Tilda rules (critical)
1) **T123** supports HTML + CSS (`<style>`) + JS (`<script>`): https://help.tilda.cc/html  
2) In editor/preview, embedded code may not execute. Verify on **published** page.  
3) **HEAD** code:
   - Site Settings → More → HTML code for the HEAD section
   - Page Settings → Additional → HTML code for the HEAD section  
   After changing HEAD you must **republish all pages**: https://tilda.cc/en/answers/a/html-in-head-en/  
4) No PHP/server-side code in page. For server actions use Webhook: https://help.tilda.cc/forms/webhook

---

## 1) TILDA-ONLY rule (anti-confusion)
- Working files live ONLY in `/tilda/`.
- Never maintain a second copy in `/src/` or “preview” folders inside the project.

---

## 2) What goes into HEAD (copy/paste)
**File:** `tilda/head/site-head.html`

Put here:
- Google Fonts `<link>` (or other font loading)
- Optional global tokens / shared CSS (only if used across multiple T123 sections)
- Optional shared JS (only if truly needed on all pages)

**After any HEAD change:** click **Publish all pages**.

---

## 3) What goes into T123 (copy/paste)
**File:** `tilda/t123/home/hero.html`

Put here:
- One section wrapper: `<section class="x-site">...</section>`
- Scoped CSS inside `<style>` (recommended)
- JS inside `<script>` only if unavoidable

**After any T123 change:** **Publish** the page where the block is placed.

---

## 4) Exact paste order (no mistakes)
1) Paste HEAD (if it changed)
   - Tilda → Site Settings → More → HEAD
   - Paste content of `tilda/head/site-head.html`
2) **Publish all pages** (HEAD rule)
3) Paste T123
   - Add block: Other → T123 “Embed HTML Code”
   - Paste `tilda/t123/home/hero.html`
4) Publish that page
5) Verify on public URL (not editor preview)
6) Save release snapshot:
   - copy `site-head.html` + `hero.html` into `tilda/releases/2026-02-17_vX/`

---

## 5) Fast debug (“it doesn’t work”)
1) Confirm the page is **published** (T123 runs after publish).
2) If you changed HEAD, confirm you **published all pages**.
3) Open DevTools → Console (red errors = fix JS/selector).
4) Temporarily remove/disable the T123 block to isolate.

---

## 6) Anchors (CTA without JS)
Use Tilda block ids:
- Form block id: `#recXXXXXX`
- Contacts block id: `#recYYYYYY`

Store them in: `tilda/docs/TILDA_ANCHORS.md`
