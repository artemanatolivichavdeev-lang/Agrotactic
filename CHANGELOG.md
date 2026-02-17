# CHANGELOG (TILDA-ONLY)

## 2026-02-17 — v0.4 (Enterprise Polish)

- **CSS Fixes**: Added Missing styles for Trust Badges, Chips, Self-Check, and Contacts.
- **Localization**: Translated all UI elements (Badges, Navigation) to Russian.
- **Content**: Added 4th bullet point to Role Switcher tabs (IT/Eng/COO).
- **Tilda Compatibility**: Replaced `#recFORM` with safe placeholder `#rec99999999`. Scoped all animations.
- **Accessibility**: Added ARIA roles and attributes for Tabs.

---

## 2026-02-17 — v0.3

- **Visual Upgrade**: Added "Industrial Tactical" FUI elements.
- **Hero**: Replaced mockup placeholder with live CSS/SVG "Operations Map" (Radar scan + Active zones).
- **Command Center**: Added CSS-animated bar charts and process flow visualizations to cards.
- **Effects**: Added global "Scanline" overlay and "Glitch" text effects on hover.
- **Icons**: Enhanced card icons with technical UI elements.

---

## 2026-02-17 — v0.2

- **Redesign & Remaster**: Applied "Industrial Tactical / Mission Control" aesthetic.
- **Visuals**: Primary accent switched to Cyan (`#00e5ff`). Added technical grid backgrounds and corner bracket decorations.
- **Typography**: Labels and controls strictly use JetBrains Mono. Increased contrast.
- **Refinement**: Improved card hover states ("glitch" effect), sharper borders, and technical UI elements.
- **TILDA-ONLY confirmed**: No external dependencies.

---

## 2026-02-17 — v0.1 (Rev 2)

- Полная сборка Home: Header (sticky + mobile) + Hero (role switcher, hotspots, trust strip) + все секции S2–S12.
- Реализованы компоненты: Drawer (Trust Pack / Procurement Pack), Accordion, Stepper A2→A4, Self-check, Cards.
- CSS полностью скоуплен в `.x-site` + `x-*` классы. Токены через `:root` / `.x-site`.
- JS: sticky, burger, tabs, accordion, drawer (overlay + Escape + focus), hotspots (hover/tap), self-check.
- Шрифты: Inter + JetBrains Mono (через HEAD).
- TILDA-ONLY confirmed. Единственный артефакт: `/tilda/t123/home/home.html`.
- **UX Fixes (Revision 2):** Stepper A2-A4 clickable + JS logic, de-duped buttons in S10, "Download" links open Drawer instead of scroll-to-top.

---

## 2026-02-17

- Перевод проекта в режим **TILDA-ONLY**: единственная "истина" = папка `/tilda/`.
- Убраны упоминания и зависимость от `/src/` (чтобы Antigravity не плодил две версии).
- Введён обязательный релизный снимок: `/tilda/releases/YYYY-MM-DD_vX/` (HEAD + T123 артефакты).
- Обновлены WORKFLOW/COPY_TO_TILDA/QA_CHECKLIST/AGENTS под новый режим.

---

## 2026-02-15

- Обновлён Hero под ТЗ "Industrial Tactical / Mission Control".
- Унифицированы тексты CTA, eyebrow, trust bar в RU.
- Добавлены состояния кнопок (hover/focus/active/disabled) и видимый focus.
- Усилено скопирование в Tilda: весь CSS заскоуплен в `.x-site` и префикс `x-`.
- Обновлён T123-артефакт до формата "только секция" + inline style.
