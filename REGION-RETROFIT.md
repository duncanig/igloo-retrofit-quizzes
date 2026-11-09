# Original region quiz — retrofit dimensions only

The whole original application from
https://github.com/duncanig/QuickFloorSessions/blob/main/region-quiz-floor.html
is retained: Glacier, Forest, Desert, Reef, original artwork and animations,
embedded recorded voices and browser voice fallback, music, effects, game flow,
sample questions, editor, share links, HTML downloads, floor compass, calibration,
rotation and mirroring. The original timer/manual-lock and 2.3-second reveal
delay are unchanged. Select **Edit** in the original toolbar to edit content.

Only the output geometry and resolution descriptions are adapted:

| Surface | X | Y | Width | Height |
|---|---:|---:|---:|---:|
| Wall 1 | 0 | 0 | 3974 | 2160 |
| Wall 2 | 3974 | 0 | 3588 | 2160 |
| Wall 3 | 7562 | 0 | 3974 | 2160 |
| Wall 4 | 11536 | 0 | 3588 | 2160 |
| One combined floor | 3974 | 2160 | 3588 | 3974 |

Total source: **15124 × 6134**. The floor contains both 3588 × 1987 lower outputs,
stacked at Y=2160 and Y=4147. It is not two separately controlled floor regions.
All unused lower areas remain black. Wall artwork is cropped at its original
theme boundaries and fitted to each actual wall width, not stretched as a strip
of four equal-width walls. The original logical floor is fitted into the full
combined floor. Floor rotation/mirroring remain available.

## ICE links and mapping

- Browser preparation/play/editor: **region.html**. Use the existing Play/Edit
  toolbar and original share-link controls. No files or local server are needed.
- Clean ICE output: **region.html?projection=1**. For an edited original `#r=`
  share URL, add `projection=1` to the query before the hash to hide browser chrome.
- **This is the original native projector atlas, not 2:1 equirectangular output.**
  Its mapping must match the supplied retrofit layout. Do not feed this atlas
  through the hazard quiz’s equirectangular/True Perspective conversion. The
  hazard quiz and its ICE settings have not changed. Check the appropriate ICE
  mapping/effect chain for each content type; no ICE settings are changed by the
  website itself. If the existing ICE source accepts only equirectangular input,
  it needs a matching atlas mapping setup before this original layout will fit.
- Use the original calibration overlay to check wall borders and the one floor.
  The dashed line on the floor overlay is the join between the lower outputs.
  Actual blending, physical alignment, touch/source input and readability still
  require a room check.

The source file is preserved as `region-original.html`, SHA-256
`74ff702813d8dd0dbf99febb9d13140d7bce37795337fc317ed5b73779b6b15e`.
`scripts/original-region.mjs` injects the layout-only adapter before the original
boot; it does not replace any original game or authoring functions. The earlier
simplified region implementation is not used by the published region page.
