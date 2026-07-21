<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from content/workflows/availability-alert.ts. Edit the config + re-run. -->

# Property availability watch → alert

Given a known listing (or a batch) and a date window, poll day-by-day availability on a schedule and alert the instant a wanted date becomes bookable. It calls GET /v1/availability with onlyAvailable=true, flattens the returned calendar, de-dups against the previous run so you are only pinged on a real change, and posts the newly-available dates. This is the automation twin of the App’s availability-alert saved search.

## How it works

1. **Pick the listing and the date window** — Set the platform, the listing id (or a full listing URL), and the start / end dates to watch (window ≤ 365 days, not in the past).
2. **Poll availability on a schedule** — Every few hours the workflow calls GET /v1/availability with onlyAvailable=true, returning the day-by-day calendar for the listing.
3. **Detect what newly became available** — A Code node flattens the calendar to the bookable dates and compares them to the previous run (stored in n8n static data), so you are alerted only when the available set changes — no duplicate pings.
4. **Send the availability alert** — When a wanted date opens up, a message listing the newly-available dates is posted to Slack — swap the last node for email, Telegram, a webhook or Discord.

## Get it

- **AI-agent skill + n8n workflow:** [availability-alert in travel-workflows](https://github.com/stayingapi/travel-workflows) · rendered detail page: [https://stayingapi.com/workflows/availability-alert](https://stayingapi.com/workflows/availability-alert)
- **Endpoints used:** `availability`, `listing`

Failed/empty calls are free; sandbox calls cost 0. Costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing).

---

Back to the [hotel-api README](../README.md)
