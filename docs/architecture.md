# Operator Funding Site — architecture v1.2

## Canonical repository and deployment
- GitHub `JFeimster/operator-funding-site`, branch `main`.
- Vercel hosts static HTML/CSS/JavaScript with no framework or build step.
- Public URLs `/index.html` and `/{page}.html` remain unchanged. Vercel rewrites those secondary page URLs to physical files under `pages/`.
- The funding intake UI is **not** a working lead-delivery backend.

## Repository layout
```text
/
├── index.html
├── pages/
│   ├── get-funded.html
│   ├── options.html
│   ├── calculator.html
│   ├── process.html
│   ├── playbooks.html
│   ├── proof.html
│   ├── about.html
│   ├── privacy.html
│   └── terms.html
├── assets/
│   ├── css/styles.css
│   ├── js/app.js
│   ├── images/.gitkeep
│   └── icons/.gitkeep
├── api/
│   └── integrations.md
├── tests/
│   └── .gitkeep
├── docs/
│   ├── architecture.md
│   └── launch-checklist.md
├── vercel.json
├── AGENTS.md
├── TASKS.md
├── PROJECT_STATUS.md
├── README.md
└── .gitignore
```

## Routing rules
- Keep `index.html` at root.
- Keep secondary HTML sources under `pages/`.
- The `vercel.json` rewrite maps each existing public `/{name}.html` to `/pages/{name}.html` without changing the visitor-facing URL.
- All links between pages and to assets use **root-relative paths** such as `/get-funded.html` and `/assets/css/styles.css`, so both canonical URLs and direct `/pages/` accesses resolve references correctly.
- Do not replace the rewrites with permanent redirects unless a deliberate URL migration is authorized.
- A basic `python -m http.server` does **not** process Vercel rewrites; use a Vercel-compatible local preview to test canonical URLs. Python static preview can load `/pages/{name}.html` directly.

## Assets
- `assets/images/` and `assets/icons/` are intentionally empty except for `.gitkeep` so Git tracks the folders. Replace placeholders with real assets when approved.
- Existing CSS and JS contents were preserved. No new framework, npm dependency, or component system was introduced.

## Future backend boundary
- `api/integrations.md` contains planning guidance only; **no server handler** is implemented.
- A future authorized server-side endpoint may securely validate and transmit applications to the approved system. Success must mean the application was durably received.
- The current false-success submission state and sensitive browser draft remain unresolved and must not be treated as production-ready.

## Change control
Read the root README, AGENTS, TASKS and PROJECT_STATUS first. Document actual source changes, tests, deployment SHA, and outstanding blockers.
