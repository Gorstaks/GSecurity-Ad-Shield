# GSecurity Ad Shield

A Chrome (Manifest V3) extension that blocks ads, trackers, and adult ad networks using `declarativeNetRequest`, with targeted fixes so YouTube embeds on forums keep working and normal video playback isn't broken.

## Features
- Network-level ad and tracker blocking via `declarativeNetRequest` (ruleset in `rules.json`)
- Cosmetic filtering injected at `document_start` across all sites (`content-cosmetic.js`)
- YouTube-specific handling to protect embeds and keep playback working (`content.js`)
- Per-site tuning for Reddit, Facebook, Twitter/X, Instagram, LinkedIn, Twitch, TikTok, major news sites, Fandom/Wikia, Pinterest, and TeamOS (`content-sites.js`)
- Generic fallback for all other sites (`content-generic.js`)
- Lightweight: no background polling, no remote code

## Requirements
- Chromium-based browser (Chrome, Brave, or Edge), **version 114 or newer** (set in `manifest.json` as `minimum_chrome_version`)

## Installation

### Chrome Web Store (recommended)
[Get it on the Chrome Web Store](https://chromewebstore.google.com/detail/gsecurity-ad-shield/hhpmmmfnjckeffhaafpjmioogcbclbof)

Updates are delivered automatically through the Web Store.

### Enterprise / managed deployment
Use `Install.reg` to force-install the extension via policy on Chrome, Brave, and Edge. It points the browser at the Chrome Web Store update service using the extension ID `hhpmmmfnjckeffhaafpjmioogcbclbof`.

### Load unpacked (development)
1. Clone the repository:
   ```bash
   git clone https://github.com/CroatiaSecurity/GSecurity-Ad-Shield.git
   ```
2. Open `chrome://extensions/`
3. Enable **Developer mode**
4. Click **Load unpacked** and select the project folder

## Building a release
`Build.ps1` bumps the version in `manifest.json`, assembles the package, and (if a Chromium browser is available) produces a signed `.crx`:

```powershell
.\Build.ps1 -Version 1.6.0
```

Artifacts are written to `dist/` and copied to `releases/<version>/`.

## Project layout
- `manifest.json` — MV3 manifest
- `rules.json` — declarativeNetRequest blocking rules
- `background.js` — service worker
- `content-cosmetic.js` — global cosmetic filtering
- `content.js` — YouTube handling
- `content-sites.js` — per-site tuning
- `content-generic.js` — fallback for all other sites
- `main-world.js` — main-world injected helper
- `icons/` — extension icons

## Legal
THIS SOFTWARE IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED. USE AT YOUR OWN RISK.
