# LeonLink Game Build SOP
**Standard Operating Procedure: how every LeonLink game is built, audited, shipped and handed to testers**
Status: ENFORCED, LeonLink-wide | Owner: Leon Tucker | Version 1.0 (Oct 2026)
Source: direct instructions from Leon Tucker while building *Ashes of the Ninth Bell* and *NEON CRYPT*.

The words **MUST**, **MUST NOT** and **SHOULD** are binding. A build that breaks a MUST is not done.

---

## 1. Core principles
1. **Finish what you start.** A game MUST be fully completed (all chapters/levels, an ending, a win state). No half-built handoffs.
2. **Leon decides.** Leon approves direction, scope and what ships. When an instruction is ambiguous, the builder states its interpretation in the report and asks Leon to correct it.
3. **Keep what works.** New modes or features MUST NOT replace a working version unless Leon says so. Add alongside it (e.g. "Walk For Me" was added as a second mode; normal steering stayed the default).
4. **Mobile matters.** Every game MUST be playable on a phone without a keyboard and mouse.
5. **Honesty.** The builder MUST say what it tested and what it could not (e.g. "code runs without errors, but I couldn't play, watch or hear it").

## 2. Project setup
1. One GitHub repo per game under **leonptucker3886-lab**, named after the game (e.g. `neon-crypt`).
2. The game is a **single self-contained `index.html`** (HTML, CSS, JS inline; sound generated in code). No external asset dependencies.
3. Extending an existing game: add new chapters/content as layered additions (monkey-patches) on top of existing code instead of rewriting what works.
4. Look and feel MUST match the LeonLink house style (reference: *Arcadeline* and *Knockout Queens* on leonlink.net): neon, arcade, bold glow typography.

## 3. Mandatory opening sequence (every LeonLink game)
1. **Full screen, on black, first.** The LeonLink logo and words fill the whole screen before anything else. No scores or menus visible yet.
2. **"LEONLINK PRESENTS..."** fades in.
3. **The LeonLink anchor logo spins for 5 seconds.**
4. **"ARCADELINE"** glows in under the logo, with **"EPIC"** below it.
5. The logo fades; the **game title flashes in** with the game's theme music/stinger (for NEON CRYPT: blood-red title, creepy clown music).
6. The game's title character/screen appears (NEON CRYPT: the scary clown). After the intro the game **starts fresh**.
7. **The start target MUST work with mouse AND touch.** Clicking/tapping the start character or buttons MUST start the game. Touch controls MUST NOT swallow taps on menus (intro, pause, death, level-clear).

## 4. Story and theme
1. Every game SHOULD open with a **story cutscene** that sets the stakes (NEON CRYPT: you're trapped in SunNFun park; "get out... or die with the clowns"). Cutscenes MUST be skippable by tap/click.
2. **Enemies MUST be themed variations,** not one generic type: distinct looks AND distinct behaviours (e.g. juggler clowns throw, balloon clowns spit, strongmen charge).
3. Levels/zones SHOULD carry the theme (named areas, title cards, a themed ending screen).

## 5. Controls and modes
1. Standard mode: classic controls (keyboard + mouse on desktop, on-screen controls on mobile).
2. Where steering is hard on mobile, provide an **assisted mode** (pattern: "Walk For Me") as a separate, selectable option:
   - auto-walk forward, auto-turn toward enemies and along corridors, so no mouse is needed;
   - faster movement;
   - **harder, longer, more tactical combat** to balance the assist (tougher enemies, strafing, ranged enemies that keep distance and lead their shots);
   - a stop/hold control to fight from cover.
3. Mode buttons MUST be clearly labelled with the trade-off (e.g. "WALK FOR ME (FAST & TACTICAL)").

## 6. The 3-Audit Rule (mandatory before testing)
After features are complete, the builder MUST run **three audit passes**. **Each pass MUST improve all three of:**
| Area | Examples |
|---|---|
| **Graphics** | effects, readability of enemies, screen grain/flicker, title cards, lighting |
| **UI** | menus, buttons, HUD, feedback (low-health warnings), touch targets |
| **Sound** | music layers, enemy voices/death sounds, stingers, heartbeat, mixing |

Rules:
- A pass that improves only one or two areas does not count.
- Each pass is logged (what changed in graphics, UI and sound) in the delivery report.
- After pass 3, the code MUST run with no errors before handoff.

## 7. Ship every change
1. Every change MUST be **committed and pushed to GitHub**, and the commit link shared.
2. Every change MUST be **deployed to Vercel production** (account: leonptucker3886-lab's projects) and the live link shared.
3. The live link MUST be **public** (no login wall).
4. If auto-deploy from GitHub isn't connected, the builder redeploys manually on each change and tells Leon.

## 8. Reporting to Leon
Every delivery report MUST include:
- live link + commit link;
- what changed, in plain language, step by step how it now plays;
- how each ambiguous instruction was interpreted;
- what was verified and what could not be (and what testers should check).

## 9. Tester handoff (end of build phase)
When the builder is sure the game is ready, it MUST tell Leon "ready for testing." The builder then moves to the next project and **testers take over**. Before that, the repo MUST contain in `docs/`:
1. **Tester tech sheet** (Markdown preferred): play link, repo, how it's built, hosting, supported devices, modes, game flow, enemies, controls, what to test first (priority order), known issues, how to report bugs.
2. **Tester SOP**: strict, based on peer-reviewed research and industry standards (ISTQB, ISO/IEC/IEEE 29119, ISO/IEC 25010, IEEE 1044, WCAG, platform guidelines), written for **AI testers first** (only report what was actually observed; mark claims seen/inferred/opinion; flag NEEDS HUMAN items; second-tester reproduction of serious bugs).
3. **Job position framing**: title, mission, duties, skills, authority limits (testers recommend; they do not change code/deployments or close their own issues; Leon decides what ships).
4. **Combined handbook** named **"<GameName> Phase 2"** containing all of the above, delivered as **both `.md` and `.pdf`**.

## 10. Definition of Done (checklist)
- [ ] Game complete with ending
- [ ] Single `index.html`, LeonLink house style
- [ ] Full opening sequence (Section 3), start works on touch
- [ ] Story cutscene, skippable; themed enemy variations
- [ ] Mobile playable; assisted mode if steering is hard
- [ ] 3 audit passes, each improving graphics + UI + sound
- [ ] Pushed to GitHub, deployed public on Vercel, links shared
- [ ] Docs: tech sheet, tester SOP, job framing, Phase 2 handbook (.md + .pdf)
- [ ] Leon told "ready for testing"

---

## 11. Game Designer Checklist (game design phase)
Complete every box before declaring a build "ready for testing". Any unchecked MUST item blocks handoff.

### A. Concept & design doc
- [ ] Game title, genre, theme/setting and win/lose conditions written down
- [ ] Core loop defined (what the player does every 30 seconds)
- [ ] Target platforms confirmed: desktop AND mobile/touch
- [ ] Visual style matches Arcadeline / Knockout Queens (neon, arcade, LeonLink brand)
- [ ] Leon's unclear instructions listed with the interpretation chosen

### B. Repo & structure
- [ ] One GitHub repo per game under leonptucker3886-lab
- [ ] Single self-contained index.html (no external asset dependencies)
- [ ] New features/chapters layered on top; working versions are never removed

### C. Opening sequence
- [ ] Full-screen black, "LEONLINK PRESENTS..."
- [ ] LeonLink anchor logo spins 5 seconds
- [ ] "ARCADELINE" with "EPIC" beneath
- [ ] Game title flashes in with themed music + stinger
- [ ] Title character / start screen appears; game starts fresh
- [ ] Tap/click to start verified on touch AND mouse

### D. Story, enemies, levels
- [ ] Skippable story cutscene stating setting, goal and threat
- [ ] At least 3 enemy variations, each distinct in look AND behaviour
- [ ] Named zones/levels with title cards
- [ ] Clear ending/escape screen and death screen

### E. Controls & modes
- [ ] Normal (manual steer) mode is the default
- [ ] Mobile-friendly assisted mode (e.g. Walk For Me) offered as an option
- [ ] Assisted mode balanced: faster, longer/tactical fights, harder combat
- [ ] Touch controls never block menu/button taps
- [ ] Keyboard + mouse controls documented

### F. Graphics, UI, sound
- [ ] Readable HUD (health, ammo, score, zone)
- [ ] Low-health feedback (visual + audio)
- [ ] Music and SFX for: intro, combat, enemy alert, enemy death, damage, win/lose
- [ ] Audio unlocks on first tap (browser autoplay rules handled)
- [ ] No flashing faster than 3 times per second (WCAG 2.2)
- [ ] Touch targets ≥ 44×44 pt (Apple) / 48×48 dp (Google)

### G. 3-Audit Rule
- [ ] Audit 1 done — graphics, UI AND sound each improved (logged)
- [ ] Audit 2 done — graphics, UI AND sound each improved (logged)
- [ ] Audit 3 done — graphics, UI AND sound each improved (logged)
- [ ] Code runs with zero console errors after each audit

### H. Ship & hand off
- [ ] Every change committed and pushed to GitHub
- [ ] Deployed to a public Vercel link (login wall off)
- [ ] Report to Leon: links, how it plays, interpretations, what was/wasn't verified
- [ ] Tech sheet + tester focus list written
- [ ] "<Game> Phase 2" handbook (tech sheet + tester SOP + job description) in .md AND .pdf in /docs
- [ ] Leon told "ready for testing"; designer moves to next project

---

## 12. Game Tester Checklist (AI and human testers)
Follow the game's Phase 2 handbook. Any unchecked MUST item invalidates the session report.

### A. Before the session
- [ ] Read the Phase 2 handbook and this SOP in full
- [ ] Confirm build: live URL + exact GitHub commit hash recorded
- [ ] Device, OS, browser, screen size and input method recorded
- [ ] Capability statement written (AI testers: what you can and cannot actually observe — e.g. audio, feel, real touch)
- [ ] Session charter chosen from the handbook priority list; timebox set

### B. During the session
- [ ] Only report what was actually run and observed — no fabricated evidence
- [ ] Every claim tagged OBSERVED / INFERRED / OPINION
- [ ] Items you cannot judge marked NEEDS HUMAN (sound balance, scariness, motion comfort, auto-turn feel)
- [ ] Opening sequence: timing, logo spin, text, music, start tap work
- [ ] Cutscene: plays, readable, skippable
- [ ] Both modes start and behave as documented
- [ ] Each enemy type: distinguishable at distance, behaviour matches spec
- [ ] Combat balance: damage, enemy health, fight length recorded with numbers
- [ ] Menus: pause, death, level clear, win screens all work
- [ ] Performance: FPS / stutter noted on mobile
- [ ] Accessibility: flashing ≤ 3/sec, touch target sizes, readable text
- [ ] Console errors captured

### C. Reporting bugs
- [ ] One GitHub Issue per bug, using the handbook template
- [ ] Title, build hash, device, steps to reproduce, expected vs actual, evidence
- [ ] Severity S1–S4 and priority P1–P3 assigned
- [ ] S1/S2 bugs reproduced by a second tester before escalation
- [ ] No code or deployment changes; never close your own issue

### D. End of session
- [ ] Session log completed (charter, time spent, coverage, bugs filed)
- [ ] End-of-session summary: pass/fail per area, risks, NEEDS HUMAN list
- [ ] Release bar checked: no open S1; no S2 in start flow, assisted mode or accessibility
- [ ] Summary sent to Leon; Leon decides what ships
