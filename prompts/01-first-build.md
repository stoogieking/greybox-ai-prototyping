Build a browser-based [GENRE AND CAMERA, e.g. third-person melee combat] [SCOPE, e.g. vertical slice] as ONE self-contained HTML file: no build step, no asset files. The only external file allowed is [three.js r128 from cdnjs / nothing: use the 2D canvas]. Everything is greybox: [e.g. boxes, capsules, flat-coloured materials].

## Goal
[One sentence on the game, e.g. "A superhero game with grounded, impactful melee combat."]
This build answers one question: "[THE QUESTION, e.g. Is punching a guy fun?]"
Put the question on the title screen.
Out of scope: [e.g. story, menus, saving, final art], except [e.g. a dialogue placeholder, see below].

## Design pillars (for later; keep the code modular enough to grow)
- [e.g. Melee is the core: heavy, grounded, readable]
- [e.g. Corridor levels with branching paths, not open world]
- [e.g. Final art will be cel-shaded or hand-drawn]

## Technical rules (non-negotiable)
- One HTML file, under [e.g. 2500] lines, with commented section headers.
- Fixed 60 Hz simulation with interpolated rendering. Hit-stop freezes the simulation, not the render loop.
- [e.g. One directional light, no shadow maps, flat shading, no textures.]
- Pool all particles, decals and floating text. No allocations in the per-frame loop.
- Target a steady 60 fps on [e.g. a mid-range laptop with integrated graphics].

## Controls
- [e.g. WASD move, mouse look (pointer lock), Shift sprint, Space dodge]
- [e.g. LMB light attack, hold LMB heavy, RMB block / parry]
- [e.g. E interact / grab]
- [Gamepad support via the Gamepad API? yes / no]
- Camera: [e.g. over-the-shoulder third person, collides with walls, soft lock-on toggled with Q]

## Player movement (feel first)
- [e.g. Acceleration and deceleration curves, not instant velocity. Slight lean into movement.]
- [e.g. Dodge with invincibility frames, short recovery, FOV kick.]
- Input buffering of [e.g. 150] ms. [e.g. Attacks cancel into dodge. Some forgiveness on parry timing.]
- [e.g. Attacks step the player toward the target so hits connect without perfect positioning.]

## Core system (the main focus)
[The mechanic the question is about. Put its timings in a data table at the top of the file.]
- [e.g. Light combo: 3 hits, each with its own wind-up, active and recovery frames]
- [e.g. Heavy attack: chargeable, slower, causes stagger]
- [e.g. Block and parry: a parry opens a counter window]
- [e.g. Grab a staggered enemy, then a context finisher: wall, crate, another enemy]
- [e.g. One weapon pickup with limited durability]

## Enemies or obstacles
[Each type with a colour and size code, and how the player reads and counters it.]
1. [e.g. Grunt: basic, telegraphed swings]
2. [e.g. Brute: slow, heavy, needs a heavy attack or parry to stagger]
3. [e.g. Rusher: fast gap-closer, punishes button mashing]
- [e.g. Token system: only 1–2 enemies attack at once, the rest circle.]
- Telegraphs: [e.g. colour flash plus wind-up pose], so every hit on the player feels fair.
- [e.g. Directional hit reactions with spring-damped procedural animation on a box rig, no keyframes.]
- HUD: [e.g. a thin player health bar, small bars over enemies]. Failure: [e.g. quick restart at the last checkpoint].

## Juice
Make each effect a separate layer with its own on/off toggle and strength slider. Route every [e.g. impact] through one function so all layers fire together.
1. [e.g. Hit-stop: freeze the simulation for 2–8 frames, light < heavy < finisher]
2. [e.g. Impact frames: 1–3 frames of high-contrast black and white with radial speed lines on heavy hits]
3. [e.g. Directional motion blur on punches as a post-process pass, spiking on impact and decaying fast]
4. [e.g. Camera: trauma-based directional shake, FOV punch, slight roll, brief slow motion on finishers]
5. [e.g. Pooled particles: hit sparks, shards, dust on landings]
6. [e.g. Comic sound-effect text with scale pop, jitter and fade]
7. Audio, all synthesised with WebAudio, no files: [e.g. low thump plus noise burst scaled by weight, whoosh on swings, a short low-pass muffle on big hits]
8. Target feedback: [e.g. white flash, squash and stretch, knockback with a spring settle]
9. Player feedback: [e.g. arms lead the hit, body twist, step in, recover]

## Tuning panel
- Put every game-feel number in one TUNING table at the top of the file: key, label, min, max, step, default, group.
- Build the panel from that table automatically: one slider per row, grouped, plus a checkbox per juice layer. Open it with [`]. Pause the game while it's open.
- Save values in localStorage. Add "Reset to defaults" and "Copy values" (copies every value as JSON).
- At minimum, expose: [e.g. hit-stop length, shake, blur, FOV punch, slow-motion scale, time scale, attack damage and speed, enemy aggression].
- Debug buttons: [e.g. spawn enemy].

## Level
[The beats, in order. Delete if the prototype is a single arena.]
1. [e.g. Entry hallway: control hints, one Grunt]
2. [e.g. Arena with crates, a pillar, a wall for finishers and a weapon pickup: 3–4 mixed enemies]
3. [e.g. Two routes to choose from: a direct fight, or a side path that flanks it]
4. [e.g. Final room with a Brute mini-boss, then a results screen: time, hits taken, finishers]
- [e.g. Checkpoints, invisible walls, a brighter doorway showing where to go]

## Dialogue placeholder
[Delete if not needed.]
- [e.g. Comic panels as HTML/CSS over the canvas: thick borders, halftone backgrounds, speech bubbles, typewriter text, click to continue]
- Lines in a data array at the top of the file, placeholder text only, e.g. "HERO: Placeholder line one."
- Triggered at: [e.g. level start, mid-arena, before the mini-boss]. Skippable with [key].

## Visual style
- [e.g. Player in a bright colour, enemies muted, telegraph flashes on top]
- Colour only as gameplay information: [e.g. red = attack coming, yellow = opening]
- [e.g. Optional cheap inverted-hull outline and 2–3 step toon shading, only if it costs nothing]

## Deliverable
Before the code, state the architecture in 6–10 bullets: game loop, input, state machine, data tables, [post-process chain], pooling. Then output ONLY the complete HTML file in one code block. Then one line per slider saying what it does.
It must run by opening the file directly in a modern browser, with no console errors.

## Acceptance checklist
- [ ] Steady 60 fps, no garbage-collection stutters
- [ ] The question can be answered by playing for a few minutes
- [ ] [e.g. A light punch feels crisp; a heavy punch feels devastating]
- [ ] All juice layers fire together on [e.g. impact], and each one can be switched off
- [ ] [One check per core feature, e.g. Parry-to-counter feels rewarding]
- [ ] [e.g. Two distinct routes through the level]
- [ ] Tuning panel works, pauses the game, persists, and Copy values works
