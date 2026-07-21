<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/cross-ota-price-comparison.ts. Edit the config + re-run. -->

# Multi-source price comparison → cheapest-rate report

Given a property (or a search) plus dates and occupancy, fetch prices across booking platforms and produce a cheapest-rate report — the trusted, ToS-clean replacement for the fragile "hotel price comparison via scraping" templates. It calls the flagship cross-OTA endpoint, sorts every offer, picks the cheapest, and computes the savings against the StayingAPI-computed median.

## How it works

1. **Provide the property and dates** — Give the workflow a property name (plus an optional location to disambiguate), check-in / check-out dates, occupancy and a currency.
2. **Call the flagship price-compare endpoint** — The workflow calls GET /v1/price-compare, which resolves one property and returns every OTA offer for the dates — plus StayingAPI-computed min and median aggregates.
3. **Pick the cheapest and compute savings** — It sorts the offers by total price, selects the cheapest, and computes the savings versus the median so you see both the best deal and how good it is.
4. **Deliver the cheapest-rate report** — A formatted report (cheapest OTA, price, savings, the full offer list and the credits charged) is posted to Slack — swap the last node for email, Telegram, Discord or a Google Sheet.

## Get it

- **AI-agent skill + n8n workflow:** [cross-ota-price-comparison in travel-workflows](https://github.com/stayingapi/travel-workflows) · rendered detail page: [https://stayingapi.com/workflows/cross-ota-price-comparison](https://stayingapi.com/workflows/cross-ota-price-comparison)
- **Endpoints used:** `price-compare`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing).

---

Back to the [hotel-api README](../README.md)
