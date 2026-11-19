# TASKS.md — Operator Funding Site Roadmap

> **Proposed replacement**, prepared November 19, 2026. Not committed. Use this rather than resuming the stale Google Jules checklist.

## Status and sequencing
- Source of truth: `main` at baseline SHA `4bfa569`.
- **DONE (merged, runtime QA outstanding):** prior Task 01 fail-safe styles, Task 02 homepage hardening (PR #1), Task 03 CSS polish (PR #2).
- **OPEN:** legacy Task 04 CTA consistency; re-scope after reviewing claim accuracy and verified submission infrastructure. Do **not** replicate the old `Fast approvals • Minimal docs` microline without substantiation.
- **PRODUCTION GATE:** do not collect real financing applications until Critical tasks pass actual end-to-end verification and legal/claims review.
- **Execution sequence:** [1] FND-001, FND-003 and FND-005 truth/claims guardrails → [2] FND-002 and FND-004 secure intake/consent → [3] FND-006 and FND-007 behavior/math → [4] FND-008/009 UX and visual clarity → [5] FND-010/011/012 analytics, QA, launch.
- No external state changes or code changes until a specific task or batch is approved.

## 1. Site Audit & Architecture

### FND-001 — Stop false application success until durable lead delivery is available
- **Priority:** Critical | **Value:** Prevents applicant loss and misleading receipt messages | **Size:** S | **Deployment risk:** Medium
- **Scope:** Gate/replace the present faux success state on submission. Keep it a prototype until FND-002 is active. Clearly differentiate incomplete drafts from received applications.
- **Files:** `get-funded.html`; potentially `AGENTS.md`, `PROJECT_STATUS.md`.
- **Dependencies:** None. Avoid taking real submissions during implementation.
- **Acceptance:** No pathway shows “Received” without an acknowledged successful response from a live intake handler. Failed/offline submissions display a truthful recovery state. QA uses fictitious test data.
- **Evidence:** `get-funded.html` application submit handler comments say `no backend yet` and no POST exists.

### FND-006 — Repair capital options accordion and semantic markup
- **Priority:** High | **Value:** Fixes navigation and product comprehension | **Size:** S | **Deployment risk:** Low
- **Scope:** Replace nested button/anchor blocks with native accessible disclosure or equivalent valid markup; preserve card copy and CTAs. Verify the local lane wizard's jump links.
- **Files:** `options.html`, `styles.css`.
- **Dependencies:** None; can ship independently of intake.
- **Acceptance:** Each lane opens and closes by mouse and keyboard; links inside open content work; markup is valid; no JS dependency for basic disclosure; no regressions on mobile.

### FND-010 — Static architecture, SEO, and accessibility hardening
- **Priority:** Medium | **Value:** More discoverability, less regression risk | **Size:** M | **Deployment risk:** Low
- **Scope:** Finish URL/canonical metadata, sitemap/robots when site is publication-ready, valid semantics, keyboard focus, menu focus restoration, reduced-motion and reveal fail-safe; preserve no-build architecture.
- **Files:** `app.js`, `styles.css`, targeted HTML pages, `sitemap.xml`, `robots.txt` if approved.
- **Dependencies:** FND-003 for canonical brand/domain; browser QA access.
- **Acceptance:** No unverified structured-data claims; no hidden no-JS content; tab order, screen-reader labels, and mobile behavior tested; no broken routes.

## 2. Design System & UI Upgrades

### FND-008 — Conversion-driven page and mobile UX improvements
- **Priority:** High | **Value:** Higher qualified application starts and less abandonment | **Size:** M | **Deployment risk:** Medium
- **Scope:** Prioritize operator positioning by audience, clear primary action, trust near CTA, form progress/field explanations, meaningful cross-page sequencing, and mobile action-bar/form readability. Preserve current aesthetics and functional sections.
- **Files:** `index.html`, `options.html`, `get-funded.html`, `styles.css`, selected supporting pages.
- **Dependencies:** FND-001/002/003/004 definitions, and proof replacement strategy.
- **Acceptance:** One obvious primary CTA; no contradictory copy; mobile layouts verified at representative small/medium/large viewports; CTA path has no dead end; measurable start/completion events once tracking exists.

### FND-009 — Targeted design polish (not another micro-interaction task)
- **Priority:** Medium | **Value:** Credibility and product quality without costly rebuild | **Size:** M | **Deployment risk:** Low
- **Scope:** Use existing blue-violet/dark-ops system, but improve hierarchy, whitespace, proof presentation, form/error visual states, and card density. Do not redo already merged Task 03.
- **Files:** `styles.css`, approved HTML files.
- **Dependencies:** FND-008 priorities and browser visual review.
- **Acceptance:** Responsive, high-contrast, reduced-motion-aware layouts; no performance regression; design remains coherent across all pages.

## 3. Funding Application & Integrations

### FND-002 — Build a real secure, idempotent funding-intake pipeline
- **Priority:** Critical | **Value:** Creates real applications and traceable lead delivery | **Size:** L | **Deployment risk:** High
- **Scope:** First inspect existing approved Supabase/CRM/webhook infrastructure and choose a single canonical destination. Preferred minimal pattern: existing static form → same-origin Vercel Function → server-side validation, spam and rate controls, idempotent durable record → monitored routing/notification. No privileged keys in browser. Use least-privilege server secrets and redact logs. Do not build a full portal.
- **Files:** `get-funded.html`, proposed `api/apply.js` (or approved existing endpoint adapter), `vercel.json` only if necessary, docs and test fixtures.
- **Dependencies:** FND-003 verified operating identity/consent requirements; authorized destination credentials and record owner; explicit implementation approval.
- **Acceptance:** Test application with fictitious values reaches the approved system exactly once and can be traced by safe request ID; invalid, duplicate, bot-like, offline, and upstream-failure cases fail honestly; monitoring/owner handoff defined; client cannot access secrets.

### FND-004 — Intake validation, consent, and save/resume redesign
- **Priority:** Critical | **Value:** Data quality, applicant trust, lower support overhead | **Size:** M | **Deployment risk:** Medium
- **Scope:** Enforce complete step and final-submit schema; validate state/phone/email/numeric bounds and choices; review opt-in contact channel and appropriate partner-sharing/communications permission. Remove insecure sensitive draft storage or replace with explicitly approved secure resume design. Do not claim a server-side resume feature until implemented.
- **Files:** `get-funded.html`; selected `privacy.html`; server validator from FND-002.
- **Dependencies:** FND-002 endpoint schema, FND-003 policy decisions.
- **Acceptance:** No sensitive application draft persists in unapproved localStorage; invalid inputs cannot reach storage or show success; consent state is captured with the application; truthful save/resume behavior and accessible errors verified.

### FND-007 — Reframe funding calculator as an illustrative decision tool
- **Priority:** High | **Value:** Protects trust and qualifies users more reliably | **Size:** M | **Deployment risk:** Medium
- **Scope:** Remove implication of underwriting or eligibility from unsupported multipliers and the $50k minimum clamp. Either calibrate against verified partner eligibility logic or explicitly reframe as scenario planning with non-offer outputs and sensible out-of-range behavior. Keep genuine financial estimates distinct from a financing offer.
- **Files:** `calculator.html`, `index.html` and CTA copy if necessary.
- **Dependencies:** FND-003 product/claim verification; product-lane assumptions from actual partners.
- **Acceptance:** Low-revenue examples never imply guaranteed $50k eligibility; range inputs have defensible boundaries; disclaimer visible at results; outputs tested across edge cases.

## 4. Conversion Copy & Trust

### FND-003 — Verify identity, privacy, consent, and all financial claims
- **Priority:** Critical | **Value:** Legitimacy and protection of applicants | **Size:** M | **Deployment risk:** Medium
- **Scope:** Confirm brand/operator legal name, contact, geography, lender/broker/marketplace role, applicable disclosures, sharing policy, credit-check statements, speed/eligibility language, and Terms/Privacy effective dates. Legal/compliance reviewers must assess applicable requirements; do not assume approvals.
- **Files:** `privacy.html`, `terms.html`, headers/footers on all 10 pages, `get-funded.html`, potentially new disclosure page if required.
- **Dependencies:** Real operating entity and partner arrangements; legal/compliance input.
- **Acceptance:** No placeholder contacts, dates, or governing state; clear data use and consent; material claims supported or qualified; legal owner signs off before public collection.

### FND-005 — Replace or validate evidence on the proof wall
- **Priority:** Critical | **Value:** Removes unsupported trust claims | **Size:** M | **Deployment risk:** Medium
- **Scope:** Audit each of the nine proof entries and any homepage outcomes. Either attach documented client authorization and evidence or remove/relabel as clearly hypothetical examples; avoid testimonial wording for invented examples. Never publish fabricated logos/reviews/metrics.
- **Files:** `proof.html`, `index.html`, potentially `about.html`.
- **Dependencies:** Actual partner/client evidence owner; FND-003 claims policy.
- **Acceptance:** Every presented result has verifiable provenance or is unmistakably an illustrative scenario; disclosures appear with content; no unsupported “real deals” claim remains.

## 5. QA, Deployment & Optimization

### FND-011 — Implement privacy-appropriate analytics and attribution
- **Priority:** Medium | **Value:** Makes funnel performance measurable | **Size:** M | **Deployment risk:** Medium
- **Scope:** Select minimal events (CTA click, application start, step completion, validated submit attempt, actual accepted receipt, error). Use approved privacy approach; avoid PII in event names, URLs, payloads or logs. Capture source attribution only when appropriate.
- **Files:** `get-funded.html`, `app.js`, approved endpoint/integration.
- **Dependencies:** FND-002 confirmed receipt; FND-003 consent/analytics policy.
- **Acceptance:** Conversion success counts only durable acknowledged intake; test events trace a funnel, without raw personal/financial data.

### FND-012 — Cross-browser, mobile, failure-path, and launch checks
- **Priority:** Critical launch gate | **Value:** Prevents production regressions and lost applications | **Size:** M | **Deployment risk:** Low (test-only; release separately approved)
- **Scope:** Browser and keyboard QA across all ten pages; form validation/failure/duplicate/offline tests; no-JS content; performance and accessibility checks; stage/preview parity and post-deploy smoke test.
- **Files:** Test checklist/fixtures, `PROJECT_STATUS.md`, minimal corrections only under separately approved task scope.
- **Dependencies:** All required Critical tasks, available test environment and consent/claims approvals.
- **Acceptance:** End-to-end verified test lead is durably received; no false success on network failure; zero P0/P1 issues; production SHA/alias confirmed; browser findings recorded.

## Evidence baseline
- PR #1 https://github.com/JFeimster/operator-funding-site/pull/1
- PR #2 https://github.com/JFeimster/operator-funding-site/pull/2
- Source baseline https://github.com/JFeimster/operator-funding-site/tree/4bfa56905670f55034aeab40a0842f421fe8097a
- Vercel production SHA `4bfa569` verified through deployment record

## Status update convention
For every approved task: `TODO → IN PROGRESS → READY FOR REVIEW → DONE` or `BLOCKED`. Record exact SHA/PR, verification result, deployment and next owner in `PROJECT_STATUS.md`. Never claim complete based solely on merged code or Vercel `READY` status.
