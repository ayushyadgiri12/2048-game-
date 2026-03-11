# 2048 Clone with Leaderboard System

> A fully browser-based 2048 puzzle game with real-time score tracking, a persistent leaderboard, and a community strategy forum — built with pure HTML5, CSS3, and vanilla JavaScript. No frameworks. No backend. No install.

---

## Live Preview

Open `index.html` directly in any modern browser — that's it.

```
2048/
└── index.html   ← everything is in this single file
```

---

## Features

| Feature | Description |
|---|---|
| 🎮 **2048 Game** | Classic 4×4 grid with tile merging logic |
| ⌨️ **Keyboard Controls** | Arrow keys to slide tiles |
| 👆 **Touch / Swipe** | Full swipe support for mobile |
| 📊 **Score Tracker** | Live score + all-time best score |
| 🏆 **Leaderboard** | Ranked table of saved scores, sorted by highest |
| 💬 **Strategy Forum** | Post and read strategy comments |
| 💾 **Persistence** | All data saved to `localStorage` — survives page refresh |
| 📱 **Responsive** | Playable on desktop and mobile browsers |

---

## How to Play

1. Open `index.html` in your browser.
2. Click **Play Now** on the Home screen.
3. Use **Arrow Keys** (desktop) or **Swipe** (mobile) to slide all tiles.
4. Tiles with the same number **merge** when they collide — their sum becomes the new tile.
5. After every move, a new **2** (90% chance) or **4** (10% chance) appears on a random empty cell.
6. **Goal:** Create a tile with the value **2048**.
7. The game ends when no moves remain.

### Scoring
- Every merge adds the **merged tile's value** to your score.
- Your all-time **Best** score is saved automatically.
- Click **Save Score** anytime to submit your score to the leaderboard.

---

## Tile Color Reference

| Tile | Color |
|---|---|
| 2 | Beige `#eee4da` |
| 4 | Wheat `#ede0c8` |
| 8 | Orange `#f2b179` |
| 16 | Deep Orange `#f59563` |
| 32 | Coral `#f67c5f` |
| 64 | Red-Orange `#f65e3b` |
| 128 – 512 | Gold shades `#edcf72` → `#edc850` |
| 1024 – 2048 | Bright Gold `#edc53f` → `#edc22e` |

---

## Sections

### 🏠 Home
Landing page with a **Play Now** button. Navigate between sections using the top nav bar.

### 🎮 Play
The main game board. Controls:

```
New Game     → Resets the board and score
Save Score   → Opens a dialog to save your current score with a name
```

Overlays appear automatically on **Win** (tile reaches 2048) and **Game Over** (no moves left), both offering options to save, continue, or restart.

### 🏆 Leaderboard
Displays all saved scores sorted from highest to lowest, with medal icons for the top 3. Includes **Refresh** and **Clear All** buttons.

### 💬 Strategy Forum
Post text comments with your name. All comments are stored locally and shown in reverse-chronological order. Great for sharing tips and high-score strategies.

---

## Tech Stack

```
HTML5       Semantic layout, CSS Grid game board, data attributes for tile values
CSS3        Grid layout, custom properties for tile colors, CSS transitions for animation
JavaScript  Vanilla ES5/ES6 — DOM manipulation, event listeners, localStorage API
Storage     Browser localStorage (no server, no database)
Design      Inspired by Gabriele Cirulli's original 2048 — minimal, warm color palette
```

---

## File Structure

```
index.html          Single-file application
├── <style>         All CSS — layout, tile colors, animations, overlays, responsive rules
└── <script>
    ├── Navigation  showSection() — SPA-style section switching
    ├── Game Logic  initGame(), move(), slideRow(), addRandomTile()
    ├── Detection   checkState() — win (2048 tile) and game-over detection
    ├── Events      keydown (arrow keys), touchstart/touchend (swipe)
    ├── Leaderboard saveScore(), renderLeaderboard() — localStorage JSON array
    └── Forum       btn-post, renderComments() — localStorage JSON array
```

---

## Game Logic Overview

```
moveLeft(row)
  1. Filter out zeros            [2, 0, 2, 4]  →  [2, 2, 4]
  2. Merge adjacent equal pairs  [2, 2, 4]     →  [4, 4]   (score += 4)
  3. Pad with zeros to length 4  [4, 4]        →  [4, 4, 0, 0]

moveRight  →  reverse row → moveLeft → reverse back
moveUp     →  operate on columns like rows
moveDown   →  reverse column → moveLeft → reverse back
```

**Win condition:** Any cell value equals `2048`.  
**Game-over condition:** No empty cells AND no adjacent equal tiles in any direction.

---

## localStorage Keys

| Key | Type | Contents |
|---|---|---|
| `2048-best` | `string` | All-time best score (integer) |
| `2048-scores` | `JSON array` | `[{ name, score, date }, ...]` |
| `2048-forum` | `JSON array` | `[{ name, text, time }, ...]` |

---

## Browser Support

Works in all modern browsers with no dependencies.

| Browser | Support |
|---|---|
| Chrome | ✅ |
| Firefox | ✅ |
| Safari | ✅ |
| Edge | ✅ |
| Mobile (iOS/Android) | ✅ (swipe enabled) |

---

## Future Enhancements

- [ ] Backend (Node.js + database) for a global leaderboard
- [ ] User authentication and personal profiles
- [ ] Undo / redo move functionality
- [ ] Timed challenge mode
- [ ] 5×5 and 6×6 grid variants (premium modes)
- [ ] PWA wrapper for offline play and mobile installation

---

## References

- Cirulli, G. (2014). *2048* — Original game. [github.com/gabrielecirulli/2048](https://github.com/gabrielecirulli/2048)
- MDN Web Docs — HTML5, CSS Grid, Web Storage API. [developer.mozilla.org](https://developer.mozilla.org)
- W3Schools — DOM manipulation & event listeners. [w3schools.com](https://www.w3schools.com)
- ECMA International (2022). *ECMAScript 2022 Language Specification (ES13)*.

---

## Author

**Ayush Prakash Yadgiri** · `150096725098`  
School of Future Tech · ITM Skills University

---

*"Merge tiles. Reach 2048. Beat the leaderboard."*
