<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/rate-parity-monitor.ts. Edit the config + re-run. -->

# Cross-OTA rate-parity monitor → parity-exception digest

Rate parity erodes quietly: one OTA quietly undersells the rate you want your property to hold, and you only find out when direct bookings dry up. This monitor calls the flagship price-compare endpoint for your property on a schedule, ranks every OTA offer, measures each against the StayingAPI-computed median, and posts a parity-exception digest — which platforms are below the median, by how much, and the total spread — so a revenue manager can act on a paper trail instead of a hunch.

## How it works

1. **Point it at your property + a target stay** — Give the workflow your property name (plus an optional location to disambiguate), the check-in / check-out dates and occupancy to monitor, and a currency.
2. **Pull every OTA rate for the property** — On each scheduled run it calls GET /v1/price-compare, which resolves the one property and returns every OTA offer for those dates plus StayingAPI-computed min and median aggregates.
3. **Flag the parity exceptions** — The transform ranks the offers, measures each against the median, and flags any OTA sitting below it — the platforms undercutting the rate you want to hold — and computes the overall spread.
4. **Deliver the parity digest** — A digest (median, spread, each OTA with its delta vs. median, and the flagged exceptions) is posted to Slack — swap the last node for email or a Google Sheet to keep a running parity log.

## Get it

- **AI-agent skill + n8n workflow:** [rate-parity-monitor in travel-workflows](https://github.com/stayingapi/travel-workflows) · rendered detail page: [https://stayingapi.com/workflows/rate-parity-monitor](https://stayingapi.com/workflows/rate-parity-monitor)
- **Endpoints used:** `price-compare`, `listing`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing).

---

Back to the [hotel-api README](../README.md)
