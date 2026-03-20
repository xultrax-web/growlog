# GrowLog

> **v4.1 — Security & reliability fixes. Back up your data before updating.**

**A personal grow tracker built for privacy-first growers.**

No account. No cloud. No telemetry. No ads. Your data never leaves your device.

**[Try it live →](https://xultrax-web.github.io/growlog)** *(or download the file and open it locally)*

---

## What is it?

GrowLog is a single HTML file that runs entirely in your browser. Download it, open it, use it. That's it.

It tracks your plants from seed to harvest — strains, stages, journal entries, cure logs, seed library, breeding records, and more. It's built to be the grow journal you actually want to keep.

---

## Why should I trust it?

You shouldn't trust any software blindly — including this. Here's how to verify it yourself.

**1. It makes zero network requests.**
Open the file in your browser. Open DevTools (F12) → Network tab. Reload. Nothing. No Google. No analytics. No fonts. No CDN. Empty.

**2. Your data never leaves your device.**
Everything is stored in your browser's `localStorage`. Open DevTools → Application → Local Storage and read it yourself. It goes nowhere.

**3. You can read every line of code.**
It's one HTML file. No minification, no obfuscation, no build step. Open it in a text editor and read exactly what it does.

**4. Optional encryption is built in.**
Enable it in the sidebar. It uses **AES-256-GCM** via the browser's built-in Web Crypto API — the same standard used by Signal and your bank. Your passphrase is never stored. Only a salt is saved. If someone pulls your localStorage without your passphrase, they get noise.

**5. It works offline after your first visit.**
Your browser automatically caches the file after loading it. No internet required after that first load. If you download the file and open it locally, it works offline immediately — no first visit needed.

---

## Changelog

### v4.1 — Security & Reliability Fixes
- **Encryption hardened** — undo no longer bypasses encryption; all undo operations now write through the encrypted save path
- **Import confirmation** — importing a backup now requires explicit confirmation before overwriting existing data
- **Export warning** — exporting while encryption is enabled now warns that the backup file is plaintext
- **Clear All fixed** — "Burn All Data" now fully wipes all app storage, not just the main data key
- **Startup error handling** — corrupted data on load now shows a user-facing recovery message instead of a silent blank screen
- **Mobile menu** — Export, Import, Settings, Encryption, and all sidebar actions are now accessible on mobile via the ⋮ menu in the nav bar

### v4.0 Beta
- **VPD auto-calculator** — enter temp and RH in any log entry and VPD fills in automatically using leaf-surface VPD formula
- **Trend sparklines** — VPD, temp, and RH trends visualized inline in each plant's log tab
- **Light / dark mode** — toggle in the sidebar, preference persists across sessions
- **Photo notes** — attach photos to journal entries, compressed and stored locally *(note: heavy photo use can approach browser storage limits — export backups regularly)*
- **Print / PDF export** — clean print layout with sidebar hidden and tiles reformatted for paper
- **PWA install prompt** — install button appears automatically when the browser supports it
- **Keyboard shortcuts** — `N` new plant, `J` log entry on open plant, `/` focus search, `ESC` close modal
- **Breeding Lab rebuilt** — status tracking (Active / Seeds Harvested / Complete), pollination progress bar, quick-complete flow that auto-adds seeds to the library
- **History yield stats** — avg flower time, avg dry yield, best yield, most-run strain, success rate shown above the timeline
- **Breeding → Seed Library** — one-click to add a completed run's seeds directly to your library
- **Lucide icon system** — all emoji replaced with consistent SVG icons throughout the app
- **VPD ranges corrected** — seedling (0.4–0.8), veg (0.8–1.2), early flower (1.0–1.5), mid/late flower (1.2–1.8). Source-cited on reference page.
- **Settings panel** — configure stage duration defaults (seedling, veg, flower, drying)
- **About panel** — privacy model, architecture explanation, source link
- **Symptom checker disclaimer** — educational tool notice on every diagnosis
- **Drag-and-drop tile reordering** — rearrange plants within each stage group
- **Stage grouping** — plants page permanently grouped by stage with colored headers

### v4.0
- **Containers** — organize your grow space, assign seed packs to containers
- **Clone batch tracking** — log batches with target root days, graduate directly into active plants
- **Plant tiles** — responsive card grid with at-a-glance status signals, stage, age, VPD, and progress bars
- **Harvest pulse** — tiles within 7 days of harvest animate with a red heartbeat glow
- **Drying & Curing redesign** — rebuilt with the same tile/drawer layout as plants
- **Dashboard stats** — full grow stats embedded directly on the dashboard
- **Renamed sections** — "Seed Vault" → "Seed Library", "Cure Tracker" → "Drying & Curing"

---

## Features

- **Plants** — full lifecycle: seedling → veg → flower → drying → cure → complete
- **Seed Library** — catalog your collection, breeders, bins, quantities, lineage, wish list
- **Containers** — organize your grow space, assign seed packs to containers
- **Breeding Lab** — crosses, pollen donors, seed runs, reversals, status tracking, progress
- **Drying & Curing** — drying progress, jar tracking, phase tracking, smoke reports
- **History** — complete fate records: culls, males, mutants, runts, losses. Yield stats per strain.
- **Symptom Checker** — guided decision tree for deficiencies, pests, environmental issues
- **Reference** — VPD charts, PPFD targets, Aerocloner calculator, drying and cure protocol
- **Export / Import** — JSON backups, CSV import. Your data is always portable.
- **Encryption** — optional AES-256 passphrase lock
- **Installable** — works as a PWA on desktop and mobile
- **Undo** — last 20 actions undoable
- **Print / PDF** — clean printable grow report from any page
- **Light / Dark mode** — toggle in sidebar

---

## How to use it

1. Download `index.html`
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge)
3. That's it

To install it as an app: look for the install icon in your browser's address bar, or use the **Install App** button in the sidebar when available.

To back up your data: **Export Backup** in the sidebar. Do this regularly. The app will remind you if you haven't exported in a week.

---

## Encryption — how it actually works

- Algorithm: **AES-GCM, 256-bit key**
- Key derivation: **PBKDF2** with 100,000 iterations, SHA-256, random 128-bit salt
- The salt is stored in localStorage. Your key and passphrase are **never** stored anywhere.
- Each save generates a new random 96-bit IV (nonce)
- If you forget your passphrase, your data cannot be recovered. Export a backup first.

All of this code is in the HTML file, clearly commented, starting at the line marked `ENCRYPTION ENGINE`.

---

## VPD Targets

| Stage | VPD (kPa) |
|---|---|
| Seedling / Clone | 0.4 – 0.8 |
| Early Veg | 0.8 – 1.0 |
| Late Veg | 1.0 – 1.2 |
| Early Flower (wk 1–3) | 1.0 – 1.5 |
| Mid / Late Flower | 1.2 – 1.8 |

Ranges based on leaf-surface VPD research and widely validated commercial cultivation data. Treat as starting points — genetics and environment vary.

---

## Privacy

| What we collect | Amount |
|---|---|
| Your grow data | Stored locally on your device only |
| Usage analytics | None |
| Crash reports | None |
| IP address | Never transmitted |
| Email / account | Not required, not possible |

---

## Compatibility

Works in any browser with Web Crypto API support (all modern browsers since ~2017):
- Chrome / Chromium 60+
- Firefox 57+
- Safari 11+
- Edge 79+

---

## Architecture

GrowLog is intentionally a single HTML file with no build step, no dependencies, and no CDN calls. This is a deliberate choice — the entire codebase is auditable by anyone in minutes, works offline after first load, and can be self-hosted by dropping one file anywhere.

The golden rule: **a paranoid grower should be able to verify what this software does in under 10 minutes.**

---

## Contributing

Issues and PRs welcome at [github.com/xultrax-web/growlog](https://github.com/xultrax-web/growlog). Keep it single-file. Keep it zero-dependency. Keep it auditable.

---

## License

MIT — do whatever you want with it.

---

*Built for growers, by growers. Stay safe out there.*
