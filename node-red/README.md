# Node-RED Flow

Routes in the supplied flow:
- `POST /api/feed` — validates and records a simulated feed.
- `GET /api/status` — returns simulated status/history.

MQTT topics:
- `petfeeder/status`
- `petfeeder/foodlevel`

WebSocket listener path: `/ws/petfeeder`.

The JSON pasted in chat was truncated at the start and is not a complete importable flow. In Node-RED, use Menu → Export to save the complete flow as `flows-export.json` in this folder. Remove private credentials before committing.

The broker config says `localhost:1883`. If Node-RED runs in Docker, localhost points to the container, so configure the broker host appropriately.
