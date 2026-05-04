# RID SENTINEL II

**A tactical sci‑fi tower defense game – pure HTML5 Canvas & vanilla JavaScript.**  
Protect the exit node from relentless waves. Build and upgrade towers directly on the grid; every placement alters the enemy path in real time. Block too much and you lose your route – strategy is everything.

---

## 🎯 Overview

| | |
|---|---|
| **Genre** | Tower Defense with dynamic pathfinding |
| **Platform** | Web browser (Chrome, Firefox, Edge, Safari) |
| **Technology** | HTML5 Canvas, CSS Grid/Flexbox, pure JavaScript – no frameworks, no dependencies |
| **Controls** | Mouse only (click to place / select, hover for preview) |
| **License** | Educational & entertainment |

---

## ✨ Features

- **6 upgradable towers** – each with unique stats and special abilities (pierce, splash, slow, burn)
- **7 enemy types** – from fast scouts to colossal bosses, scaling with wave number
- **Real‑time A\* pathfinding** – enemies recalculate routes whenever the grid changes
- **Strategic blocking** – towers physically block the path; you can't fully seal the exit
- **4 targeting modes** – Closest, Weakest, Furthest, Strongest
- **Speed control** – 1× / 2× / 3× / Pause
- **Visual effects** – particle systems, enemy health bars, slow/freeze indicators
- **Persistent HUD** – gold, lives, score, kills, wave preview and in‑game log
- **Automatic scaling** – canvas resizes with the window

---

## 🚀 How to Run

1. **Download or clone** the repository.
2. Open `index.html` in any modern browser.
3. Click **BOOT SEQUENCE** to start the game.

> No build tools, npm, or server required – runs directly from the file system.

---

## 🎮 Gameplay

### Core Loop
1. Place towers by clicking an empty cell (cost deducted from gold).
2. Towers block enemy movement; the path recalculates instantly.
3. Enemies follow the shortest route to the exit using A\* pathfinding.
4. If a tower would make the map unsolvable, placement is refused.
5. Defeat enemies to earn gold and score, survive waves, and upgrade your arsenal.

### Economy
- Start with **200 gold** and **20 lives**.
- Earn gold per kill plus a wave‑clear bonus: `30 + wave × 50`.
- Spend gold on towers, upgrades, and optionally sell towers for **60%** of total investment.

### Tower Reference

| Tower    | Cost | Special          | Description                                      |
|----------|------|------------------|--------------------------------------------------|
| Sentinel | 60   | –                | Balanced, all‑rounder                            |
| Railgun  | 120  | **Pierce**       | Shots pass through all enemies in a line         |
| Burst    | 80   | –                | Extremely rapid fire                             |
| Cryo     | 90   | **Slow 50%**     | Slows enemies for 2 seconds                      |
| Cannon   | 150  | **Splash**       | Deals area damage on impact                      |
| Laser    | 200  | **Burn**         | Applies damage‑over‑time for 3 seconds           |

- Upgrade levels: **0 → 1 → 2** (max). Upgrades increase damage, range, and fire rate.
- Sell a tower at any time for **60%** of total investment.

### Enemy Types

| Enemy   | HP (base) | Speed | Armor | Special                      |
|---------|-----------|-------|-------|------------------------------|
| Scout   | 80        | 110   | 0     | –                            |
| Grunt   | 200       | 75    | 0     | –                            |
| Speeder | 120       | 180   | 0     | Very fast                    |
| Tank    | 600       | 45    | 2     | High armor                   |
| Healer  | 250       | 60    | 0     | Heals nearby allies          |
| Elite   | 400       | 90    | 3     | Tough hybrid                 |
| Boss    | 2000      | 40    | 5     | Appears every 5 waves        |

Enemy health scales by **+8% per wave**.

---

## 🧠 Technical Insights

### A\* Pathfinding
- Custom implementation with a **binary heap** (MinHeap) for the open set.
- **Manhattan distance** heuristic ensures fast, optimal path calculation.
- Every `placeTower()` or `sellSelected()` triggers a full repath; performance remains solid up to ~100 enemies.

### Rendering
- `requestAnimationFrame` loop with delta‑time driven game speed.
- **Projectiles** are pooled for minimal garbage collection overhead.
- **Particles** are recycled; no external rendering libraries used.

### State Management
All game objects are stored as plain arrays:

- `towers[]` – position, type, level, cooldown, kills
- `enemies[]` – position, health, path index, status effects
- `projectiles[]` – trajectory, target reference, special flags
- `particles[]` – position, velocity, lifetime

---

## 📁 File Structure

- **`index.html`** – The complete game source: HTML structure, CSS styles, and all JavaScript logic in a single, portable file.
- **`README.md`** – Project documentation and instructions.

---

## 🎨 Customization

You can easily tweak the game by editing the constants at the top of the `<script>` block:

| Constant  | Description                     |
|-----------|---------------------------------|
| `COLS`    | Grid columns                    |
| `ROWS`    | Grid rows                       |
| `CELL`    | Tile size                       |
| `SR, SC`  | Start coordinates               |
| `ER, EC`  | Exit coordinates                |
| `TDEFS`   | Tower stats and abilities       |
| `EDEFS`   | Enemy stats                     |
| `gold`    | Starting gold                   |
| `lives`   | Starting lives                  |

---

## 🔮 Future Ideas

- Sound effects and background music (Web Audio API)
- More tower levels or upgrade branches
- Additional enemy abilities (shield, speed aura)
- Save / load system using LocalStorage
- Mobile touch support
- Map editor

---

## 👤 Author

**Rahul Raj Singh**  
- GitHub: [https://github.com/rahulrajsinghwork15072005-a11y](https://github.com/rahulrajsinghwork15072005-a11y)  
- LinkedIn: [https://www.linkedin.com/in/rahul-raj-singh-57442a3b3/](https://www.linkedin.com/in/rahul-raj-singh-57442a3b3/)  
- Email: rahulrajsingh.work.15072005@gmail.com

---

## 🧾 License

This project is provided for educational and entertainment purposes.  
Feel free to modify and share it. No warranty.

**Stay sharp, commander – the grid won’t defend itself.**
