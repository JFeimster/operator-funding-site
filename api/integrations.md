# Future integrations — Operator Funding Site

**Documentation only. There are no active API handlers or integrations in this directory.**

## Purpose
The `api/` directory is reserved for a future same-origin, server-side Vercel Function to receive and route funding requests. It is not an application backend today.

## Proposed intake flow (subject to separate approval)
1. The frontend at `/get-funded.html` sends an HTTPS POST to a validated server-side handler.
2. The handler checks the full input schema, consent state, abuse limits and idempotency key.
3. Server-only credentials write the application once to the **existing approved canonical destination**.
4. Only a confirmed durable receipt returns success; a failure must be displayed truthfully to the applicant.
5. Logs and analytics must not contain private applicant or financial data.

## Integration decisions outstanding
- Verified operating business and disclosures
- Authorized receiving system and record owner
- Approved form data contract and consent
- Rate limiting, retention, incident handling, and notification requirements
- QA plan with synthetic values and duplicate/failure tests

**Security:** Do not add secrets, real customer records, API tokens or live connection strings to this file or commit history. Refer to [../docs/architecture.md](../docs/architecture.md), [../TASKS.md](../TASKS.md) and [../PROJECT_STATUS.md](../PROJECT_STATUS.md).
