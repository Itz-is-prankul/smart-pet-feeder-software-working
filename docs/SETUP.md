# Setup guide (Windows)

1. Install Node.js and Node-RED following their official installation instructions.
2. In PowerShell, run `node-red` and keep the terminal open.
3. Open `http://localhost:1880`.
4. Import the complete Node-RED flow using Menu → Import, then click Deploy. Export the complete flow to `node-red/flows-export.json`; the pasted excerpt was truncated.
5. Start Mosquitto if needed and confirm the broker is reachable at the host/port configured in Node-RED (the supplied config says `localhost:1883`).
6. Open `website/smart-pet-feeder.html` in Chrome or Edge.
7. Click Refresh status, then Feed Now. Check the Debug sidebar and MQTT subscribers.
8. If the browser blocks API calls, configure `httpNodeCors` in Node-RED `settings.js` for your local test origin, restart Node-RED, and try again.

Routes used by the website: `GET /api/status` and `POST /api/feed`, at `http://localhost:1880`. If Node-RED is on another computer, update the URL in the HTML. If using Docker, remember localhost inside a container is the container itself.
