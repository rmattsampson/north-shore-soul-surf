# 🌊 North Shore — Soul Surf

A tiny 16-bit web surf game. No winners, no losers — just you, the lineup, and
good vibes on the North Shore. Homage to the 1987 movie *North Shore*.

Runs 100% offline in a single HTML file. Your high score is saved in your
browser's `localStorage`.

## Play

Open `index.html` in any browser. That's it — no build step, no server, no
install.

```
open index.html        # macOS
xdg-open index.html     # Linux
# or just double-click the file
```

## Controls

| Key | Action |
|-----|--------|
| `← →` / `A D` | Move / trim |
| `↑` / `W` | Paddle out (from the shoreline) |
| `↓` / `S` | Go back to shore / kick out |
| `SPACE` | Drop in on a wave / end your ride |
| `Z` | Cutback |
| `X` | Off-the-lip |
| `Z + X` | Barrel (big combo) |
| `ENTER` | Start / confirm |
| `M` | Mute / unmute |

Touch: tap left/right thirds to move, top of screen to act.

## How it plays

- **Splash** → **Beach** → paddle out → **Lineup** → surf → (hazards) → back to beach.
- **Score** by reading waves. Longer, cleaner rides = more points. Tricks stack a combo multiplier.
- **Photographer** on the beach? Catch a wave while he's shooting for **double points**.
- **Walk the beach** and pick up random stuff (lost slipper, a honu, a cooler).

### The cast & hazards

- **Chandler** — soul surfer on the beach; heals you after a shark run.
- **The Hui** — territorial locals in the lineup. Get too close and they knock you off. Respect the lineup.
- **Laird** — cocky big-wave guy. Snakes your wave and gets in the way, but never hurts you.
- **Shark** — doesn't kill you, just messes you up. Paddle to shore and let Chandler patch you up before you go again.
- **Messy wave** — a closeout will buss you up if you try to drop in on it.
- **Lifeguard buggy** — rolls down the beach now and then.

## Tech

Plain HTML5 `<canvas>` + vanilla JS. All pixel art is drawn in code — no external
assets, no dependencies, no network calls.

## License

MIT — see `LICENSE`.

*Cheehoo! Surf wit' aloha, braddah.* 🤙

## Install as an app / play online (PWA)

The game is a Progressive Web App — it can install to your device and play offline.

### Host it free on GitHub Pages
1. Push this repo to GitHub (you already have it at `github.com/<you>/north-shore-soul-surf`).
2. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pick `main` / `/ (root)`, Save.
3. After a minute it's live at `https://<you>.github.io/north-shore-soul-surf/` — a public link you can send anyone.

### Install it
Open that URL in Chrome/Edge/Safari and use **Install** (the install icon in the address bar, or Share → Add to Home Screen on iOS). It gets its own icon and window and works offline after the first load.

> Note: the install/offline features need `http(s)` (GitHub Pages or any web server). Opening `index.html` straight off disk still plays the game fine — it just won't register the offline service worker.
