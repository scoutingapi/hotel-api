<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/new-inventory-lead-gen.ts. Edit the config + re-run. -->

# New-inventory monitor → CRM lead feed

Fresh inventory is a lead: a new short-term rental appearing in your target market is a management pitch, an acquisition target, or a comp to underwrite. This workflow re-runs your saved search on a schedule, keeps a memory of everything it has already seen, and emits only the listings that are new since the last run — one row per lead, with platform, name, URL, beds, rating and price — straight into your CRM or a Google Sheet. The first run quietly seeds the baseline so you are never flooded with the whole market.

## How it works

1. **Define the market to watch** — Give the workflow a location (and optional dates, platforms and result limit) — the same inputs you would use for a one-off search, saved as a recurring watch.
2. **Re-run the search on a schedule** — On each scheduled run it calls GET /v1/search across the requested platforms and merges every match into one normalized Property list.
3. **Diff against the last run** — The transform compares the result ids against the ids it saw last time (kept in n8n workflow static data) and keeps only the listings that are new — the first run seeds the baseline silently.
4. **Sync new leads to your CRM or Sheet** — Each new listing is emitted as its own row (platform, name, URL, beds, rating, price) and appended to a Google Sheet or pushed to your CRM — swap the delivery node for Slack to get a new-inventory ping instead.

## Get it

- **AI-agent skill + n8n workflow:** [new-inventory-lead-gen in travel-workflows](https://github.com/stayingapi/travel-workflows) · rendered detail page: [https://stayingapi.com/workflows/new-inventory-lead-gen](https://stayingapi.com/workflows/new-inventory-lead-gen)
- **Endpoints used:** `search`, `availability`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing).

---

Back to the [hotel-api README](../README.md)
