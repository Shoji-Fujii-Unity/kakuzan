# Kakuzan — Arithmetic × Grid Puzzle

**Kakuzan** is a one-file KenKen/Calcudoku-style puzzle that combines the four basic arithmetic operations with a number grid.

You can use any of `1` through `N` exactly once in every row and column.

## Getting Started

| Device | Instructions |
| --- | --- |
| PC | Double-click `index.html` |
| Android | Copy the file to your device and open it in Chrome. You can also add it to the home screen for a full-screen app-like experience. |
| iPhone | Save the file in the Files app and open it in Safari. From Share, choose “Add to Home Screen.” |
| LAN sharing | On a PC, run `python -m http.server 8000`, then open `http://<PC-IP>:8000/` on your phone |

The app attempts to load libraries and fonts from CDNs on first launch. If you are offline, built-in fallbacks keep the game working:

- Sound: Web Audio API
- Languages: Built-in translations
- Saving: `localStorage`

## Rules

1. Fill the board with `1` through `N`.
2. Use each number exactly once in every row and column.
3. A clue in the upper-left corner of a cage describes the numbers inside it.
   - `7+`: the sum is `7`
   - `12×`: the product is `12`
   - `3-`: the difference between two cells is `3`
   - `2÷`: dividing one cell by the other gives `2`
   - `5`: the single cell contains `5`
4. `+` and `×` cages may contain 3 or 4 cells. `-` and `÷` cages contain exactly 2 cells.
5. Every puzzle has exactly one solution. The generator verifies uniqueness with a solver.

## Features

- 4×4, 5×5, and 6×6 boards
- Stage progression with unlocked stages
- Daily challenge: the same puzzle is generated for all devices on the same date
- Difficulty based on actual puzzle analysis
- Tap input and drag-to-fill
- Pencil notes for possible digits
- Hint and board-check functions
- Undo and pause
- Keyboard controls
- Optional sound effects and ambient BGM
- Light and dark themes
- Japanese, English, Chinese, Korean, and Spanish
- Saved records for time, hint count, mistake count, and stars

## Controls

| Action | Control |
| --- | --- |
| Enter a digit | Tap a number button or press `1`–`9` |
| Move the selection | Arrow keys |
| Erase | Backspace, Delete, or Space |
| Toggle notes mode | `N` |
| Use a hint | `H` |
| Check the board | `C` |
| Undo | `U` or `Z` |
| Pause | `Esc` |

On touch devices, press a number button and drag across cells to fill the same digit into multiple cells.

## Star Rating

- 3 stars: no hints and at most 1 mistake
- 2 stars: no hints but more than 1 mistake, or 1–2 hints
- 1 star: 3 or more hints

## Save Data

Save data stays in the browser on the current device. It is not sent to a server.

| Key | Purpose |
| --- | --- |
| `kakuzan.settings.v1` | Settings |
| `kakuzan.progress.v1` | Progress, records, and statistics |
| `kakuzan.game.v2.<size>.<mode>` | In-progress game for a specific size and mode |

Daily puzzle progress does not overwrite unfinished stage progress.

Use **Delete Save Data** in Settings to remove all saved data. If storage is unavailable, the Settings screen displays a warning.

## CDN Libraries

- i18next 23
- localforage 1.10
- Tone.js 14
- Google Fonts (M PLUS Rounded 1c)

## Development

The project uses a single `index.html` file.

Puzzle generation logic is tested by comparing solutions against an independent brute-force solver to ensure each puzzle is unique.
