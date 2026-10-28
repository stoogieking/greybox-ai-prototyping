# 01 · First build

Use this for the first playable version of a new prototype. Fill in every `[BRACKET]`. If you can't write the one question, you're not ready to prompt.

---

```
Build a greybox prototype as ONE self-contained HTML file.

THE ONE QUESTION THIS PROTOTYPE ANSWERS:
[e.g. "Does this punch feel heavy?" / "Does holding one button to balance a sail feel tense?"]
Put the question on the title screen.

I'LL KNOW THE ANSWER IS YES IF: [e.g. I want to keep playing after 5 minutes]
I'LL KNOW IT'S NO IF: [e.g. it still feels floaty after 20 minutes of tuning]

WHAT THE PLAYER DOES:
[2–5 sentences: the core action, the camera, the controls.]

THE CORE LOOP:
[e.g. Dodge → Grab → Wrestle → Escape → repeat]

RULES:
- One HTML file. No build step, no asset files. The only external file allowed is [three.js r128 from cdnjs / nothing: use the 2D canvas].
- Greybox: simple shapes, flat colours, no textures, no music.
- Juice is in scope: [e.g. hit-stop, screen shake, flashes, synthesised sounds]. Route it through one function so every event gets the same feedback.
- Colour only as gameplay information: [e.g. red = attack coming, yellow = opening].
- Fixed 60 Hz simulation with interpolated rendering. If there's hit-stop, it freezes the simulation, not the render loop.
- Pool particles and text. No allocations in the per-frame loop.
- Every game-feel number goes in one TUNING table at the top of the file: key, label, min, max, step, default, group.
- Build a tuning panel from that table automatically: one slider per row, grouped, opened with the [`] key. Pause the game while it's open. Save values in localStorage. Add "Reset to defaults" and "Copy values" (copies every value as JSON).
- At minimum, expose: [e.g. hit-stop, knockback, shake, move speed, jump height, telegraph length].
- Target 60 fps on a mid-range laptop.

OUT OF SCOPE:
[e.g. story, menus, saving, art, more than one level]

TIME BOX: [e.g. one evening]

DELIVERABLE:
Before the code, list the architecture in 6–10 bullets. Then the complete HTML file. Then one line per slider saying what it does.

ACCEPTANCE CHECKLIST:
- [ ] Opens by double-clicking the file, no console errors
- [ ] The question can be answered by playing for 2 minutes
- [ ] Every number I'd want to tweak is a slider
- [ ] [Your own checks]
```
