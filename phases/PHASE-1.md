# Phase 1 — Sovereign Mobile (the 2.0 rebuild)

**Goal:** Blake voice-commands Cortana 100% from his Galaxy S24, end-to-end inside Solomon brand, custom UI, sideload APK, owned distribution.

## Day 0 — Audit

Run the deep sweep per `SOLOMON-AUDIT-INDEX-2026-05-07.md` (forklifted into this repo as `audit/PHASE-0-AUDIT.md`). Find anything Solomon-relevant scattered across:
- Gmail (search "Solomon" / "Cortana" / "Dominion" / "MCP")
- Chrome bookmarks + history
- All Blake1194 GitHub repos (esp. blake-marshall-os, ai-os, sentinel-core)
- base44 apps
- OneDrive Documents/Claude/Scheduled
- Notion / other workspace tools

Output: extended audit document with INTEGRATE / ARCHIVE / DISCARD verdict per item. Get Blake's sign-off before Day 1.

## Day 1 — solomondominion.com foundation

- Set up Cloudflare Pages pointing at this repo's `web/` directory
- Configure DNS for solomondominion.com (Namecheap → Cloudflare)
- SSL via Cloudflare auto-cert
- Deploy bare landing page using `theme/tokens.css` for branding
- Acceptance: solomondominion.com loads, purple+gold visible, ≤2s load on mobile

## Day 2 — Custom voice UI

- Replace any Convai widget reference with custom chat + voice UI
- Hits ElevenLabs Conversational API directly: `POST /v1/convai/conversations` + WebRTC voice streaming
- Solomon-branded message bubbles, mic button, transcript display
- Acceptance: voice input → Cortana speaks → tools fire → response renders. NO ElevenLabs branding visible.

## Day 3 — Bubblewrap APK

- Generate TWA project pointing at solomondominion.com
- Generate signing keystore (encrypt, back up to Bitwarden + USB + offline)
- Build first APK
- Acceptance: APK installs on Galaxy S24, opens fullscreen, mic permission requested via origin model

## Day 4 — Sideload distribution

- Build solomondominion.com/app release page (signed manifest, SHA-256, QR code, install instructions)
- In-app updater wired (PackageInstaller pattern from playbook)
- Acceptance: Blake taps QR code on phone, downloads APK, sideloads, app launches as Solomon

## Day 5 — Acceptance

- Full end-to-end voice command test on Blake's S24
- DO! adversarial QA
- Iterate any failures, ship final v1.0.0

## Reference docs

- `../DOCTRINE.md` — the 8 cheatcodes (LAW)
- `../audit/PHASE-0-AUDIT.md` — Day 0 starting input
- `playbook/PHASE-2-BUILD-PLAYBOOK.md` — DO!'s detailed build commands
- `../README.md` — kingdom mission
