<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from the export script. Edit the config + re-run. -->

# Contributing

This repository is a resource hub for the modern Hotel API via [StayingAPI](https://stayingapi.com) — a curated README, language examples, endpoint references, and recipes. Pull requests are welcome.

## This is a generated repository

Most files here are **generated from the StayingAPI product source** and carry an HTML-comment `DO NOT EDIT` banner; they are regenerated on each release, so a direct edit to a generated file would be overwritten. The best way to contribute to generated content (README, endpoint references, the unified-schema examples) is to **open an issue** describing the fix or idea — we fold it into the source and it ships on the next regeneration. New, non-generated additions (extra language examples, new recipes) are very welcome as pull requests.

## What we accept

- **New language examples** — Rust, Java, Kotlin, Swift, C#, Elixir, etc., following the existing folder pattern under `examples/`.
- **New recipes** — short, practical walkthroughs backed by working code that calls the StayingAPI REST API or MCP server.
- **Documentation fixes** — typos, clearer prose, corrected field names or parameters when the API evolves.

## What we don't accept

- **A maintained SDK.** This repository is a resource hub, not a package — the official typed client is `@stayingapi/sdk`.
- **Scrapers.** Every example calls the StayingAPI REST API or MCP server. Code that scrapes booking sites directly will be closed without review.
- **Marketing copy** or **emojis** in committed files. Keep prose technical.

## Ground rules

- Every example must run end-to-end with a real `STAYINGAPI_KEY` env var against the live API or the deterministic `stay_test_` sandbox (which is free).
- Never commit credentials. The `STAYINGAPI_KEY` environment variable is the only auth surface.
- Match the unified schema and the machine contract at [openapi.json](https://api.stayingapi.com/openapi.json).
- Sign off your commits (`git commit -s`).

## License

By contributing you agree that your contributions are licensed under the [MIT](LICENSE) license.
