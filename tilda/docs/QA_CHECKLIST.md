# QA_CHECKLIST — Pre-Launch (TILDA-ONLY, 1 page)

Goal: In 10–20 minutes, verify the website before launch / before handing it over.

---

## A) Tilda specifics (critical)
- [ ] Pages are **published** (verify via public URL).
- [ ] If you changed **HEAD** code — you **republished all pages**.
- [ ] All custom sections are inserted into **T123** (not a regular text block).
- [ ] CTA anchors use real Tilda block IDs (`#rec...`) and actually scroll.

---

## B) Head / SEO basics (minimum)
- [ ] Title exists and is unique.
- [ ] Meta Description exists and is relevant.
- [ ] Charset UTF-8 and viewport meta are set.
- [ ] Favicon is set and visible.

---

## C) Content & UX (showcase)
- [ ] All copy is **in Russian** (consistent wording).
- [ ] First screen answers: who/what + one main CTA.
- [ ] Contacts: phone clickable, messengers open, address correct.
- [ ] No placeholder/junk text.

---

## D) Lead form (most important)
- [ ] Submitted 3 test leads (different names/phones).
- [ ] Leads arrive (email/CRM/spreadsheet).
- [ ] Clear “success” state (thank-you).
- [ ] If using Webhook — POST payload arrives on your URL.

---

## E) Responsive (3 widths)
- [ ] 375px: no overflow, readable text, tappable buttons.
- [ ] 768px: grid doesn’t break, spacing OK.
- [ ] 1440px: no too-wide text lines, Hero coherent.

---

## F) Performance
- [ ] Images are optimized (no raw 10MB files).
- [ ] Not too many font weights.
- [ ] No heavy libraries “for one effect”.

---

## G) JavaScript sanity (errors & conflicts)
- [ ] Published page Console: **no red errors**.
- [ ] Custom CSS/JS is scoped to `.x-site` and `x-...` classes.
- [ ] CTAs, anchors, menus, modals (if any) work.

---

## H) Accessibility (minimum)
- [ ] One H1; headings are logical (H2/H3).
- [ ] Important images have alt.
- [ ] Contrast is sufficient.
- [ ] Keyboard navigation works for main actions.

---

## I) Final link check
- [ ] No broken links.
- [ ] External links open correctly.
- [ ] Privacy/terms present if required.

---

## J) Release steps (do at the end)
- [ ] Re-check published version in incognito.
- [ ] Save a “release” copy: `tilda/releases/YYYY-MM-DD_vX/` (HEAD + T123 snippets).
- [ ] Record changes in `tilda/docs/CHANGELOG.md`.
