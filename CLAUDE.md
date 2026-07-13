# La Única — radio site

Independent web radio, broadcast from the mountains near Bogotá, Colombia. This repo is the public listener page (GitHub Pages). One creator, non-programmer — give click-level instructions, never assume terminal comfort.

## Stack
- Static `index.html` (no build step) on GitHub Pages: https://launicaradio.github.io/launica-radio/
- Backend is **AzuraCast** in a Multipass VM on the creator's Mac, exposed via a **Cloudflare quick tunnel** whose URL rotates on every restart.
- The page finds the current backend by reading `pointer.json` (same repo), which an automated agent keeps updated. Station shortcode: `la_unixa`.

## Working on the site
1. **Before local preview, sync the pointer** or now-playing shows offline:
   `cd ~/launica-radio && git stash -q && git pull -q && git stash pop -q`
2. Preview: launch.json server `launica-site` (port 8420), open in the browser pane.
3. Deploy = commit + push to `main`; Pages rebuilds in ~1 min.
4. **Cache**: after deploy the creator often "sees the same page" — it's browser cache. Tell them to hard-refresh or use a `?v=N` cache-buster; that's not a bug.

## Design language (current: v4 "spinning record player")
- The album art IS a vinyl disc (round, grooves, center hole); the disc/center button plays; disc spins while playing.
- Palette: deep forest `#0b1d12`, electric green `#35e07c`, cream `#efe7d2`, orange pop `#ff5a36`.
- Type: **Futura** display (song title/wordmark) vs **American Typewriter** for all labels/data (zine voice).
- Mascot/logo: 8-bit pygmy-goose duck (also the favicon + Mac app icon).
- **The creator reads geometric perfection as "AI-made."** Keep deliberate imperfection: slight tilts, wobbly hand-drawn rules, print-misregistration shadows, hard offset shadows. Composed, not messy. Refs they love: radio-sofa.com, pinataradio.com, egrego.re. Read the `frontend-design` skill before redesigns.

## Roadmap (not yet built)
- **Pending tweaks**: footer = only "Bogotá, Colombia"; move the live clock out of the footer and make it bigger; slow the disc spin (9s → 20–30s, current speed is dizzying).
- **Side styling**: the wide/desktop layout feels empty at the edges — add tasteful side treatment.
- **Ephemeral shoutbox**: name + short message + a few "trashy" emoji; messages appear and disappear, nothing stored ("people just take shit and let it go"). Needs a free realtime relay, no database.
- **Dedicated app**: make the site an installable **PWA** first (manifest + service worker → home-screen icon, full-screen, keeps playing). Only wrap with **Capacitor** for the App/Play stores later. The app should reuse this same page so they never diverge.

## Deeper history
Infra details, past incidents, and the Mac control app live in Claude's project memory (`launica-webradio`), not here.
