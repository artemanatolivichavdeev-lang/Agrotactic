# CHANGELOG

## v0.4 — Tilda-safe split (2026-02-28)

### Architecture

- **CSS moved to Custom CSS** (Site Settings → More → Custom CSS) instead of HEAD
  - Prevents HEAD truncation that caused white-screen incident in v0.3
- **SITE_HEAD.html** reduced to fonts only (289 bytes) — impossible to truncate
- **JS moved to T123_3.html** (end of file) instead of HEAD
  - JS wrapped in safe IIFE with try/catch to prevent cascade failures
- Each T123 file has **self-contained `.x-site` wrapper** (opens and closes in same file)
  - Only T123_1 has `id="agro-home"`; T123_2/3 use class-only wrapper

### Changes from v0.3

- Removed all CSS from HEAD (was 252 KB → now 0 KB)
- Removed all JS from HEAD (was in DOMContentLoaded wrapper → now in T123_3 IIFE)
- Added `CUSTOM_CSS.css` as separate file for Tilda Custom CSS field
- Added try/catch around merged JS to prevent one error from killing the page
- Fixed duplicate `id="x-open-drawer-3"` (replaced with onclick delegation in T123_3)

### Files

- `SITE_HEAD.html` — 289 bytes (Google Fonts only)
- `CUSTOM_CSS.css` — 213 KB (17 CSS blocks, pure CSS)
- `T123_1.html` — 13 KB (Header + Hero + Trust)
- `T123_2.html` — 38 KB (S2–S5)
- `T123_3.html` — 104 KB (S6–S13 + Footer + Drawers + JS)
- `VALIDATION_REPORT.md` — full split map + checks
- `DEPLOY_TILDA.md` — step-by-step paste order
