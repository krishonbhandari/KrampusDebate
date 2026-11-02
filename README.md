# KrampusDebate — cinematic collaborative presentation

**Website:** https://krishonbhandari.github.io/KrampusDebate/

An immersive debate presentation for **Group 1: The Traditionalists**, supporting the preservation of the Alpine Krampuslauf festival. It uses cinematic scene-to-scene transitions instead of a conventional slide deck.

## Current status

- The animated website and an in-page **Edit** panel are in `index.html`.
- Images, motion effects, and scene templates are embedded inside the HTML, so **no assets folder is needed for this deployment**.
- The site uses **local-only saving until Firebase is configured**. Do not expect classmates' edits to sync before completing the Firebase setup below.
- Historical revisions are locally saved in each browser at first. Once Firebase is connected, every published revision is shared and can be restored.
- Anyone who can open the public website can edit it once shared editing is enabled. Anonymous editing is a deliberate project choice, but the URL is **not an access-control mechanism**.

## Enable GitHub Pages

Open **Settings → Pages** in this repository. Under **Build and deployment**, select **Deploy from a branch**, choose `main`, folder `/ (root)`, and save.

After deployment, visit https://krishonbhandari.github.io/KrampusDebate/ .

## Enable shared editing and version history (Firebase)

1. Visit https://console.firebase.google.com/ and create a project.
2. Add a **Web App** to the project and copy its public Firebase SDK config values.
3. In this repo, edit **firebase-config.js**, fill in its keys (apiKey, authDomain, projectId, appId, etc.), and commit the change. Never upload service-account credentials or private keys.
4. In Firebase **Authentication → Sign-in method**, enable **Anonymous** sign-in.
5. In Firebase **Firestore Database**, create a Standard database, open **Rules**, paste the contents of this repo's `firestore.rules` and **Publish**.
6. Reload the website. The status badge should display **SHARED LIVE** rather than **LOCAL PREVIEW**.
7. Open the website in two browsers to confirm edits and revision history sync between viewers.

For optional large media uploads, use Firebase Storage and its `storage.rules` (may require the Blaze billing plan). The built-in photos and text editing do not require Storage.

**Security note:** Because editing is public, strangers who discover the link may edit. Version histories can help restore past content, but do not prevent abuse or bills from excessive usage. Consider closing writes after the class debate.

## Editing the presentation

- **Edit** button or `E`: open the editor.
- Change a scene's headline, supporting text, image, transition, color, speaker notes, layout, or order.
- **Save Version**: publish your changes. For now the save is local; after connecting Firebase, the save synchronizes to everyone.
- **History**: inspect and restore older revisions; a restoration creates a new revision.
- Arrows, mouse wheel, swipes, or chapter markers: navigate the story.
- `N`: show speaker notes.

## Assignment reminder

The teacher specifically requires submitting a PowerPoint or Google Slides presentation. **This website is not a replacement for that required file**; export or build a matching slide backup before submitting.

The AI-generated pictures in the site are illustrative, not historical documentary evidence. Avoid unverified tourism statistics.

## Source references

- [Austria Tourism: Raucous Winter Traditions](https://www.austria.info/en-us/inspiration/raucous-traditions/)
- [Smithsonian: Origin of Krampus](https://www.smithsonianmag.com/travel/krampus-could-come-you-holiday-season-180957438/)
- [Salzburg Tourism: Traditional Krampus Run](https://www.salzburg.info/en/events/events-calendar/traditional-krampus-run-at-the-salzburg-christmas-market_event_42164626)
