# Operator Funding Site

**Operator-first business funding website · Static HTML/CSS/JavaScript · [Live site](https://operator-funding-site.vercel.app/)**

> **Current status: Prototype — not cleared for real funding applications.** The published interface is not a verified working intake channel. In particular, the application currently shows a receipt message without transmitting a lead to a backend. Do not send real applicants or paid conversion traffic to this funnel until the critical readiness work is complete.

## Purpose

Build a fast, credible, conversion-focused business funding experience for U.S. established, revenue-generating small businesses exploring approximately **$50,000–$500,000** in capital.

The primary audience includes DTC/ecommerce operators, B2B SaaS founders, agencies, and professional-service businesses. The primary call to action is **Get Funded** → `get-funded.html`.

The product should help operators understand capital options, repayment tradeoffs, likely documentation needs, and next steps—without promising approvals, rates, timelines, or eligibility.

**Brand/operator identity:** TBD. Do not treat placeholder business information as an approved legal identity.

## Links

- **Repository:** https://github.com/JFeimster/operator-funding-site
- **Production URL:** https://operator-funding-site.vercel.app/
- **Development guardrails:** [AGENTS.md](AGENTS.md)
- **Prioritized backlog:** [TASKS.md](TASKS.md)
- **Verified status and handoff:** [PROJECT_STATUS.md](PROJECT_STATUS.md)

The GitHub `main` branch is the canonical source of truth. Vercel deploys from GitHub; a `READY` deployment indicates deployment status, **not** verified functional or compliance readiness.

## Architecture

This project intentionally uses a simple, framework-free multipage architecture:

- **HTML5** for page structure and content
- **CSS3** in `assets/css/styles.css` for shared visual styles and responsive layouts
- **Vanilla JavaScript** in `assets/js/app.js` plus small page-local scripts for interactions
- **GitHub** for source control and **Vercel** for hosting

There is **no framework or build step**. Do not migrate to Next.js, React, Vite, or a website builder without a demonstrated need and explicit approval. A narrowly scoped server-side Vercel Function may eventually be appropriate for secure application intake without replacing the static frontend.

### Pages

| File | Purpose |
| --- | --- |
| `index.html` | Homepage / primary funding entry point |
| `pages/options.html` | Capital options and tradeoffs |
| `pages/calculator.html` | Illustrative Funding Fit calculator |
| `pages/playbooks.html` | Growth and capital-use scenarios |
| `pages/proof.html` | Funding outcomes / proof wall (**unverified content; review required**) |
| `pages/process.html` | Application and funding process |
| `pages/get-funded.html` | Four-step application UI (**no working lead submission yet**) |
| `pages/about.html` | Operating approach and positioning |
| `pages/privacy.html` | Draft privacy policy (**placeholders remain**) |
| `pages/terms.html` | Draft terms (**placeholders remain**) |

Shared files: `assets/css/styles.css`, `assets/js/app.js`, `AGENTS.md`, `TASKS.md`, `PROJECT_STATUS.md`, and this README.

## Repo organization

The homepage stays at the root; nine secondary HTML files live under `pages/`. Vercel rewrites in `vercel.json` preserve the original public `/*.html` URLs. Shared assets live in `assets/css/` and `assets/js/`, with tracked placeholders for `assets/images/` and `assets/icons/`. The `api/integrations.md` document is planning-only; `tests/` is tracked with `.gitkeep`. No server endpoint or tests have been created.

- [Architecture v1.2](docs/architecture.md)
- [Launch checklist](docs/launch-checklist.md)

## Run locally

No dependencies need to be installed.

1. Clone the repository: `git clone https://github.com/JFeimster/operator-funding-site.git`
2. Enter it: `cd operator-funding-site`
3. Open `index.html` in a browser, or use a local static HTTP server for more realistic navigation and loading behavior.

For example, with Python installed:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000/`. Python’s simple static server does **not** implement the Vercel rewrites: secondary pages can be previewed at `/pages/{name}.html`, while canonical public URLs must be checked on Vercel or in a Vercel-compatible preview. Local static previewing **does not** validate submission, routing, security, or Vercel behavior.

## Current implementation

**Source-verified:**

- Ten HTML pages and a shared CSS/JavaScript layer
- Homepage Funding Fit selector, process stepper, and filtering logic
- Mobile navigation and responsive CSS rules
- Initial content fallbacks and native `details`/`summary` on the homepage (merged [PR #1](https://github.com/JFeimster/operator-funding-site/pull/1))
- CSS-only hover and staggered reveal enhancements (merged [PR #2](https://github.com/JFeimster/operator-funding-site/pull/2))
- Four-step applicant questionnaire and client-side draft-save logic

**Not verified:** cross-device rendering, live browser interactions, accessibility/performance results, real lead intake, or legal/compliance approval. See [PROJECT_STATUS.md](PROJECT_STATUS.md) for the audit evidence and current testing limitations.

## Production-readiness blockers

**Do not accept real applications until these are resolved and tested.**

1. **False submission receipt:** `get-funded.html` intercepts submission and shows “Received” without a network request or durable lead delivery.
2. **Sensitive local drafts:** current Save & Continue stores financial and contact fields in browser `localStorage`; no secure cross-device resume exists.
3. **Unverified proof:** `proof.html` presents specific outcomes and testimonial-style statements without source evidence in this repository.
4. **Identity, legal and consent gaps:** operating brand and some effective dates, email addresses, jurisdiction and disclosures are still placeholders or need review.
5. **Illustrative calculator:** its hardcoded multipliers and $50,000 minimum display floor should not be represented as an eligibility or underwriting result.
6. **Interaction/accessibility defects:** capital-option accordions contain invalid nested interactive controls; other mobile and failure-state behavior needs browser QA.

These are **known gaps**, not allegations of verified customer losses, security incidents, or actual false funding outcomes.

## Development priorities

Execute only the authorized work, in this order:

1. **Truth and trust:** eliminate false submission success; verify branding, disclosures, funding claims, and proof.
2. **Real intake:** connect the existing application to a reviewed, secure, server-validated and traceable submission destination; fix consent, validation and draft behavior.
3. **Core functionality:** repair accordions and ensure the calculator communicates illustrative—not guaranteed—results.
4. **Conversion and design:** improve mobile usability, CTA sequencing, error states, hierarchy, and trust elements while preserving the existing visual system.
5. **Launch QA and optimization:** verify accessibility, failure paths, performance, analytics without applicant PII, deployment parity, and end-to-end lead receipt.

**Implementation detail and acceptance criteria:** [TASKS.md](TASKS.md). **Latest verified state, blockers, and commit/deployment history:** [PROJECT_STATUS.md](PROJECT_STATUS.md).

## Working conventions

- Review `AGENTS.md`, `TASKS.md`, and `PROJECT_STATUS.md` before starting a new task.
- Preserve working code, the static-site approach, and the approved operator-first voice; avoid speculative rewrites.
- Treat `main` as canonical and make small, reviewable changes.
- Never invent testimonials, lender relationships, approval odds, rate claims, or funding timelines.
- Never report a funding application as **received** until an actual server acknowledgment confirms durable receipt.
- Do not expose credentials or sensitive applicant data in browser scripts, logs, analytics, or URLs.
- Test with synthetic information; record evidence, commit/PR, deployment state, blockers, and next steps in `PROJECT_STATUS.md`.
- No external integrations, file changes beyond approved scope, merges, or deployments without explicit authorization.

## Immediate next milestone

**Restore integrity to the funding funnel before visual expansion.** Confirm the approved operating entity and actual lead destination; remove the false-success behavior; then implement and test a minimal secure application pipeline. The existing static UI remains the foundation.

---

*Status described above reflects source review and project records as of November 19, 2026. Consult [PROJECT_STATUS.md](PROJECT_STATUS.md) for updates; this README is an overview, not the live task tracker.*
