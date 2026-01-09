# TASKS — Operator Funding Site

## Global rules for all tasks
- Small diffs preferred
- Keep copy operator-sharp (no fluff)
- Preserve primary CTA: Get Funded → get-funded.html
- No new frameworks

---

## Task 01 — Make site fail-safe if JS fails
Add `.js` gating so `.reveal` is visible by default.
- styles.css: set default reveal visible
- app.js: add `document.documentElement.classList.add('js')`
- ensure reveal animations still work

Acceptance:
- With JS disabled: content still visible
- With JS enabled: reveal animations run

---

## Task 02 — Finish homepage interactions
Implement in app.js:
- Funding Fit selector (data-fit)
- Stepper (data-stepper)
- Proof filters (data-filters)
- Accordions (data-acc)
Acceptance:
- No console errors
- Interactions work on mobile

---

## Task 03 — Tighten hero + proof copy for conversion
Improve:
- index.html hero headline/subhead
- proof cards (make more specific)
Acceptance:
- No new sections added
- Copy stays punchy and concrete

---

## Task 04 — Add "speed + requirements" microline to all pages
Add a consistent microline near primary CTA:
"$50k–$500k • Fast approvals • Minimal docs"
Acceptance:
- Present on all pages
- No layout breaks
