# MQTT

The supplied flow configures a local Mosquitto broker at `localhost:1883`.

| Topic | Purpose | QoS | Retained |
|---|---|---:|---|
| `petfeeder/status` | Feed result; blocked and successful results can be published | 1 | No |
| `petfeeder/foodlevel` | Simulated food level | 0 | Yes |

Subscribe using Mosquitto tools:
```powershell
mosquitto_sub -h localhost -p 1883 -t "petfeeder/status" -v
mosquitto_sub -h localhost -p 1883 -t "petfeeder/foodlevel" -v
```
Use the actual broker host for your setup. In a container, localhost means that container.
