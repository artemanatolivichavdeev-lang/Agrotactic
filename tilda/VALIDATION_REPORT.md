# VALIDATION_REPORT.md — v0.5 Tilda Split (25KB limit + Icon Audit)

## File Table (UTF-8 bytes)

| File           |   Bytes | ≤25KB | `<style>`? |   `<script>`?   | `.x-site` self-contained? |
| -------------- | ------: | :---: | :--------: | :-------------: | :-----------------------: |
| SITE_HEAD.html |     287 |  n/a  |     no     |       no        |            n/a            |
| CUSTOM_CSS.css | 205,161 |  n/a  |     no     |       no        |            n/a            |
| T123_01.html   |  20,569 |  ✅   |     no     |       no        |            ✅             |
| T123_02.html   |  17,221 |  ✅   |     no     |       no        |            ✅             |
| T123_03.html   |  12,880 |  ✅   |     no     |       no        |            ✅             |
| T123_04.html   |  24,824 |  ✅   |     no     |       no        |            ✅             |
| T123_05.html   |  17,336 |  ✅   |     no     |       no        |            ✅             |
| T123_06.html   |  21,961 |  ✅   |     no     |       no        |            ✅             |
| T123_07.html   |  24,039 |  ✅   |     no     | yes (JS part 1) |        script-only        |
| T123_08.html   |  14,689 |  ✅   |     no     | yes (JS part 2) |        script-only        |

## Split Map

### CSS: 17 blocks → CUSTOM_CSS.css (205 KB)

Extracted in original order. Pure CSS, no `<style>` tags, no `<` chars. Ends with `}`.

### JS: 14 blocks → T123_07 + T123_08 (split because merged JS > 25KB)

Each wrapped in safe IIFE with try/catch + DOMContentLoaded.

### HTML sections

| T123 File | Sections                                                                    |
| --------- | --------------------------------------------------------------------------- |
| T123_01   | Scanline + S0 Header + S1 Hero + Trust strip + S2 Operational model (start) |
| T123_02   | S2 Operational model (end) + S3 Architecture                                |
| T123_03   | S4 Autonomy + S5 Scenarios                                                  |
| T123_04   | S6 Integrations + S7 Compliance                                             |
| T123_05   | S8 Security + S9 Pilot                                                      |
| T123_06   | S10 Procurement + S11 CTA + S12 Contacts + S13 Partners + Footer + Drawers  |
| T123_07   | JS (blocks 1-11)                                                            |
| T123_08   | JS (blocks 12-14: partners reveal + demo form + main init)                  |

## ID Uniqueness

- **76 total IDs, 76 unique — no duplicates** ✅
- Fix applied: `id="x-open-drawer-3"` removed from procurement link in T123_06, replaced with `onclick` delegation

## Forbidden Artifacts Check

No files contain: `<!DOCTYPE>`, `<html>`, `<head>` (only `<header>`), `<body>`, `nominify`, `t-records`, `allrecords` ✅

## Icon Audit

### Inventory

| Type                   | Source  |           Output            | Match |
| ---------------------- | :-----: | :-------------------------: | :---: |
| Inline SVG             |   48    |             48              |  ✅   |
| HTML entities (&#...)  |   17    |             17              |  ✅   |
| Emoji in icon spans    |   19    |             19              |  ✅   |
| CSS content properties | present | present (in CUSTOM_CSS.css) |  ✅   |
| `????` occurrences     |    0    |              0              |  ✅   |
| `�` replacement chars  |    2    |        **0** (fixed)        |  ✅   |

### Defects Fixed

| Location                                        | Before       | After        | Reason                                                                                               |
| ----------------------------------------------- | ------------ | ------------ | ---------------------------------------------------------------------------------------------------- |
| T123_01 line 198: `data-doc="security"` badge   | `�` (U+FFFD) | 🔒 (U+1F512) | Replacement char in source — replaced with lock emoji matching "Защита данных" context               |
| T123_01 line 204: `data-doc="compliance"` badge | `�` (U+FFFD) | 📋 (U+1F4CB) | Replacement char in source — replaced with clipboard emoji matching "Документы и отчётность" context |

### Render Sanity

- All 48 SVGs have visible stroke/fill attributes ✅
- All `<span class="x-badge__icon">` contain emoji or entity (none empty) ✅
- CSS `content` properties preserved in CUSTOM_CSS.css (no loss during extraction) ✅
- No `�` (U+FFFD) anywhere in output ✅

### Icon Audit Result: **PASS** ✅
