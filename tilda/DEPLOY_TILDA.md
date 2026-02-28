# DEPLOY_TILDA.md — Deterministic Paste Order

## Prerequisites

- Access to Tilda project for Агротактик
- Files ready: `SITE_HEAD.html`, `CUSTOM_CSS.css`, `T123_1.html`, `T123_2.html`, `T123_3.html`

---

## Step 1 — Custom CSS (Site-wide)

1. Go to **Tilda → Site Settings → More → Custom CSS**
2. **Delete** any existing custom CSS
3. Paste the **entire contents** of `CUSTOM_CSS.css` (pure CSS, ~205 KB)
4. Click **Save**

> ⚠️ This is plain CSS — no `<style>` tags. Tilda wraps it automatically.

---

## Step 2 — Page HEAD (Fonts only)

1. Go to **Page Settings → Additional → HTML code in the HEAD of the page**
   - ⚠️ Use **Page HEAD**, not Site HEAD — to avoid affecting other pages
2. Paste the contents of `SITE_HEAD.html` (3 lines, ~287 bytes — fonts only)
3. Click **Save**

> ✅ HEAD contains only Google Fonts links. No CSS. No JS. Cannot be truncated.

---

## Step 3 — T123 Blocks (Page Content)

1. Open the Home page in Tilda editor
2. **Remove** any existing T123 blocks that contain old code
3. Add 3 new blocks: **Other → T123 "Embed HTML Code"** (three times)
4. Configure each block:

| Block   | File to paste | Contains                                               |
| ------- | ------------- | ------------------------------------------------------ |
| T123 #1 | `T123_1.html` | Header + Hero + Trust strip (HTML only)                |
| T123 #2 | `T123_2.html` | Middle sections S2–S5 (HTML only)                      |
| T123 #3 | `T123_3.html` | Bottom sections S6–S13 + Footer + Drawers + **all JS** |

5. In each T123 block settings, set **top/bottom padding = 0** if the option exists
6. **Publish the page**

> ⚠️ T123 blocks execute only after publishing. Preview will show raw HTML.

---

## Step 4 — Verify on Published Page

Open the published URL and check:

- [ ] Page renders (no white screen)
- [ ] Open DevTools Console: **no red errors**
- [ ] Header navigation works (scroll to anchors)
- [ ] Burger menu works on mobile
- [ ] Role switcher (Hero tabs) switches content
- [ ] Autonomy level switcher works
- [ ] Scenario picker (Command Center) works
- [ ] "Запросить демо" opens the demo form drawer
- [ ] "Получить пакет документов" opens the document drawer
- [ ] Form stepper (page navigation) works
- [ ] Scroll-reveal animations trigger on scroll
- [ ] Integration calculator (checkboxes) updates results

---

## ⚡ Emergency: If You See a White Screen

1. **Immediately** go to **Page Settings → HEAD** — remove all code, save, republish
2. Check that **Custom CSS** does not contain `<style>` tags or `<script>` code
3. Check that **T123_3** is the ONLY block with `<script>` — T123_1 and T123_2 must be pure HTML
4. In DevTools Console, look for the specific error:
   - CSS parse error → CSS pasted incorrectly (check for truncation)
   - `TypeError: null` → an element ID is missing (check T123 block order)
5. Republish and test again

---

## Architecture Rationale

| Where      | What                   | Why                                                          |
| ---------- | ---------------------- | ------------------------------------------------------------ |
| Custom CSS | All 205 KB of CSS      | Avoids HEAD truncation that caused the white-screen incident |
| Page HEAD  | Fonts only (287 bytes) | Too small to be truncated; loads fonts before content        |
| T123_1     | HTML only              | Clean fragment, no execution risk                            |
| T123_2     | HTML only              | Clean fragment, no execution risk                            |
| T123_3     | HTML + JS at end       | JS runs last, after all DOM elements exist in T123_1/2/3     |
