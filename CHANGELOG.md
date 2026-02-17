# CHANGELOG (TILDA-ONLY)

## 2026-02-17
- Перевод проекта в режим **TILDA-ONLY**: единственная “истина” = папка `/tilda/`.
- Убраны упоминания и зависимость от `/src/` (чтобы Antigravity не плодил две версии).
- Введён обязательный релизный снимок: `/tilda/releases/YYYY-MM-DD_vX/` (HEAD + T123 артефакты).
- Обновлены WORKFLOW/COPY_TO_TILDA/QA_CHECKLIST/AGENTS под новый режим.

---

# CHANGELOG

## 2026-02-15
- Обновлён Hero под ТЗ "Industrial Tactical / Mission Control".
- Унифицированы тексты CTA, eyebrow, trust bar в RU.
- Добавлены состояния кнопок (hover/focus/active/disabled) и видимый focus.
- Усилено скопирование в Tilda: весь CSS заскоуплен в `.x-site` и префикс `x-`.
- Обновлён T123-артефакт до формата "только секция" + inline style.
