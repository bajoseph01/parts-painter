# Session Handoff - Parts Painter Classroom App

## Where it started

The user wanted a new app folder for `Parts Painter`: a single-page HTML/CSS/JS classroom board where Grade 4-7 learners classify words by painting parts of speech. The first generated layout was too generic; the user then clarified that the app should visually match the supplied notebook-style image exactly and use that image as the background.

## Decisions locked + what shipped

- Real image background - `index.html` now uses `assets/background.png` as the full-page visual background instead of recreating the art with CSS/SVG.
- Live central overlay - the app masks the central writing area with a white interactive layer and renders either reading text or word tiles there.
- Dynamic autofit restored - `fitReadingText()`, `fitTiles()`, and `applyTileScale()` resize content so short passages grow and longer passages shrink without overflowing.
- iPad-ready teacher tray - a visible `Tools` button opens the tray on touch devices, while hover/focus still works on desktop and smartboards.
- Learner-safe startup - the app opens in Free Paint mode with plain tiles, not with the answer memo showing.
- Passage bank - dropdown includes the original demo plus 9 keyed South African English texts: 3 Grade 4, 3 Grade 6, 3 Grade 9.
- Custom text retained - `Add Text` opens a textbox; custom text can be read, blocked, free-painted, erased, and printed, but has no memo/check/teach key.
- Modes shipped - Free Paint, Teach Mode, Eraser, Guided Check, Show Memo toggle, Reset, Print.
- Teach Mode shipped - click a keyed word to reveal its correct colour; double-click it to reveal all words with the same part of speech.
- Show Memo toggle shipped - first click reveals memo colours, second click hides memo and returns tiles to plain.
- Print shipped - prints the current visible mode/state only and hides teacher UI in print CSS.

## Key files for next session

- `C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding\Parts Painter\index.html` - main app; read this first.
- `C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding\Parts Painter\assets\background.png` - background artwork required by the app.
- `C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding\Parts Painter\README.md` - current feature and implementation notes.
- `C:\Users\bjoseph\OneDrive - Merrifield Prep & College\2026_Coding\Parts Painter\CONTINUATION_PROMPT.md` - ready-to-paste next-agent prompt.
- Plan file: none
- Memory files touched: none

## Running state

- Background processes: none
- Dev servers / ports: none
- Open worktrees / branches: local git repo may exist after the GitHub Pages prep pass; check `git status` first.

## Verification - how to confirm things still work

- `npm.cmd run visual-check -- --width 1180 --height 820 --out screenshots/parts-painter-ipad-landscape.png --full-page` - captures the iPad landscape view.
- Use Playwright/Chromium or the visible `Tools` button to open the tray and screenshot `screenshots/parts-painter-tools-open.png` - controls should be large, readable, and not overlap the title badly.
- In browser/Playwright: select a bank text, click `Block Words`, then `Show Memo` twice - first click should colour all keyed tiles; second click should clear them.
- In browser/Playwright: click `Teach Mode`, click one keyed tile, then double-click it - first click reveals one correct colour; double-click reveals all words with that same POS.
- In browser/Playwright: click `Print` after changing states - print CSS should hide teacher tray, hotspots, mixer, hint, drawer, and toast while preserving current board content.

## Deferred + open questions

- Deferred: manual answer-key editor for custom texts - intentionally left for a later version.
- Deferred: AI auto-tagging - explicitly out of scope for MVP.
- Deferred: saved library/accounts/dashboard/marks book/full assessment mode - out of scope.
- Open: whether Grade 9 passage POS labels should be reviewed for IEB grammar nuance before classroom use.
- Open: whether the background image should be edited to remove the printed demo tiles behind the white overlay area for cleaner alignment.

## Pick up here

The most likely next action is GitHub remote creation/push if it has not already been completed, followed by a final real-iPad classroom smoke test. Preserve the PNG-background approach and avoid rebuilding the art manually.
