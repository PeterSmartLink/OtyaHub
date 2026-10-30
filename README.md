# OtyaHub

**OtyaHub** is the public developer and partner entry point for **Otya OS**, the connected ecosystem operated by **Otya Hold Ltd**. It publishes public documentation, safe examples, product guidance and integration information. It is not an administrative console or a source of private operational data. The canonical public product website remains https://petersmartlink.com; this repository should complement it, not duplicate the marketing site.

## Public surfaces

- Product: https://petersmartlink.com
- Help and documentation: https://docs.petersmartlink.com
- Service status: https://status.petersmartlink.com
- Account and product space: https://space.petersmartlink.com
- Privacy: https://petersmartlink.com/privacy
- Terms: https://petersmartlink.com/terms
- Download: https://petersmartlink.com/download/otya-player
- News: [Otya News](news/)

## Latest update

- [Otya 1.0 confirms its local-first Music scope — 2 September 2026](news/2026-09-02-local-first-music-scope.md)

## Operating documents

- [Beta scope and acceptance](BETA.md)
- [AI operating model](AI_OPERATING_MODEL.md)
- [User-side Next](USER_SIDE_NEXT.md)
- [AI provider strategy](AI_PROVIDER_STRATEGY.md)
- [Public automation policy](PUBLIC_AUTOMATION.md)
- [Developer and communication channels](DEVELOPER_CHANNELS.md)
- [Public Postman collection](postman/Otya-public.postman_collection.json)
- [Security and vulnerability reporting](SECURITY.md)

## What belongs here

This repository may contain:

- public product and developer-facing documentation;
- public release and service-health checks;
- safe API examples that contain no credentials or private user data;
- links to official Otya support, security and community surfaces;
- public GitHub Actions that operate only on information safe to expose.

## What does not belong here

Do not commit or print:

- production credentials, API keys, signing material, tokens or service-account files;
- private source code copied here only to obtain public-runner minutes;
- internal infrastructure inventories, private endpoints or administrative procedures;
- user data, crash payloads, private logs or account-recovery material.

If Otya's application or server repositories become private later, this repository can remain public as the stable product/developer hub. Public workflows must continue to operate only on public inputs unless a separately reviewed security design explicitly permits otherwise.

## Product naming

- **Otya Hold Ltd** — legal company/operator
- **Otya OS** — connected ecosystem and unified operating model
- **Otya Server** — shared control plane, identity/API governance and central integrations
- **Otya Next (Leo)** — private owner assistant; owner-only access
- **OtyaPoint** — shop and agency application for Otya Hold Ltd; legal/trading wording remains **Otya Hold Ltd T/A OmniPoint** until formally changed
- **Otya Media** — offline-first media player (existing repository/app identifiers may remain during a controlled rename)
- **OtyaHub** — public developer/partner hub

Legacy all-caps `OTYA` identifiers may remain in compatibility-sensitive code or historical records, but public product copy should use **Otya**.

## Release status

Otya v1 is still under acceptance. A successful CI build is not the same as a released or physically device-tested build.

## Security

Please use the [Otya Security Policy](SECURITY.md) to report vulnerabilities privately. Do not publish secrets, tokens, exploit details or user data in a public issue.
