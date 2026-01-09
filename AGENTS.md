# AGENTS.md — Operator Funding Site (Static)

## What this repo is
A static multi-page marketing site for US small business funding ($50k–$500k).
Stack: plain HTML + styles.css + app.js (no build step).

## Non-negotiables
- Do NOT introduce frameworks (React/Next/Vite/etc).
- Do NOT add npm/package.json unless explicitly requested.
- Keep the conversion flow: primary CTA is always "Get Funded" → get-funded.html
- Do NOT remove or hide visible copy. If you change copy, it must stay punchy + operator tone.

## File layout
- index.html (home)
- options.html, calculator.html, playbooks.html, process.html, proof.html, about.html
- privacy.html, terms.html
- styles.css (global styles)
- app.js (global interaction logic)

## Interaction rules
If you add a new interactive block:
- Prefer data-* attributes
- Keep logic in app.js
- Ensure page still works if JS fails (content visible by default)

## “Definition of done” for changes
- No console errors
- No broken links
- Layout still works on mobile
- CTA buttons still point to get-funded.html

## Deployment
Vercel deploys from main branch. Keep changes small and reviewable.
