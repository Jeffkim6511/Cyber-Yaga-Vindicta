# Cyber-Yaga Vindicta — Team 08  
**Team Members:** Clive Yong, Parsa Saeedi, Jeff Kim, Matias Chomali, Mana Longhenry  

An action-packed top-down shooter with strategic AI, immersive lighting, and dynamic gameplay.

---

## 🔧 Building the Game

1. Ensure CMake version **3.1 or higher** is installed.
2. Use CMake to build the project.
3. Run the compiled executable: `cyber_yaga_vindicta`.

---

## 🧪 M1: Core Systems and Creative Features

### 🔄 Player Movement
- Smooth acceleration and deceleration via **linear interpolation** (`lerp` in `player_system.cpp:221`).
- Player velocity gradually approaches the target, simulating realistic movement.

### 🎨 Rendering Effects
- **Chromatic aberration** when the player is hit.
- Pre-renders all map tiles into a single **framebuffer texture**, drastically improving frame performance.

### 🧱 Basic Physics & Collision
- Wall collisions redirect player movement using **normal vector projection**.
- Collision detection techniques:
  - **AABB** (Axis-Aligned Bounding Boxes)
  - **Circle-circle**
  - **SAT** (Separating Axis Theorem) for rotated rectangle collisions
  - **Swept collision** for high-speed projectiles

### 📷 Camera Controls
- The camera dynamically tracks and follows the player’s position.

### 🔊 Audio Feedback
- Includes:
  - Gunfire
  - Footsteps
  - Player hurt sound

---

## 🌑 M2: Shadows & Lighting

### 💡 2D Dynamic Shadows
- Light sources cast **real-time shadows** from walls and objects, enhancing visual depth and atmosphere.

---

## 🔦 M3: Advanced Lighting & AI

### ✨ 2.5D Lighting
- **Normal maps** on environment assets simulate realistic light reflections.
- Variations in reflection based on surface grooves and orientation.

### 🧠 Advanced Enemy AI
- Combines **A\*** pathfinding and **decision trees** for:
  - Engaging and retreating from the player
  - Investigating player’s last known location
- **Line-of-sight** detection with memory tracking

---

## 🎮 M4: Polish, Feedback, and Game Balance

### 🔊 Expanded Audio
- Over 12 sound effects for player actions and feedback, including:
  - Gunfire, reload, footsteps, dashing, pickups, melee, and more

### ⚖️ Game Balance (Based on User Feedback)
1. **Enemy Alert Sensitivity:**
   - Enemies now alert each other based on shots fired, room presence, and line-of-sight logic.

2. **Detection & Attack Distance:**
   - Attack range now spans screen height to prevent unfair off-screen deaths.
   - Pursuit range governed by line-of-sight instead of arbitrary distance.

3. **Weapon Tuning:**
   - Shotgun switched to single-round reload for vulnerability tradeoff.
   - Enemy weapons rebalanced for challenge and fairness.

4. **Enemy Reaction:**
   - Enemies have a turn rate and reaction delay before firing.
   - Accuracy tweaked to allow room for player counterplay.

5. **Dash Mechanic:**
   - Dash range and cooldown reduced to prevent overuse and add strategic value.

6. **Health Pickups:**
   - Health packs added to lower entry difficulty and allow recovery between fights.

---

## 📜 Citations

### 🎨 Textures

- Enemy sprite: [Itch.io](https://itch.io/queue/c/5235441/top-down-shooter?game_id=889128)
- Guns: 
  - [Gun 1](https://itch.io/queue/c/5235441/top-down-shooter?game_id=2065422)
  - [Gun 2](https://itch.io/queue/c/5235441/top-down-shooter?game_id=3233191)
- Wall Particles: [nyknck.itch.io](https://nyknck.itch.io/fx062)
- Health bar: [bdragon1727.itch.io](https://bdragon1727.itch.io/basic-pixel-health-bar-and-scroll-bar)
- Tileset: [deakcor.itch.io](https://deakcor.itch.io/zelda-like-futuristic-tileset)
- Blood splatter: [bdragon1727.itch.io](https://bdragon1727.itch.io/free-smoke-fx-pixel-2)
- Crosshair: [Wikipedia](https://en.m.wikipedia.org/wiki/File:Crosshairs_Red.svg)
- Custom assets made with:
  - ChatGPT
  - Figma
  - Pixquare
  - Piskel

### 🔊 Audio

#### Zapsplat (licensed)
- Bullet flyby
- Bullet impact (wall, brick, flesh, rock)
- Dash
- Gunfire, reloads, dry-fire (pistol, revolver, railgun, shotgun)
- Player hurt
- Melee slash

#### Freesound.org
- [Footsteps](https://freesound.org/people/florianreichelt/sounds/459964/)
- [Door breaking](https://freesound.org/people/qubodup/sounds/160213/)

#### 🎵 Music
- Level 0: [YouTube](https://youtu.be/MoLSQPtyLWE?si=Adyq-TSqofpCo6Bf)
- Level 1: [YouTube](https://youtu.be/RpzKNnw1Jog?si=E3uo4Vo1StSkxuoP)
- Level 2: [YouTube](https://www.youtube.com/watch?v=VEQ2oEnDYms)
- Level 3: [YouTube](https://youtu.be/J_6HIlpkDCI?si=8lYtRmSThSUS3wEH)

### 🔤 Font
- Rajdhani — Available via Figma

### License
