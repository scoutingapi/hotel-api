<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from app/docs/_data/endpoints.ts (the endpoint SSOT). Edit the config + re-run. -->

# Reviews — `GET /v1/reviews`

Normalized, paginated reviews for one listing.

Normalized, paginated reviews for one listing on one platform. Native rating scales are preserved and echoed alongside each rating (TripAdvisor/Airbnb/Vrbo use 5; Booking.com/Expedia/Hotels.com use 10) — never silently rescaled.

## Example — cross-platform

```bash
curl -s "https://api.scoutingapi.com/v1/v1/reviews" \
  -G \
  -H "Authorization: Bearer $SCOUTINGAPI_KEY"
```

## Parameters

| Parameter | In | Type | Required | Notes |
|---|---|---|---|---|
| `platform` | query | enum | Yes | Platform enum. |
| `listingId` | query | string | One of | Listing id on platform. |
| `url` | query | string | One of | Full listing URL. |
| `limit` | query | integer | No | 1–100. |
| `cursor` | query | string | No | Opaque base64 cursor. |
| `language` | query | string | No | ISO-639-1 filter. |
| `minRating` | query | number | No | On the response ratingScale. |
| `sort` | query | enum | No | recent | rating_desc | rating_asc. |

## Response

```jsonc
{
  "data": [
    {
      "platform": "booking",
      "listingId": "abramovic2",
      "reviewId": "r987",
      "rating": 9, "ratingScale": 10,
      "title": "Perfect family stay",
      "text": "Spotless apartment a short walk from the old town…",
      "author": "Jane D.", "date": "2026-05-10", "tripType": "family",
      "language": "en", "ownerResponse": "Thank you!",
      "liked": "Location and cleanliness", "disliked": null
    }
  ],
  "meta": {
    "requestId": "req_rv…",
    "platforms": ["booking"],
    "cached": false, "partial": false,
    "creditsCharged": 20, "currency": "USD",
    "pagination": { "limit": 20, "cursor": null, "nextCursor": "eyJ…", "hasMore": true },
    "platformResults": [
      { "platform": "booking", "status": "ok", "creditsCharged": 20, "cached": false, "count": 20 }
    ],
    "warnings": []
  }
}
```

> This endpoint is cross-platform — pass `booking` (this repo's focus) or any of `airbnb,booking,vrbo,google`; the response is the same unified schema.

## Credits

Billed only on success; failed/empty calls are free; sandbox calls cost 0. Current costs: [https://scoutingapi.com/pricing](https://scoutingapi.com/pricing) · full contract: [openapi.json](https://api.scoutingapi.com/openapi.json).

---

Back to the [hotel-api README](../README.md) · [Docs](https://scoutingapi.com/docs/endpoints/reviews)
