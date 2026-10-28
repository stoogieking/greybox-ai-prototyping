# 02 · One change at a time

Most prompts after the first build should look like this: one change, one reason, and a check you'll do when it comes back. If something breaks, you know what caused it.

---

## Change something

```
Attached is the current build of [PROTOTYPE NAME]. Make exactly ONE change:

[e.g. "The heavy punch feels weak. Add 3 more wind-up frames and a stronger camera kick on impact."]

- Expose any new numbers in the TUNING table so they get a slider.
- Don't touch anything else. Don't refactor.
- Output the complete file, then one line saying what changed and which sliders to try.
```

## Report a bug

The more exact you are, the better the fix. Copy the red error from the browser console (F12 → Console in Chrome, Edge and Firefox; Cmd+Option+J in Chrome on a Mac) whenever there is one.

```
Attached is the current build of [PROTOTYPE NAME]. Bug:

WHAT I DID: [e.g. grabbed the lion while it was charging]
WHAT I EXPECTED: [e.g. a grab]
WHAT HAPPENED: [e.g. the player teleported inside the lion]
CONSOLE ERROR: [paste it, or "none"]
HAPPENS: [every time / sometimes / once]

Fix only this bug. Explain the cause in plain words in two sentences before the code, so I can judge whether the fix makes sense.
```

## Fix before you add

If the last change made things worse, don't stack another feature on it:

```
Your last change broke [X]. Go back to the version I'm attaching and try a different approach to [the change]. Tell me what you'll do differently before writing code.
```
