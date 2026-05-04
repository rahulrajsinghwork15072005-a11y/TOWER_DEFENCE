# GRID SENTINEL II

**A tactical tower defense game – pure HTML5 Canvas & vanilla JavaScript.**  
Protect the exit node from relentless waves. Build and upgrade towers directly on the grid; every placement alters the enemy path in real time. Block too much and you lose your route – strategy is everything.

---

## 🎯 Overview

| | |
|---|---|
| **Genre** | Tower Defense with dynamic pathfinding |
| **Platform** | Web browser (Chrome, Firefox, Edge, Safari) |
| **Technology** | HTML5 Canvas, CSS Grid/Flexbox, pure JavaScript – no frameworks, no dependencies |
| **Controls** | Mouse only (click to place / select, hover for preview) |
| **Difficulty** | Easy / Normal / Hard – selectable before start (affects lives, gold, enemy scaling) |
| **License** | Educational & entertainment |

---

## ✨ Features

- **6 upgradable towers** – each with unique stats and special abilities (pierce, splash, slow, burn)
- **7 enemy types** – from fast scouts to colossal bosses, scaling with wave number
- **3 difficulty levels** – Easy, Normal, Hard that change starting resources and enemy strength
- **Real‑time A\* pathfinding** – enemies recalculate routes whenever the grid changes
- **Strategic blocking** – towers physically block the path; you can't fully seal the exit
- **4 targeting modes** – Closest, Weakest, Furthest, Strongest
- **Speed control** – 1× / 2× / 3× / Pause
- **Visual effects** – particle systems, enemy health bars, slow/freeze indicators, burn effects
- **Wave preview** – see incoming enemy composition before starting a wave
- **In‑game log** – real‑time feed of builds, kills, and events
- **Persistent HUD** – gold, lives, score, kills
- **Automatic scaling** – canvas resizes with the window

---

## 🚀 How to Run

1. **Download or clone** the repository.
2. Open `index.html` in any modern browser.
3. Select a difficulty (Easy / Normal / Hard) and click **START GAME**.

> No build tools, npm, or server required – runs directly from the file system.

---

## 🎮 Gameplay

### Core Loop
1. Choose a tower from the sidebar.
2. Click an empty cell to place it (cost deducted from gold).
3. Towers block enemy movement; the path recalculates immediately.
4. Enemies follow the shortest route to the exit using A\* pathfinding.
5. If a tower would make the map unsolvable, placement is refused.
6. Defeat enemies to earn gold and score, survive waves, and upgrade your arsenal.
7. **Click a tower** to select it, then upgrade or sell it.
8. Press **Start Wave** when ready.

### Economy
- Starting resources depend on difficulty:
  - **Easy**: 30 lives, 350 gold
  - **Normal**: 20 lives, 250 gold
  - **Hard**: 10 lives, 150 gold
- Earn gold per kill plus a wave‑clear bonus (scaled by difficulty multiplier).
- Sell a tower for **60%** of total investment (including upgrades).

### Tower Reference

| Tower    | Cost | Special          | Description                                      |
|----------|------|------------------|--------------------------------------------------|
| Sentinel | 50   | –                | Balanced, all‑rounder                            |
| Railgun  | 100  | **Pierce**       | Shots pass through all enemies in a line         |
| Burst    | 70   | –                | Extremely rapid fire                             |
| Cryo     | 80   | **Slow 55%**     | Slows enemies for ~2.2 seconds                   |
| Cannon   | 130  | **Splash**       | Deals area damage on impact                      |
| Laser    | 180  | **Burn**         | Applies damage‑over‑time for ~3.2 seconds        |

- Upgrade levels: **0 → 1 → 2** (max). Upgrades increase damage, range, and fire rate.
- Target the strongest, weakest, closest, or furthest enemy.

### Enemy Types

| Enemy   | HP (base) | Speed | Armor | Special                      |
|---------|-----------|-------|-------|------------------------------|
| Scout   | 70        | 105   | 0     | –                            |
| Grunt   | 180       | 70    | 0     | –                            |
| Speeder | 110       | 170   | 0     | Very fast                    |
| Tank    | 500       | 42    | 2     | High armor                   |
| Healer  | 220       | 58    | 0     | Heals nearby allies          |
| Elite   | 350       | 85    | 3     | Tough hybrid                 |
| Boss    | 1800      | 38    | 5     | Appears every 5 waves        |

Enemy health scales by **+7% per wave** (modified by difficulty).

---

## 🧠 Technical Insights

### A\* Pathfinding
- Custom implementation with a **binary heap** (MinHeap) for the open set.
- **Manhattan distance** heuristic ensures fast, optimal path calculation.
- Every tower placement or sale triggers a full repath; performance remains solid even with many enemies.

### Rendering
- `requestAnimationFrame` loop with delta‑time driven game speed.
- **Projectiles** are pooled for minimal garbage collection.
- **Particles** are recycled; no external rendering libraries used.

### State Management
All game objects are plain arrays or Maps:

- `towers[]` – position, type, level, cooldown, kills, total damage dealt
- `enemies[]` – position, health, path index, status effects (slow, burn), armor
- `projectiles[]` – trajectory, target reference, special flags (pierce, splash, slow, burn)
- `particles[]` – position, velocity, lifetime
- `grid[]` – 2D array determining walkability (`OPEN`, `TOWER`, `START`, `END`)

### Difficulty Scaling
Selected difficulty modifies:
- Starting lives and gold
- Enemy HP multiplier (0.7/1.0/1.5)
- Enemy speed multiplier (0.85/1.0/1.2)
- Wave clear reward multiplier (1.3/1.0/0.8)

---

## 📁 File Structure

- **`index.html`** – The complete game: HTML structure, CSS styling, and all JavaScript logic in a single portable file.
- **`README.md`** – Documentation.

---

## 🎨 Customization

Tweak the game by editing constants inside the `<script>` block:

| Constant        | Description                     |
|-----------------|---------------------------------|
| `COLS`, `ROWS`  | Grid dimensions (default 26×18) |
| `CELL`           | Tile size (34px)                |
| `SR`, `SC`, `ER`, `EC` | Start and exit coordinates |
| `TDEFS`          | Tower stats (cost, damage per level, range, rate, special) |
| `EDEFS`          | Enemy stats (HP, speed, armor, reward) |
| `DIFF`           | Difficulty preset multipliers    |

---

## 🔮 Future Ideas

- Sound effects and music (Web Audio API)
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

**The grid won’t defend itself – commander, build wisely.**
