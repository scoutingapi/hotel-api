<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from app/docs/_data/endpoints.ts (the endpoint SSOT). Edit the config + re-run. -->

# Price — `GET /v1/price`

A real price quote for one listing, for your dates and occupancy.

Quote one listing for specific dates and occupancy. Pass the platform-native platformListingId returned by /v1/search — numeric on Airbnb and Vrbo, a slug string on Booking.com and Google (e.g. "abramovic2") — or a full listing URL. The response is always a real numeric price or a typed error — never a wrong property's price.

## Example — cross-platform

```bash
curl -s "https://api.scoutingapi.com/v1/v1/price" \
  -G \
  -H "Authorization: Bearer $SCOUTINGAPI_KEY"
```

## Parameters

| Parameter | In | Type | Required | Notes |
|---|---|---|---|---|
| `platform` | query | enum | Yes | vrbo | booking | airbnb | google. |
| `listingId` | query | string | Yes | Platform-native id from /v1/search platformListingId — numeric (Airbnb/Vrbo) or a slug string (Booking.com/Google). Or pass a url. |
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
    "platform": "booking",
    "listingId": "abramovic2",
    "currency": "EUR",
    "nightlyPrice": 303,
    "totalPrice": 2122,
    "fees": { "cleaning": null, "service": null, "taxes": null },
    "nights": 7,
    "occupancy": { "adults": 2, "children": 2, "childAges": [8, 13] },
    "source": "booking",
    "url": "https://www.booking.com/hotel/hr/abramovic2.html"
  },
  "meta": {
    "requestId": "req_pr…",
    "platforms": ["booking"],
    "cached": false, "partial": false,
    "creditsCharged": 3, "currency": "EUR", "pagination": null,
    "platformResults": [
      { "platform": "booking", "status": "ok", "creditsCharged": 3, "cached": false, "count": 1 }
    ],
    "warnings": []
  }
}
```

> This endpoint is cross-platform — pass `booking` (this repo's focus) or any of `airbnb,booking,vrbo,google`; the response is the same unified schema.

## Credits

Billed only on success; failed/empty calls are free; sandbox calls cost 0. Current costs: [https://scoutingapi.com/pricing](https://scoutingapi.com/pricing) · full contract: [openapi.json](https://api.scoutingapi.com/openapi.json).

---

Back to the [hotel-api README](../README.md) · [Docs](https://scoutingapi.com/docs/endpoints/price)
