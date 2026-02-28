# CHANGELOG

## v0.5 — Tilda-safe split + Icon audit (2026-02-28)

### Architecture

- **25KB per T123 file limit** enforced (Tilda T123 block max)
- 8 T123 files (6 HTML-only + 2 JS-only)
- CSS 205KB → Site Settings → Custom CSS (not HEAD)
- SITE_HEAD 287B → fonts only
- JS split across T123_07 + T123_08 (IIFE with try/catch)
- Each HTML T123 has self-contained `.x-site` wrapper

### Icon Audit

- Fixed 2 `�` (replacement chars) inherited from source:
  - `data-doc="security"` badge → 🔒
  - `data-doc="compliance"` badge → 📋
- All 48 SVGs, 17 entities, 19 emoji verified matching source
- No `????` in any output file

### Changes from v0.4

- Split T123_3 (104KB) into 4 files to meet 25KB limit
- Split JS (38KB) into 2 T123 files (T123_07 + T123_08)
- Added Icon Audit with defect fixes
- Removed `/tilda/release/v0.4/` subfolder structure — flat `/tilda/` output

## v0.4 — Tilda-safe split (2026-02-28)

- CSS in Custom CSS, fonts-only HEAD, self-contained wrappers
- Fixed duplicate id=x-open-drawer-3

## v0.3 — Initial split (2026-02-28)

- First split attempt — caused white screen due to HEAD truncation
