# VALIDATION_REPORT.md — Tilda Split Validation

## Split Map

### Source: `home.html` (10,492 lines, 369 KB)

#### Style blocks extracted (17 total → `CUSTOM_CSS.css`)

| #   | Original lines | Section                                                   | Approx size |
| --- | -------------- | --------------------------------------------------------- | ----------- |
| 1   | 5–2301         | Global tokens, layout, buttons, header, hero, radar, tabs | ~80 KB      |
| 2   | 2344–2920      | Hero scoped overrides (gradient, pain pills, hotspots)    | ~20 KB      |
| 3   | 3103–3311      | Operational model (S2)                                    | ~7 KB       |
| 4   | 3451–3638      | Architecture / platform (S3)                              | ~6 KB       |
| 5   | 3744–3987      | Autonomy levels (S4)                                      | ~8 KB       |
| 6   | 4127–4668      | Command center / scenarios (S5)                           | ~18 KB      |
| 7   | 4909–5051      | Integrations modes (S6)                                   | ~5 KB       |
| 8   | 5085–5242      | Integration calculator                                    | ~5 KB       |
| 9   | 5358–5557      | Integration cards/steps                                   | ~7 KB       |
| 10  | 5689–6242      | Compliance (S7)                                           | ~18 KB      |
| 11  | 6425–6822      | Security (S8)                                             | ~13 KB      |
| 12  | 6962–7401      | Pilot (S9)                                                | ~14 KB      |
| 13  | 7555–7871      | Procurement (S10)                                         | ~10 KB      |
| 14  | 7970–8280      | Final CTA (S11)                                           | ~10 KB      |
| 15  | 8395–8597      | Contacts (S12) + Partners (S13)                           | ~7 KB       |
| 16  | 8639–8766      | Drawer styles                                             | ~4 KB       |
| 17  | 8878–9752      | Demo form drawer styles                                   | ~28 KB      |

**Total CSS: 205,002 bytes extracted → `CUSTOM_CSS.css`**

#### Script blocks extracted (14 total → end of `T123_3.html`)

| #   | Original lines | Purpose                                                      |
| --- | -------------- | ------------------------------------------------------------ |
| 1   | 3071–3082      | Role switcher (hero tabs)                                    |
| 2   | 3430–3447      | Operational model scroll-reveal                              |
| 3   | 3715–3732      | Architecture scroll-reveal                                   |
| 4   | 4879–4905      | Scenario picker                                              |
| 5   | 5559–5686      | Integration calculator                                       |
| 6   | 6395–6421      | Compliance scroll-reveal                                     |
| 7   | 6932–6958      | Security scroll-reveal                                       |
| 8   | 7534–7551      | Pilot scroll-reveal                                          |
| 9   | 7949–7966      | Procurement scroll-reveal                                    |
| 10  | 8374–8391      | CTA scroll-reveal                                            |
| 11  | 8618–8635      | Contacts/Partners scroll-reveal                              |
| 12  | 8800–8817      | Partners scroll-reveal                                       |
| 13  | 10003–10227    | Demo form drawer open/close + form logic                     |
| 14  | 10228–10492    | Main app init (header, drawer, scroll, IntersectionObserver) |

**All 14 blocks concatenated in original order, wrapped in single `DOMContentLoaded` listener.**

#### HTML split boundaries

| File        | Original lines (approx) | Sections                                                                                                                                                        |
| ----------- | ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T123_1.html | 2302–3100               | `.x-site` wrapper open + S0 Header + S1 Hero + Trust strip                                                                                                      |
| T123_2.html | 3101–4906               | S2 Operational model + S3 Architecture + S4 Autonomy + S5 Scenarios                                                                                             |
| T123_3.html | 4907–10002              | S6 Integrations + S7 Compliance + S8 Security + S9 Pilot + S10 Procurement + S11 CTA + S12 Contacts + S13 Partners + Footer + Drawers + `.x-site` wrapper close |

---

## Validation Results

### 1. File sizes

| File             | Size          | Content                           |
| ---------------- | ------------- | --------------------------------- |
| `SITE_HEAD.html` | 287 bytes     | 3 Google Fonts `<link>` tags only |
| `CUSTOM_CSS.css` | 205,002 bytes | Pure CSS, 17 blocks merged        |
| `T123_1.html`    | 10,465 bytes  | HTML only                         |
| `T123_2.html`    | 29,855 bytes  | HTML only                         |
| `T123_3.html`    | ~90,095 bytes | HTML + JS at end                  |

### 2. Tag safety checks

| Check                            | Result                          |
| -------------------------------- | ------------------------------- |
| No `<style>` in T123_1           | ✅ PASS                         |
| No `<style>` in T123_2           | ✅ PASS                         |
| No `<style>` in T123_3           | ✅ PASS                         |
| No `<script>` in T123_1          | ✅ PASS                         |
| No `<script>` in T123_2          | ✅ PASS                         |
| `<script>` at end of T123_3 only | ✅ PASS                         |
| SITE_HEAD has NO CSS             | ✅ PASS (287 bytes, fonts only) |
| SITE_HEAD has NO JS              | ✅ PASS                         |

### 3. CUSTOM_CSS purity checks

| Check                           | Result  |
| ------------------------------- | ------- |
| No `<style>` tags in CSS        | ✅ PASS |
| No `<script>` tags in CSS       | ✅ PASS |
| No `<` characters in CSS        | ✅ PASS |
| CSS ends with valid token (`}`) | ✅ PASS |

### 4. Truncation safety

| Item           | Size      | Risk                                                          |
| -------------- | --------- | ------------------------------------------------------------- |
| SITE_HEAD.html | 287 bytes | ✅ No risk — too small to truncate                            |
| CUSTOM_CSS.css | 205 KB    | ✅ Safe — Tilda Custom CSS handles large CSS better than HEAD |

### 5. ID uniqueness

| Check                            | Result                                                                              |
| -------------------------------- | ----------------------------------------------------------------------------------- |
| Duplicate `id="x-open-drawer-3"` | ✅ FIXED — removed from T123_3 procurement link, replaced with `onclick` delegation |
| All remaining IDs                | ✅ Unique across T123_1 + T123_2 + T123_3 combined                                  |

### 6. Defensive JS changes

| Change                                                         | Location              | Reason                                                                                                                           |
| -------------------------------------------------------------- | --------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Removed `id="x-open-drawer-3"` from procurement link in T123_3 | T123_3.html line ~630 | Duplicate with T123_2 autonomy button. Replaced with `onclick="document.getElementById('x-open-drawer').click(); return false;"` |
| DOMContentLoaded wrapper                                       | T123_3.html (end)     | All JS concatenated and wrapped in single `DOMContentLoaded` listener since scripts are now at end of page, not in HEAD          |

### 7. Sections accounted for

| Section               | Present in | Verified |
| --------------------- | ---------- | -------- |
| S0: Header            | T123_1     | ✅       |
| S1: Hero              | T123_1     | ✅       |
| Trust strip           | T123_1     | ✅       |
| S2: Operational model | T123_2     | ✅       |
| S3: Architecture      | T123_2     | ✅       |
| S4: Autonomy          | T123_2     | ✅       |
| S5: Command center    | T123_2     | ✅       |
| S6: Integrations      | T123_3     | ✅       |
| S7: Compliance        | T123_3     | ✅       |
| S8: Security          | T123_3     | ✅       |
| S9: Pilot             | T123_3     | ✅       |
| S10: Procurement      | T123_3     | ✅       |
| S11: Final CTA        | T123_3     | ✅       |
| S12: Contacts         | T123_3     | ✅       |
| S13: Partners         | T123_3     | ✅       |
| Footer                | T123_3     | ✅       |
| Document drawer       | T123_3     | ✅       |
| Demo form drawer      | T123_3     | ✅       |
