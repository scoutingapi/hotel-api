<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/platforms/hotel-api.ts. Edit the config + re-run. -->

# Hotel API — search, availability & price data in one schema (2026)

**[Get a free API key →](https://stayingapi.com/signup)** — free tier, no credit card.

Stop wiring up Amadeus, Hotelbeds, and a different gated portal per source. StayingAPI returns live hotel search, availability, and cross-OTA price in one schema — the very same one you use for Airbnb, Booking.com, Vrbo, and Google Hotels.

This repository is a resource hub for the modern **Hotel API**: REST endpoints, working code samples in six languages, and recipes you can copy in under five minutes. It is not a maintained SDK (the official typed client is [`@stayingapi/sdk`](https://stayingapi.com/docs/sdk)) — it is a curated set of examples and references that match the machine contract at [openapi.json](https://api.stayingapi.com/openapi.json). Every response is the same unified schema across Airbnb, Booking.com, Vrbo and Google Hotels, so one integration covers them all.

`99.9% uptime SLA` · `Failed calls cost 0 credits` · `Native MCP for AI agents` · `One unified schema`

---

## Quick start

Search live Hotel stays with one HTTPS call — a bearer token, no SDK, no partner approval.

```bash
curl -s "https://api.stayingapi.com/v1/search" \
  -G --data-urlencode "location=Split, HR" \
  --data-urlencode "platforms=booking" \
  --data-urlencode "limit=5" \
  -H "Authorization: Bearer $STAYINGAPI_KEY" \
  | jq '.data[] | {platform, name, price}'
```

You get back the unified `{ "data": [...], "meta": {...} }` envelope. [Sign up](https://stayingapi.com/signup) for a free key, set `STAYINGAPI_KEY`, and the request runs as-is. Prefer to try before signing up? A `stay_test_` sandbox key returns deterministic fixtures at **zero cost**.

---

## What you can pull

The Hotel data surface maps to these REST endpoints — each one HTTPS call, returning the unified schema, billed only on success:

- **Search** — `GET /v1/search` — Cross-platform property discovery, merged into one schema.
- **Price** — `GET /v1/price` — A real price quote for one listing, for your dates and occupancy.
- **Price compare** — `GET /v1/price-compare` — Cross-OTA price comparison for one property — the flagship endpoint.
- **Availability** — `GET /v1/availability` — Day-by-day availability for a known listing over a date window.
- **Listing** — `GET /v1/listing/{platform}/{id}` — Full listing detail — amenities, photos, host, and optional live price.
- **Reviews** — `GET /v1/reviews` — Normalized, paginated reviews for one listing.
- **Account** — `GET /v1/account` — Check your plan, credit balance and rate limit — programmatically.

Full machine contract: [openapi.json](https://api.stayingapi.com/openapi.json). Per-endpoint references: [`endpoints/`](endpoints/).

**Ready to try?** [Get a free StayingAPI key →](https://stayingapi.com/signup).

---

## What you can build

- **Cross-OTA rate shopping & meta-search** — Pull one hotel’s price across Google, Booking, and Expedia in a single call, with computed lowest and median — the engine behind a rate-shopping or meta-search app.
- **Hotelier competitive-rate monitoring** — Track a property’s nightly rate against its real competitive set — including nearby short-term rentals — in one normalized feed instead of three integrations.
- **Travel-planning agents** — Give your AI agent a dependable hotel tool: “4-star near Šibenik, July 13–20, 2 adults + 2 kids, pool and spa” → real, normalized results via the native MCP server.
- **Market-rate intelligence** — Benchmark hotel and STR rates across a market and date range; feed dashboards and pricing models with live data, not last quarter’s analytics.
- **Corporate travel & TMC sourcing** — Source compliant rates across sources for a trip request, and surface the cheapest bookable option — hotels and apartments together — to the traveler.
- **Price-drop monitoring & alerts** — Poll a property and date range; fire a Slack, email, or Telegram alert when a rate drops below a threshold — shippable from /workflows in minutes.

---

## Code examples by language

Six languages, each in its own folder under [`examples/`](examples/). Every snippet is one screen, uses the language's standard library or a single zero-friction dependency, and resolves to the same unified envelope.

- [curl](examples/curl/) · [Node.js](examples/node/) · [Python](examples/python/) · [Go](examples/go/) · [Ruby](examples/ruby/) · [PHP](examples/php/)

---

## Recipes

Ready-made automations built on Hotel data — importable n8n workflows and portable AI-agent skills. See [`recipes/`](recipes/) and the full [travel-workflows](https://github.com/stayingapi/travel-workflows) repo, or browse them rendered at [https://stayingapi.com/workflows](https://stayingapi.com/workflows).

---

## Pricing & credits

Every call bills against a credit balance. **Failed, empty and blocked calls are never billed**, and `stay_test_` sandbox calls are always free. The exact, current per-endpoint costs live on the [pricing page](https://stayingapi.com/pricing) and in the machine-readable [openapi.json](https://api.stayingapi.com/openapi.json) — this repo stays number-free so it never drifts.

---

## FAQ

### Does StayingAPI cover both hotels and short-term rentals?

Yes — that’s the point. Hotels (via Google Hotels and Booking.com) and short-term rentals (Airbnb, Vrbo) come back in one unified schema. A hotel and a holiday villa return the same object shape, so a single integration covers both halves of the accommodation map.

### How is this different from a Google Hotels SERP scraper like SerpApi or SearchApi?

SERP scrapers return a raw snapshot of the Google Hotels results page that you have to parse and normalize yourself. StayingAPI returns a normalized property with a guest rating on a stated scale, a canonical amenities list, and live price — plus a flagship /v1/price-compare that gives you each OTA’s rate with a computed lowest and median. You get structured data and an SLA, not a page to scrape.

### How is this different from Amadeus, Hotelbeds, or Expedia Rapid?

Those are powerful but partner-gated — application, contract, and often a sales call before your first request — and they cover hotels (and flights) only. StayingAPI is self-serve, returns hotels and short-term rentals in one schema, and adds cross-OTA price comparison with computed min/median that the official hotel APIs don’t provide.

### How do I get the cheapest rate for a hotel across OTAs?

Call the flagship /v1/price-compare endpoint with a hotel name (or Google hotel id) and your dates. You get back each OTA’s total price plus a computed lowest (min) and median rate, all in one schema — see the dedicated Google Hotel API page for a live example.

---

## Related repositories

Part of the StayingAPI open resource set — one unified accommodation-data API across Airbnb, Booking.com, Vrbo and Google Hotels, with a REST API, a native MCP server, and importable workflows.

- [airbnb-api](https://github.com/stayingapi/airbnb-api)
- [booking-com-api](https://github.com/stayingapi/booking-com-api)
- [vrbo-api](https://github.com/stayingapi/vrbo-api)
- [google-hotels-api](https://github.com/stayingapi/google-hotels-api)
- [travel-api](https://github.com/stayingapi/travel-api)
- [travel-skills](https://github.com/stayingapi/travel-skills)
- [hotel-mcp](https://github.com/stayingapi/hotel-mcp)
- [travel-workflows](https://github.com/stayingapi/travel-workflows)
- [airbnb-skills](https://github.com/stayingapi/airbnb-skills)
- [booking-com-skills](https://github.com/stayingapi/booking-com-skills)
- [vrbo-skills](https://github.com/stayingapi/vrbo-skills)
- [google-hotels-skills](https://github.com/stayingapi/google-hotels-skills)

- Website: <https://stayingapi.com> · Docs: <https://stayingapi.com/docs> · Status: <https://status.stayingapi.com>

---

**Get your free key — no card → <https://stayingapi.com/signup>** · [Docs](https://stayingapi.com/docs) · [Pricing](https://stayingapi.com/pricing) · [Status](https://status.stayingapi.com)

Built with [StayingAPI](https://stayingapi.com) — trusted, ToS-clean, real-time accommodation data across Airbnb, Booking.com, Vrbo and Google Hotels, normalized to one schema. REST + a native MCP server.

> StayingAPI is an independent service and is not affiliated with or endorsed by any booking platform. Platform names are trademarks of their respective owners.
