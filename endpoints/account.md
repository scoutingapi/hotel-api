<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from app/docs/_data/endpoints.ts (the endpoint SSOT). Edit the config + re-run. -->

# Account — `GET /v1/account`

Check your plan, credit balance and rate limit — programmatically.

Programmatic account introspection for the authenticated key: credit balance, plan (code / name / subscription status), key environment (live | sandbox) and the per-plan rate limit (requests per minute). Works for both live and sandbox keys, is read-only, synchronous and free — use it to check your balance from code instead of inferring it from meta.creditsCharged on each call.

## Example — cross-platform

```bash
curl -s "https://api.scoutingapi.com/v1/v1/account" \
  -G \
  -H "Authorization: Bearer $SCOUTINGAPI_KEY"
```

## Parameters

None — authenticate with your bearer key; the response describes the account that key belongs to.

## Response

```jsonc
{
  "data": {
    "plan": { "code": "free", "name": "Free / Sandbox", "status": "active" },
    "key": { "env": "sandbox" },
    "credits": { "balance": 300 },
    "rateLimit": { "requestsPerMinute": 30 }
  }
}
```


## Credits

Billed only on success; failed/empty calls are free; sandbox calls cost 0. Current costs: [https://scoutingapi.com/pricing](https://scoutingapi.com/pricing) · full contract: [openapi.json](https://api.scoutingapi.com/openapi.json).

---

Back to the [hotel-api README](../README.md) · [Docs](https://scoutingapi.com/docs/endpoints/account)
