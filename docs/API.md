# API reference

Base URL: `http://localhost:1880`

## POST `/api/feed`
Content type: `application/json`

Example:
```json
{"command":"FEED","quantity":50,"user":"owner","command_id":"demo-001"}
```
- `command` must be `FEED`.
- Quantity defaults to 50 if missing/falsy and must be > 0 and <= 100.
- `user` defaults to `owner`; the supplied function records it but does not authenticate it.
- `command_id` is generated if absent. A recent duplicate ID is blocked.

Successful payload contains `status`, `command`, `quantity`, `user`, `command_id`, `time`, `food_level`, `daily_total`, and `daily_limit`.

Blocked reasons include invalid command, invalid quantity, duplicate/replay command, daily feeding limit exceeded, and food container empty. The flow does not explicitly set a non-2xx HTTP status for blocked results, so check JSON `status`, not just `response.ok`.

## GET `/api/status`
Returns `online`, `food_level`, `daily_total`, `daily_limit`, `history`, and security flags. `online: true` is a software status, not proof of connected hardware. This handler does not itself check date rollover.
