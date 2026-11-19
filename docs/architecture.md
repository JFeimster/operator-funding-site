# Operator Funding Site — architecture v1.1

## Source and deployment
- Canonical repo: `JFeimster/operator-funding-site`, branch `main`.
- Hosting: Vercel; no build step or framework.
- Current interface is a prototype: `get-funded.html` does **not** deliver real applications.

## Directory layout
```text
/
├── index.html
├── get-funded.html
├── options.html
├── calculator.html
├── process.html
├── playbooks.html
├── proof.html
├── about.html
├── privacy.html
├── terms.html
├── assets/
│   ├── css/styles.css
│   └── js/app.js
├── docs/
│   ├── architecture.md
│   └── launch-checklist.md
├── README.md
├── AGENTS.md
├── TASKS.md
├── PROJECT_STATUS.md
└── .gitignore
```

## URL and asset contract
1. All 10 HTML pages stay at repository root to preserve existing `.html` links and public URLs.
2. Each page loads `assets/css/styles.css` (preload and stylesheet) and `assets/js/app.js` (deferred).
3. The moved CSS and JS retain their original contents; layout, behavior, and app logic are not intentionally changed.
4. Add `assets/images/`, `assets/icons/`, `tests/`, or `api/` only when actual files exist.
5. No Next.js/React or new build system without separate approval.

## Future integration boundary
- Keep the funding intake UI at `get-funded.html`.
- An approved same-origin Vercel Function may later accept securely validated requests and deliver them to an approved canonical destination.
- Do not expose privileged credentials to frontend JavaScript. Show a successful receipt only after durable server acknowledgment.
- No API route or backend was added with this architecture change.

## Project workflow
Read [../README.md](../README.md), [../AGENTS.md](../AGENTS.md), [../TASKS.md](../TASKS.md), and [../PROJECT_STATUS.md](../PROJECT_STATUS.md) before implementing new tasks. Record real commit, deployment, and test results in the status document. A Vercel READY status is not browser-level verification.
