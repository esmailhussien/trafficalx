# TrafficALX

An Arabic traffic-map frontend prototype centered on Alexandria, built with HTML, Tailwind CSS, vanilla JavaScript, and Leaflet.

## Implemented interface

- Traffic-flow tiles and an incident list with a time-window filter.
- Optional traffic-signal and water-accumulation hotspot layers.
- Place-name search and map-based route start/end selection.
- A route-scenario interface with a rectangular avoidance area.
- A separate login page that depends on an external service.

## Files and services

- `index.html`: map, layers, incident filtering, and route-scenario interface.
- `login.html`: login form and client-side session-state handling.

The frontend references an external Worker through `WORKER_URL`. Its backend implementation, provider credentials, and datasets are not included. It expects traffic-flow tiles, incident data, signal/hotspot features, and route results from that service. CARTO tiles, OpenStreetMap Nominatim search, Leaflet, Tailwind, and hosted fonts/icons also require network access.

## Local preview

Before opening a local copy, review the service settings and point both pages at an authorized test backend with synthetic or approved data. The dashboard requests flow, incidents, and hotspots on startup; searches and route coordinates are sent to external services. Do not use personal credentials or sensitive locations for a prototype review.

No build step or package installation is defined. With Python 3 installed, serve the repository directory:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open `http://127.0.0.1:8000/`. A static server supplies the frontend only; it does not provide the external backend or its authentication. The command above was not executed during this documentation review.

## Prototype limitations

- The displayed congestion percentage and average speed are calculated from incident count. They are illustrative indicators, not measured traffic statistics.
- The code includes a camera layer container but no camera-data loader.
- A login page or client-side session flag does not establish server-side authorization. Backend access controls require separate review before production use.
- Route suggestions, data freshness, service availability, and avoidance behavior have not been end-to-end validated. Do not rely on this prototype for emergency response or safety-critical routing.

Documentation reflects source inspection on October 5, 2026. No live traffic-service calls, login attempts, route requests, or deployments were tested.
