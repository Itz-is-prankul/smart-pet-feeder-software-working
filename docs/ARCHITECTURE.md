# Architecture

```text
Website --POST /api/feed--> Node-RED validation logic
  |                            |--> HTTP response to website
  |                            |--> MQTT petfeeder/status
  |                            |--> WebSocket /ws/petfeeder
  |                            `--> Debug sidebar
  `--GET /api/status---------> Node-RED status logic --> website

Inject node (startup + every 10 seconds)
  --> Virtual Food Sensor --> MQTT petfeeder/foodlevel
                         `--> WebSocket output
```

The feed logic checks command `FEED`, quantity > 0 and <= 100, duplicate command IDs, daily total <= 300 units, and food level > 5. Accepted requests increase daily total and reduce the simulated food level. Recent history is capped at 50 events and command IDs at 100.

No physical hardware or sensor is connected. Date rollover uses UTC and is checked in the feed handler only. Flow state persistence depends on Node-RED settings.
