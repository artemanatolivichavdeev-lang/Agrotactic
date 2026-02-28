# DEPLOY_TILDA.md — v0.4 Deterministic Paste Order

---

## Step 0 — Clean old code

1. Open the Home page in Tilda editor
2. **Remove** any existing T123 blocks that contain old code
3. Go to **Page Settings → Additional → HTML code in HEAD** — clear everything, Save
4. Go to **Site Settings → More → Custom CSS** — clear everything, Save

---

## Step 1 — Site Custom CSS (site-wide)

1. Go to **Tilda → Site Settings → More → Custom CSS**
2. Paste the **entire contents** of `CUSTOM_CSS.css` (~213 KB)
3. Click **Save**

> ⚠️ This is pure CSS — no `<style>` tags. Tilda adds the wrapper automatically.
> ⚠️ Do NOT paste CSS into HEAD. HEAD truncation caused the white-screen incident.

---

## Step 2 — Page HEAD (fonts only)

1. Go to **Page Settings → Additional → HTML code in the HEAD of the page**
2. Paste the contents of `SITE_HEAD.html` (3 lines, 289 bytes — fonts only)
3. Click **Save**

> ✅ HEAD contains only Google Fonts `<link>` tags. Cannot be truncated.
> ⚠️ Use **Page HEAD**, not Site HEAD — avoids affecting other pages.

---

## Step 3 — Add 3 T123 blocks on the page

1. In Tilda page editor, add 3 new blocks: **Other → T123 (Embed HTML Code)**
2. Paste in this exact order:

| Block   | File          | Contains                                  |
| ------- | ------------- | ----------------------------------------- |
| T123 #1 | `T123_1.html` | Header + Hero + Trust strip (HTML only)   |
| T123 #2 | `T123_2.html` | S2–S5 middle sections (HTML only)         |
| T123 #3 | `T123_3.html` | S6–S13 + Footer + Drawers + ALL JS at end |

3. In each T123 block settings, set **top/bottom padding = 0** if the option exists
4. **Keep order exactly 1 → 2 → 3** (JS in T123_3 depends on DOM from T123_1/2/3)

> ⚠️ T123 executes only after publishing. Editor preview shows raw HTML — this is normal.

---

## Step 4 — Publish

1. Click **Publish** on the page
2. Then click **"Publish all pages"** from the project dashboard (to apply Custom CSS)

---

## Step 5 — Verify on published page (NOT preview)

Open the published URL and check:

- [ ] Page renders (no white screen)
- [ ] DevTools Console: **no red errors**
- [ ] Header navigation works (scroll to anchors)
- [ ] Burger menu works on mobile
- [ ] Role switcher (Hero tabs) switches content
- [ ] Autonomy level switcher works
- [ ] Scenario picker (Command Center tabs) works
- [ ] "Запросить демо" / "Открыть Trust Pack" — opens drawer
- [ ] "Получить пакет документов" — opens document drawer
- [ ] Demo form stepper works (page navigation + validation)
- [ ] Scroll-reveal animations trigger on scroll
- [ ] Integration calculator (checkboxes → result update)
- [ ] Footer links and copyright visible at bottom

---

## ⚡ TROUBLESHOOTING — If you see a white screen

### Quick diagnosis

1. **Open DevTools → Console** — report the first red error line
2. **Check Elements tab**: does `#allrecords` / `.t-records` have `opacity: 0` that never becomes `1`?
   - If yes → JS crashed early or HEAD markup is broken

### Isolation steps

| Test          | Action                             | If content appears             |
| ------------- | ---------------------------------- | ------------------------------ |
| CSS problem?  | Remove Custom CSS → Save → Publish | CSS was corrupted or truncated |
| JS problem?   | Remove T123_3 block → Publish      | JS has a runtime error         |
| HEAD problem? | Clear Page HEAD → Save → Publish   | HEAD code was corrupted        |

### Rules for recovery

- **NEVER** paste CSS inside HEAD (causes truncation → white screen)
- CSS goes **only** into Site Settings → Custom CSS
- JS goes **only** into T123_3 (never in HEAD)
- SITE_HEAD must contain **only** font links (≤300 bytes)
- Always test on **published page**, never in preview

---

## Architecture Reference

| Where      | What             | Size   | Why safe                                                         |
| ---------- | ---------------- | ------ | ---------------------------------------------------------------- |
| Custom CSS | All project CSS  | 213 KB | Tilda Custom CSS handles large CSS safely (no truncation)        |
| Page HEAD  | Font links only  | 289 B  | Too small to truncate                                            |
| T123 #1    | HTML only        | 13 KB  | No execution risk                                                |
| T123 #2    | HTML only        | 38 KB  | No execution risk                                                |
| T123 #3    | HTML + JS at end | 104 KB | JS runs last after DOM is ready; try/catch prevents white screen |
