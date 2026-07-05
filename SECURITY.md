<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from the export script. Edit the config + re-run. -->

# Security policy

## Reporting a vulnerability

Please email **hello@scoutingapi.com** with the subject line `SECURITY: hotel-api`. Do not open public GitHub issues for security reports. We acknowledge within 72 hours and aim to publish a fix or mitigation within 14 days for confirmed issues.

## Scope

This repository contains documentation and code examples for the [ScoutingAPI](https://scoutingapi.com) REST API and MCP server. It is a resource hub, not a runtime service.

- **Example code** — the language folders under `examples/`. Report any snippet that mishandles credentials, fails open on errors, or demonstrates an unsafe pattern.
- **Documentation accuracy** — endpoint references or recipes that recommend insecure practices (hardcoding keys, disabling TLS verification, ignoring error responses) are in scope.

For vulnerabilities in the **ScoutingAPI service itself** (auth, billing, data exposure), email **hello@scoutingapi.com** with the subject line `SECURITY: scoutingapi-service`.

## Credential handling in examples

Every example reads the API key from the `SCOUTINGAPI_KEY` environment variable, sends it only over HTTPS to `https://api.scoutingapi.com`, and never writes it to disk or logs. If you find an example that violates this, that is a vulnerability — please report it.

## Trademark

ScoutingAPI is an independent service and is not affiliated with, endorsed by, or sponsored by Airbnb, Booking.com, Vrbo, Google, or any other booking platform. All platform names are trademarks of their respective owners and are used here for identification only.
