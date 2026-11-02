# KrampusDebate — cinematic PowerPoint visual foundation

[Open the presentation](https://krishonbhandari.github.io/KrampusDebate/) · [Open the existing shared deck](https://krishonbhandari.github.io/KrampusDebate/?shared=1)

Twelve editable 16:9 scenes: eight opening scenes (480 seconds), cross-examination, alliance/rebuttal, closing and research. Short headlines and research prompts leave space for classmates' contributions. AI imagery is labeled illustration, not archival evidence.

## Present

Right Arrow / Space / click: reveal, finish the current animation, then advance. Left Arrow: previous scene. Escape: chapters. F: fullscreen. N: notes. E: editor. Settings offers reduced motion, audio and a disabled-by-default presenter-triggered scare. The mask-removal clip is skippable and muted by default.

## Edit without replacing existing work

The default **visual foundation** uses local drafts. **Shared deck** (`?shared=1`) retains the existing Firebase project and revisions. The rework does not automatically publish new content into the old deck. Both modes retain editor fields, ordering, notes, images/crops, layout, timing and JSON backups.

To deliberately migrate after group review: export backups in both modes, import the foundation JSON in Shared deck, review the draft, then Save Version. Shared saves require Firebase setup and successful server reads. Configuration alone is not proof of collaboration.

## Firebase setup still required

Project: `krampuslauf-abe21`. Anonymous sign-in returned `CONFIGURATION_NOT_FOUND` in the latest check.

1. Open Firebase Authentication, Get started if prompted, enable Anonymous and save.
2. Confirm the `(default)` Firestore database and publish this repository's `firestore.rules`.
3. Open Shared deck in two browsers; save a small edit in one, verify content/history in the other, and test restore as a new revision.

Existing rules allow anonymous signed-in visitors to edit. The public URL is not access control. No rules were changed by this rework. Storage uploads remain optional.

## PowerPoint reference

See [production-reference.md](production-reference.md), [sources.json](sources.json), and [VERIFICATION.md](VERIFICATION.md). The delivered local production ZIP contains twelve 1920×1080 PNG references, editable scene JSON, backgrounds and the 8-second mask-removal MP4. It is not an editable PPTX. Use system-font text boxes and the supplied timing map to build PowerPoint.

The reference mode uses local media and system fonts. Serve the folder over HTTP for module loading; opening index.html directly through file:// is not supported. Shared mode additionally needs internet access for Firebase.

## Deployment

GitHub Pages: Settings → Pages → Deploy from a branch → main → / (root). No build step is needed.
