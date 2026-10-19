# Safety logic and caveats

Current Node-RED behavior:
- Command must be `FEED`.
- Quantity defaults to 50 and must be > 0 and <= 100.
- Daily quantity limit is 300.
- Recent duplicate command IDs are blocked; list holds up to 100.
- Feed blocked when simulated food level <= 5.
- Initial food level is 75; successful feed reduces it by `max(1, round(quantity / 5))`.
- Successful history holds up to 50 events.

Caveats:
- `user` is not authenticated by the supplied function.
- `Number("abc")` becomes `NaN`; current quantity checks should explicitly reject non-finite values.
- UTC date rollover is checked only on a feed request.
- Flow context persistence depends on Node-RED settings.
- Website displays feeds as `daily_total / 50` and has a local default limit of 3, while Node-RED caps quantity units at 300.
- Website food is a percentage; Node-RED uses a separate simulated scale.
- Browser security buttons are demos, not server-side security.

This is not a real pet-feeding device. A physical version requires independent hardware safety controls and testing.
