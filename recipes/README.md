<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from the workflow SSOT (content/workflows). Edit the config + re-run. -->

# Recipes

Ready-made automations you can run on accommodation data — each ships as an importable n8n workflow and a portable AI-agent skill. Browse them all in the [travel-workflows](https://github.com/scoutingapi/travel-workflows) repo or rendered at [https://scoutingapi.com/workflows](https://scoutingapi.com/workflows).

- [Multi-source price comparison → cheapest-rate report](./cross-ota-price-comparison.md) — Compare one property across booking platforms and report the cheapest rate, with savings vs. the median.
- [Property availability watch → alert](./availability-alert.md) — Watch a listing over a date window and get alerted the moment a wanted date becomes available.
- [Price-drop watcher](./price-drop-watcher.md) — Watch a specific stay and get alerted the moment its total price falls to or below your threshold.
- [Cross-OTA rate-parity monitor → parity-exception digest](./rate-parity-monitor.md) — Watch how your own listing's rate shows across OTAs on a schedule and flag any platform underselling the market median.
- [STR market scan → Google Sheet dataset](./str-market-scan.md) — Scan a short-term-rental market — discover listings across platforms, price the top N for your dates, and append a normalized row-per-listing dataset to a Google Sheet.
- [New-inventory monitor → CRM lead feed](./new-inventory-lead-gen.md) — Re-run a saved search on a schedule, diff it against the last run, and sync only the newly-listed properties into a CRM or Sheet as leads.
