# Test plan

| Test | Expected result |
|---|---|
| `GET /api/status` | JSON status |
| Valid feed request | `SUCCESS` if safety rules allow |
| Wrong command | `BLOCKED` |
| Quantity 101 | `BLOCKED` |
| Duplicate command ID | Second request blocked while ID remains in list |
| Request exceeding total 300 | Blocked |
| Food level <= 5 | Blocked |
| MQTT subscriber on `petfeeder/status` | Feed result appears |
| MQTT subscriber on `petfeeder/foodlevel` | Retained simulated food level appears |
| Debug sidebar | Payload visible |
| Restart Node-RED | Verify whether context persists |

All tests are software-only; no food is dispensed.
