# Ireland & Scotland — July 2026

A single-file, editable trip itinerary (17 days: Dublin → Wild Atlantic Way → Scotland), shared live across everyone's phones.

## How it works
- **`index.html`** is the app (no build step, no dependencies). **`trip.json`** is the live shared itinerary data.
- Two views (Day-by-Day and Calendar) render from the same data, so they stay in sync.
- Every device fetches `trip.json` on open, when you return to the tab, and every 60 seconds — so **all viewers see edits within ~1 minute**. Viewing needs **no login**.

## Editing & publishing
- Tap **✎ Edit** to change entry text/times, set status colours, and add/remove items. Edits save on your device (localStorage) immediately.
- Tap **💾 Save** to publish to everyone. This commits `trip.json` back to the repo via the GitHub API.
- **Saving requires a token** (one-time **☁ Connect**). See below.
- **↺ Reset** discards local edits and reloads the published version. **⤓ Export** downloads an offline snapshot.

### Getting a token (editors only)
1. github.com → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**
2. **Resource owner:** the account that owns this repo · **Repository access:** *Only select repositories* → this repo
3. **Permissions → Repository → Contents: Read and write** (leave everything else "No access")
4. **Expiration:** set a date (e.g. just after the trip)
5. Generate, copy the `github_pat_…` string, and paste it into the page's **☁ Connect** prompt. It's stored only on that device and never published.

A single token can be shared with a second editor (paste it on their phone too). Revoke it anytime in GitHub settings to cut off writing.

## Concurrent edits
Saves merge at the meal-slot level: your changes to a slot are kept, and everyone else's changes to *other* slots are pulled in automatically. If two people edit the *exact same* slot before syncing, the last save wins and the app shows a "kept yours on N overlapping slot(s)" note — no silent data loss.

## Editing the source
Data is generated from `scratchpad/build.js` in the working copy — edit the `trip` object there and run `node build.js <outputDir>` to regenerate both `index.html` and `trip.json`. (Routine trip edits should use the in-page editor instead.)
