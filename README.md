# Wayman Fleet Tools

One single-file web app for Wayman Aviation Academy students (KHWO / North Perry):

**[index.html](index.html)** — on desktop, live fleet map on the left and the C-172 / C-152
weight & balance + short-field performance calculator on the right (stacked on phones,
calculator first).

- **Calculator**: all constants follow the school's paperwork conventions (fuel arms
  back-derived from the school-sheet full-fuel moments: 172 → 11500/240, 152 → 6200/147
  displayed as 42.17; taxi defaults −7 / −6; all 152s enforce 1670 lb max takeoff with
  1675 ramp).
- **Live map**: embeds the [adsb.lol](https://adsb.lol) tar1090 globe in an
  iframe, filtered (`icaoFilter`) to the fleet's 23 ICAO hex codes — live positions with
  zero API calls of our own. If a tail is on the map it's transmitting (flying or taxiing);
  if not, it's parked with the master off. Tapping a fleet row selects that aircraft in
  the calculator.

## Deploy on GitHub Pages

1. Create a new GitHub repository (e.g. `wayman-fleet`).
2. Push this folder's contents to the `main` branch.
3. Repo **Settings → Pages → Build and deployment**: Source = "Deploy from a branch",
   Branch = `main`, folder = `/ (root)`. Save.
4. After a minute the site is live at `https://<your-username>.github.io/wayman-fleet/`.

No build step, no dependencies to install — Leaflet and map tiles load from CDNs at runtime.

## Data sources & caveats

- Live positions: embedded adsb.lol globe (their REST API closed to anonymous use
  in Aug 2026, which killed the old fetch-and-draw map; no free ADS-B aggregator allows
  direct browser API calls anymore, airplanes.live also 403s iframe embeds — but adsb.lol's globe embeds fine and needs no key).
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
