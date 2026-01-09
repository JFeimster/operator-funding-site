# TASKS — Operator Funding Site

> This file defines the only work allowed for automated agents (Jules).
> Small diffs. Conversion-first. No rewrites.

---

## Global Rules (Non-Negotiable)

- Follow AGENTS.md
- No frameworks, no npm, no build tools
- Preserve existing structure and copy tone (operator-first, blunt, no fluff)
- Do NOT remove visible content
- Primary CTA must remain: **Get Funded → get-funded.html**
- Site must remain functional if JavaScript fails

Every task must:
- produce zero console errors
- work on mobile
- keep links intact
- deploy cleanly to Vercel

---

## ✅ Task 01 — Reveal Animation Fail-Safe (COMPLETE)

**Goal:** Prevent blank pages if JavaScript fails.

**Status:** Done  
**Notes:**
- `.js` class added to `<html>`
- `.reveal` visible by default
- Animations gated behind `.js`

_No further action required._

---

## 🚧 Task 02 — Homepage Interaction Hardening

**Goal:** Ensure all homepage interactions are stable and resilient.

**Scope (only these components):**
- Funding Fit selector (`data-fit`)
- Stepper (`data-stepper`)
- Proof filters (`data-filters`)
- Accordion cards (`data-acc`)

**Requirements:**
- No JS errors if elements are missing
- Graceful no-op behavior if DOM nodes don’t exist
- Keyboard-accessible where applicable
- No layout shifts

**Acceptance Criteria:**
- All interactions work on desktop and mobile
- No console warnings or errors
- Content remains visible if JS is disabled

---

## 🚧 Task 03 — Micro-Interaction Polish (CSS-Only)

**Goal:** Increase perceived quality without structural changes.

**Allowed Changes:**
- Hover and active states for:
  - chips
  - cards
  - buttons
- Subtle lift + shadow (≤ 6px movement)
- Staggered reveal using existing `.reveal` classes

**Not Allowed:**
- New sections
- New animation libraries
- JavaScript changes unless strictly necessary

**Acceptance Criteria:**
- No performance degradation
- Motion timing between 150–300ms
- CTA buttons feel responsive and “alive”

---

## 🚧 Task 04 — Conversion Consistency Pass

**Goal:** Reduce friction before “Get Funded”.

**Scope:**
- Ensure every page includes:
  - a visible primary CTA
  - a consistent microline near CTAs:
    > `$50k–$500k • Fast approvals • Minimal docs`

**Rules:**
- CTA links must always point to `get-funded.html`
- No duplicate or conflicting CTAs

**Acceptance Criteria:**
- No broken links
