# Design source

`Wayman Fleet Mobile.dc.html` is the mobile-first mockup the phone layout in
`../index.html` was built from (a Claude Design canvas; `support.js` is its
runtime, needed only to open the mockup in a browser). Nothing here ships as part
of the app and nothing in `index.html` loads from this folder — it is kept as the
reference for what the phone layout is supposed to look like.

The shipped layout follows the mockup with these deliberate differences:

- **Bottom nav is a floating pill**, not a full-width bar pinned to the bottom edge,
  so it clears the home indicator and stays reachable one-handed.
- **Flight Conditions** puts the GPH unit inside the burn-rate field so the rate is
  never clipped.
- **Fleet rows are inert and fully untangled** (founder decision, superseding the
  mockup's "tap a tail to load it in the calculator"): the list is information only;
  the aircraft picker is the sole way to switch the calculator's aircraft.
- **Wind and performance inputs are never written without being asked.** The METAR
  is displayed on arrival; **Auto-fill** copies it into the fields.
- The hero live-status row, collapsible fleet list, collapsible CG plot (mobile),
  map legend, and lazy map load are implemented as designed. The CG plot stays
  always-visible on desktop, where space isn't scarce.
