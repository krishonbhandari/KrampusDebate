# Rework verification — November 2, 2026

Implemented as a visual foundation with editable placeholders, not a completed debate script or editable PPTX.

## Verified

- JavaScript syntax parses; 12 scenes; first eight speaking durations total 480 seconds.
- 1920×1080 Chromium in-app browser rendering and twelve final-state screenshots.
- Direct chapter access, editor opening, headline editing, local Save Version and history entry creation.
- N presenter notes, Escape chapter menu, right-arrow advance and animation completion/skip.
- Eight-second mask-removal MP4 plays after deliberate input; opening and final unmasked image reviewed.
- Images extracted as reusable local assets. Presentation typography uses system fonts.
- Reference and shared modes have separate local draft/history keys. No Firestore documents or existing revisions were changed by this rework.

## Not verified / remaining limits

- Firebase Anonymous Authentication still returns CONFIGURATION_NOT_FOUND. Live saving, cross-browser sync and shared restoration cannot be verified until Firebase Authentication is initialized and Anonymous enabled, and the default Firestore database/rules are ready.
- Fullscreen request is implemented, but the embedded test browser did not confirm entering native fullscreen. Test F in Chrome and Edge before presenting.
- Standalone Chrome/Edge parity and sustained 60 FPS performance were not measured.
- Optional scare is a deliberate, disabled-by-default browser animation, not a separate MP4. Bell sound is synthesized in the browser; the mask-removal MP4 contains its own audio and defaults to muted playback.
- The opening uses a still-image lighting/scale reveal and then a rendered mask-removal clip; a separate realistic mask-turn shot is not delivered.
- Twelve PNGs are 1920×1080 screen references converted from browser JPEG captures; source images are 1672×941 and the clip is 1280×720.

## Safe collaboration

The default URL opens the new visual foundation and saves reference drafts locally. Shared deck (`?shared=1`) opens the original Firebase workspace. Export a JSON backup from both modes before intentionally importing the new foundation into the shared deck. Import only prepares a draft; Save Version publishes it after backend setup. Existing history is retained. Do not mistake local reference saves for shared saves.

## Production package

`reference-exports/01.png` through `12.png`: final slide references. `slides.json`: editable text, layout choices, durations and speaker prompts. `assets/`: reusable imagery and the MP4. `production-reference.md`: scene/source/reproduction guide. `sources.json`: verified source details. This package is not a PPTX.
