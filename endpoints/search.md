<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from app/docs/_data/endpoints.ts (the endpoint SSOT). Edit the config + re-run. -->

# Search — `GET /v1/search`

Cross-platform property discovery, merged into one schema.

Discover properties matching a location, dates, occupancy and filters across one or more platforms. Results from every requested platform are normalized to the same Property shape and merged into a single, cursor-paginated list. This is the breadth / funnel endpoint — and the clearest demonstration of "one schema, every platform".

## Example — cross-platform

```bash
curl -s "https://api.stayingapi.com/v1/v1/search" \
  -G \
  --data-urlencode "location=Split, HR" \
  -H "Authorization: Bearer $STAYINGAPI_KEY"
```

## Parameters

| Parameter | In | Type | Required | Notes |
|---|---|---|---|---|
| `location` | query | string | Yes | Place name ("Split, HR") or "lat,lng". Required. |
| `checkIn` | query | date | No | YYYY-MM-DD; required if checkOut given; not in the past. |
| `checkOut` | query | date | No | YYYY-MM-DD; required if checkIn given; must be after checkIn. |
| `adults` | query | integer | No | ≥ 1. |
| `children` | query | integer | No | ≥ 0. |
| `childAges[]` | query | integer[] | No | Length must equal children. Coarsened for Vrbo/Airbnb. |
| `rooms` | query | integer | No | ≥ 1. Meaningful for hotel platforms. |
| `propertyType[]` | query | enum[] | No | hotel | apartment | house | villa | cottage | other. |
| `amenities[]` | query | enum[] | No | Canonical amenity taxonomy. Airbnb amenity/pool is post-filtered. |
| `minBedrooms` | query | integer | No | ≥ 0. |
| `priceMin` | query | number | No | ≥ 0, in currency. |
| `priceMax` | query | number | No | ≥ priceMin. |
| `minGuestRating` | query | number | No | Normalized to the response ratingScale. |
| `platforms[]` | query | enum[] | No | Drives fan-out + per-platform billing. |
| `limit` | query | integer | No | 1–40. |
| `cursor` | query | string | No | Opaque base64 cursor from a previous page. |
| `sort` | query | enum | No | recommended | price_asc | price_desc | rating_desc. |
| `currency` | query | string | No | ISO-4217; pass-through + echo. |

## Response

```jsonc
{
  "data": [
    {
      "id": "stays_booking_abramovic2",
      "platform": "booking",
      "platformListingId": "abramovic2",
      "url": "https://www.booking.com/hotel/hr/abramovic2.html",
      "name": "Apartments Abramović",
      "propertyType": "apartment",
      "location": { "lat": 43.51, "lng": 16.44, "city": "Split", "country": "HR" },
      "starRating": null,
      "guestRating": 9.1, "ratingScale": 10, "reviewCount": 142,
      "maxOccupancy": 4, "bedrooms": 2, "bathrooms": 1,
      "amenities": ["pool", "kitchen", "air_conditioning", "wifi"],
      "host": { "name": "Marko", "isSuperhost": false },
      "price": { "currency": "USD", "nightlyPrice": 303, "totalPrice": 2122, "nights": 7 }
    }
    // … more Property objects
  ],
  "meta": {
    "requestId": "req_8sf…",
    "platforms": ["airbnb", "booking"],
    "cached": false, "partial": false,
    "creditsCharged": 56, "currency": "USD",
    "pagination": { "limit": 20, "cursor": null, "nextCursor": "eyJ…", "hasMore": true },
    "platformResults": [
      { "platform": "airbnb", "status": "ok", "creditsCharged": 36, "cached": false, "count": 18 },
      { "platform": "booking", "status": "ok", "creditsCharged": 20, "cached": true, "count": 20 }
    ],
    "warnings": []
  }
}
```


## Credits

Billed only on success; failed/empty calls are free; sandbox calls cost 0. Current costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing) · full contract: [openapi.json](https://api.stayingapi.com/openapi.json).

---

Back to the [hotel-api README](../README.md) · [Docs](https://stayingapi.com/docs/endpoints/search)
