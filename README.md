# Omaze

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Omaze is a for-profit social-impact entertainment company that runs online prize draws to raise money for charity. Founded in 2012 in Culver City, California by Matthew Pohlson and Ryan Cummins, it lets people enter draws for houses, supercars, cash and once-in-a-lifetime experiences, with a share of every entry going to a partner nonprofit; the company reports raising more than $250 million for over 600 charities and creating 50+ millionaires. Its live consumer operations today are the United Kingdom (omaze.co.uk) and Germany (omaze.de), both built on Shopify, while omaze.com serves as the corporate and brand site. Omaze publishes no developer program, no OpenAPI and no SDKs, but both storefronts do expose a genuine machine-readable agent surface: a Universal Commerce Protocol (UCP) merchant profile at /.well-known/ucp, a UCP Shopping MCP endpoint at /api/ucp/mcp, published agent instructions at /llms.txt and /agents.md, anonymous read-only storefront product JSON, and a standards-compliant OpenID Connect authorization server for customer accounts.

**Areas:** Company · Charity · Fundraising · Non-Profit · Prize Draws · Sweepstakes · E-Commerce · Agentic Commerce · Universal Commerce Protocol · MCP · Shopify · United Kingdom

## Omaze on APIs.io

Everything profiled for Omaze is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/omaze/](https://apis.io/providers/omaze/)** — or go straight to one of the APIs or properties below.

### APIs (3)

- [Omaze UK UCP Shopping MCP](https://apis.io/apis/omaze/omaze-uk-ucp-shopping-mcp/) — The Universal Commerce Protocol Shopping service that Omaze UK exposes over the Model Context Protocol, advertised by Omaze in its own /agents.md and…
- [Omaze Germany UCP Shopping MCP](https://apis.io/apis/omaze/omaze-de-ucp-shopping-mcp/) — The German-market counterpart of the Omaze UCP Shopping service, exposed over MCP at omaze.de/api/ucp/mcp and described by the merchant profile at…
- [Omaze UK Storefront JSON](https://apis.io/apis/omaze/omaze-uk-storefront-json/) — The anonymous, read-only JSON surface of the Omaze UK storefront, documented by Omaze itself in /agents.md for agents that only need to read store data…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [omaze-mcp.yml](https://apis.io/servers/omaze/omaze-mcp-yml/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Omaze Authentication](https://apis.io/security/omaze/omaze-authentication/)
- [Omaze Domain Security](https://apis.io/security/omaze/omaze-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Omaze Scopes](https://apis.io/scopes/omaze/omaze-scopes/)

#### Rate limits (1)

Published request limits.

- [Omaze Rate Limits](https://apis.io/rate-limits/omaze/omaze-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.omaze.com)
- [Documentation](https://omaze.co.uk/agents.md)
- [Getting started](https://omaze.co.uk/llms.txt)
- [Sign up](https://omaze.co.uk/account/register)
- [Support](https://omaze.co.uk/pages/contact-us)
- [Blog](https://omaze.co.uk/blogs/news)
- [Terms of service](https://omaze.co.uk/pages/legal-terms)
- [Privacy policy](https://omaze.co.uk/policies/privacy-policy)
- [GitHub](https://github.com/Omaze)

## API Evangelist rating

**Kin Score 30.6** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 0.0 |
| Contract governance | 18.2 |
| Operational transparency | 2.6 |
| Developer ergonomics | 51.8 |
| Access clarity | 34.2 |

**Agent readiness 23.7** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | platform (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | platform (partial credit) |

**Regulatory alignment 34.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/omaze/](https://apis.io/providers/omaze/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Omaze: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/omaze/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
