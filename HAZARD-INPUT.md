# Hazard Hunt — ICE input check

The hazard lesson encodes equirectangular longitude/latitude in normalised UVs.
**The WebView itself does not have to be 2:1** when ICE maps the full texture by
normalised UVs. Leave its space-locked resolution as configured. A conventional
equirectangular image is 2:1, but that does not make a non-2:1 browser viewport
the proven cause of distortion. Keep True Perspective applied; do not switch to
the region quiz's native atlas mapping or use desktop preview to compensate.

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
- **Render / actual / DPR / GPU limits**: the page's internal render buffer is
  now independent of the CSS/WebView size. ICE output uses no extra Windows-DPI
  multiplier and the internal long edge is capped at 4096 (or a smaller GPU
  limit), preserving the WebView's aspect. For 10032×4066 this is 4096×1660; it
  still covers the whole WebView, not a centred/letterboxed 2:1 sub-rectangle.
  The readout reports both requested and actual WebGL buffer dimensions and GPU
  viewport/renderbuffer/texture limits. A requested/actual mismatch or different
  limits between laptop and venue helps identify driver/allocation differences.
  This is a safeguard, not confirmation that the GPU caused the room warping.
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

For machine comparisons use the **same quiz, same selected hazard and same
effect settings/viewpoint**. Different tangent-panel headings can look different
when flattened into the room's output atlas. A screenshot of that atlas alone
does not establish whether the panel appears rectangular on the physical wall.
