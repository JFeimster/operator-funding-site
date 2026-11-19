# AGENTS.md — Operator Funding Site

> Proposed revision, prepared November 19, 2026. Not merged to GitHub.

## Project mandate
A US operator-first business funding website for established small businesses exploring approximately $50,000–$500,000 in capital. Brand is TBD. Primary action: **Get Funded** → `get-funded.html`.

## Canonical source and architecture
- Canonical repository: `JFeimster/operator-funding-site`, branch `main`.
- Keep the existing static HTML5/CSS3/vanilla JavaScript architecture. No framework, build pipeline, or `package.json` without a specific, approved justification.
- Preserve the 10 current HTML routes, `assets/css/styles.css`, and `assets/js/app.js`. Do not duplicate pages or rebuild working sections.
- A narrowly scoped Vercel Function/API endpoint is compatible with the static frontend **if approved**, because true secure lead handling cannot be implemented in browser-only JavaScript.
- Keep root HTML page routes; shared assets live in `assets/css/` and `assets/js/`. See `docs/architecture.md`.
- Check the current source, recent PRs, and actual Vercel deployment before proposing changes.

## Execution constraints
- Audit and draft work are read-only by default. No GitHub edits, PRs, deployments, external records, paid actions, integration changes, or production tests with real personal information without specific authorization.
- Implement only the approved task ID(s). Small, reviewable changes; no speculative rewrites or unrelated cleanup.
- Run applicable checks before recommending merge. A `READY` deployment is not equivalent to functional QA.
- Record task ID, commit/PR, deployment, tests, blockers, and next action in `PROJECT_STATUS.md` for every completed change. Update `TASKS.md` statuses in the same change.

## Conversion and evidence guardrails
- Primary CTA must remain Get Funded → `get-funded.html` unless the user approves an alternate funnel.
- Never display an application as **received, submitted, routed, or approved** before an actual successful server response confirms durable receipt.
- Do not invent financial outcomes, reviews, partner relationships, certifications, pricing, approval timelines, rates, credit-pull practices, or eligibility guarantees.
- Product, funding, and compliance claims require an evidence owner and review before public release. Distinguish illustration from eligibility or a financing offer.
- If an operating brand is TBD, do not invent corporate identity, legal address, contact inbox, or governing jurisdiction. Publication must be blocked on actual identity/consent gaps.
- No legal conclusion should be implied by a draft Privacy or Terms page; route material gaps for qualified legal/compliance review.

## Data security and intake
- No secrets in static HTML or JavaScript. No client-side calls carrying privileged API keys.
- Do not retain contact or financial application information in `localStorage` or `sessionStorage` without a deliberately reviewed privacy/security design. Prefer a server-side secure save/resume mechanism if actually required.
- Use same-origin HTTPS POST to a server-validated intake endpoint, with field restrictions, abuse controls, least-privilege storage, request identifiers/idempotency, sensible logging/redaction, explicit error and retry behavior, and verified routing.
- Do not expose personal or financial fields in analytics URLs, browser logs, tracking events, or client-visible response payloads.
- Use test data for QA, not genuine applicant details.

## UX, accessibility, and performance
- Keep content visible without JavaScript; progressive enhancement over JS-required display.
- Use semantic elements (`details/summary` for disclosure), valid nesting, keyboard operation, visible focus, and reduced-motion behavior.
- Verify 320–1440px layouts, mobile menu behavior, no horizontal overflow, form navigation, touch targets, and readable contrast.
- Prefer functional clarity over ornamental animation. Preserve existing dark-ops/neo-SaaS aesthetic unless a new direction is approved.

## Definition of done
- Relevant links and routes work; no unexpected browser errors.
- All accepted functional behaviors have been exercised, including failure cases.
- Financial/trust assertions are supported or explicitly labeled as illustrative.
- Any application success state is backed by confirmed server receipt and record availability.
- `TASKS.md` and `PROJECT_STATUS.md` reflect the exact verified change, SHA, test results, and remaining blockers.
- Production deployment only when explicitly authorized.
