# Otya Ecosystem — Execution Program

**Status:** maintainer execution plan; not a claim that every integration is implemented or deployed.  
**Owner:** Otya Hold Ltd  
**Canonical product names:** Otya OS, Otya End, OtyaPoint, Otya Media, OtyaHub, Leo / Otya Next.

## Objective

Improve the existing ecosystem as one connected family, reusing repositories and services rather than creating disconnected projects. Prefer GitHub for source, review and CI; Cloudflare Workers/D1/R2/KV/Queues/Workflows for the shared runtime and data services; and Resend for transactional email where it fits. Do not introduce Supabase, Appwrite or Vercel into new OtyaPoint runtime paths without explicit owner approval. Legacy dependencies remain until their users, data, sessions and runtime paths have been migrated and verified.

This document is a coordinated work queue, not an implementation or deployment certificate. Each work item must be delivered through a focused branch/PR, validated with relevant tests, and released only after its explicit gate passes.

## Shared engineering rules

1. **Preserve before replacing.** Inventory the current source, data, migrations, users, workflows, domains, bindings and release paths before changing them. Keep a recovery point and a rollback procedure for data or runtime changes.
2. **One public identity.** Customer-facing OtyaPoint UI says OtyaPoint only. Otya Hold Ltd appears in legal/business contexts; infrastructure/provider names belong in maintainer documentation.
3. **One trusted identity boundary.** Otya Auth authenticates; each application/backend authorizes its own active tenant/company/branch membership on every request. Browser role claims and locally minted substitute JWTs are never authoritative.
4. **Server-side secrets.** No tokens, service credentials, database IDs or private endpoints in client bundles, URLs, browser-visible errors or logs. Authenticated business responses are not publicly cacheable.
5. **Honest capability states.** Empty data, unavailable services, blocked features and successful operations are distinct states. Never seed fake business data to make a dashboard look complete.
6. **Financial safety by default.** No real-money execution until provider approval, signed callback verification, idempotency/replay controls, timeout/reversal handling, balanced ledger checks, reconciliation and owner release approval are complete.
7. **Safe delivery.** CI/security controls are not weakened to make a check green. Keep changes in draft PRs while contracts, tests or environment assumptions remain unresolved. No unapproved merge, production deploy, DNS/secret/access-policy change, destructive migration or live transaction.

## Workstreams and acceptance gates

### 1. Otya End — shared backend and identity

- Confirm canonical Worker entrypoints, deployed service bindings, D1 schemas/migration histories, queues, KV, R2 and workflow consumers from source and Cloudflare configuration.
- Add contract tests for login, refresh rotation, logout revocation, expiry, throttling, missing bindings, malformed requests and safe error responses.
- Define and test the supported server-to-server identity contract; remove any reliance on unverified locally minted JWTs.
- Ensure per-request tenant and staff membership checks, bounded payloads, request IDs, rate limits and audit trails.
- Add migration/backup/restore drills with checksums and documented recovery steps.
- **Gate:** source tests pass; binding and deployment state verified separately; auth and authorization integration tests pass; no secrets exposed.

### 2. OtyaPoint — frontend, backend and shop operations

- Keep the dashboard behind same-origin server-side route handlers/BFF; validate API payloads at the boundary.
- Implement inventory, stock adjustments, cash retail sales, summary, ledger and read-only agency views against the authenticated Cloudflare API; distinguish zero records from API failure.
- Complete session BFF design only after the actual hosting runtime, public hostname, Auth binding and CSRF/Origin model are verified. Preserve the existing login until the replacement is tested end-to-end.
- Add tests for company/branch isolation, role denial, sale idempotency, stock/ledger invariants, API timeouts, empty states and mobile-responsive flows.
- Keep agency provider execution fail-closed. Separate retail checkout from cash-in/out, airtime, bills and float operations.
- **Gate:** CI green; runtime and bindings confirmed; seeded test fixtures are isolated; browser/mobile verification documented; no real-money endpoints enabled without explicit approval.

### 3. Otya Media — local-first player

- Prioritize reproducible crash-on-open diagnosis, lifecycle-safe initialization, playback regression coverage and device-level smoke tests.
- Preserve offline playback, local media access, audio/video features, vault security and sharing behavior while modernizing dependencies.
- Keep crash telemetry privacy-conscious and avoid collecting media filenames/content by default.
- Verify signed release artifacts and reproducible CI outputs before distribution.
- **Gate:** automated tests/build pass and actual supported Android device/emulator launch/playback is verified. CI success alone is not device verification.

### 4. OtyaHub — public developer and partner surface

- Publish only public-safe architecture, stable product names, integration contracts, API examples and support/security reporting guidance.
- Keep internal infrastructure inventories, account details, private operational instructions, credentials and customer data out of the public repository.
- Link to maintained canonical docs instead of copying private implementation details into public pages.
- **Gate:** links work, examples contain no secrets, and public claims match implemented capabilities.

### 5. Leo / Otya Next — ecosystem coordination and automation

- Treat Leo as the coordinator for issue triage, plans, cross-repository dependency mapping, evidence collection and draft PR preparation—not as an automatic production operator.
- Use explicit autonomy tiers: read-only discovery; reversible branch/PR edits; reviewed staging changes; owner-approved production/financial changes.
- Require idempotent jobs, bounded retries, observability, audit events, human escalation and spend limits for automated workflows.
- Keep AI-provider routing replaceable and do not send sensitive business or authentication data to an external model without a reviewed data policy.
- **Gate:** automation permissions are least-privilege, actions are traceable, and destructive/financial actions require explicit approval.

### 6. Cloudflare platform and reliability

- Maintain a single documented service map for Workers, D1, R2, KV, Queues, Workflows, AI and Analytics bindings.
- Verify actual deployment/routes/bindings independently from Wrangler configuration. A binding in source does not prove the live Worker is connected.
- Use separate development/staging/production resources and explicit environment targeting; do not point tests at production data.
- Add structured, redacted logs, request correlation, health checks, alerting, backup freshness checks and restore drills.
- Avoid deleting legacy databases or recovery snapshots until source-of-truth and retention decisions are documented.
- **Gate:** current resource map reconciles with live account configuration; restore drill succeeds; alerting and rollback are tested.

### 7. Resend — transactional messaging

- Centralize verified sender configuration and reusable templates for login verification, account recovery, receipts and operational alerts where approved.
- Keep secrets server-side; implement suppression/unsubscribe handling where applicable, rate limits, delivery-event verification and retry deduplication.
- Do not send real customer messages from test workflows or expose private account details in email subjects.
- **Gate:** sender/domain and webhook verification are confirmed; templates are reviewed; test delivery and failure handling pass.

### 8. Payments and external partners

- Keep provider adapters behind a replaceable interface, with separate credentials/configuration per environment.
- Treat Quickteller Business checkout and InterSwitch Marketplace Routing APIs as distinct products; do not infer one contract from another.
- Confirm provider documentation, regional endpoints, currency/amount units, signing keys, callback signatures and go-live approval before implementation.
- Test duplicate callbacks, reordered events, timeouts, reversals, partial failures and reconciliation against an immutable ledger.
- **Gate:** sandbox contract tests pass, security review is complete, and owner explicitly approves any live activation. Until then, transactions stay disabled.

## Delivery order

1. **P0 — safety and evidence:** reconcile CI failures; map source/runtime/deployment facts; confirm auth contracts; preserve backups and migration history.
2. **P1 — trustworthy foundation:** authentication/session BFF design and tests; authorization; common API schemas/errors; audit and idempotency tests.
3. **P2 — usable business flows:** inventory and cash retail flows; agency read-only readiness; mobile responsiveness; accessible empty/error states.
4. **P3 — ecosystem hardening:** Otya Media device regression coverage; shared observability and alerting; Resend templates/events; Leo bounded automation.
5. **P4 — controlled integrations:** provider sandbox adapters and reconciliation; only then a separately approved production-readiness review.

Dependencies can change after repository and live-resource evidence is gathered. Do not claim a workstream complete based only on documentation or source presence.

## Evidence record template

For each PR/release, record:
- repository, branch, commit and linked issue/PR;
- changed behavior and migration impact;
- commands/tests run and actual outcomes;
- security/authorization checks and any gaps;
- staging/runtime/binding evidence;
- rollback/recovery path;
- explicit approval required, if any;
- deployment status (never infer deployment from merge or CI).

## Current known OtyaPoint integration gaps

At the time this plan was written, OtyaPoint's Next.js sign-in still uses legacy Supabase Auth; its product bridge is deliberately fail-closed because the local-token-to-Otya-Auth contract is unverified; Cloudflare API deployment/custom routing is not confirmed; and recent verification/security workflows failed with root cause not yet established. These gaps must be investigated, not hidden by weakening checks or switching auth prematurely.

The OtyaPoint connection contract is maintained in its private repository at `docs/FRONTEND_BACKEND_CONNECTION_CONTRACT.md`. This public hub intentionally does not copy private infrastructure details.
