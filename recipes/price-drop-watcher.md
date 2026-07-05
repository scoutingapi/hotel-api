<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/price-drop-watcher.ts. Edit the config + re-run. -->

# Price-drop watcher

Track a known listing for specific dates on a schedule and alert when its total price falls to or below a threshold you set. It calls GET /v1/price, compares the returned totalPrice to your priceBelow threshold, and — tracking the last-alerted price in static data — fires only on a NEW drop (first time below, or a further drop since the last alert) with the new price and a booking link. This is the automation twin of the App’s price-drop saved search.

## How it works

1. **Pick the stay and set a threshold** — Set the platform, listing id, check-in / check-out dates and occupancy, plus the total-price threshold you want to be alerted below.
2. **Re-price on a schedule** — Every few hours the workflow calls GET /v1/price for the listing and dates, returning a real numeric total for that stay.
3. **Compare to the threshold and de-dup** — A Code node checks the total against your threshold and against the last-alerted price (stored in n8n static data), so it fires only on a genuinely new drop — never twice for the same price.
4. **Send the price-drop alert** — When the price drops, a message with the new total, the threshold, the per-night rate and a booking link is posted to Slack — swap for email, Telegram or Discord.

## Get it

- **AI-agent skill + n8n workflow:** [price-drop-watcher in travel-workflows](https://github.com/scoutingapi/travel-workflows) · rendered detail page: [https://scoutingapi.com/workflows/price-drop-watcher](https://scoutingapi.com/workflows/price-drop-watcher)
- **Endpoints used:** `price`, `price-compare`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://scoutingapi.com/pricing](https://scoutingapi.com/pricing).

---

Back to the [hotel-api README](../README.md)
