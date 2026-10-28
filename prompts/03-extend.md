# 03 · Extend a working build

Use this when the core feels right and you want a bigger step, like Heavy Hands → Heavy Hands II (flight, a laser, a boss). Only use it on a build that already works.

---

```
I'm attaching [PROTOTYPE NAME], a working single-file greybox prototype. Use it as the base. Keep its architecture, game feel, juice, TUNING table, dialogue system and code style, and EXTEND it. Don't rewrite systems that already work unless a change below requires it.

Same rules as the original: one HTML file, no new external files, fixed 60 Hz, hit-stop freezes the simulation not the render, pooled effects, greybox only, 60 fps on a mid-range laptop.

Before the code, list in 8–12 bullets what you changed and why.

## 1. [New system, e.g. Flight]
- Controls: [...]
- Feel: [...]
- Sliders to expose: [...]

## 2. [New system, e.g. Ranged enemy]
- Behaviour: [...]
- Telegraph: [...]
- How the player counters it: [...]

## 3. Level changes
[What stays the same, what opens up]

## 4. Tuning panel
Keep every existing slider. Add: [list]. Add preset buttons: [e.g. NORMAL / HARD / BRUTAL].

## Acceptance checklist
- [ ] The original feel is unchanged or better
- [ ] [Each new system works on its own]
- [ ] [The systems work together]
- [ ] All new values are sliders and persist
- [ ] No console errors
```

**Tip:** if the first answer is too big or buggy, split it. Ask for section 1 only, play it, then section 2.
