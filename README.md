# 🌿 GrowLog

> ⚠️ **Early development — not production ready. Features and data formats may change between versions. Back up your data before updating.**

**A personal grow tracker built for privacy-first growers.**

No account. No cloud. No telemetry. No ads. Your data never leaves your device.

**[Try it live →](https://xultrax-web.github.io/growlog)** *(or download the file and open it locally)*

---

## What is it?

GrowLog is a single HTML file that runs entirely in your browser. Download it, open it, use it. That's it.

It tracks your plants from seed to harvest — strains, stages, journal entries, cure logs, seed vault, breeding records, and more. It's built to be the grow journal you actually want to keep.

---

## Why should I trust it?

You shouldn't trust any software blindly — including this. Here's how to verify it yourself.

**1. It makes zero network requests.**
Open the file in your browser. Open DevTools (F12) → Network tab. Reload. Nothing. No Google. No analytics. No fonts. No CDN. Empty.

**2. Your data never leaves your device.**
Everything is stored in your browser's `localStorage`. Open DevTools → Application → Local Storage and read it yourself. It goes nowhere.

**3. You can read every line of code.**
It's one HTML file. ~4,400 lines. No minification, no obfuscation, no build step. Open it in a text editor and read exactly what it does.

**4. Optional encryption is built in.**
If you want your localStorage data encrypted, enable it in the sidebar. It uses **AES-256-GCM** via the browser's built-in Web Crypto API — the same standard used by Signal and your bank. Your passphrase is never stored. Only a salt is saved. If someone pulls your localStorage without your passphrase, they get noise.

**5. It works offline forever.**
Once opened, it installs a service worker (also readable in the file) that caches itself. No internet required, ever.

---

## Changelog

### v4.0
- **Containers** — new page to organize your grow space. Assign seed packs to containers and track what's where.
- **Clone Batch tracking** — log batches of clones with target root days, then graduate them directly into active plants.
- **Plant Tiles view** — plants now display as a responsive card grid with at-a-glance status signals (green/yellow/red), stage, age, and recent VPD.
- **Drying & Curing redesign** — cure tracker rebuilt with the same tile/drawer layout as plants for consistency.
- **Dashboard stats** — full grow stats (flower times, strain history, issue tracking, VPD compliance) now embedded directly on the dashboard.
- **Renamed sections** — "Seed Vault" → "Seed Library", "Cure Tracker" → "Drying & Curing" for clarity.
- **Nav polish** — improved section label visibility, primary nav items more prominent.

---

## Features

- 🪴 **Plants** — full lifecycle tracking: seedling → veg → flower → drying → cure → done
- 🌱 **Seed Library** — catalog your collection, breeders, bins, quantities, lineage, wish list
- 📦 **Containers** — organize your grow space, assign seed packs to containers
- 🧬 **Breeding Lab** — crosses, pollen donors, seed runs, reversals, generation tracking
- 🫙 **Drying & Curing** — clone batch tracking, jar RH, burp schedule, phase tracking, smoke reports
- 📜 **History** — complete fate records: culls, males, mutants, runts, losses
- 🩺 **Symptom Checker** — guided decision tree for deficiencies, pests, environmental issues
- 📖 **Reference** — VPD charts, stage guides, feeding schedules
- 💾 **Export / Import** — JSON backups, CSV import. Your data is always portable.
- 🔒 **Encryption** — optional AES-256 passphrase lock
- 📱 **Installable** — works as a PWA on desktop and mobile. Add to home screen.
- ↩ **Undo** — last 20 actions undoable

---

## How to use it

1. Download `growlog.html`
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge)
3. That's it

To install it like an app: look for the install icon in your browser's address bar, or on mobile use "Add to Home Screen."

To back up your data: **Export Backup** in the sidebar. Do this regularly. The app will remind you if you haven't exported in a week.

---

## Encryption — how it actually works

For anyone who wants the technical detail:

- Algorithm: **AES-GCM, 256-bit key**
- Key derivation: **PBKDF2** with 100,000 iterations, SHA-256, random 128-bit salt
- The salt is stored in localStorage. Your key and passphrase are **never** stored anywhere.
- Each save generates a new random 96-bit IV (nonce)
- If you forget your passphrase, your data cannot be recovered. Export a backup first.

All of this code is in the HTML file, clearly commented, starting at the line marked `ENCRYPTION ENGINE`.

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

## Contributing

Issues and PRs welcome at [github.com/xultrax-web/growlog](https://github.com/xultrax-web/growlog). Keep it single-file. Keep it zero-dependency. Keep it auditable.

The golden rule: **a paranoid grower should be able to verify what this software does in under 10 minutes.**

---

## License

MIT — do whatever you want with it.

---

*Built for growers, by growers. Stay safe out there.*
