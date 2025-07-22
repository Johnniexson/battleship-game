# Battleship Game – Documentation

This web-based Battleship game lets the user play against a randomly initialized grid of battleships and destroyers. The player inputs coordinates to try and sink all ships.

---

## 📁 Table of Contents

1. [Overview](#overview)
2. [Game Rules](#game-rules)
3. [File Structure](#file-structure)
4. [Grid Structure](#grid-structure)
5. [Ship Types](#ship-types)
6. [Functions](#functions)
   - `init()`
   - `play()`
   - `setShip()`
   - `placeShip()`
   - `selectRandomPoint()`
7. [Logging and UI Feedback](#logging-and-ui-feedback)
8. [Game End Conditions](#game-end-conditions)

---

## 📌 Overview

This game simulates a simple Battleship setup using plain HTML and JavaScript. The player clicks "Play" and inputs coordinates (e.g. `A5`) to fire at a hidden grid of ships. The game provides feedback on whether the guess was a **hit** or **miss**, and announces when a ship is **sunk** or when the game is **over**.

---

## 🎯 Game Rules

- The grid is **10x10**, using rows `1–10` and columns `A–J`.
- There are:
  - 1 Battleship (`BS`) — takes 5 hits to sink.
  - 2 Destroyers (`DT`) — take 2 hits each to sink.
- A ship is randomly placed vertically or horizontally on the grid.
- The player enters coordinates like `B3`, and the game responds with a **Hit**, **Miss**, or **Sunk** message.

---

## 📂 File Structure

- **HTML UI**
  - A centered title and instructions.
  - A `div` (`#logs`) for displaying messages.
  - Two buttons: "Reset" (calls `init()`) and "Play" (calls `play()`).
- **JavaScript**
  - Logic for grid initialization, ship placement, and gameplay.

---

## 🗺️ Grid Structure

```js
grid = {
  A: [null, null, ..., null], // 10 elements (rows 0–9)
  B: [...],
  ...
  J: [...]
}
```

Each column is represented as a key in the `grid` object, mapping to an array of 10 rows.

---

## 🚢 Ship Types

| Type       | Code | Size | Count |
| ---------- | ---- | ---- | ----- |
| Battleship | BS   | 5    | 1     |
| Destroyer  | DT   | 2    | 2     |

Each ship is given a unique ID such as `BS-A_13` or `DT-B_47`.

---

## 🧠 Functions

### 🔁 `init()`

Initializes the game:

- Resets the grid and logs.
- Defines valid `rows` (1–10) and `cols` (A–J).
- Randomly places ships using `setShip()`.

### ▶️ `play()`

- Prompts user for a coordinate input.
- Validates bounds and format.
- Checks the grid for a hit or miss.
- Updates hit count and checks for ship destruction.
- Ends the game when all ships are sunk.

### ⚓ `setShip([col, row], type)`

Attempts to place a ship starting from a given coordinate:

- Checks available space in all 4 directions.
- Chooses a direction that fits and places the ship.
- If no valid space, chooses a new coordinate recursively.

### 🧱 `placeShip(orientation, type, key, start, end)`

Places the ship on the grid:

- `V` for vertical placement along rows.
- `H` for horizontal placement across columns.
- Updates `grid` and `hitCounts`.

### 🎯 `selectRandomPoint()`

Returns a random valid coordinate (e.g. `['B', 4]`) that hasn’t been tried before.

---

## 🧾 Logging and UI Feedback

- Logs are displayed in the `#logs` element using `<p>` tags.
- Feedback includes:
  - `Hit`
  - `Miss`
  - `Sunk` (with ship type and ID)
  - `Game Over` when all ships are destroyed.

---

## ❌ Game End Conditions

The game ends when `totalShips === 0`. At that point:

- A final log entry is shown:  
  **"Game Over: All ships have been sunk!!!"**
- The **Play** button is disabled.

---

## 📝 Notes

- `grid[col][row]` values may be:
  - `undefined` (no ship)
  - Ship ID string (e.g. `BS-A_13`)
  - `'X'` (already hit)
- Ships are not rendered on the UI — this is a text-based game.

---

## ✅ To-Do (Optional Improvements)

- Add a visible 10x10 grid to click on instead of text input.
- Highlight previously entered coordinates.
- Add ship animation/sound effects.
- Track number of moves.
- Rewrite ship placement checks as a modular reusable logic.
- Rewrite selectRandomPoint() to avoid recursive calls.

---

## 🧩 Example Coordinate Inputs

| Input | Interpretation                    |
| ----- | --------------------------------- |
| `A1`  | Column A, Row 1                   |
| `D10` | Column D, Row 10                  |
| `j5`  | Automatically capitalized to `J5` |

---

## 🤖 Use of AI

AI tool (**ChatGPT** to be precise) was used **ONLY** to generate the most part of the documentation for this assessment in a clean and well structured manner. No AI tool was used in the development of the game.

#### Signed

Theophilus Johnson

---
