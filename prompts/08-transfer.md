# 08 · Transfer to a real build

Use this when a prototype has earned a proper rebuild. First sort your sliders, then ask for a spec and a data file.

## 1. Sort the sliders

Open the tuning panel, press **Copy values**, and fill in this table:

| Variable | Default | Range tried | Best value | Group (Keep / Tune / Cut) | Why |
|---|---|---|---|---|---|
| [`hitstop`] | [5] | [2–10] | [ ] | [ ] | [e.g. under 4 felt weightless, over 8 felt sticky] |
| | | | | | |

- **Keep:** found, and it holds up across sessions and players.
- **Tune:** still moving, or depends on content that doesn't exist yet. Record the range that worked.
- **Cut:** never changed how the game felt.

Everything except Cut transfers.

## 2. Ask for the spec and data

Attach the prototype's HTML file, the table and the Copy values JSON.

```
I'm rebuilding [PROTOTYPE NAME] in [ENGINE, e.g. Godot 4]. Attached are the greybox prototype, my slider table and the final values.

Don't port the prototype's code. Instead, produce:

1. A system spec: for each system in the prototype (e.g. movement, attack, enemy AI, juice), list its inputs, states, timings and edge cases, based on what the code actually does. Mark anything the prototype does that I didn't ask for, so I can decide whether to keep it.

2. A data file as [FORMAT, e.g. JSON / a Godot Resource]:
   - KEEP values as fixed defaults
   - TUNE values as defaults with the min/max range I recorded
   - a one-line comment per variable saying what it controls
   - frame counts converted to seconds, with the original frame count in the comment
   Leave out anything marked Cut.

3. A short list of shortcuts in the prototype that the real build must do properly (e.g. collision, saving, input remapping).

Don't write the engine code yet.
```

Then build each system against the spec, one at a time, and compare it side by side with the prototype.
