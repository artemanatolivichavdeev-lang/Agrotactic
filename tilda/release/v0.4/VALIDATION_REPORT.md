# VALIDATION_REPORT.md — v0.4 Tilda Safe Split

## Split Map

### Source: `home.html` (10,492 lines, 336 KB)

### CSS blocks extracted → `CUSTOM_CSS.css` (17 blocks, 213 KB)

| #   | Section                                                   | Approx size |
| --- | --------------------------------------------------------- | ----------- |
| 1   | Global tokens, layout, buttons, header, hero, radar, tabs | ~80 KB      |
| 2   | Hero scoped overrides (gradient, pain pills, hotspots)    | ~20 KB      |
| 3   | S2 Operational model                                      | ~7 KB       |
| 4   | S3 Architecture / platform                                | ~6 KB       |
| 5   | S4 Autonomy levels                                        | ~8 KB       |
| 6   | S5 Command center / scenarios                             | ~18 KB      |
| 7   | S6 Integrations modes                                     | ~5 KB       |
| 8   | S6 Integration calculator                                 | ~5 KB       |
| 9   | S6 Integration cards/steps                                | ~7 KB       |
| 10  | S7 Compliance                                             | ~18 KB      |
| 11  | S8 Security                                               | ~13 KB      |
| 12  | S9 Pilot                                                  | ~14 KB      |
| 13  | S10 Procurement                                           | ~10 KB      |
| 14  | S11 Final CTA                                             | ~10 KB      |
| 15  | S12 Contacts + S13 Partners                               | ~7 KB       |
| 16  | Drawer styles                                             | ~4 KB       |
| 17  | Demo form drawer styles                                   | ~28 KB      |

### JS blocks extracted → end of `T123_3.html` (14 blocks)

| #   | Purpose                                                  |
| --- | -------------------------------------------------------- |
| 1   | Role switcher (hero tabs)                                |
| 2   | Operational model scroll-reveal                          |
| 3   | Architecture scroll-reveal                               |
| 4   | Scenario picker                                          |
| 5   | Integration calculator                                   |
| 6   | Compliance scroll-reveal                                 |
| 7   | Security scroll-reveal                                   |
| 8   | Pilot scroll-reveal                                      |
| 9   | Procurement scroll-reveal                                |
| 10  | CTA scroll-reveal                                        |
| 11  | Contacts/Partners scroll-reveal                          |
| 12  | Partners scroll-reveal                                   |
| 13  | Demo form drawer + form logic                            |
| 14  | Main init (header, drawer, scroll, IntersectionObserver) |

All 14 blocks wrapped in safe initializer:

```js
(function () {
  function init() {
    try {
      /* merged JS */
    } catch (e) {
      console.error("[Agrotactic] init error", e);
    }
  }
  if (document.readyState === "loading")
    document.addEventListener("DOMContentLoaded", init);
  else init();
})();
```

### HTML split boundaries

| File        | Sections                                                            | Wrapper                               |
| ----------- | ------------------------------------------------------------------- | ------------------------------------- |
| T123_1.html | Scanline + S0 Header + S1 Hero + Trust strip                        | `<div class="x-site" id="agro-home">` |
| T123_2.html | S2 Operational model + S3 Architecture + S4 Autonomy + S5 Scenarios | `<div class="x-site">`                |
| T123_3.html | S6–S13 + Footer + Drawers + JS                                      | `<div class="x-site">`                |

---

## Validation Results

### 1. Tag hygiene

| Check                                    | Result  |
| ---------------------------------------- | ------- |
| T123_1.html: no `<style>`                | ✅ PASS |
| T123_1.html: no `<script>`               | ✅ PASS |
| T123_2.html: no `<style>`                | ✅ PASS |
| T123_2.html: no `<script>`               | ✅ PASS |
| T123_3.html: no `<style>`                | ✅ PASS |
| T123_3.html: exactly 1 `<script>` at end | ✅ PASS |
| SITE_HEAD.html: no `<style>`             | ✅ PASS |
| SITE_HEAD.html: no `<script>`            | ✅ PASS |

### 2. Forbidden artifacts

| File           | `<!DOCTYPE>` | `<html>` | `<head>` | `<body>` | `nominify` | `t-records` | `allrecords` |
| -------------- | :----------: | :------: | :------: | :------: | :--------: | :---------: | :----------: |
| T123_1.html    |      ✅      |    ✅    |   ✅\*   |    ✅    |     ✅     |     ✅      |      ✅      |
| T123_2.html    |      ✅      |    ✅    |    ✅    |    ✅    |     ✅     |     ✅      |      ✅      |
| T123_3.html    |      ✅      |    ✅    |    ✅    |    ✅    |     ✅     |     ✅      |      ✅      |
| SITE_HEAD.html |      ✅      |    ✅    |    ✅    |    ✅    |     ✅     |     ✅      |      ✅      |
| CUSTOM_CSS.css |      ✅      |    ✅    |    ✅    |    ✅    |     ✅     |     ✅      |      ✅      |

\* T123_1 contains `<header>` tag (not `<head>`) — this is expected HTML, not a forbidden artifact.

### 3. Wrapper correctness

| File        | `.x-site` opens | First line                            | Last HTML line |
| ----------- | :-------------: | ------------------------------------- | -------------- |
| T123_1.html |        1        | `<div class="x-site" id="agro-home">` | `</div>`       |
| T123_2.html |        1        | `<div class="x-site">`                | `</div>`       |
| T123_3.html |        1        | `<div class="x-site">`                | `</div>`       |

Each T123 file opens AND closes exactly one `.x-site` wrapper ✅

### 4. ID uniqueness

- Total IDs in HTML (excluding JS string literals): **76**
- Unique IDs: **76**
- Duplicates: **NONE** ✅

#### ID fix applied:

| Before                                     | After                                                                      | File        | Reason                               |
| ------------------------------------------ | -------------------------------------------------------------------------- | ----------- | ------------------------------------ |
| `id="x-open-drawer-3"` on procurement link | Replaced with `onclick="document.getElementById('x-open-drawer').click()"` | T123_3.html | Duplicate with button in T123_2.html |

Only T123_1 has `id="agro-home"`. T123_2 and T123_3 use `class="x-site"` only.

### 5. JS placement

- JS present in T123_3.html: ✅ (1 `<script>` block at end)
- JS absent from T123_1.html: ✅
- JS absent from T123_2.html: ✅
- Safe initializer wrapper: ✅ (IIFE + try/catch + DOMContentLoaded check)

### 6. CSS purity

| Check                       | Result  |
| --------------------------- | ------- |
| No `<` character in CSS     | ✅ PASS |
| No `<style>` tags           | ✅ PASS |
| No `<script>` tags          | ✅ PASS |
| Ends with valid token (`}`) | ✅ PASS |

### 7. Size report

| File           | Size   | Notes                            |
| -------------- | ------ | -------------------------------- |
| SITE_HEAD.html | 289 B  | Fonts only — cannot be truncated |
| CUSTOM_CSS.css | 213 KB | For Site Settings → Custom CSS   |
| T123_1.html    | 13 KB  | Well within T123 limit           |
| T123_2.html    | 38 KB  | Well within T123 limit           |
| T123_3.html    | 104 KB | HTML + JS, within T123 limit     |

### 8. Sections accounted for

| Section               | File   | ✓   |
| --------------------- | ------ | --- |
| Scanline              | T123_1 | ✅  |
| S0: Header            | T123_1 | ✅  |
| S1: Hero              | T123_1 | ✅  |
| Trust strip           | T123_1 | ✅  |
| S2: Operational model | T123_2 | ✅  |
| S3: Architecture      | T123_2 | ✅  |
| S4: Autonomy          | T123_2 | ✅  |
| S5: Command center    | T123_2 | ✅  |
| S6: Integrations      | T123_3 | ✅  |
| S7: Compliance        | T123_3 | ✅  |
| S8: Security          | T123_3 | ✅  |
| S9: Pilot             | T123_3 | ✅  |
| S10: Procurement      | T123_3 | ✅  |
| S11: Final CTA        | T123_3 | ✅  |
| S12: Contacts         | T123_3 | ✅  |
| S13: Partners         | T123_3 | ✅  |
| Footer                | T123_3 | ✅  |
| Document drawer       | T123_3 | ✅  |
| Demo form drawer      | T123_3 | ✅  |

**All 19 content areas accounted for.**
