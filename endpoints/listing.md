<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from app/docs/_data/endpoints.ts (the endpoint SSOT). Edit the config + re-run. -->

# Listing — `GET /v1/listing/{platform}/{id}`

Full listing detail — amenities, photos, host, and optional live price.

Full normalized detail for one listing: amenities (canonical taxonomy), photos, host, geo, ratings, and — when you pass dates — an embedded live price. The detail body is cached 24 h; any embedded live price is cached at the 1 h price TTL and composed at read time, so a stale price never rides on fresh detail.

## Example — cross-platform

```bash
curl -s "https://api.scoutingapi.com/v1/v1/listing/booking/12345678" \
  -G \
  -H "Authorization: Bearer $SCOUTINGAPI_KEY"
```

## Parameters

| Parameter | In | Type | Required | Notes |
|---|---|---|---|---|
| `platform` | path | enum | Yes | vrbo | booking | airbnb | google. |
| `id` | path | string | Yes | Platform-native listing id (case-sensitive, verbatim from source). |
| `checkIn` | query | date | No | Pairs with checkOut; presence embeds a best-effort live price (may be null; the call still bills). |
| `checkOut` | query | date | No | Must be after checkIn. |
| `adults` | query | integer | No | ≥ 1 (only used with dates). |
| `children` | query | integer | No | ≥ 0. |
| `childAges[]` | query | integer[] | No | Length must equal children. |
| `currency` | query | string | No | ISO-4217. |

## Response

```jsonc
{
  "data": {
    "id": "stays_booking_abramovic2",
    "platform": "booking",
    "platformListingId": "abramovic2",
    "name": "Apartments Abramović",
    "propertyType": "apartment",
    "location": { "lat": 43.51, "lng": 16.44, "city": "Split", "country": "HR" },
    "guestRating": 9.1, "ratingScale": 10, "reviewCount": 142,
    "maxOccupancy": 4, "bedrooms": 2, "bathrooms": 1,
    "amenities": ["pool", "kitchen", "air_conditioning", "wifi"],
    "images": ["https://…"],
    "host": { "name": "Marko", "isSuperhost": false },
    "price": { "currency": "USD", "nightlyPrice": 303, "totalPrice": 2122, "nights": 7 }
  },
  "meta": {
    "requestId": "req_li…",
    "platforms": ["booking"],
    "cached": false, "partial": false,
    "creditsCharged": 3, "currency": "USD", "pagination": null,
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

Back to the [hotel-api README](../README.md) · [Docs](https://scoutingapi.com/docs/endpoints/listing)
