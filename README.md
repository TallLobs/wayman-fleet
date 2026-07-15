# Wayman Fleet Tools

One single-file web app for Wayman Aviation Academy students (KHWO / North Perry):

**[index.html](index.html)** — on desktop, live fleet map on the left and the C-172 / C-152
weight & balance + short-field performance calculator on the right (stacked on phones,
calculator first).

- **Calculator**: all constants follow the school's paperwork conventions (fuel arms
  back-derived from the school-sheet full-fuel moments: 172 → 11500/240, 152 → 6200/147
  displayed as 42.17; taxi defaults −7 / −6; all 152s enforce 1670 lb max takeoff with
  1675 ramp).
- **Live map**: polls [airplanes.live](https://airplanes.live) every 10 s with one batched
  ~1 KB query for all 23 aircraft (by ICAO hex, resolved from the FAA registry), draws them
  on a dark Leaflet map with smooth marker motion, and shows per-tail status: airborne /
  on ground / last seen. Positions persist in localStorage so "last seen" survives reloads.
  Tapping a fleet row selects that aircraft in the calculator and centers the map on it.

## Deploy on GitHub Pages

1. Create a new GitHub repository (e.g. `wayman-fleet`).
2. Push this folder's contents to the `main` branch.
3. Repo **Settings → Pages → Build and deployment**: Source = "Deploy from a branch",
   Branch = `main`, folder = `/ (root)`. Save.
4. After a minute the site is live at `https://<your-username>.github.io/wayman-fleet/`.

No build step, no dependencies to install — Leaflet and map tiles load from CDNs at runtime.

## Data sources & caveats

- Live positions: airplanes.live REST API (CORS-open, free; the only major open ADS-B
  aggregator that allows browser calls — adsb.lol, adsb.fi and OpenSky do not).
- A parked aircraft with the master off transmits **nothing**: "No signal" almost always
  means it's on the ramp. "Last seen" shows the final received position.
- Aircraft hex codes came from the FAA registry (registry.faa.gov) on 2026-07-15; if the
  school adds/re-registers aircraft, update the `AIRCRAFT` array in index.html (hex + W&B
  data from the aircraft's official records).

## Roadmap

- Fuel-consumption / cross-country planning helpers (flight-plan prep with a Wayman aircraft)
- KHWO METAR integration
- URL deep-link to a tail (`?tail=N155SK`)

## Disclaimers

Training aids only. Verify all weight & balance figures against the aircraft's official
records and POH before flight. The map is a planning convenience — positions may lag or
drop out; never use it for traffic separation.
