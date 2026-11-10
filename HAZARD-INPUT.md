# Hazard Hunt — ICE input check

The hazard lesson is still a 2:1 equirectangular source. Keep its True Perspective
effect applied; do not switch to the region quiz's native atlas or use desktop
preview mode to compensate for incorrectly forwarded coordinates.

Open `viewer.html?inputDebug=1` in ICE (add `&inputDebug=1` before the hash if
using an edited activity link). It appends an input readout to the same spherical
panel texture. This is not an unprojected HTML overlay. It starts with zero event
counts; it does not automatically start/answer the lesson or choose a mapping.

Click the visible **Start inspection** once and check:

- **Down / Up / Click / Touch**: do these counts increase? If none do, the page
  isn't receiving those events. Check ICE's input forwarding/interactive WebView
  settings and source focus, rather than changing the quiz's answer regions.
- **Image READY**: if not, the scene has not loaded. The Start button is disabled
  until it loads. Check network access to the image on GitHub Pages.
- **Result / source coordinates / pink ring**: the ring shows where the received
  event lands in the equirectangular source and is transformed with the picture.
  If it is visibly elsewhere than the physical click, ICE isn't returning the
  expected inverse-mapped source coordinates. Send a screenshot of the readout
  and tell us the input device and the exact ICE play URL. Do not assume raw
  projector/atlas/screen pixels are WebView CSS pixels.
- **Outside WebView CSS bounds**: reported pixel coordinates exceed the browser
  content size (also shown). We deliberately do not silently clamp/guess a scale.
- **Miss** with counts increasing: events reach the webpage, but miss the button.
  The displayed Start centre gives a source-coordinate reference. Arbitrary
  installation-specific True Perspective transforms can't be inverted by this
  webpage without knowing the coordinate mapping ICE sends back.
- **Enter** also starts/resumes from the introduction if keyboard input reaches
  the WebView. This is a diagnostic/fallback, not a pointer-coordinate fix.

The room input handler now accepts pointer/mouse release, ordinary click and
touch-end paths. The six-pixel desktop camera-drag filter is used **only in
desktop preview**, never to discard room taps because of host pointer jitter.
Compatibility events are deduplicated after a successful activation; a miss does
not swallow a later corrected event. Desktop drag-to-look remains unchanged.
Native canvas-targeted events and document/root-targeted forwarded events are
handled; real DOM accessibility buttons keep their own click handlers.

Without `inputDebug=1` the diagnostic footer and pink ring are absent. No remote
input logs, screenshots, learner data or telemetry are collected or uploaded.
Browser tests cover the event streams and projection math; actual ICE forwarding
and True Perspective inversion still need an on-site test.
