# perth-scout-fixtures

Event fixtures for the Perth rideshare Demand Scout and Perth Pulse. The VPS pulls the raw files from here
(no auth: they hold only public listings).

## fixtures.json

A JSON list of events:

| Field | Required | Meaning |
| --- | --- | --- |
| `name` | yes | Event name |
| `venue` | yes | Venue name (Perth Pulse matches venues by name, not coordinates) |
| `lat`, `lon` | yes | Venue coordinates (used by the Demand Scout's egress alerts) |
| `finish` | yes | Local AWST `YYYY-MM-DDTHH:MM`: when the crowd leaves (event end, conference day close, last cruise disembarkation) |
| `crowd` | yes | Rough expected attendance (integer) |
| `start` | no | Local AWST start; otherwise estimated from the category |
| `category` | no | `nbl`, `a_league`, `afl`, `cricket`, `rugby`, `concert`, `theatre`, `conference`, `cruise`, `market` |
| `note` | no | What's confirmed vs estimated |

Venue coordinates: RAC Arena -31.9483,115.8519 · HBF Park -31.9429,115.8703 · Optus Stadium -31.9513,115.8890 ·
Crown Theatre -31.9610,115.8947 · PCEC -31.9605,115.8565 · Fremantle Passenger Terminal -32.0500,115.7420.

Multi-day conferences get one record per day. Cruise ship calls: `start` = disembarkation start, `finish` = end.

## closures.json

Transperth planned line closures, a JSON list of `{line, start, end, detail, source}` in AWST.
An empty list means no confirmed closures in the window. Never add a closure that isn't confirmed by a primary source.

Refreshed weekly by the "Demand Board weekly refresh" scheduled task (pushed from an interactive session); can also be hand-edited.
