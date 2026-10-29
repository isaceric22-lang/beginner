# iPhone Wedding Invitation (static build)

Static HTML/CSS/JS build of
[nguyenhuugiatri/iphone-wedding-invitation](https://github.com/nguyenhuugiatri/iphone-wedding-invitation)
(MIT, see `LICENSE`; music credits in `CREDITS.md`). No build step or server needed.

- `index.html` contains all JS and CSS inline.
- Images, icons, photos and music sit next to it and use relative paths.

## Run locally

Double-click `index.html`, or serve the folder:

```bash
python -m http.server 8080
```

## Deploy to GitHub Pages

1. Push the contents of this folder to a repository (root of `main`, or a `docs/` folder).
2. Repository Settings > Pages > Source: "Deploy from a branch", pick the branch and folder.
3. Open `https://<user>.github.io/<repo>/`.

`.nojekyll` is included so Pages serves every file as-is.

## Notes

- Safari (RSVP form) and YouTube load in iframes from external sites, so they need internet.
  YouTube embeds may refuse to play when opened via `file://`; use a server or Pages for that.
- To change names, photos, dates or text, edit the source in `../source` and rebuild (below).

## Edit and rebuild

Requires Node.js 20+. From the `source` folder:

```bash
npm install
npm run dev
npm run build:site
```

`npm run dev` gives a live preview while editing. `npm run build:site` rebuilds and copies the result into this `site` folder.

Where things live in `source`:

- Wedding date, events, countdown target: `components/calendarData.ts` (`WEDDING_DATE_ISO`)
- Names in the unlock greeting: `components/UnlockCelebration.tsx`
- Notes invitation text: `src/NotesPage.tsx`; chat: `src/MessagesPage.tsx`
- RSVP form link: `src/SafariPage.tsx`; map link: `lib/maps.ts`
- Photos and music: `public/photos/`, `public/music/` (track list in `src/music/MusicProvider.tsx`)
- Petal/sparkle amounts: `src/LockScreen.tsx` and `src/IosAppFolder.tsx` (`<MagicParticles />`)
