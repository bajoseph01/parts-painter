# Parts Painter

Parts Painter is a single-page classroom app for teaching parts of speech on a smartboard or learner iPads. Learners read a passage, turn the passage into tappable word tiles, and paint each word according to its grammatical job.

The current build uses the supplied notebook artwork as the real background image:

`assets/background.png`

The live app layer sits inside the central writing space and dynamically fits reading text or word tiles to the available area.

## Deployment Status

Ready for GitHub Pages as a static site. No build step is required.

Live site:

`https://bajoseph01.github.io/parts-painter/`

Recommended GitHub Pages settings:

- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/ (root)`

For learner iPads, share the live GitHub Pages URL and ask learners to use landscape orientation. The app now opens in learner-safe Free Paint mode, not with the answer memo showing.

## Files

- `index.html` - complete self-contained HTML/CSS/JavaScript app.
- `assets/background.png` - visual background artwork.
- `.nojekyll` - tells GitHub Pages to serve the static files directly.
- `README.md` - current app notes.
- `HANDOFF.md` - structured next-session handoff.
- `CONTINUATION_PROMPT.md` - ready-to-paste prompt for a fresh Codex session.

## Current Features

- Full-screen landscape notebook/anchor-chart design.
- Real PNG background, no SVG background reconstruction.
- Touch-friendly Tools button for opening the teacher tray on iPads.
- Hover/focus teacher tray still works on desktop and smartboards.
- Passage dropdown with:
  - original demo text
  - 3 Grade 4 South African English texts
  - 3 Grade 6 South African English texts
  - 3 Grade 9 South African English texts
  - custom pasted text option
- Custom textbox pathway remains available.
- Dynamic autofit:
  - reading text scales up/down to fill the central writing space
  - word tiles scale up/down to avoid overflow
- Part-of-speech hotspots over the background labels.
- Free Paint mode.
- Teach Mode:
  - click a word to reveal its correct colour
  - double-click the word to reveal all words with the same part of speech
- Eraser mode.
- Guided Check mode.
- Show Memo toggle:
  - first click reveals memo colouring
  - second click hides memo colouring and returns to plain word tiles
- Print button:
  - prints the current visible mode/state only
  - hides teacher controls, hotspots, mixer, hint, drawer, and toast

## Colour System

| Part of speech | Colour |
| --- | --- |
| Noun | Black |
| Verb | Red |
| Adjective | Blue |
| Adverb | Orange |
| Preposition | Green |
| Pronoun | Pink |
| Conjunction | Purple |
| Interjection | Teal/turquoise |
| Article | Light grey dotted |

## Passage Bank

The passage bank lives inside `TEXT_BANK` in `index.html`.

Each bank passage is stored with a local teacher-approved POS key using this compact format:

```js
words: tagged(`
  The|article small|adjective taxi|noun stopped|verb near|preposition the|article school|adjective gate.|noun
`)
```

Keyed bank passages support:

- Show Memo
- Guided Check
- Teach Mode
- Print in any current state

Custom pasted text supports:

- Add Text
- Block Words
- Free Paint
- Eraser
- Print

Custom pasted text does not support Memo, Guided Check, or Teach Mode until an answer key is added.

## Modes

### Free Paint

Choose a part of speech by tapping a label on the background. Then tap any word tile to paint it with the selected colour.

### Teach Mode

For keyed passages only:

- single-click a tile to reveal that word's correct POS colour
- double-click the tile to reveal every word with the same POS

This is designed for live teacher modelling and discussion.

### Eraser

Tap any painted tile to clear it back to plain/unpainted.

### Guided Check

For keyed passages only:

- correct choices stick
- incorrect choices shake
- a short hint appears

### Show Memo

Toggles the memo:

- click once to reveal all correct colours
- click again to hide the memo and return to plain word tiles

### Print

Prints whatever state is currently visible. The teacher tray and helper UI are hidden in print media.

## Dynamic Fit Notes

The app uses JavaScript fitting functions:

- `fitReadingText()`
- `fitTiles()`
- `applyTileScale()`

These run after passage changes, blocking words, memo reveal, print, and window resize.

The fitter has deliberately high ceilings so short passages grow large enough for a classroom board, while longer passages shrink to avoid overflow.

## Verification Commands

From this project folder:

```powershell
node "$env:USERPROFILE\.codex\tools\visual-check-runtime\run-visual-check.mjs" --project-root "." --page "index.html" --width 1180 --height 820 --out "screenshots/parts-painter-ipad-landscape.png" --full-page
```

Recent working screenshots:

- `screenshots/parts-painter-ipad-landscape.png`
- `screenshots/parts-painter-ipad-portrait.png`

## Deferred Ideas

Do not add these until the classroom board workflow feels finished:

- accounts
- saved activity library
- teacher dashboard
- AI auto-tagging
- learner accounts
- marks book
- full assessment/test mode
- manual answer-key editor UI
- exports beyond browser print
