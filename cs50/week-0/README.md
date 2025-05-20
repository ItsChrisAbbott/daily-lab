# CS50 • Problem Set 0 — Scratch  
**Project:** Basketball Game  
<https://cs50.harvard.edu/x/2025/psets/0/scratch/>

---

## Assignment Requirements — Summary
Your Scratch project must satisfy **all** of the following:

| # | Requirement | Meaning |
|---|-------------|---------|
| 1 | **Sprites** | At least **2 sprites**, and one **must not** be the default cat. |
| 2 | **Scripts** | At least **3 separate scripts** total (they can belong to any sprites). |
| 3 | **Logic** | Use at least one **conditional**, one **loop**, and one **variable**. |
| 4 | **Custom Block** | Create at least **one custom block** (*Make a Block*) that takes **≥ 1 input parameter**. |
| 5 | **Complexity** | Project should involve a *few-dozen* blocks—more involved than lecture demos but needn’t be as hard as *Oscartime* or *Ivy’s Hardest Game*. |
| 6 | **Good Design** | Break long scripts into smaller ones, name custom blocks descriptively, and save incrementally. |

---

## My Basketball Game

### Gameplay
* **Aim** – A pink arrow sprite above the player continuously points toward your **mouse cursor**.  
* **Shoot** – Press **Space** to launch the basketball; it travels in the arrow’s direction.  
* **Scoring** – If the ball touches the **Top of Rim** sprite, your **score** increases by 1 and the ball falls through the hoop and to the ground.  
* **Misses** – Hitting the backboard, rim edges, boundary walls, or ground scores **0** and resets the ball to the player's hands.  
* **Timer** – A 60-second countdown implemented via the custom block **`TimeCounter`** runs in the corner. When it reaches 0, play stops and the game displays your final score.

### Core Features & Scratch Blocks

| Feature | Key Blocks / Variables |
|---------|-----------------------|
| **Mouse-driven aiming** | `forever` → `point towards [mouse-pointer]` (Arrow sprite) |
| **Spin animation** (visual polish) | Custom block **`Spin`** runs a small loop to rotate Arrow each time you shoot |
| **Launch physics** | Basketball sprite sets **`LaunchAngle`**, initial velocities **`vx`/`vy`**, then `repeat until <touching [Ground]>` moves by `change x by (vx)` and `change y by (vy)` (gravity simulated by `change vy by -1`) |
| **Scoring logic** | `if <touching [Top of Rim]>` then `change [Score] by 1` and call **`Scored (true)`** |
| **Game timer** | Custom block **`Time Counter`**: `repeat (60)` → wait 1 sec → `change [Time] by -1` → at 0 broadcast `"game-over"` |
| **State control** | Boolean var **`inFlight`** prevents new shots until the ball resets |

---

## How to Run

1. **Download** `basketball_game.sb3` from this folder.  
2. Open the Scratch editor → <https://scratch.mit.edu/projects/editor/>  
3. **File ▸ Load from your computer…** and select the `.sb3` file.  
4. Click the green flag **▶️** to start.  
   *Controls:* **Mouse Cursor** aim · **Space** shoot.

---

## Reflection & Future Improvements
* **Bounce physics**  
  *Add backboard and ground bounce detection so players can bank shots and watch the ball ricochet before resetting.*
* **Power bar mechanic**  
  *Introduce a charge-up meter using the current variable `LaunchSpeed` that changes shot force. Holding Space fills the bar; releasing fires—preventing “spam-score” exploits.*
* **Audio polish**  
  *Layer crowd ambience, rim “clang,” and swish sounds; add bounce SFX for ball-ground/backboard collisions.*
* **Code cleanup via custom blocks**  
  *Refactor long scripts into additional custom blocks (`shootBall`, `resetAfterBounce`, `playSFX`) for clearer, more efficient code and easier tweaking.*

> Created for **CS50 Week 0** to demonstrate events, loops, variables, conditionals, and custom blocks in Scratch.
