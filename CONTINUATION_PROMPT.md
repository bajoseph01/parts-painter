# Continuation Prompt

You are continuing work on `Parts Painter`, a self-contained classroom HTML app.

Current branch for Test Mode progression:

`feature/test-mode-progression`

Project root:

`C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding`

Read these files first:

1. `C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding\Parts Painter\README.md`
2. `C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding\Parts Painter\HANDOFF.md`
3. `C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding\Parts Painter\index.html`

Important design direction:

- Use the real PNG background image at `assets/background.png`.
- Do not recreate the background art with SVGs or CSS doodles.
- Keep the live interaction layer inside the central writing space.
- Preserve dynamic autofit for reading text and word tiles.
- Keep teacher controls large and readable. Preserve the small pulsing top-middle pull-down arrow for opening the tray.
- Do not reintroduce hover-open behavior for the teacher tray.
- Keep startup learner-safe: Free Paint mode with plain tiles, not memo reveal.
- Use Playwright screenshot checks before finalising visual changes.

Current app features:

- passage dropdown: original demo plus 9 keyed SA English texts
- level-gated passage access: Demo + Grade 4 first, then Grade 6 and Grade 9 unlock via Test Mode full marks
- custom pasted text textbox
- Free Paint
- Teach Mode
- Eraser
- Guided Check
- Test Mode with floating Submit Test and local `partsPainterProgressV1` progress
- Show Memo toggle
- Print current mode/state
- dynamic text/tile fitting

Next likely work:

1. Check `git status`.
2. Run iPad landscape and portrait visual checks.
3. Use the visible pull-down arrow and capture a controls-open screenshot.
4. Re-run the Test Mode progression check before merging: Demo + Grade 4 only at first, wrong Grade 4 test does not unlock, full marks Grade 4 unlocks Grade 6, full marks Grade 6 unlocks Grade 9.
5. If adding features, keep them teacher-board simple and avoid accounts, dashboards, AI tagging, marks, or a full assessment system.

Useful command:

```powershell
npm.cmd run visual-check -- --width 1180 --height 820 --out screenshots/parts-painter-ipad-landscape.png --full-page
```
