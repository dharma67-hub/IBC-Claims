# IBC Claims Register — Installable App (PWA)

Claim verification and tracking for CIRP and Liquidation processes under the Insolvency and Bankruptcy Code, 2016. This folder is a complete Progressive Web App: once hosted, it can be installed on desktop and mobile and works fully offline, including Excel export.

## What's in the folder

| File | Purpose |
|---|---|
| `index.html` | The app itself |
| `sw.js` | Service worker — caches everything for offline use |
| `manifest.webmanifest` | Makes the app installable (name, icons, colours) |
| `xlsx.full.min.js` | Excel library, bundled locally so exports work offline |
| `icons/` | App icons (192 px and 512 px) |

## Step 1 — Host it (one-time, ~5 minutes)

PWAs must be served over HTTPS. Either free option below works; keep all files together in one folder.

**Option A — Netlify (easiest):**
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You get a link like `https://your-name.netlify.app` — that's your app.

**Option B — GitHub Pages:**
1. Create a repository on GitHub and upload all these files to it.
2. In the repository: Settings → Pages → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.
3. Your app appears at `https://<username>.github.io/<repository>/`.

To try it locally instead, run `python -m http.server` in this folder and open `http://localhost:8000`.

## Step 2 — Install it

Open your hosted link once while online, then:

- **Desktop (Chrome / Edge):** click the **⤓ Install app** button in the app's header, or the install icon in the address bar. It opens in its own window with a taskbar/dock icon.
- **Android (Chrome):** tap the **Install app** button, or menu (⋮) → *Add to Home screen* / *Install app*.
- **iPhone / iPad (Safari):** tap Share → **Add to Home Screen**. (iOS does not show install buttons; this is the standard route.)

After the first visit, the app works entirely offline — register claims, record security interests, view the Section 53 waterfall, and export to Excel with no connection.

## Your data

- The register is saved automatically **on the device, in that browser** — close and reopen anytime.
- Data does not sync between devices. Use **Export to Excel** for backups and sharing.
- **Reset case** clears the register to start a fresh assignment (export first if needed).
- Updating the app: replace the hosted files; the service worker picks up the new version on the next visit (bump the `CACHE` name in `sw.js`, e.g. `ibc-claims-v2`, to force it immediately).

## Notes

- Typefaces load from Google Fonts when online and are cached for offline use afterwards; if never loaded, the app falls back to system fonts.
- This tool assists record-keeping; it is not legal advice. Verify statutory timelines and forms against the current IBBI regulations.
