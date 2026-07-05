<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/str-market-scan.ts. Edit the config + re-run. -->

# STR market scan → Google Sheet dataset

Underwriting a short-term-rental market means one repeatable dataset: what is listed, on which platform, at what price, with how many beds and what rating. This workflow fans a search across platforms to discover listings in your area and dates, keeps the top N, re-prices each precisely with the dedicated price endpoint, and appends a normalized row per listing — name, platform, beds, occupancy, rating (on its native scale), nightly and total price, and URL — to a Google Sheet or CSV. Re-run it on a cadence to build a time series for comps and occupancy signals.

## How it works

1. **Define the market + dates** — Give the workflow a location, the check-in / check-out dates, occupancy, which platforms to scan, how many results to discover per platform, and how many of them to price precisely.
2. **Discover listings across platforms** — It calls GET /v1/search across the requested platforms and merges every match into one normalized Property list — the discovery pass.
3. **Price the top N precisely** — It ranks the discovered listings, keeps the top N, and calls GET /v1/price for each with the exact dates and occupancy — a precise per-date quote per listing.
4. **Append the market dataset** — Each listing becomes one normalized row (name, platform, beds, occupancy, rating + scale, nightly + total price, URL) appended to a Google Sheet or CSV — re-run on a cadence for a time series.

## Get it

- **AI-agent skill + n8n workflow:** [str-market-scan in travel-workflows](https://github.com/scoutingapi/travel-workflows) · rendered detail page: [https://scoutingapi.com/workflows/str-market-scan](https://scoutingapi.com/workflows/str-market-scan)
- **Endpoints used:** `search`, `price`, `listing`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://scoutingapi.com/pricing](https://scoutingapi.com/pricing).

---

Back to the [hotel-api README](../README.md)
