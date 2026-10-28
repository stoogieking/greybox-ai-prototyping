# 05 · Full asset list

When the greybox plays well, find out exactly what art and sound it needs. This turns "make the art" into a list you can estimate and tick off.

---

```
Attached is [PROTOTYPE NAME], a greybox prototype. Read the code and list EVERY placeholder the game actually uses that a human artist or sound designer would replace. Group them:

1. Characters and models: each part, its current size, and its pivot point
2. Animations: every pose or animation state the code drives
3. Effects: particles, trails, flashes, impact frames
4. UI: HUD elements, icons, menus, fonts
5. Text art: every on-screen word that's drawn as an effect
6. Dialogue: portraits and panel frames
7. Audio: every sound the code synthesises, and what triggers it

Output one markdown table with these columns:
# | Asset | Type | Where in the code | In-game size | Suggested source size | Priority (must / nice) | Status | Made by | Notes

Set every Status to "placeholder". Don't invent assets the code doesn't use.
```

Status goes `placeholder` → `draft` → `in progress` → `final` → `checked`. Mark a row `checked` only after you've played the scene with the new asset in. Note anything AI-generated in **Notes**, so you can disclose it where a store asks.
