# Simon Says Game

A browser-based recreation of the classic **Simon** memory game, built with vanilla HTML, CSS, and JavaScript. The game generates a random sequence of colored button flashes that grows each round, and the player must repeat it correctly to advance.

## 🚀 Features

- Press any key to start the game
- Randomly generated, ever-growing color sequence each level
- Visual "flash" feedback when the game plays a sequence
- Visual "flash" feedback when the player presses a button
- Level counter displayed in real time (`Level 1`, `Level 2`, ...)
- Game over screen showing final score, with a red screen-flash on failure
- Instant reset — press any key after losing to play again

## 🛠️ Built With

- **HTML5**
- **CSS3** (Flexbox layout, circular buttons via `border-radius`)
- **Vanilla JavaScript** (DOM events, `setTimeout`, no libraries or frameworks)

## 📁 Project Structure

```
simon-says-game/
├── index.html      # Game markup (4 color buttons)
├── simon.css       # Button styling & flash states
├── simon.js        # Game logic
└── README.md
```

## ⚙️ How It Works

1. **Start** — Any keypress sets `started = true` and calls `levelUp()`.
2. **Level up** — `levelUp()` increments the level, updates the `<h2>`, picks a random color from `btns`, pushes it onto `gameSeq`, and flashes that button (`gameFlash`).
3. **Player's turn** — Clicking a button triggers `btnPress()`, which flashes it (`userFlash`), records the color in `userSeq`, and calls `checkAns()`.
4. **Checking answers** — `checkAns()` compares the player's latest press against the game sequence at the same index:
   - If it matches and the player has completed the full sequence, `levelUp()` is called again after a short delay to continue.
   - If it doesn't match, the game shows a "Game Over" message with the final score, flashes the screen red, and resets.
5. **Reset** — `reset()` clears `started`, `gameSeq`, `userSeq`, and `level`, returning the game to its initial state.

## ▶️ Getting Started

1. Clone or download this project.
2. Open `index.html` in any modern browser.
3. Press any key to start, then repeat the flashing color sequence by clicking the buttons.

```bash
git clone <your-repo-url>
cd simon-says-game
open index.html   # or just double-click the file
```

## 🔧 Customization

| What to change            | Where                                      |
|------------------------------|-----------------------------------------------|
| Button colors                | `.yellow`, `.red`, `.green`, `.purple` in `simon.css` |
| Flash duration                | `setTimeout(..., 250)` in `gameFlash` / `userFlash` in `simon.js` |
| Delay before next round     | `setTimeout(levelUp, 1000)` in `checkAns`   |
| Game-over flash duration    | `setTimeout(..., 150)` in `checkAns`         |
| Button size/shape            | `.btn { height, width, border-radius }` in `simon.css` |

## 🐞 Known Issues / To-Do

- No sound effects — classic Simon relies heavily on audio cues per color.
- No difficulty scaling (e.g., speeding up flashes at higher levels).
- No visible "best score" / high score tracking across sessions (e.g., via `localStorage`).
- Relies on `id` attributes matching color names exactly (`id="red"`, `id="yellow"`, etc.) — fragile if buttons are ever renamed or reordered without updating the JS.
- No keyboard-based gameplay (only mouse/touch clicks are handled once the game starts).

## 📄 License

This project is open source and available for learning purposes.
