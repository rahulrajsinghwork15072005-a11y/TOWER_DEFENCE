# GRID SENTINEL II

**A tactical sci‑fi tower defense game – pure HTML5 Canvas & vanilla JavaScript.**  

Protect the exit node from relentless waves. Build and upgrade towers directly on the grid; every placement alters the enemy path in real time. Block too much and you lose your route – strategy is everything.

![Game Screenshot](screenshot.png) <!-- replace with actual screenshot if available -->

---

## 🎯 Overview

- **Genre**: Tower defense with dynamic pathfinding  
- **Platform**: Web browser (Chrome, Firefox, Edge, Safari)  
- **Tech**: HTML5 Canvas, CSS Grid/Flexbox, JavaScript – no frameworks, no dependencies  
- **Controls**: Mouse only (click to place/select, hover for preview)

---

## ✨ Features

- **6 upgradable towers** – each with unique stats and special abilities (pierce, splash, slow, burn)  
- **7 enemy types** – from fast scouts to colossal bosses, scaling with wave number  
- **Real‑time A\* pathfinding** – enemies recalculate routes whenever the grid changes  
- **Strategic blocking** – towers physically block the path; you can't fully seal the exit  
- **4 targeting modes** – Closest, Weakest, Furthest, Strongest  
- **Speed control** – 1× / 2× / 3× / Pause  
- **Particle effects**, enemy health bars, slow/freeze indicators  
- **In‑game log**, wave preview, and persistent HUD (gold, lives, score, kills)  
- **Automatic scaling** – canvas resizes with the window

---

## 🚀 How to Run

1. Download or clone the repository.
2. Open the `index.html` file (or whatever you named it) in any modern browser.
3. Click **BOOT SEQUENCE** to start.

No build tools, npm, or server required – it runs directly from the file system.

---

## 🎮 Gameplay

### Core Loop

- Place towers by clicking an empty cell (cost deducted from gold).
- Towers block enemy movement; the path recalculates instantly.  
- Enemies follow the shortest route to the exit.  
- If a tower would make the map unsolvable, placement is refused.
- Defeat enemies to earn gold and score, survive waves, and accumulate upgrades.

### Tower Reference

| Tower    | Cost | Special   | Description                            |
|----------|------|-----------|----------------------------------------|
| Sentinel | 60   | –         | Balanced, all‑rounder                  |
| Railgun  | 120  | Pierce    | Shots pass through all enemies         |
| Burst    | 80   | –         | Extremely rapid fire                   |
| Cryo     | 90   | Slow 50%  | Slows enemies for 2 seconds            |
| Cannon   | 150  | Splash    | Deals area damage on impact            |
| Laser    | 200  | Burn      | Applies damage‑over‑time for 3 seconds |

- Upgrade level 0 → 1 → 2 (max). Upgrades increase damage, range, and fire rate.
- Sell a tower for 60% of total investment.

### Enemy Types

| Enemy    | HP (base) | Speed | Armor | Special          |
|----------|-----------|-------|-------|------------------|
| Scout    | 80        | 110   | 0     | –                |
| Grunt    | 200       | 75    | 0     | –                |
| Speeder  | 120       | 180   | 0     | Very fast        |
| Tank     | 600       | 45    | 2     | High armor       |
| Healer   | 250       | 60    | 0     | Heals nearby allies |
| Elite    | 400       | 90    | 3     | Tough hybrid     |
| Boss     | 2000      | 40    | 5     | Appears every 5 waves |

Enemy health scales by +8% per wave.

### Economy

- Start with **200 gold** and **20 lives**.
- Earn gold per kill plus a wave‑clear bonus (30 + wave × 50).
- Spend gold on towers, upgrades, and (indirectly) on selling losses.

---

## 🧠 Technical Insights

### A\* Pathfinding

- Custom implementation with a binary heap for the open set (MinHeap).
- Manhattan distance heuristic ensures fast, optimal path calculation.
- Every `placeTower()` or `sellSelected()` triggers a full repath – performance remains solid up to ~100 enemies.

### Rendering

- `requestAnimationFrame` loop with delta‑time game speed.
- Projectiles are pooled for minimal GC.
- Particles are recycled; no external rendering libraries.

### State Management

All game objects are plain arrays:
- `towers[]` – each tower stores position, type, level, cooldown, kills.
- `enemies[]` – position, health, path index, status effects.
- `projectiles[]` – trajectory, target reference, special flags.
- `particles[]` – position, velocity, lifetime.

---

## 📁 File Structure
grid-sentinel-ii/
├── index.html # Game source (HTML + CSS + JS all in one)
└── README.md

All code is self‑contained in a single file for maximum portability.

---

## 🎨 Customization

You can easily tweak the game by editing the constants at the top of the `<script>` block:

- `COLS`, `ROWS`, `CELL` – grid dimensions and tile size
- `SR`, `SC`, `ER`, `EC` – start/end coordinates
- `TDEFS` – tower stats and abilities
- `EDEFS` – enemy stats
- `gold`, `lives` starting values

---

## 🔮 Future Ideas

- Sound effects and background music (Web Audio API)
- More tower levels or upgrade branches
- Additional enemy abilities (shield, speed aura)
- Save / load system using LocalStorage
- Mobile touch support
- Map editor

---

## 🧾 License

This project is provided for educational and entertainment purposes.  
Feel free to modify and share it. No warranty.

---

**Stay sharp, commander – the grid won’t defend itself.**
