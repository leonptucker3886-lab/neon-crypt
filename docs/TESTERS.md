# NEON CRYPT — Tester Tech Sheet

**Play:** https://neon-crypt-goodbyedawg-7221s-projects.vercel.app
**Repo:** https://github.com/leonptucker3886-lab/neon-crypt

## Tech overview
- One file: `index.html` (HTML5 canvas raycaster, plain JavaScript, no build step).
- Sound is made in code with the Web Audio API. There are no audio files.
- Hosted on Vercel (project `neon-crypt`). Deploys are manual uploads for now. Pushing to GitHub does **not** redeploy yet.
- Targets: current Chrome, Safari, Firefox and Edge on desktop, plus iOS Safari and Android Chrome.
- Best score is saved in the browser's localStorage.

## Game flow
1. Full-screen LeonLink intro: "LEONLINK PRESENTS...", then the anchor logo spins for 5 seconds. "ARCADELINE" and "EPIC" appear under it.
2. "NEON CRYPT" flickers in with the creepy clown music, then the scary clown lunges in.
3. Mode select: click the clown or tap **I'LL STEER** for normal mode. Tap **WALK FOR ME (FAST & TACTICAL)** for auto-walk mode.
4. SunNFun cutscene, typed out line by line. Tap to skip.
5. Three park zones: **SunNFun Midway**, **The Funhouse**, **The Big Top**. Each zone opens with a title card.
6. Ending screen: "YOU ESCAPED SUNNFUN".

## Enemies
| Clown | Look | Attack |
|---|---|---|
| Juggler | Purple, ruffled collar, grin | Throws fireballs |
| Balloon-head | Floating pink head on a string | Spits at you |
| Strongman | Big and red | Charges you |

## Controls
**Keyboard/mouse:** WASD to move, mouse to turn, click to fire, Shift to sprint, Esc to pause, R to STOP/WALK (Walk For Me only).
**Touch:** left thumb moves and steers, the right side turns, FIRE button to shoot, yellow STOP/WALK button.

## Modes
- **I'll Steer (default):** standard balance.
- **Walk For Me:** auto-walks about 60% faster than before. It turns you to face clowns in sight within about 10 tiles and follows corridors at walls. It aims a little for you. Clowns have **1.8x health** and do **+30% damage**. Ranged clowns strafe, keep their distance and aim where you're heading. Strongmen come at you from an angle.

## What to test (priority order)
1. Walk For Me auto-turning on a phone: does it feel natural, too strong or too weak?
2. Difficulty fairness in both modes (1.8x health and +30% damage in Walk For Me).
3. Tapping the clown and the mode buttons reliably starts the game (on both touch and mouse).
4. Can you tell the clown types apart at a distance?
5. Sound balance: music, organ, laughs, honks, heartbeat.
6. Cutscene pacing and skipping it.
7. Low-health effects (red pulse, "THE CLOWNS SMELL BLOOD", heartbeat).
8. Performance and smoothness on phones. Check the pause, "You died" and "Floor cleared" screens.

## Known issues
- Browsers mute sound until the first tap or click, so the intro music may be silent on a fresh load.
- No one has played it by hand yet. It has only been checked by script.
- No auto-deploy from GitHub yet.

## Reporting bugs
Open a GitHub Issue on the repo, or send it to Leon. Include:
- Device, OS and browser, plus the mode (Steer or Walk For Me)
- The zone, the steps to reproduce, what you expected and what happened
- A screenshot or screen recording if possible
- Severity: **Blocker** (can't play), **Major** (feature broken), **Minor** (annoying), **Polish** (cosmetic)
