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
- **Fleet rows are inert.** The mockup's "tap a tail to load it in the calculator"
  is gone: tapping a row does nothing, and a per-row **Load W&B** button is the only
  way to switch the calculator's aircraft.
- **Wind and performance inputs are never written without being asked.** The METAR
  is displayed on arrival; **Auto-fill** copies it into the fields.
- The hero's live status line and the collapsible fleet/CG sections in the mockup are
  not implemented — there is no per-aircraft live status to show (the map is an
  embedded globe, not our own data).
