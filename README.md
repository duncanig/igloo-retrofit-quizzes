# Igloo Retrofit Quizzes

Online teaching activities for four walls and one combined floor.

**Website:** https://duncanig.github.io/igloo-retrofit-quizzes/

- Region quiz: [Play](region.html) · [Editor](region-editor.html) · [Desktop test](region.html?desktop=1)
- Spot the Hazard: [Play](viewer.html) · [Editor](hazard-editor.html) · [Desktop test](viewer.html?desktop=1)

## No local installation

Open the website on an internet-connected venue PC. In ICE use a play URL, a 2:1 equirectangular WebView source (e.g. 4096×2048), and keep True Perspective applied. Do not use desktop-test mode or the old flat wall/floor atlas in ICE. The two lower projector outputs are one floor; ICE owns their calibration/blending. Use the region quiz's alignment screen and measured roomYaw/UI-band calibration before teaching. Input, floor/wall orientation, seams and readability need a real room check.

## Editing without a server

Edit in your browser, click **Create shareable play link**, and copy the generated URL to ICE on the other PC. The fragment contains a compressed, validated snapshot of the questions, answers and settings; no files or local server needed. Existing links are immutable and do not change when you edit again. Browser drafts stay in that browser; saving a share link transfers the activity. These links include the answer key, so they are not suitable for private exams. GitHub Pages does not provide cloud publishing, live updates, accounts or image uploads; this edition uses the bundled construction image. Scene replacement needs a storage-backed host. Do not put personal learner information into activity links.

## Teaching notes

Region quiz: original eight sample questions, editable names/timer/content. Learners move physically; timer expiry or **Answer locked in** immediately highlights the correct wall and floor sector. Pause freezes time. Tutor group-confidence records are not automatic or individual scores. No tracking hardware required.

Hazard quiz: eight editable construction hazards, risk/response questions, feedback, scores and debrief. Supplied scene is AI-generated, not a verified seamless 360 photograph. Review safety content with a competent tutor; not certification.

Region adaptation: https://github.com/duncanig/QuickFloorSessions/blob/main/region-quiz-floor.html . Simplified projected graphics; original embedded recorded narration/animations are not included. Three.js and font licence notices are included.

## Repository layout

Root HTML files are standalone production bundles (no npm needed to run). The image is under images/. Unbundled source and rebuild instructions are in source.zip. GitHub Pages serves main at the repository root. No local publications, browser progress, Windows executable or credentials are included.
