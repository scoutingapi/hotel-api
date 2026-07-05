<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from app/docs/_data/endpoints.ts (the endpoint SSOT). Edit the config + re-run. -->

# Price compare — `GET /v1/price-compare`

Cross-OTA price comparison for one property — the flagship endpoint.

Compare the price of one property across booking platforms in a single call, resolved through the Google Hotels backbone. The response carries the offers plus ScoutingAPI-computed min and median as first-class fields, so you can read the cheapest and typical cross-OTA price without re-deriving them. No cross-platform short-term-rental price-comparison API exists elsewhere — this is the wedge.

## Example — cross-platform

```bash
curl -s "https://api.scoutingapi.com/v1/v1/price-compare" \
  -G \
  --data-urlencode "location=Split, HR" \
  --data-urlencode "name=Hotel Park Split" \
  -H "Authorization: Bearer $SCOUTINGAPI_KEY"
```

## Parameters

| Parameter | In | Type | Required | Notes |
|---|---|---|---|---|
| `name` | query | string | One of | Property name to resolve. |
| `googleHotelId` | query | string | One of | Precise Google Hotels id. |
| `location` | query | string | One of | Disambiguating place / "lat,lng". |
| `checkIn` | query | date | Yes | YYYY-MM-DD; not in the past. |
| `checkOut` | query | date | Yes | Must be after checkIn. |
| `adults` | query | integer | No | ≥ 1. |
| `children` | query | integer | No | ≥ 0. |
| `childAges[]` | query | integer[] | No | Length must equal children. |
| `currency` | query | string | No | ISO-4217; pass-through + echo. |

## Response

```jsonc
{
  "data": {
    "property": "Hotel X, Sibenik",
    "checkIn": "2026-07-13",
    "checkOut": "2026-07-20",
    "currency": "EUR",
    "min": 2122,
    "median": 2151,
    "offers": [
      { "ota": "booking.com", "totalPrice": 2122, "currency": "EUR", "url": "https://…" },
      { "ota": "expedia", "totalPrice": 2180, "currency": "EUR", "url": "https://…" }
    ]
  },
  "meta": {
    "requestId": "req_pc…",
    "platforms": ["google"],
    "cached": false, "partial": false,
    "creditsCharged": 22, "currency": "EUR", "pagination": null,
    "platformResults": [
      { "platform": "google", "status": "ok", "creditsCharged": 22, "cached": false, "count": 1 }
    ],
    "warnings": []
  }
}
```


## Credits

Billed only on success; failed/empty calls are free; sandbox calls cost 0. Current costs: [https://scoutingapi.com/pricing](https://scoutingapi.com/pricing) · full contract: [openapi.json](https://api.scoutingapi.com/openapi.json).

---

Back to the [hotel-api README](../README.md) · [Docs](https://scoutingapi.com/docs/endpoints/price-compare)
