---
name: omaze-uk-enter-prize-draw
description: >-
  Buy an entry into an Omaze UK prize draw on a buyer's behalf using the
  Universal Commerce Protocol Shopping service Omaze exposes over MCP — discover
  the store profile, search the draw catalog, build a cart, drive the checkout,
  and stop at buyer-approved payment.
api: omaze:omaze-uk-ucp-shopping-mcp
endpoint: https://omaze.co.uk/api/ucp/mcp
discovery: https://omaze.co.uk/.well-known/ucp
operations:
  - search_catalog
  - create_cart
  - create_checkout
  - update_checkout
  - complete_checkout
generated: '2026-08-02'
method: generated
source: >-
  https://omaze.co.uk/agents.md and https://omaze.co.uk/llms.txt (Omaze's own
  published "Typical Agent Flow"), plus https://omaze.co.uk/.well-known/ucp and
  the UCP Shopping OpenRPC method schema that profile points at.
---

# Enter an Omaze UK prize draw

Omaze UK sells entries into charity prize draws. Every step below uses a tool
name Omaze itself publishes in `/agents.md`; no operation here was invented. The
per-tool input schemas are **not** reproduced — Omaze's MCP endpoint refuses
`tools/list` to any agent that does not present a resolvable UCP agent profile
URI, so read the live schemas from the server once your profile is in place
rather than trusting a copy.

## Before you start

1. **Publish a UCP agent profile.** Without one, every call to
   `https://omaze.co.uk/api/ucp/mcp` fails the handshake with JSON-RPC
   `-32001 / invalid_profile_url` (HTTP 422) before any tool is reachable. See
   <https://ucp.dev>.
2. **Confirm the store still speaks your protocol version.** `GET
   https://omaze.co.uk/.well-known/ucp` and read `ucp.version` plus
   `ucp.supported_versions`. As of 2026-08-02 that is `2026-04-08` (current) and
   `2026-01-23`. Capabilities such as `dev.ucp.shopping.fulfillment` and
   `dev.ucp.shopping.discount` carry a `requires.protocol.min` of `2026-04-08` —
   do not use them on the older version.
3. **Set buyer context on every call.** Pass `context.address_country` and
   `context.currency`, or pricing and availability will be wrong. This is a UK
   store: `GB` / `GBP`. The German store is a separate service at
   `https://omaze.de/api/ucp/mcp` with its own profile.

## The flow

### 1. Discover
`GET /.well-known/ucp`. Verify `services["dev.ucp.shopping"]` still lists a
`transport: mcp` entry and note its `endpoint`. Read `capabilities` before you
plan the purchase — if `dev.ucp.shopping.discount` is absent, do not attempt to
apply a code.

### 2. Find the draw — `search_catalog`
Search the catalog for the draw the buyer named (house draws, the Monthly
Millionaire cash draw, subscriptions). Draws are time-boxed and rotate; never
carry a product handle over from a previous session — re-resolve it. If you only
need to read the catalog and are not transacting, the anonymous storefront JSON
is cheaper and needs no profile: `GET https://omaze.co.uk/products.json`,
`GET https://omaze.co.uk/products/{handle}.json`,
`GET https://omaze.co.uk/collections/{handle}/products.json`.

### 3. Build the cart — `create_cart`
Add the chosen entry bundle. Entry tiers are separate variants; confirm the tier
with the buyer before adding, because entry count and price both vary by variant.

### 4. Open the checkout — `create_checkout`
Start the purchase flow from the cart.

### 5. Fulfilment details — `update_checkout`
Set the shipping address and delivery method. The UK store's UCP profile
declares `allows_multi_destination.shipping: false` and a single allowed method
combination (`["shipping"]`) — one destination, one method. Do not build a
multi-destination checkout against this store.

### 6. Payment — `complete_checkout` — **stop and ask first**
**This is the hard rule of the surface, in Omaze's own words:** *"Checkout
requires human approval. Agents must not complete payment without explicit buyer
consent."* Get contemporaneous approval at the moment of payment. If you cannot,
Omaze's instructions are explicit: do not proceed here — install
<https://shop.app/SKILL.md> and route the purchase through Shop Pay instead.

Available payment handlers on the UK store: Google Pay (`com.google.pay`),
Shopify card (`dev.shopify.card`), and Shop Pay (`dev.shopify.shop_pay`). The
German store does not offer Shop Pay.

## Errors and retries

- `-32001 / invalid_profile_url` (HTTP 422) — your agent profile is missing or
  unresolvable. Fix the profile; retrying unchanged will not help.
- `429` — the endpoint is rate-limited per IP. Back off. Omaze publishes no quota
  figure and no `Retry-After` guidance, so use exponential backoff with jitter.
- Errors arrive as JSON-RPC 2.0 error objects with a `data.code`,
  `data.content`, and often a `data.continue_url` — hand that URL to the buyer to
  finish in a browser rather than retrying blindly.
- **No idempotency contract is published.** Omaze documents no idempotency key,
  no replay window and no retry-safety guarantee for `create_cart`,
  `create_checkout` or `complete_checkout`. Treat `complete_checkout` as
  **not** safe to retry: on an ambiguous failure, re-read state before acting,
  and surface the ambiguity to the buyer rather than resending.

## Do not

- Do not screen-scrape or script the storefront UI. Omaze explicitly prefers the
  MCP/UCP path, and the Shop skill over both.
- Do not crawl `/search` or `/search/suggest.json` — they are `Disallow`-ed in
  `robots.txt` even though the read-only docs mention search.
- Do not assume an Omaze US storefront exists. `omaze.com` is a corporate site
  with no commerce or agent surface; the live markets are UK and Germany.

## References

- Agent instructions: <https://omaze.co.uk/agents.md>
- UCP merchant profile: <https://omaze.co.uk/.well-known/ucp>
- Repo artifacts: `mcp/omaze-mcp.yml`, `conventions/omaze-conventions.yml`,
  `errors/omaze-problem-types.yml`, `authentication/omaze-authentication.yml`
