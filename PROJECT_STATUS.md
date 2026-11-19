# PROJECT_STATUS.md — Operator Funding Site

> Proposed initial status file. Audit date: **2026-11-19**. Read-only inspection; no repo or deployment changes made.

## Current status
**PROTOTYPE / NOT CLEARED FOR REAL LEAD COLLECTION**

- **Repo:** https://github.com/JFeimster/operator-funding-site
- **Canonical branch:** `main`
- **Head SHA:** `4bfa56905670f55034aeab40a0842f421fe8097a` (2026-01-09)
- **Vercel project:** `operator-funding-site`, ID `prj_dVn4rdzfHZLZkKcWJHe22FyzMiUI`
- **Production deployment:** `dpl_EMyigt2QXgBf1LGL2UjbxuFmrU8r` — READY, same SHA, target=production, mapped to `operator-funding-site.vercel.app`
- **Stack:** 10 static HTML pages, `styles.css`, `app.js`, no build step
- **Operating brand:** TBD
- **QA limitation:** Direct public-site retrieval failed. Vercel indicates SSO protection on deployment URLs; browser-rendered visuals, functional click paths, console logs, mobile layouts, and a no-JS run were not verified.

## Verified completed work
| Work | Evidence | Status |
| --- | --- | --- |
| Basic ten-page architecture and primary CTA navigation | `main` tree and source links | Source verified |
| Reveal default-visible styles and `.js` gating | `styles.css` lines 680–696 | Source verified; runtime pending |
| Homepage `<details>/<summary>` hardening and initial fallback content | PR #1, merge `aefedb1` | Merged; runtime pending |
| CSS micro-interaction polish and staggered reveal | PR #2, merge `4bfa569` | Merged; runtime pending |
| Current production target | Vercel deployment record | READY; rendered runtime pending |
| Static href / fragment scan across ten pages | Local analysis of checked-out `main` file contents | No missing local HTML destinations or missing same-page IDs found; runtime pending |

## Critical open blockers
1. **FND-001:** `get-funded.html` uses client-only success and no outbound submission. Evidence: lines ~805–829.
2. **FND-002:** Draft saved in browser localStorage with financial/contact fields; no secure cross-device resume. Evidence: `get-funded.html` ~776–799.
3. **FND-003:** Unverified quantified funding outcomes and testimonials on `proof.html` (nine proof-wall entries; individual statements presented as real).
4. **FND-004:** Privacy/Terms contain placeholders for effective date, contact and legal jurisdiction; business/operator identity and consent need review.
5. **FND-005:** Heuristic calculator clamps estimates to $50k minimum; cannot be treated as qualification. Evidence: `calculator.html` calculation script.

## Additional priority defects
- `options.html` uses `<button>` wrappers containing anchor links in the capital lane accordion and lacks matching disclosure toggle behavior in the current global script.
- `get-funded.html` only validates basic values and the current wizard step; lacks complete per-field and server-side validation.
- `app.js` reveal logic has no `IntersectionObserver` feature test or fallback after setting `.js`; keyboard focus for mobile drawer requires audit.
- Existing `TASKS.md` still marks Task 02/03 in progress despite merged PR #1/#2 and references discontinued Google Jules.
- No test suite, sitemap, `robots.txt`, or `PROJECT_STATUS.md` is in `main`.

## Known code-level facts versus pending tests
- **Confirmed from source:** mock application submit, localStorage draft, calculator multipliers, legal placeholders, source-level accordion markup, existing JS event handlers and CSS.
- **Not yet verified:** interactive correctness in desktop/mobile browsers, live HTML without authentication, header dropdown behavior, form browser flow, accessibility audit, network responses, production errors, performance scores, consent/provider systems, or actual lender/business claims.

## Approved next action
**None yet.** Propose FND-001/002/003/004/005 as the first cohesive readiness block, with explicit approval required before modifying GitHub, Vercel, or external systems.

## Most important next decision
Confirm the **legitimate submission destination and operating entity** before activating Get Funded. Preserve the static frontend. A same-origin Vercel Function that validates and durably stores/routes leads in an already approved source-of-truth system is a good default; do not create a new database, CRM pipeline, or webhook until the existing systems are inspected and the specific implementation is approved.

## Update log
| Date | Task ID | Commit / PR | Deploy | Verification | Open blocker |
| --- | --- | --- | --- | --- | --- |
| 2026-11-19 | Read-only baseline audit | `4bfa569` (existing) | `dpl_EMyigt2QXgBf1LGL2UjbxuFmrU8r` READY | GitHub source, PR history, Vercel records, static links | Lead funnel mock; proof/legal/estimates unverified; runtime browser QA pending |

## Future update format
`YYYY-MM-DD — Task FND-### — PR # / SHA — Preview/production deployment — checks passed/failed — blockers — next action`.
