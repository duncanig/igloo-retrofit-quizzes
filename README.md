# Igloo Retrofit Quizzes

**[Open the website](https://duncanig.github.io/igloo-retrofit-quizzes/)**

Both quizzes run online on the venue PC. No installation, local server or local
files are required. The editor can be closed during play.

## Move to the Right Region — whole original quiz

**[Open original quiz & editor](region.html)** · **[Clean ICE output](region.html?projection=1)**

This is the whole original [QuickFloorSessions region quiz](https://github.com/duncanig/QuickFloorSessions/blob/main/region-quiz-floor.html),
not the simplified remake. Glacier, Forest, Desert and Reef, artwork, animations,
recorded voices, music, effects, original game flow, editor, share links and
download options are retained. Timer expiry or manual lock uses the original
2.3-second answer-reveal sequence. Select **Edit** in its toolbar to author the
quiz; its original share links carry the edits to another PC. No tracking needed.

**Only output dimensions/layout have changed:** native **15124 × 6134** source,
wall widths **3974 / 3588 / 3974 / 3588**, all **2160** high. One **3588 × 3974**
combined floor sits below wall 2, including both stacked lower outputs. See
**[REGION-RETROFIT.md](REGION-RETROFIT.md)** for exact coordinates and ICE setup.

**The region quiz is a native projector atlas, not equirectangular.** Use ICE
mapping matching that atlas; do not apply the hazard quiz's equirectangular
conversion to it. The website does not change ICE settings. The clean region
output is `region.html?projection=1`; append the original `#r=` share fragment
for an edited activity. Check calibration, input and readability in the room.

## Spot the Hazard — unchanged

**[Play](viewer.html)** · **[Editor](hazard-editor.html)** · **[Desktop test](viewer.html?desktop=1)**

This remains the projection-aware construction lesson with its existing
questions, feedback, scoring and debrief. Keep its existing equirectangular /
True Perspective mapping. **ICE's locked WebView resolution does not have to be
2:1**: the shader and picking use the full frame's normalised UVs. Conventional
panoramas are 2:1, but changing the browser aspect is not a requirement or a
proven fix for warping. Internal GPU allocation is capped independently of the
WebView's CSS/input size. Use **[the input/GPU check](viewer.html?inputDebug=1)**
and **[HAZARD-INPUT.md](HAZARD-INPUT.md)** to compare machines. Desktop-test
mode is not the ICE source. The supplied scene is AI-generated, not a verified
seamless 360 photograph. Tutor review is needed; this is not certification.

The hazard editor's **Create shareable play link** creates an immutable URL
snapshot containing the content and answer key. Copy that URL to the venue PC.
Browser drafts are not cloud publications; older links do not change. GitHub
Pages has no server-side publishing or image-upload storage, so this edition
uses the bundled scene. Do not include personal information in activity links.

## Source and maintenance

The original region source is preserved unchanged in `region-original.html`
inside **source.zip**, with a separate dimension-only adapter. Root region.html
is that original plus the adapter; the earlier simplified region modules are
not used for this published page. The hazard HTML remains its existing built
bundle. Source/rebuild instructions are in **source.zip** and
**[PAGES-REBUILD.md](PAGES-REBUILD.md)**. Three.js and font licence notices are
included. No local publications, learner progress, executables or credentials
are uploaded. GitHub Pages serves the main branch at the repository root.
