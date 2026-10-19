# Website

`smart-pet-feeder.html` is the website supplied for this project.

Open it in a browser while Node-RED is running. It calls `http://localhost:1880/api/status` and `http://localhost:1880/api/feed`.

If Node-RED runs on another computer, update the API base URL in the HTML. If browser requests are blocked, configure Node-RED CORS for local testing and restart Node-RED.

Schedule controls, virtual sensor controls, and cybersecurity test buttons are browser-side simulations. Do not assume these actions are persisted in Node-RED.
