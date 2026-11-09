# GitHub Pages build — igloo-retrofit-quizzes

The uploaded root HTML pages are standalone built web apps. No Node or local
files are required on the venue PC. `source.zip` contains the unbundled template
for future development; this document describes rebuilding it, not running it
in the venue.

Using Node.js on a development machine, extract source.zip and enter
`templates/360-hosted/` inside it:

```powershell
npm install
npm test
$env:VITE_STATIC_HOST='1'
npm run build -- --base=./
npm run package:pages
```

Upload the contents of `web-release/` to the repository root. GitHub Pages must
serve the `main` branch, `/ (root)`. The `images/` folder must retain its name.
`package-pages.mjs` bundles the generated JavaScript/CSS/fonts into each HTML
file and makes root `index.html` the activity menu. `hazard-editor.html` is the
hazard authoring page, rather than the menu. Include the font and Three.js
licence notices. The upload should never include `.local-data`, local browser
data, node_modules, credentials or Windows delivery executables.

The hosted edition creates compressed snapshot URLs instead of writing to a
server. Drafts are browser-local; generated links carry the content and answer
key to the venue PC. Older links are immutable. No SSE/API, cloud upload,
remote tutor controller or live publication is required. Custom image uploads
are disabled because GitHub Pages has no storage API. They can be restored only
with an explicitly designed storage-backed hosting service.

For a local development host with the existing persistent publication API,
unset VITE_STATIC_HOST before building. That is an alternative developer setup,
not part of the web-only delivery requested for the venue.
