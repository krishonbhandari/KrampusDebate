# KrampusDebate — cinematic collaborative presentation

**Website:** https://krishonbhandari.github.io/KrampusDebate/

An immersive debate presentation for **Group 1: The Traditionalists**, supporting the preservation of the Alpine Krampuslauf festival. It uses cinematic scene-to-scene transitions instead of a conventional slide deck.

## Current status

- The animated website and an in-page **Edit** panel are in `index.html`.
- Images, motion effects, and scene templates are embedded inside the HTML, so **no assets folder is needed for this deployment**.
- `firebase-config.js` now points to Firebase project **krampuslauf-abe21**. Backend setup and two-browser sync still need verification; configuration alone does not enable shared editing.
- An anonymous sign-in check on November 2, 2026 returned `CONFIGURATION_NOT_FOUND`. Complete Authentication setup below, then test again.
- Historical revisions are locally saved in each browser at first. Once Firebase is connected, every published revision is shared and can be restored.
- Anyone who can open the public website can edit it once shared editing is enabled. Anonymous editing is a deliberate project choice, but the URL is **not an access-control mechanism**.

## Enable GitHub Pages

Open **Settings → Pages** in this repository. Under **Build and deployment**, select **Deploy from a branch**, choose `main`, folder `/ (root)`, and save.

After deployment, visit https://krishonbhandari.github.io/KrampusDebate/ .

## Enable shared editing and version history (Firebase)

1. Open [the Firebase project](https://console.firebase.google.com/project/krampuslauf-abe21/overview). The web configuration is already committed; do not paste the npm SDK example into this static site.
2. In **Authentication**, click **Get started** if prompted. Under **Sign-in method**, enable **Anonymous** and save. See [Firebase's anonymous authentication guide](https://firebase.google.com/docs/auth/web/anonymous-auth).
3. In **Firestore Database**, inspect whether the project's **(default)** database exists and confirm its edition/mode. This website uses the Firestore Web SDK's document API, not MongoDB. If there is no database, create a Standard database for this existing integration.
4. In that database's **Rules** tab, paste the exact contents of [firestore.rules](./firestore.rules) and **Publish**. The repository file is not automatically deployed by GitHub Pages.
5. The rules allow public reads, require sign-in for writes, and require the deck and matching immutable history entry in the same transaction. Anonymous sign-in allows any visitor to edit; it does not restrict editing to classmates. All other document paths are denied.
6. Wait for GitHub Pages deployment, then reload the website. **SHARED LIVE** appears only after both the deck and history listeners receive server responses. It confirms reads, not a successful write.
7. Open the website in two different browsers. In browser A, make a small edit and **Save Version**; confirm browser B receives it and the same history revision. Restore the prior version and confirm that restoration also appears in both browsers. Until this passes, shared editing remains unverified.

If the badge says **SETUP REQUIRED**, check Anonymous sign-in and the browser console's Firebase error. **SYNC ERROR** indicates a Firestore listener failure: confirm the default database and published rules. If an `auth/unauthorized-domain` error occurs, add `krishonbhandari.github.io` under Authentication → Settings → Authorized domains (hostname only).

For optional large media uploads, use Firebase Storage and its `storage.rules` (may require the Blaze billing plan). The built-in photos and text editing do not require Storage.

**Security note:** Because editing is public, strangers who discover the link may edit. Version histories can help restore past content, but do not prevent abuse or bills from excessive usage. Consider closing writes after the class debate.

## Editing the presentation

- **Edit** button or `E`: open the editor.
- Change a scene's headline, supporting text, image, transition, color, speaker notes, layout, or order.
- **Save Version**: publish your changes once the shared connection is ready. If Firebase initialization fails, saving remains local. Shared saves wait for the server listeners and reject conflicting revisions.
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
