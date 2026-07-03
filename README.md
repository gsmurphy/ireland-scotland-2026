# Ireland & Scotland — July 2026

A single-file, editable trip itinerary (17 days: Dublin → Wild Atlantic Way → Scotland).

- **`index.html`** is the whole app — no build step, no dependencies.
- Two views (Day-by-Day and Calendar) render from one shared `TRIP` data object, so they stay in sync.
- Click **✎ Edit** to change entry text/times, set status colours, and add/remove items. Edits are saved in your browser (localStorage) per device.
- Click **⤓ Export** to download a copy of `index.html` with your edits baked in. Replace this repo's `index.html` with that file (and commit) to publish your changes to every device.
- **↺ Reset** discards local edits and reloads the published version.

## Publishing updates from the phone/laptop
1. Make edits in the browser (they persist locally).
2. **Export** → you get `ireland-scotland-itinerary.html`.
3. Rename it to `index.html` and upload it to this repo (GitHub web UI → "Add file" → "Upload files", or commit via git).
4. GitHub Pages redeploys in ~1 minute; other devices pick up the new baseline automatically.

> Note: publishing a newer export overwrites unpublished local edits on *other* devices. Whoever exports last wins.
