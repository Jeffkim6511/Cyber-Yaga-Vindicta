# team-08
**Project:** Cyber-Yaga Vindicta\
**Team Members:** Clive Yong, Parsa Saeedi, Jeff Kim, Matias Chomali, Mana Longhenry

## Building the Game
1. Ensure a minimum of version 3.1 for CMake
2. Build the project using CMake
3. Run the executable `cyber_yaga_vindicta`

## M1 Interpolation Implementation
- Player movement uses linear interpolation. Rather than setting the player's speed to a target value directly, we have a linear interpolation function that smoothly changes player's current velocity to approach the target velocity
- Because our `lerp` function (`player_system.cpp:221`) will only approach the target velocity, the player never fully reaches it, but continously approaches it. This small difference is negligible, if the target velocity is 400, after a few seconds (depending on smoothing factor) the player speed will be 399.99...

## M1 Creative Element Features
- **[1] Simple rendering effects:**
  1. Chromatic aberration effect when player gets hit.
  2. Renders all map tiles at the beginning of the game into a frame buffer, saves the FBO as a texture, and now every frame we only have to render a single quad with one texture for the entire map.
- **[8] Basic Physics:**  
  1. The player will collide with the wall and the wall applies a normal vector velocity onto the player preventing them from passing through the wall. We used several methods for collisions:
      - Axis-aligned bounding boxes (AABB) collision used for detecting between two rectangles when both are rotated in 90 degree increments.
      - Circle-circle collision to check between two objects with circular bounding volumes.
      - Seperating Axis Thereom (SAT) collision detection for any rectangle-rectangle collision when one or both are arbitrarily rotated (i.e. not in 90 degree incemenes). This uses circle-rectangle checks.
      - Swept collision checks are used for fast-moving projectiles and are applied to both circle-circle and SAT-based collisions.
  2. Additionally, the player's current velocity has acceleration and deceleration, similar to real world physics.
      - Using linear interpolation, the player movement is calculated smoothly, mimicking  basic acceleration and deceleration of objects in the real world.
- **[21] Camera Controls:** The camera will follow the player as the player moves.
- **[23] Audio Feedback:** There are 3 audio feedbacks for M1
  1. Gunshot audio when a player is shooting.
  2. Footsteps audio when player is moving.
  3. Hurt sound when player is hit by an enemy projectile.

## M2 Creative Element Features
- **[7] 2D Dynamic Shadows:**
  1. Light sources emit light and walls cast shadows from light sources onto different parts of the map.

## M3 Creative Element Features
- **[6] 2.5 (3D) Lighting:**
  1. Light reflects differently along the grooves of the floor, wall and props
  2. Normal maps give each wall, floor, and prop tiles non uniform light reflection properties
- **[15] Advanced Decision-Making:**
  1. Enemies use a mixture of A* pathfinding coupled with decision trees to pathfind towards to the player, engage in combat, and retreat if the player gets too close to the player.
  2. Enemies have line of sight checks, and when line of sight with an enemy is lost, enemies will pathfind to your last known location.
 
## M4 Creative Element Features
- (From M1) **[21] Camera Controls:** The camera will follow the player as the player moves.
- (From M1) **[23] Audio Feedback:** There are many audio feedbacks for M4. These include
  1. Gunshot audio when a player is shooting.
  2. Footsteps audio when player is moving.
  3. Hurt sound when player dies.
  4. Ticking sound when gun is out of ammo.
  5. Reloading sound when gun is being reloaded.
  6. Dash sound when the player dashes.
  7. Sword slash sound when the player uses melee.
  8. Blood impact sound when a bullet hits an enemy.
  9. Pickup sound when player picks up a gun.
  10. Bounce sound when a gun bounces off a wall.
  11. Power-up sound when the player uses a health-pack.
  12. Door break sound when a door is broken.
- **[25] Game Balance:** User feedback was generated from cross-plays, internal play-testing and other informal feedback from classmates, team members and friends. We have optimized our game to be beatable but still require a solid level of challenge to the player. The following are a brief list of some of the changes we made to the game's balance:
  1. Enemy alert sensitivity: Feedback suggested that enemies were too easy to sneak up on, and were too easy to take out in a room as the other enemies did not alert if a nearby enemy was in danger. In order to balance this, the sensitivity for enemy alerts was increased. Enemies are now alerted if they were shot at and the player was in the same room as the enemy. After internal testing, enemies were considered to be still too easy. As such, sensitivity was increased and enemies now become alerted when shot regardless of being in the same room or not as the player. Additionally other enemies in the same room as the enemy who was shot also become alerted, and if an enemy fires their weapon, other enemies nearby become alerted as well.
  2. Enemy detection and attack distance: Lots of feedback from cross-plays about distance for enemy detection of player and attack ranges. To balance a mixture of realism with playability, we extended the enemy attack distance to close to the height of the screen, so that enemies who fire at the player are likely to be within the display already, contributing to less player frustration caused by being killed by enemies off screen. Additionally, the distance at which the enemy continues to pursue the player was increased from player feedback, as players felt that since most people in real life would be able to see to the end of a hallway, the major limiting factor for enemy pursuit should be line of sight rather than a set distance down a hallway.
  3. Gun balancing: Both player held and enemy held guns were balanced to encourage more challenging gameplay, while making weapons feel impactful and easily usable by the player. Initially the shotgun had a magazine style reloading system, but due to the high damage of this weapon, the shotgun's reloading was changed to a single round reload, increasing overall reload time. This leaves players vulnerable to attacks by enemies, thereby balancing a high damage weapon with a high period of vulnerability during reloading.
  4. Enemy accuracy and reaction time: During cross-plays, some players felt that the enemies were unrealistic. Some felt that the enemies were too good at aiming, often hitting the player with every round even when the player was moving. To balance this struggle, enemies were given increased aim inaccuracy, allowing players to have more opportunity to fire back at the enemy without dying. Additionally, players felt that the game was unfair with enemies who could instantly snap to the player instead of having to turn to face the player. Therefore to make the game easier for players, enemies were given both a rotation with max rotation speed, and a reaction timer to prevent the enemies from being able to fire at the player as soon as they become alerted.
  5. Dash: During early builds of the game, players were able to dash much further and more often. the game team felt that this allowed players to unfairly defeat enemies who were unable to damage the player while the player character was within the invulnerability frames of the dash. Therefore, both dash cooldown and dash distance were reduced to encourage players to use the dash wisely and with more strategy in mind.
  6. Health packs: Another major feedback from players was that since the player character dies in very few hits, that they were unable to beat the first level and therefore the game was too hard. Therefore, the game team decided to implement health pickups that would allow the player to rejuvinate a portion of their health. These health packs are scattered throughout each level and provide a lower bar for entry to players who are newer to harcore or precision shooter style games.



# Citations
## Textures:
- Enemy sprite: https://itch.io/queue/c/5235441/top-down-shooter?game_id=889128
- Guns: https://itch.io/queue/c/5235441/top-down-shooter?game_id=2065422
- Guns: https://itch.io/queue/c/5235441/top-down-shooter?game_id=3233191
- Wall Particles: https://nyknck.itch.io/fx062
- Health bar: https://bdragon1727.itch.io/basic-pixel-health-bar-and-scroll-bar
- Tileset: https://deakcor.itch.io/zelda-like-futuristic-tileset
- Wall particles: https://nyknck.itch.io/fx062
- Blood Splatter: https://bdragon1727.itch.io/free-smoke-fx-pixel-2
- Crosshair: https://en.m.wikipedia.org/wiki/File:Crosshairs_Red.svg
- Title screen: Made with ChatGPT and Figma
- Player sprite: Made by ChatGPT, edited with Pixquare and Figma
- Cutscenes: Made with ChatGPT, edited in Figma
- Dead enemy: Made manually in Figma
- Projectile: Made manually in Piskel and Figma
- Tutorial instructions: Made manually in Figma
- Muzzle flash: Manually made in Piskel and Figma
- Health box: Made manually in Figma
- Damage indicator: Made manually in Figma
- Laser: Manually made in Figma

## Audio
- Zapsplat (paid subscription):
    - Bullet_flyby
    - Bullet hit wall/brick/flesh/rock
    - Dash
    - Pistol shot, dry-fire, load, reload
    - Player hit
    - Railgun reload, shot, cock, dry-fire, 
    - Revolver shot, cock, dry-fire, reload
    - Shotgun shot, reload, cock
    - Slash (melee)
- Freesound.org:
    - Footstep: https://freesound.org/people/florianreichelt/sounds/459964/
    - Door breaking: https://freesound.org/people/qubodup/sounds/160213/
- Music:
    - Level0 song: https://youtu.be/MoLSQPtyLWE?si=Adyq-TSqofpCo6Bf
    - Level1 song: https://youtu.be/RpzKNnw1Jog?si=E3uo4Vo1StSkxuoP
    - Level2 song: https://www.youtube.com/watch?v=VEQ2oEnDYms
    - Level3 song: https://youtu.be/J_6HIlpkDCI?si=8lYtRmSThSUS3wEH
## Font
- Font: Rajdhani (available on Figma)
