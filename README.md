# perth-scout-fixtures

Event fixtures for the Perth rideshare Demand Scout. The Scout's VPS pulls `fixtures.json`
from here (the raw file) to drive event-egress alerts.

- **fixtures.json** — a JSON list of events: `{name, venue, lat, lon, finish (local AWST), crowd}`.
- Refreshed weekly by the "Demand Board" scheduled task; can also be hand-edited here.
- Public on purpose: it holds only public event listings, so the server pulls it with no auth.
