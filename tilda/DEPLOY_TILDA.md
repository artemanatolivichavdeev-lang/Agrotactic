# DEPLOY_TILDA.md — v0.5 (8 T123 blocks, 25KB limit)

## Step 0 — Clean old code

1. Remove all existing T123 blocks on the page
2. Clear Page HEAD (Page Settings → Additional → HTML in HEAD)
3. Clear Custom CSS (Site Settings → More → Custom CSS)

## Step 1 — Custom CSS

**Site Settings → More → Custom CSS**

- Paste full contents of `CUSTOM_CSS.css` (~205 KB, pure CSS)
- Save

> ⚠️ No `<style>` tags — Tilda wraps automatically. NEVER paste CSS in HEAD.

## Step 2 — Page HEAD (fonts only)

**Page Settings → Additional → HTML code in HEAD of the page**

- Paste `SITE_HEAD.html` (3 lines, 287 bytes)
- Save

> Use Page HEAD, not Site HEAD.

## Step 3 — Add 8 T123 blocks

**Other → T123 (Embed HTML Code)** — add 8 blocks in exact order:

| #   | File         | Size  | Content                                                    |
| --- | ------------ | ----- | ---------------------------------------------------------- |
| 1   | T123_01.html | 20 KB | Header + Hero + Trust + Operational model (start)          |
| 2   | T123_02.html | 17 KB | Operational model (end) + Architecture                     |
| 3   | T123_03.html | 13 KB | Autonomy + Scenarios                                       |
| 4   | T123_04.html | 25 KB | Integrations + Compliance                                  |
| 5   | T123_05.html | 17 KB | Security + Pilot                                           |
| 6   | T123_06.html | 22 KB | Procurement + CTA + Contacts + Partners + Footer + Drawers |
| 7   | T123_07.html | 24 KB | JavaScript part 1                                          |
| 8   | T123_08.html | 15 KB | JavaScript part 2                                          |

- Set top/bottom padding = 0 on each block
- **Order matters**: 1 → 2 → 3 → 4 → 5 → 6 → 7 → 8

## Step 4 — Publish

1. Publish page
2. Publish all pages (для CSS)

## Step 5 — Verify (published page only)

- [ ] Page renders (no white screen)
- [ ] DevTools Console: no red errors
- [ ] Header nav + burger menu
- [ ] Role switcher (Hero tabs)
- [ ] Autonomy + Scenario pickers
- [ ] Drawers: "Запросить демо", "Пакет документов"
- [ ] Demo form stepper
- [ ] Scroll-reveal animations
- [ ] Integration calculator

### Icon check (after publish)

- [ ] Header logo SVG visible
- [ ] Trust badges: 🔒 ⚡ 🚧 📦 📋 visible (not "????")
- [ ] Architecture cards: SVG icons visible
- [ ] Compliance/Security: entity icons visible
- [ ] Partners section: icons visible

## ⚡ If White Screen

1. Console → first red error
2. Clear Custom CSS → publish → content appears? = CSS problem
3. Remove T123_07+08 → publish → content appears? = JS crash
4. Clear HEAD → publish → appears? = HEAD corrupt
5. **Rules**: CSS → only Custom CSS. JS → only T123_07/08. HEAD → only fonts.
