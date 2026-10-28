# Otya Family Brand Guidelines

**Brand owner:** Otya Hold Ltd  
**Umbrella line:** One connected Otya family

## Canonical names

- **Otya Hold Ltd** — parent legal entity and operator.
- **Otya OS** — unified ecosystem and platform.
- **Otya Server** — shared backend and integration layer.
- **Otya Auth** — shared identity service.
- **Otya Core** — shared core platform services.
- **Otya Next** — owner-intelligence assistant.
- **Otya Media** — local-first media player.
- **OmniPoint** — the owner's shop and retail/financial-agency operations product, operated as **Otya Hold Ltd T/A OmniPoint**.
- **OtyaHub** — public developer and partner hub.

Use these spellings in customer-facing copy. Historical all-caps names and old technical identifiers may remain where changing them would break compatibility, but should not be presented as the current public brand.

## Visual system

Canonical SVG source assets live in `assets/branding/`:

- `otya-mark.svg` — compact symbol.
- `otya-wordmark.svg` — wordmark and symbol.

| Token | Hex | Intended use |
|---|---|---|
| Otya Ink | `#102A43` | Primary text and strong backgrounds |
| Otya Teal | `#18A999` | Main brand accent |
| Otya Gold | `#F4B942` | Small highlights |
| Otya Paper | `#F7FAFC` | Light surfaces |
| White | `#FFFFFF` | Contrast surfaces and reverse logo |

Use teal and ink as the primary pairing; gold is a small accent. Maintain readable contrast, visible keyboard focus, and touch-friendly controls. Prefer a system sans-serif stack over paid fonts. Do not stretch, recolour, or add effects to the mark without updating this guide.

## Product experience

- Keep each product's name and purpose distinct while signalling that it belongs to Otya OS when useful.
- Use plain, friendly, professional language and sentence case.
- Do not describe a capability as live, verified, secure, backed up or production-ready without evidence.
- Use the legal form **Otya Hold Ltd T/A OmniPoint** for the trading business. OmniPoint is not represented here as a separate legal company.
- Shared branding does not imply shared databases, permissions or trust boundaries.

## Technical migration rules

- Update visible copy, titles, app metadata and documentation before renaming packages, repositories, routes, domains, Worker names or database identifiers.
- Preserve package IDs, deep links, API contracts, OAuth callbacks, data, users and existing integrations until compatibility and migration impacts are reviewed.
- Keep secrets out of source control; use protected secret stores.
- Prefer free, permissively licensed dependencies where useful, retaining all required license notices.
- Use branches, tests and pull requests. Do not merge, deploy, change DNS, delete resources or activate live payments without the required review and explicit approval.
