# Launch checklist — Operator Funding Site

**Not launch approval.** This is a source-backed checklist for the future production-readiness phase. Use synthetic lead data for tests.

## Repository and routing
- [ ] All ten HTML URLs resolve.
- [ ] Every HTML page loads `/assets/css/styles.css` and `/assets/js/app.js`; no stale root references.
- [ ] Internal navigation and all Get Funded CTAs work.
- [ ] Production Vercel SHA matches authorized GitHub commit.
- [ ] Desktop/mobile, keyboard navigation, reduced motion, and no-JavaScript reading verified.

## Funding intake
- [ ] Approved operating business identity and lead destination documented.
- [ ] False Received state removed; real submission only succeeds after acknowledged durable receipt.
- [ ] Server-side validation, abuse protection, privacy controls, secret management, and idempotency tested.
- [ ] Synthetic application delivered and traceable exactly once.
- [ ] Invalid/duplicate/offline/upstream-failure states tested.
- [ ] Unapproved financial/contact draft data removed from browser storage or replaced with reviewed solution.
- [ ] Consent, data sharing, and communication permissions reviewed.

## Claims and UX
- [ ] Privacy/Terms placeholders resolved and legal/compliance review completed.
- [ ] Proof-wall deals and testimonials substantiated or clearly labeled illustrative.
- [ ] Calculator outputs qualified and edge cases verified.
- [ ] Capital-option accordions and all mobile interactions usable and accessible.
- [ ] Analytics, if authorized, exclude applicant PII.
- [ ] Results, open blockers, commit SHA, and deployment evidence documented in `PROJECT_STATUS.md`.

**Do not collect real funding applications until the critical checks pass.**
