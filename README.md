# Smart Pet Feeder IoT — Software Simulation

A software-only Smart Pet Feeder project demonstrating a web dashboard integrated with Node-RED and MQTT. No physical feeder, motor, ESP32, or food sensor is connected; device and food-level behavior are simulated.

## Features
- Web dashboard and manual simulated feeding
- Node-RED HTTP API integration
- Command validation, duplicate-ID checks, daily quantity limit
- Simulated food level and feeding history
- MQTT status and food-level messages
- WebSocket output and cybersecurity demo screens

## Technologies
HTML, CSS, JavaScript, Node-RED, MQTT/Mosquitto, WebSocket.

## Repository structure
- `website/smart-pet-feeder.html` — website
- `node-red/` — instructions for adding the complete Node-RED flow export
- `mqtt/` — broker and topic notes
- `docs/` — architecture, setup, API, safety, MQTT, and testing documentation

## Quick start
1. Start Node-RED and open `http://localhost:1880`.
2. Start/configure Mosquitto if your flow uses MQTT.
3. Import your complete Node-RED flow export and click Deploy.
4. Open `website/smart-pet-feeder.html` in your browser.
5. Test Refresh status and Feed Now. Inspect Node-RED Debug and MQTT subscribers.

## Actual API routes
- `GET http://localhost:1880/api/status`
- `POST http://localhost:1880/api/feed`

Example feed payload:
```json
{"command":"FEED","quantity":50,"command_id":"demo-001","user":"owner"}
```

## Important implementation notes
- The supplied Node-RED text was truncated at the beginning; export the complete flow from Node-RED before uploading a `flows-export.json`.
- The website's schedule, virtual sensor controls, and security-test buttons mostly operate in browser-side simulation; they are not all connected to Node-RED.
- The website calculates displayed feeds as `daily_total / 50`, while Node-RED limits daily quantity to 300 units. These are not equivalent if different quantities are submitted.
- Website food is represented as a percentage; Node-RED starts at 75 and subtracts a quantity-based amount. Align units before treating these as the same sensor.
- The daily reset uses UTC and is checked by the feed function, not the status endpoint.
- Flow context may reset on Node-RED restart unless persistent context storage is configured.
- Blocked results can still be HTTP 200; inspect the JSON `status` field.
- Do not expose Node-RED publicly without authentication and network security.

## Screenshots to add
Add screenshots of the website, Node-RED flow, Debug output, MQTT status, food-level topic, and a blocked request.

## Safety
This is a software simulation, not a real pet-feeding device. Do not commit passwords, tokens, or broker credentials.
