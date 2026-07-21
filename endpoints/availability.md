<!-- generated: DO NOT EDIT BY HAND — produced by apps/web/scripts/export-github-repos.ts from app/docs/_data/endpoints.ts (the endpoint SSOT). Edit the config + re-run. -->

# Availability — `GET /v1/availability`

Day-by-day availability for a known listing over a date window.

Get day-by-day availability for a known listing (or a batch of listings) on one platform over a date window. Each day reports whether it is available, its minimum-night requirement, and whether check-in / check-out / booking is allowed.

## Example — cross-platform

```bash
curl -s "https://api.stayingapi.com/v1/v1/availability" \
  -G \
  -H "Authorization: Bearer $STAYINGAPI_KEY"
```

## Parameters

| Parameter | In | Type | Required | Notes |
|---|---|---|---|---|
| `platform` | query | enum | Yes | Single platform (not a fan-out endpoint). |
| `listingId` | query | string | One of | A single listing id on platform. |
| `listingIds[]` | query | string[] | One of | A batch of listing ids on platform. |
| `url` | query | string | One of | Full listing URL (alternative to an id). |
| `startDate` | query | date | Yes | YYYY-MM-DD; not in the past. |
| `endDate` | query | date | Yes | After startDate; window ≤ 365 days. |
| `onlyAvailable` | query | boolean | No | If true, only bookable dates are returned. |

## Response

```jsonc
{
  "data": [
    {
      "platform": "airbnb",
      "listingId": "42307961",
      "dates": [
        { "date": "2026-07-13", "available": true, "minNights": 7, "checkIn": true, "checkOut": false, "bookable": true },
        { "date": "2026-07-14", "available": true, "minNights": 7, "checkIn": false, "checkOut": false, "bookable": true }
      ]
    }
  ],
  "meta": {
    "requestId": "req_av…",
    "platforms": ["airbnb"],
    "cached": false, "partial": false,
    "creditsCharged": 5, "currency": "USD", "pagination": null,
    "platformResults": [
      { "platform": "airbnb", "status": "ok", "creditsCharged": 5, "cached": false, "count": 1 }
    ],
    "warnings": []
  }
}
```

> This endpoint is cross-platform — pass `booking` (this repo's focus) or any of `airbnb,booking,vrbo,google`; the response is the same unified schema.

## Credits

Billed only on success; failed/empty calls are free; sandbox calls cost 0. Current costs: [https://stayingapi.com/pricing](https://stayingapi.com/pricing) · full contract: [openapi.json](https://api.stayingapi.com/openapi.json).

---

Back to the [hotel-api README](../README.md) · [Docs](https://stayingapi.com/docs/endpoints/availability)
