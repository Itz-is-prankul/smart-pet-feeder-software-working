# MQTT topics

| Topic | Meaning |
|---|---|
| `petfeeder/status` | Feed logic result; blocked and successful results can be published |
| `petfeeder/foodlevel` | Simulated food-level payload, retained by MQTT output |

The configured broker is `localhost:1883`. Confirm this matches your runtime. See `../mqtt/README.md` for subscriber commands.
