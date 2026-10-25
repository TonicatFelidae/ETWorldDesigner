
# Neko Line: Save the Cat! (Working Title)

| Draw a single line to build a physics shield and protect the clumsy cat from swarms, traps, and chaos!
| Product Vision, Modular Level Architecture & Hybrid-Casual Monetization GDD
| ET STUDIO / 2026

---

## Game Concept

| Concept                  | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| :----------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Title**                | Draw 2 Meow: Save the Niiiko                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **Subtitle**             | Draw to Protect Cat Physics Puzzle                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Description**          | **Neko Line: Save the Cat!** is a 2D physics-based line-drawing puzzle game where players use a single finger stroke to draw a solid 2D barrier around a vulnerable, expressive cat. Once the player lifts their finger, gravity activates on the drawn line and environmental hazards—such as angry killer bees, rolling boulders, rising lava, acid rain, and wind fans—are unleashed. If the player's drawn structure holds up and keeps the cat unharmed for the **7-second survival countdown**, the stage is cleared! Featuring a modular level architecture that scales smoothly across **30 handcrafted core progression stages** into an **Infinite Procedural Remix Mode (Level 31–∞)**, hilarious meme-inspired cat animations, customizable ink brushes, and a high-LTV hybrid-casual ad + IAP economy, the game is engineered for rapid production and maximum profitability. |
| **Genre**                | Physics Puzzle / Draw-to-Save / Hybrid-Casual / Brain Teaser                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **Theme**                | Cute, comedic, slapstick cartoon physics with meme-worthy cat reactions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Setting**              | Whimsical hazard-filled dioramas (Sunny Backyard, Beehive Forest, Magma Cavern, Icy Peaks, Cyber Factory, Cosmic Void)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **Player Role**          | The Guardian Artist whose finger-drawn ink lines materialize into physical 2D shields                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **Core Gameplay**        | Observe the stage layout and hazards, then draw a continuous 2D line in a single stroke (`LineRenderer` + `EdgeCollider2D`/`PolygonCollider2D` + `Rigidbody2D`) before lifting your finger to trigger the 7-second hazard simulation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **Objective**            | Prevent all hazards (bees, spikes, lava, water, bombs) from touching or knocking the cat off-screen until the countdown timer reaches `0.0s`, while using as little ink as possible to earn 3 Stars                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Progression**          | Complete Levels 1–30 across 6 themed worlds (unlocking a new hazard/mechanic every 5 levels), then seamlessly enter the **Infinite Puzzle Generator (Level 31+)** while collecting Cat Skins, Brush Trails, and Cat House furniture                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Unique Selling Point** | 1. **Zero-Friction Modular Level Pipeline**: Prefab-stamp level architecture allows creating a new level in under 2 minutes and powers an infinite deterministic stage generator beyond Level 30.<br>2. **Dynamic Ink Material Physics**: Unlockable/ad-boosted ink types (Standard, Heavy Stone, Bouncy Slime, Sticky Honey, Electric Zap) change how barriers behave.<br>3. **Meme-Grade Expressive Cat States**: Panic, smug grin, teary-eyed swollen face (when stung), and victory dance animations that drive organic social sharing and high ad engagement.                                                                                                                                                                                                                                                                                                                         |
| **Art Style**            | Clean, bold-outlined 2D vector/cartoon Chibi art with high-contrast silhouettes, readable hazard telegraphs, and juicy physics squash-and-stretch                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Audio (BGM/SFX)**      | Upbeat, quirky pizzicato/marimba puzzle BGM; tension-building ticking clock + buzzing swarm loop during the countdown; comical meow/boing/splat SFX                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Target Audience**      | All genders, ages 10–45; casual puzzle players, cat lovers, and fans of quick brain-teaser mobile games                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Platform**             | Android, iOS (Portrait orientation `9:16`, one-handed thumb play)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

---

## References

- **UI / UX Flow (Figma):** `TBD — Portrait 9:16 Single-Thumb Flow (Home -> Stage Select / Play -> Draw Phase -> 7s Survival Phase -> Win/Fail Popup)`
- **Game Data Sheet:** `Assets/Game/Data/LevelProgression_30_to_Infinity.csv` (Planned ScriptableObject / JSON schema)
- **Visual / Market References:**
  - *Save the Doge* (Wonder Group / Mirai Studio) — Core one-stroke physics barrier loop, bee swarm AI, and high-converting hint/skip ad funnel.
  - *Draw 2 Save: Stickman Puzzle* — Creative environmental traps (rolling rocks, seesaws, bombs) and stencil hint overlays.
  - *Neko Atsume / Crying Banana Cat Memes* — Charming cat collectibles, cozy meta-room progression, and humorous reaction faces.

---

## Game cycle

Each stage in **Neko Line: Save the Cat!** runs on a fast, highly addictive **12-to-20 second micro-cycle** designed to maximize session length, retry rate, and ad impression velocity.

- **Step 1 (Preparation / Input — The Observation & Draw Phase):**
  - The stage loads with physics frozen (`Time.timeScale = 1`, Cat and Hazards in `Kinematic`/Standby state).
  - The player inspects the position of the Cat(s), Beehives, terrain slopes, and any Red "No-Draw" Zones.
  - The player touches the screen and drags their finger to draw a continuous 2D line. As they draw, the **Ink Bar** at the top depletes and the **3-Star Threshold Markers** tick down in real time.
- **Step 2 (Active / Simulation Phase — The 7-Second Holdout):**
  - As soon as the player lifts their finger (`OnPointerUp`)—or when the Ink Bar hits `0%`—the drawn line converts into a dynamic 2D physics body (`Rigidbody2D` + baked `PolygonCollider2D`) and drops under gravity.
  - Simultaneously, the **7.0-second Countdown Timer** starts, the Cat's gravity activates, and Beehives spawn angry physics-driven Bees that fly toward the Cat and apply impulse forces (`AddForce`) against the player's drawn barrier.
- **Step 3 (Completion / Climax):**
  - **Win Trigger:** The countdown reaches `0.0s` while all Cats remain alive and unharmed on screen. Confetti bursts, the Cat performs a smug victory dance, and the Win Popup appears.
  - **Fail Trigger:** A bee stings the Cat, or the Cat touches spikes/lava/water, or falls out of the camera bounds before the timer hits `0.0s`. The Cat plays a comical swollen/crying animation and triggers the Fail / Revive Popup.
- **Result:**
  - Clearing a stage awards **1 to 3 Stars** (based on remaining ink), **Base Coins**, **Star Chest Progress**, and **Cat Skin Unlock Progress** (`+20%` per level).

**Key Aspects of Every Cycle:**
- **Progress Tracking:** Tracked inside each stage via the **Ink Meter (`100%` down to `0%`)** featuring three Star breakpoints (`100%–60%` remaining = 3 Stars, `59%–25%` = 2 Stars, `24%–0%` = 1 Star) and the **Survival Countdown Clock (`7.0s` down to `0.0s`)**.
- **Base Duration of a Single Cycle:** `3–8 seconds` drawing + `7.0 seconds` survival simulation = **`10–15 seconds` per attempt**.
- **Cycle Time Scaling Rules:**
  - **Levels 1–10:** `6.0 seconds` survival holdout (fast onboarding and instant gratification).
  - **Levels 11–30:** `7.0 seconds` standard survival holdout.
  - **Boss / Challenge Stages (Every 5th Level: 5, 10, 15, 20, 25, 30, etc.):** `9.0 seconds` survival holdout with multi-wave bee spawns.
- **Ways to Reduce Difficulty or Speed Up Completion:**
  - **Blueprint Hint (Rewarded Ad / 1 Hint Token):** Renders a translucent dotted 3-Star solution line directly on the playfield so the player simply traces over it.
  - **Super Ink Boost (Rewarded Ad):** Grants `+50%` Ink capacity and converts the line into Heavy Golden Ink (`3x` mass + bee knockback) for the current stage.
  - **Skip Stage (Rewarded Ad):** Immediately marks the stage cleared (1 Star) if the player fails twice or chooses not to solve it.
- **How Player Choices Affect the Cycle Outcome:**
  - Drawing a tight wrap around the cat saves ink (3 Stars) but risks bees pushing the light shell into spikes; anchoring the line over terrain hooks uses more ink (1–2 Stars) but creates an immovable fortress.

---

## Game reward

After every cleared stage, players receive immediate currencies and meta-progression rewards that feed into the Cat Skin Collection and Cozy Cat Room.

- **Base Cycle Reward:**
  - **Coins:** `50 Coins` per stage clear (`100 Coins` on Boss stages every 5th level).
  - **Stars:** `1 to 3 Stars` based on ink efficiency (`RemainingInkRatio`).
  - **Skin Unlock Gauge:** `+20%` fill toward the next mystery Cat Skin (unlocks a new skin every 5 levels; claimed via Rewarded Ad or Coins).
- **Variable / Drop Reward:**
  - **Star Milestone Chest:** Every `15 Stars` collected opens a Star Chest containing `150–300 Coins`, `1 Hint Token`, or a `Rare Brush Trail` piece.
  - **Piggy Bank Bonus:** Every 3-Star clear deposits `+25 Bonus Gems/Coins` into the Piggy Bank.
- **Final Reward Formula:**
  $$\text{Final Coins} = (\text{Base Stage Coins} + \text{Star Bonus Coins}) \times \text{Ad Multiplier} \times \text{Skin Tier Bonus}$$
  - Where $\text{Star Bonus Coins} = (\text{Stars Earned} - 1) \times 15\text{ Coins}$ (`0` for 1★, `+15` for 2★, `+30` for 3★).
- **Reward Modified by Ad:**
  - **Roulette Multiplier Slider (Win Screen):** Watching a Rewarded Ad stops a moving multiplier needle (`2x`, `3x`, `4x`, `5x`), multiplying the stage's Coin payout up to **500%**.
- **Reward Modified by Mechanics:**
  - **Equipped Cat & Brush Rarity Bonus:** Equipping Rare/SR/SSR Cat Skins or Brush Trails passively grants `+5%` to `+25%` bonus Coins on every clear.

---

## Core gameplay

**Neko Line: Save the Cat!** combines tactile 2D physics drawing with a modular hazard ecosystem and an infinite stage generator so the game remains fresh from Level 1 to Level 1,000+.

### (1) 2D Physics Line Drawing & Collider Generation
The heart of the game is turning a player's freehand finger stroke into a believable, physical 2D shield.

- **Input & Drawing Rules:**
  - **Single-Stroke Rule:** The player can only draw **one continuous line** per attempt. Lifting the finger immediately finalizes the line and starts the hazard phase.
  - **Minimum Node Distance (`minVertexDistance = 0.15f` world units):** As the player drags their finger, a new vertex is appended to the `LineRenderer` only when the pointer moves at least `0.15` units from the last point, preventing vertex spam and physics jitter.
  - **Line Width & Collider Baking:** The visual line has a thickness of `0.22` units. Upon `OnPointerUp`, the point array is converted into a `PolygonCollider2D` (or thickened `EdgeCollider2D` with `edgeRadius = 0.11f`) attached to a single `Rigidbody2D`.
  - **Mass Scaling by Length:** $\text{Line Mass} = \text{BaseMass (1.0)} + (\text{NodeCount} \times 0.08)$. Longer lines are heavier and harder for bees to push, but consume more Ink.
  - **Collision Layer Rules while Drawing:**
    - The pointer **can** pass smoothly over empty air (`DrawZone`).
    - The pointer **cannot** pass through solid terrain walls, the Cat itself, Beehives, or **Red No-Draw Zones** (if the player drags across an obstacle, the line stops/clips at the obstacle edge until the finger moves back to valid space).
- **Ink Meter & Star Thresholds:**
  - Each level defines `MaxInkLength` (in world units, typically `12.0` to `25.0` units).
  - **3 Stars (★★★):** Clear using $\le 40\%$ of `MaxInkLength` ($\ge 60\%$ Ink remaining).
  - **2 Stars (★★☆):** Clear using $41\%–75\%$ of `MaxInkLength` ($25\%–59\%$ Ink remaining).
  - **1 Star (★☆☆):** Clear using $76\%–100\%$ of `MaxInkLength` ($<25\%$ Ink remaining).

### (2) Contextual Rescue & Boost Offers (Blueprint Hint, Super Ink, Revive & Skip)
To maximize ad monetization without frustrating players, the game triggers smart, contextual assistance offers based on player struggle and stage state.

| Occurrence | Trigger Timing | Role | Effect |
| :--- | :--- | :--- | :--- |
| **1st (Last-Second Shield Revive)** | Cat is stung or killed when remaining countdown is **$\le 2.5\text{s}$** (once per attempt) | Capitalize on "near-miss" tension and prevent rage-quitting | Watching 1 Rewarded Ad rewinds 1 second, spawns an unbreakable **Golden Bubble Shield** around the Cat for the remaining `2.5s`, and guarantees stage clear |
| **2nd (Blueprint Hint Offer)** | Player fails the same stage **2 times in a row** (or taps the Hint lightbulb button at any time) | Unblock stuck players while driving high-eCPM Rewarded Ad views | Watching 1 Rewarded Ad (or spending `1 Hint Token`) displays the **3-Star Dotted Ghost Line** directly on screen to trace |
| **3rd (Super Golden Ink / Skip Stage)** | Player fails the same stage **3+ times in a row** | Prevent churn on difficulty spikes (Levels 10, 15, 25, etc.) | Pulsing button offers choice: **Super Ink** (`+50%` length, `3x` mass, zaps bees on contact for 1 round) OR **Instant Skip** via Rewarded Ad |

- **Example Case:**
  - A player is on **Level 14** (Sloped Cliff + 2 Beehives, `MaxInkLength = 16.0` units, `Countdown = 7.0s`).
  - **Attempt 1:** Player draws a small dome (`5.0` units used). At `1.8s` remaining, the bees push the dome off the cliff and sting the cat. Because remaining time was `1.8s` ($\le 2.5\text{s}$), the **Last-Second Shield Revive** popup appears. The player declines and retries.
  - **Attempt 2:** Player draws a larger hook (`11.0` units used), but leaves a gap at the bottom; a bee sneaks in at `4.2s`. Now at **2 consecutive fails**, the **Blueprint Hint** button pulses with a free preview animation. The player watches 1 Rewarded Ad, sees the exact hook-and-anchor dotted path (`6.0` units = 3 Stars), traces it on Attempt 3, and clears with **3 Stars**.

### (3) Modular Level Architecture & 30-to-Infinite Difficulty Progression
To make level creation **fast, cheap, and infinitely scalable**, levels are NOT hand-painted as monolithic scenes. Instead, every stage is assembled from **4 modular building blocks** stored in a tiny JSON / `ScriptableObject` (`LevelDataSO`, $<2\text{ KB}$ per level).

| Name | Category | Description |
| :--- | :--- | :--- |
| **Terrain Base Chunk (`ChunkID`)** | Environment Geometry | 15 reusable 2D terrain prefabs (e.g., `Flat_Platform`, `V_Valley`, `Dual_Pillars`, `Sloped_Cliff`, `Seesaw_Beam`, `Suspended_Pegs`, `Funnel_Pit`). |
| **Protected Target (`CatNode`)** | Objective Entity | 1 to 3 Cat entities (`Normal_Cat`, `Rolling_Fat_Cat` on slopes, `Cat_And_Lover` where two cats must stay together, or `Cat_Near_Fishbowl`). |
| **Hazard Spawners (`HazardNode`)** | Active Threats | Modular hazard prefabs placed via coordinates (`Beehive_Standard`, `Beehive_Queen_Heavy`, `Spike_Wall`, `Lava_Floor`, `Water_Pool`, `Rolling_Boulder`, `Acid_Dropper`, `Wind_Fan`). |
| **Zone & Ink Modifiers (`RuleMod`)** | Puzzle Constraints | Optional puzzle twists (`NoDraw_RedZone` box, `Glass_Breakable_Floor`, `Gravity_Flip_Portal`, `Moving_Platform`). |

**UI & Cost Formula (Ink & Hazard Difficulty Budget System):**
- **UI Name:** In-Editor **1-Click Level Stamp Tool** (for developers) & **Infinite Stage Generator** (for runtime Levels 31+).
- **Rules & Constraints:**
  - Every level has a **Target Difficulty Score ($D$)** calculated from its hazards and constraints.
  - To create a new handcrafted level in the Unity Editor, a designer simply drags a `TerrainChunk` prefab, drops 1 `Cat` and 1–3 `HazardNodes`, draws one test line in Play Mode, and clicks **"Bake Solution Path & Auto-Set Ink Budget"** (which records the designer's stroke as the `BlueprintHintPoints[]` array and sets `ThreeStarInk = StrokeLength * 1.15f`, `MaxInk = StrokeLength * 2.5f`). **Total time to create 1 level: ~90 seconds.**

| ID | Name | Base Difficulty Point ($P_i$) | Scaling / Parameter Formula |
| :--- | :--- | :--- | :--- |
| **H1** | **Standard Beehive** | `10 pts` | Spawns `5 + floor(Level / 10)` bees (cap `12` bees/hive); Bee thrust = `3.5f + (0.02f * Level)` (capped at `6.0f`) |
| **H2** | **Slope / Unstable Terrain** | `15 pts` | Terrain angle $\theta \in [15^\circ, 45^\circ]$; requires line to brace Cat against sliding |
| **H3** | **Lethal Floor (Lava / Water / Spikes)** | `20 pts` | Instant fail if Cat or knockback pushes Cat into contact |
| **H4** | **Physics Trap (Boulder / Seesaw / Bomb)** | `25 pts` | Dynamic rigidbody (`Mass = 8.0`) that falls or tilts when simulation starts |
| **H5** | **Second Cat / Red No-Draw Zone** | `30 pts` | Requires spanning a single line across two targets or routing around a forbidden zone |

- **30-Level Handcrafted Progression Curve (Levels 1–30):**
  - **World 1 — Sunny Backyard (Levels 1–5): *Learn the Line***
    - *Mechanics:* `1 Beehive`, flat/pedestal terrains, generous ink (`MaxInk = 22`). Level 5 Boss introduces `2 Beehives`.
  - **World 2 — Steep Hills (Levels 6–10): *Gravity & Anchoring***
    - *Mechanics:* Introduces **Sloped Cliffs, Rolling Cat, and Spike Walls**. Players learn to hook lines over pegs so the cat doesn't roll into spikes.
  - **World 3 — Magma Cavern (Levels 11–15): *Lava & Heavy Rocks***
    - *Mechanics:* Introduces **Rising Lava Pools** and **Falling Boulders** from above. Lines must deflect heavy rocks while blocking bees.
  - **World 4 — Honey Factory (Levels 16–20): *Seesaws & Moving Parts***
    - *Mechanics:* Introduces **Pivot Seesaws, Breakable Glass Blocks, and Wind Fans** that blow lightweight lines away unless anchored.
  - **World 5 — Forbidden Garden (Levels 21–25): *Red No-Draw Zones & Twin Cats***
    - *Mechanics:* Introduces **Red No-Draw Zones** (cannot draw directly over the cat; must build a bridge/roof from outside) and **2 Cats** to save with a single stroke.
  - **World 6 — Queen Bee Citadel (Levels 26–30): *Mastery & Queen Bees***
    - *Mechanics:* Combines multi-hazard puzzles with **Giant Queen Bees** (`3x` knockback force, `9.0s` holdout on Level 30).

- **How & Why the Infinite Level System Works (Level 31 to $\infty$):**
  - **Why Infinite Levels Are Essential for Profitability:**
    1. **Uncapped LTV & Ad Inventory:** In draw-to-save games, players clear 30 levels in ~15–20 minutes. If the game ends at Level 30, players uninstall before Day 2, killing D7 retention and long-tail ad revenue. Infinite levels allow engaged players to reach Level 200, 500, or 1,000+ while generating continuous Interstitial and Rewarded Ad impressions.
    2. **Zero Content Bottleneck:** You don't need to manually design 1,000 levels. By using **Procedural Template Remixing + Parametric Mutation** over a pool of 30–50 core layouts, the game produces thousands of distinct-feeling stages automatically.
  - **Reward / Outcome Formula (Infinite Procedural Stage Generator for `Level > 30`):**
    $$\text{DifficultyBudget}(L) = 45 + \lfloor 15 \times \log_2(L - 29) \rfloor + ((L \bmod 5 == 0) ? 25 : 0)$$
    - For any `Level L > 30`, the deterministic generator (`Random.InitState(L * 7919)`) performs a **4-Step Mutation Pipeline**:
      1. **Base Template Selection:** Selects one of the 30 core templates (avoiding any template used in the last 12 levels).
      2. **Geometric Transformation:** `50%` chance to horizontally mirror the stage (`Scale.x = -1`); shifts Cat and Peg offsets by $\pm 0.5\text{ to }1.2$ units along valid platform surfaces.
      3. **Hazard Upgrade & Injection:** Spends $\text{DifficultyBudget}(L)$ to add an extra Beehive, upgrade a normal Beehive to a Queen Beehive, swap a Spike floor for Lava/Water, or insert a `NoDraw_RedZone` offset from the Cat.
      4. **Auto-Adjusted Ink & Blueprint Transform:** Mirrors/scales the template's baked `BlueprintHintPoints[]` to match the transformed coordinates and adds `+15%` safety margin to `MaxInkLength` so every procedural level is **100% guaranteed solvable** and still supports the Blueprint Hint ad!

### (4) Unlockable Ink Brushes & Physics Modifiers
Before starting a stage (or via the pre-stage booster bar), players can switch their **Ink Brush Material**, adding strategic depth and a strong sink for Coins and Rewarded Ads.

- **Standard Black Ink (Default):** Balanced mass (`1.0x`), normal friction (`0.4`).
- **Heavy Stone Ink (Unlock at Lv. 10 / 1,500 Coins):** `2.2x` mass; resists bee knockback and wind fans, but drops faster under gravity.
- **Sticky Honey Ink (Unlock at Lv. 20 / 2,500 Coins):** High surface friction (`0.95`); grips sloped cliffs without sliding off.
- **Bouncy Slime Ink (Unlock at Lv. 30 / 4,000 Coins):** High bounciness (`PhysicsMaterial2D.bounciness = 0.85`); deflects falling boulders and knocks bees backward on impact.
- **Golden Electric Ink (Rewarded Ad Booster):** `3.0x` mass + `+50%` ink capacity + zaps and stuns any bee that touches the line for `1.5s`.

### (5) Collection of creatures / items
Players collect **Cat Skins (Characters)**, **Ink Brush Trails**, and **Cozy Cat Room Decorations**, tracked in the **Cat Album UI**.

- **Collection Categories:**
  - **Cat Skins (30 Total):** Grouped into 5 rarity tiers (Normal, Rare, SR, SSR, UR), featuring hilarious idle, panic, stung, and victory animations (e.g., *Box Cat*, *Boba Tea Cat*, *Crying Banana Cat*, *Samurai Neko*, *Mecha Cat*, *Astro Neko*).
  - **Ink Brush Trails (15 Total):** Visual shader/particle overlays on the drawn line (*Crayon*, *Rainbow Ribbon*, *Paw Print Chain*, *Bamboo Rope*, *Neon Laser*, *Galaxy Starlight*).
- **Collection Milestone Rewards:**
  - **40% Unlocked (12 Cats):** `+500 Coins` + Exclusive *Yarn Ball Brush* + Permanent `+5%` Stage Coin Bonus.
  - **80% Unlocked (24 Cats):** `+1,500 Coins` + `5 Hint Tokens` + Permanent `+10%` Stage Coin Bonus.
  - **100% Unlocked (30 Cats):** Exclusive **UR Golden Maneki-Neko Skin** + Permanent `+25%` Stage Coin Bonus.

### (6) Gacha (option)
The **Lucky Neko Capsule Machine** acts as the primary repeatable Coin and Ad sink once players accumulate currency.

- **Gacha Cost:**
  - **1st Pull:** `300 Coins` (scales by `+100 Coins` every 3 pulls, capped at `600 Coins` per pull) OR **1 Free Ad Pull** (cooldown: `15 minutes`, max `5 Ad Pulls/day`).
- **Reward Pool & Yield Table:**
  - **Normal Cat Skin / Brush Piece:** `45%`
  - **Rare Cat Skin / Brush Piece:** `28%`
  - **SR Cat Skin:** `15%`
  - **SSR Cat Skin:** `9%`
  - **UR Cat Skin:** `3%`
  - *(Duplicate skins automatically convert into `+150 Coins` and `+15%` Pity Bar progress).*
- **Pity Bar & Guaranteed Milestone:**
  - Every pull fills the **Golden Bell Pity Bar** by `+10%`. At **`100%` (10 pulls)**, the player is guaranteed an unowned **SR, SSR, or UR Cat Skin**.

### (7) Daily Rewards (option)
A 7-day login calendar that pops up automatically on the first session of each day (unlocked after completing Level 3).

| Day | Reward Type | Amount |
| :--- | :--- | :--- |
| **Day 1** | Coins | `200 Coins` |
| **Day 2** | Hint Tokens | `2 Hint Tokens` |
| **Day 3** | Exclusive Cat Skin | **Bread Loaf Cat (Rare)** |
| **Day 4** | Coins | `500 Coins` |
| **Day 5** | Super Ink Boosters | `3 Golden Ink Boosters` |
| **Day 6** | Coins + Hint Tokens | `1,000 Coins` + `3 Hint Tokens` |
| **Day 7** | Exclusive SSR Cat Skin | **Royal Crown Neko (SSR)** (or `2,500 Coins` if owned) |

- **Buttons:**
  - **Claim (1x):** Standard green button to collect the current day's reward.
  - **Claim 2x (Watch Ad):** Highlighted gold button with a video icon that doubles currency/consumable rewards (`400 Coins` on Day 1, `4 Hints` on Day 2, etc.).
  - **Catch-Up Claim:** Missed days show a **"Unlock via Ad"** button so returning players can recover missed streak days.
- **Mechanisms:**
  - Resets at `00:00` local device time. Does NOT hard-reset progress if a day is missed; after Day 7 is claimed, the calendar loops into a recurring Weekly Bonus Table (Days 3 and 7 replaced by `1 Gacha Capsule Ticket` and `1 SSR Mystery Box`).

### (8) Daily Missions (option)
Daily Missions drive session length, encourage 3-Star replays, and incentivize voluntary Rewarded Ad views.

| ID | Mission name | Reward | Required |
| :--- | :--- | :--- | :--- |
| **1** | **Cat Guardian** | `100 Coins` | Clear `5` stages |
| **2** | **Ink Master** | `150 Coins` | Earn `3 Stars` on `3` stages |
| **3** | **Swarm Survivor** | `1 Hint Token` | Survive `60 seconds` total of bee attacks |
| **4** | **Sharp Artist** | `150 Coins` | Clear `1` stage using less than `25%` Ink |
| **5** | **Supporter** | `200 Coins` + `1 Golden Ink` | Watch `2` Rewarded Ads (Hint, 2x Reward, or Gacha) |
| **6** | **Daily All-Clear Bonus** | `1 Free Gacha Pull Ticket` | Complete all `5` Daily Missions today |

### (9) IAP Shop (option)
An integrated in-game Store accessible from the top Coin bar and main menu, combining IAP bundles, Coin packs, and Cosmetic unlocks.

- **Exchange / Store UI:**
  - Single-scroll modal divided into **Featured Bundles** (No-Ads, Starter Pack), **Booster Packs** (Hint Tokens, Golden Ink), and **Coin Packs**.
  - Displays a green **"Restored / Purchased"** badge on non-consumable items (`Remove Ads`, `Permanent 2x Coins`).
- **Multi-Provider / Store Expansion:**
  - Built on **Unity IAP (`com.unity.purchasing`)** supporting both **Google Play Billing v6+** and **Apple StoreKit 2**, with modular hooks for future webshop or point-exchange extensions.
- **Target Shop Platforms / Items:**
  - Google Play Store & Apple App Store native in-app purchases (Remove Interstitial/Banner Ads, Starter Bundles, Consumable Coin & Hint packs).

### (10) Rating UI (option)
Native store review flow designed to capture high-sentiment 5-star ratings at peak moments of player satisfaction.

- **Trigger Timing & Conditions:**
  - **1st Trigger:** Immediately after clearing **Level 5** with **3 Stars** (or unlocking the 1st Cat Skin at Level 5).
  - **2nd Trigger:** After clearing **Level 15** or pulling an **SSR/UR Cat** from Gacha (if not previously rated).
- **Frequency & Cooldown Rules:**
  - Minimum `72 hours` and `15 stages` cooldown if the player dismisses the popup.
  - Never shown again once the player submits a 5-star review or completes the feedback form.
- **UI Flow:**
  - **Two-Step Pre-Prompt Filter:** First shows a cute in-game popup with a purring cat asking *"Are you enjoying saving the cats?"* with **1 to 5 Star buttons**.
  - **If 4–5 Stars selected:** Immediately invokes the native OS dialog (`Google Play In-App Review API` / `SKStoreReviewController.requestReview()`).
  - **If 1–3 Stars selected:** Opens a simple internal text feedback box (*"Tell us how we can improve!"*) instead of sending the user to the public app store.

### (11) FAQ
In-game offline-capable Help & Troubleshooting modal to minimize support tickets.

- **Access Point:** Located inside the **Settings Popup** (`[?] FAQ` button).
- **Display Method:** Native Unity ScrollView accordion popup loaded from `Resources/Localization/FAQ_Data.csv` (supports EN, JP, KR, VN, TW).
- **Question Categories & Content:**
  1. *Why won't my line draw over certain areas?* (Explains Red No-Draw Zones and solid terrain walls).
  2. *How do I get 3 Stars on a level?* (Keep the Ink Bar above the 3-Star line marker when lifting your finger).
  3. *What does "Remove Ads" remove?* (Removes all forced Interstitial and Banner ads permanently; optional Rewarded Ads for free hints/bonuses remain available if you choose to tap them).
  4. *How do I restore my purchases on a new phone?* (Tap "Restore Purchases" in Settings while signed into the same Apple ID / Google account).
- **Contact / Support Link:** **"Contact Support"** button at the bottom opens a pre-filled `mailto:support@etstudio.com` containing device model, OS version, App version, and current `LevelIndex`.

### (12) Tutorial
Zero-wall-of-text, interactive hand-pointer onboarding across **Levels 1 to 3** that gets players into the core loop within **5 seconds of launch**.

- **Trigger Condition:**
  - **Level 1 (First Launch):** Launches **directly into Level 1** (bypasses Home Screen on first boot to maximize Day-1 FTUE completion).
  - **Contextual Feature Tutorials:** Triggered on the exact level a new hazard appears (Level 6 for Slopes, Level 11 for Lava, Level 21 for Red No-Draw Zones).
- **Tutorial Type:** Non-intrusive **Animated Hand & Dotted Stencil Guide** on the canvas—no dialogue boxes blocking gameplay.
- **Step-by-Step Flow:**
  - **Step 1 (Level 1 — Basic Dome):** A glowing animated finger traces a simple upside-down U-dome (`∩`) over the Cat along a dotted guide line. Text prompt: *"Draw a line in one stroke to protect the cat!"*
  - **Step 2 (Level 1 — Holdout):** Player lifts finger; 1 Beehive releases 5 bees that bounce harmlessly off the dome for `6.0s`. Victory confetti triggers!
  - **Step 3 (Level 2 — Ink & 3 Stars):** Highlights the **3-Star Marker** on the top Ink Bar. Dotted stencil shows a compact circle around the cat.
  - **Step 4 (Level 3 — Anchoring on Terrain):** Shows how hooking a line over a stone peg prevents the cat from sliding down a ramp. Unlocks the Home Screen & Skin Progress bar upon completion.
- **Skip / Replay Rules:**
  - The dotted tutorial stencil on Level 1 disappears immediately once the player starts drawing their own line. Players can view hazard tips anytime via the `[?]` icon in Settings.

### (13) Inbox
Lightweight in-game Mailbox for live-ops gift distribution, milestone rewards, and compensation.

- **Message Types:**
  - Seasonal event gifts (e.g., *Halloween Pumpkin Cat Skin*, *New Year 500 Coins*), update rewards, and customer support compensation.
- **UI & Actions:**
  - Accessible via the **Mail Icon** on the Home Screen (shows a red notification badge when unread rewards exist).
  - Includes **"Claim All"** (collects all attached Coins, Hints, and Skins in one tap) and **"Delete Read"**.
- **Expiration & Storage Limits:**
  - Stores up to `30 messages` locally/cloud-synced; unclaimed messages expire after `30 days`.

### (14) Settings
Accessible via the top-right **Gear Icon** on the Home Screen and Pause Popup.

- **Audio Controls:**
  - **BGM Toggle & Slider:** Mute/adjust background music.
  - **SFX Toggle & Slider:** Mute/adjust bee buzzing, cat meows, and UI clicks.
- **System / Preferences:**
  - **Haptic / Vibration Toggle:** Toggles light haptic pulses while drawing lines and heavy vibration when bees hit the barrier or sting the cat.
  - **Language Selector:** English, Japanese (日本語), Korean (한국어), Traditional Chinese, Vietnamese.
  - **Push Notifications Toggle:** Enables/disables offline reminder notifications.
- **Account & Legal Links:**
  - **User ID Display** with `[Copy]` button, **Restore Purchases** button (iOS/Android), **Privacy Policy**, **Terms of Service**, and **GDPR / ATT Consent Reset** button.

---

## Content

### (1) Rarity and tier
Cat Skins and Ink Brush Trails are structured across **5 Rarity Levels** and **5 World Tiers**, driving collection goals and passive Coin bonuses.

**Rarity value:**

| Name | Value |
| :--- | :--- |
| **N (Normal)** | `1.00x` Base Coin Multiplier (Unlocked via Level Progression bar every 5 levels) |
| **R (Rare)** | `1.05x` Coin Multiplier (`+5%` Stage Coins; Unlocked via Daily Login, Star Chests, or Gacha) |
| **SR (Super Rare)** | `1.10x` Coin Multiplier (`+10%` Stage Coins; Unlocked via Gacha or Coin Shop) |
| **SSR (Super Super Rare)** | `1.15x` Coin Multiplier (`+15%` Stage Coins + Custom Stung/Victory Animation) |
| **UR (Ultra Rare)** | `1.25x` Coin Multiplier (`+25%` Stage Coins + Unique Particle Aura & Custom Meow Voice) |

**Tier value (Stage World Tiers & Base Coin Payouts):**

| Tier | Value |
| :--- | :--- |
| **Tier 1 (Levels 1–10: Backyard & Hills)** | Base `50 Coins` / Clear (`100 Coins` on Boss Lv. 5, 10) |
| **Tier 2 (Levels 11–20: Magma & Factory)** | Base `60 Coins` / Clear (`120 Coins` on Boss Lv. 15, 20) |
| **Tier 3 (Levels 21–30: Forbidden Garden & Citadel)** | Base `75 Coins` / Clear (`150 Coins` on Boss Lv. 25, 30) |
| **Tier 4 (Levels 31–100: Infinite Remix Mode I)** | Base `85 Coins` / Clear (`170 Coins` every 5th Boss Level) |
| **Tier 5 (Levels 101–∞: Infinite Master Mode)** | Base `100 Coins` / Clear (`200 Coins` every 5th Boss Level) |

- **Total Content Scope:**
  - **30 Handcrafted Core Levels** (with baked Blueprint Hints) + **Infinite Procedural Level Generator (Level 31 to $\infty$)**.
  - **15 Modular Terrain Chunks**, **8 Hazard Types**, **30 Collectible Cat Skins**, and **15 Ink Brush Trails**.

### (2) Statistic & Reward Formula
- **Base Stat Calculation (Stage Difficulty & Bee Force):**
  - **Bee Count per Hive:** $\text{Bees} = \min(12, 5 + \lfloor \text{Level} / 10 \rfloor)$
  - **Bee Attack Impulse:** $\text{Impulse} = \min(6.0, 3.5 + 0.02 \times \text{Level})$
  - **Line Mass per Segment:** $\text{SegmentMass} = 0.08 \times \text{BrushMassMultiplier}$
- **Final Reward Calculation:**
  $$\text{Coins Earned} = \lfloor (\text{Tier Base Coins} + (\text{Stars} - 1) \times 15) \times \text{Cat Rarity Value} \times \text{Ad Roulette Multiplier} \rfloor$$
  - *Example:* Clearing Level 22 (Tier 3 = `75 Coins`) with `3 Stars` (`+30 Coins`), equipping an **SSR Cat** (`1.15x`), and hitting `3x` on the Ad Roulette yields:
    $$\lfloor (75 + 30) \times 1.15 \times 3 \rfloor = \lfloor 120.75 \times 3 \rfloor = 362\text{ Coins}$$
- **Environment Mapping:**
  - Visual background themes rotate automatically every **10 levels** (`Sunny Backyard` -> `Autumn Hills` -> `Magma Cavern` -> `Honey Factory` -> `Sakura Garden` -> `Starlight Void`, then looping with day/dusk/night palettes in Infinite Mode).

### (3) Currency

The economy uses three clean currencies to balance free progression, ad engagement, and IAP conversion:

- **Coins (Primary Soft Currency):**
  - **Used in:** Pulling the **Lucky Neko Capsule Gacha** (`300–600 Coins`), purchasing **Brush Trails** (`1,000–4,000 Coins`), and upgrading **Cozy Cat Room Furniture**.
  - **Acquired from:** Stage clears (`50–100+ Coins`), Win Screen Ad Roulette (`2x–5x`), Star Chests, Daily Login, and Daily Missions.
- **Stars (Progression & Milestone Currency):**
  - **Used in:** Unlocking **Star Milestone Chests** (every `15 Stars` earned) and ranking on the Stage Select map (`1–3 Stars` per stage).
  - **Acquired from:** Clearing stages efficiently within the 2-Star (`\ge 25%` ink left) and 3-Star (`\ge 60%` ink left) thresholds. Replaying a 1-Star stage to get 3 Stars grants the net difference (`+2 Stars`).
- **Hint Tokens & Golden Ink Boosters (Tactical Utility Currencies):**
  - **Used in:** Activating the **Blueprint Dotted Hint** (`1 Hint Token`) or **Golden Electric Ink** (`1 Booster`) without watching an ad.
  - **Acquired from:** Rewarded Ads, Star Chests, Daily Login, Daily Missions, and IAP Starter/Booster Packs.

---

## Design
## UI Design

### (1) Characters design

The Cat protagonist is the emotional anchor and marketing face of the game—designed to be instantly readable at a small size and hilariously expressive under stress.

- **Style References:**
  - *Save the Doge* (expressive cartoon panic vs. swollen stung face)
  - *Neko Atsume* & *Pusheen* (round, squishy silhouette with minimal limbs)
  - *Crying Banana Cat / Pop Cat Memes* (viral internet cat humor)
- **Features:**
  - **Proportion Traits:** `1:1` round mochi-ball body silhouette (`CircleCollider2D` radius `0.45` units) so the cat rolls predictably on slopes and fits cleanly inside player-drawn domes.
  - **4 Mandatory Animation States per Cat Skin:**
    1. **Idle / Waiting (Draw Phase):** Calmly blinking, licking paw, or looking curiously at the player's finger cursor.
    2. **Panic / Sweating (Countdown Phase):** Wide trembling eyes, frantic ear twitching, and sweat drops flying whenever a bee comes within `1.5` units.
    3. **Hurt / Stung (Fail State):** Comically oversized lumpy cheeks, waterfall tears, and a dramatic wobble before flopping over.
    4. **Victory / Smug Dance (Win State):** Happy side-to-side wiggle with sunglasses or sparkling eyes.
  - **Color Palette Direction:** High-contrast pastel and warm fur tones (Cream White, Calico Orange, Tuxedo Black) that stand out clearly against both light sky backgrounds and dark drawn ink lines.
- **Special Design Notes:**
  - On **Twin Cat stages**, the two cats wear matching accessories (e.g., Red Bow & Blue Bow) and hug each other if both survive inside the same enclosure.

### (2) Important Design Notes
- **Visual Comfort / Mitigation:**
  - **Trypophobia & Insect Mitigation:** Beehives use stylized, chunky cartoon horizontal stripes (Winnie-the-Pooh honey-pot style) rather than realistic clustered hexagonal holes. Bees are plump, round, chibi cartoon bumblebees (`2-frame` wing flap) rather than realistic wasps.
  - **Slapstick, Non-Graphic Fail State:** When stung or touching lava, the reaction is purely cartoon comedy (plump red bump on the head or soot-covered cartoon puff)—zero blood or distressful audio.
- **Visual Style:**
  - Thick `6px` dark-brown/charcoal outer outlines on all interactive gameplay objects (`Cat`, `Beehive`, `Boulders`, `Drawn Line`) contrasted against low-contrast, soft-focus (`30%` desaturated) background illustrations so the puzzle geometry is 100% readable in 0.5 seconds.
- **Information Hierarchy:**
  - **Top HUD:** Stage Number (`LEVEL 14`), **7.0s Countdown Ring** (center), and **Ink Progress Bar with 3 Star Icons** directly underneath.
  - **Action Bar (Top-Right / Side):** Large, thumb-friendly **Retry (`↻`)**, **Blueprint Hint (`💡`)**, and **Golden Ink (`✨`)** buttons.
  - **Bottom Safe Area:** Bottom `120px` reserved strictly for the Banner Ad so the player never accidentally taps the banner while drawing near the bottom of the screen.

---

## Monetization

**Neko Line: Save the Cat!** uses a proven **Hybrid-Casual Monetization Model** (targeting **80% Ad Revenue / 20% IAP Revenue**) optimized for high Day-1 retention and rapid ROAS payback.

### (1) Ad monetization (option)

Integrated via **AppLovin MAX** (or **Google AdMob Mediation**) with bidding networks (Meta Audience Network, Unity Ads, Mintegral, IronSource, Pangle).

- **Banner Ads:**
  - Persistent `320x50` adaptive banner anchored at the bottom of the screen across Home and Gameplay screens (automatically hidden for `Remove Ads` purchasers).
- **MREC Ads (`300x250`):**
  - Displayed inside the **Pause Popup** and at the bottom of the **Stage Fail Popup** (after Level 6), positioned away from the primary `Retry` button to prevent accidental clicks and policy violations.
- **Interstitial Ads:**
  - **Grace Period:** **Zero Interstitial Ads on Levels 1–3** to guarantee a smooth FTUE and high D1 retention.
  - **Trigger Frequency & Cooldown:** Starting from **Level 4**, Interstitials trigger on `Stage Clear` or `Stage Retry` only when **at least `50 seconds`** have elapsed since the last Interstitial or Rewarded Ad (`interstitial_cooldown_sec = 50`, tunable via Remote Config).
  - Watching a **Rewarded Ad resets the Interstitial cooldown timer**, rewarding players who engage with opted-in ads.
- **Rewarded Ads (High-eCPM Opt-In Placements):**
  1. **Blueprint Hint (`ad_reward_hint`):** Reveals the 3-Star dotted guide line on the current stage.
  2. **Golden Super Ink (`ad_reward_super_ink`):** Grants `+50%` Ink and electric bee-zapping shield physics for 1 stage.
  3. **Last-Second Bubble Revive (`ad_reward_revive`):** Saves the cat when killed with $\le 2.5\text{s}$ left on the clock.
  4. **Skip Level (`ad_reward_skip`):** Skips the current stage after 2 fails.
  5. **Win Screen Coin Roulette (`ad_reward_roulette`):** Multiplies stage clear Coins by `2x` to `5x`.
  6. **Skin Unlock Claim (`ad_reward_skin`):** Every 5 levels (`100%` Skin Gauge), unlocks the featured Cat Skin (players can also choose *"No Thanks"* and buy it later in the Coin Shop).
  7. **Free Gacha Pull & Daily Login 2x (`ad_reward_gacha`, `ad_reward_daily_2x`).**

### (2) IAP monetization (option)

Focused on high-conversion friction-removal bundles (`Remove Ads`) and affordable impulse packs.

| SKU / Product ID | Package Name | Type | Contents / Effect | Price |
| :--- | :--- | :--- | :--- | :--- |
| **`com.etstudio.nekoline.noads`** | **No Ads Forever** | Non-Consumable | Permanently removes all Banner, MREC, and forced Interstitial Ads + Bonus `500 Coins` | **$2.99** |
| **`com.etstudio.nekoline.vipbundle`** | **VIP Guardian Bundle** | Non-Consumable | **No Ads Forever** + Exclusive **UR Angel Cat Skin** + **Golden Rainbow Brush** + `5 Hint Tokens` + `2,500 Coins` | **$6.99** |
| **`com.etstudio.nekoline.starter`** | **Purr-fect Starter Pack** | One-Time Offer | **SSR Samurai Cat Skin** + `5 Hint Tokens` + `5 Golden Ink Boosters` + `1,500 Coins` (`70% OFF` tag) | **$1.99** |
| **`com.etstudio.nekoline.hints_10`** | **Hint & Ink Pack** | Consumable | `10 Hint Tokens` + `10 Golden Ink Boosters` (Skip watching ads for hints!) | **$1.99** |
| **`com.etstudio.nekoline.coins_small`** | **Pouch of Coins** | Consumable | `3,000 Coins` | **$0.99** |
| **`com.etstudio.nekoline.coins_large`** | **Chest of Coins** | Consumable | `12,000 Coins` (`+20%` Bonus) | **$3.99** |

- **IAP Trigger & Promotion Flow:**
  - **No-Ads Popup:** Automatically offered once after the player watches their **2nd Interstitial Ad** (around Level 7–8), and every 10 levels thereafter if not purchased.
  - **Starter Pack Popup:** Triggered upon reaching the Home Screen after clearing **Level 5**.
- **Restore Purchases:**
  - Dedicated **"Restore Purchases"** button in Settings (mandatory for iOS App Store compliance) automatically re-validates Apple/Google receipts and re-applies `No Ads Forever` and `VIP Guardian Bundle` entitlements.

---

## Appliacation System
### (1) Push notifications
Local push notifications scheduled via `Unity Mobile Notifications` (`iOSNotificationCenter` / `AndroidNotificationCenter`) whenever the app enters the background (`OnApplicationPause(true)`), automatically canceled and rescheduled on launch.

| Interval     | Push Title                             | Push Body                                     |
| :----------- | :------------------------------------- | :-------------------------------------------- |
| **6 Hours**  | 🐝 Bzzz! The bees are back!            | Quick! Draw a shield before your cat gets stung on Level {CurrentLevel}! 🐱✏️ |
| **12 Hours** | 🎁 Free Lucky Capsule Ready!           | Your cat saved a shiny Coin gift for you. Come spin the Gacha machine! 🐾 |
| **24 Hours** | 😿 Meow... Where did you go?           | Day {StreakDay} Login Reward is waiting! Don't leave your kitty unguarded! 🛡️ |
| **48 Hours** | ✨ Free Golden Ink Booster Unlocked!   | Stuck on a tricky puzzle? Claim your free Super Ink and breeze past Level {CurrentLevel}! |

### (2) Asset Dilivery by Addressable
Uses **Unity Addressables** combined with ultra-lightweight procedural `LevelDataSO` files to keep the initial APK/AAB install size **under `45 MB`** (maximizing Google Play / App Store click-to-install conversion).

- **Addressable Groups Strategy:**
  - **Local Built-in Groups (`Packed_Local_Core`):**
    - Startup UI, Tutorial assets, the 15 modular `TerrainChunk` prefabs, all 8 `HazardNode` prefabs, all 30+ `LevelDataSO` JSON/ScriptableObjects (`<100 KB` total), Core SFX/BGM, and the first 10 Cat Skins.
  - **Remote Downloadable Groups (`Remote_Cosmetics_And_Themes`):**
    - High-resolution background theme packs for Worlds 3–6, seasonal live-ops Cat Skins (Skins 11–30), UR particle effects, and bonus audio tracks hosted on Cloud CDN (Cloudflare R2 / Unity CCD).
- **Download & Preload Flow:**
  - The game is **100% playable offline from Level 1 to $\infty$ immediately upon install** using Local Built-in Groups.
  - Remote cosmetic and background bundles download silently in the background (`Addressables.DownloadDependenciesAsync`) once the player reaches Level 5, without blocking gameplay.
- **Memory & Cache Management:**
  - Only the active stage's background sprite and equipped Cat Skin spine/sprite atlas are kept in memory; previous world backgrounds are released via `Addressables.Release()` on world transitions.
- **Fallback & Error Handling:**
  - If the player is offline when entering World 3+ and the remote background bundle hasn't cached yet, the stage seamlessly falls back to the built-in `Sunny_Backyard_BG` so gameplay is never interrupted.

### (3) Multiple Input Intergrate
Built on **Unity's New Input System (`UnityEngine.InputSystem`)** with a unified pointer abstraction (`Pointer.current`) so line drawing feels identical on mobile touchscreens, tablets, PC emulators (Google Play Games on PC), and WebGL builds.

| Input Device | Supported Platform | Primary Actions Mapping | UI Navigation Behavior |
| :--- | :--- | :--- | :--- |
| **Touchscreen** | Mobile (iOS / Android) | **Single-finger Press & Drag** to draw line; **Lift Finger** to drop line and start countdown; **Tap (`↻`)** for instant 0.1s stage retry | Direct touch interaction with `1.1x` scale bounce on buttons |
| **Mouse & Keyboard** | PC / WebGL / Mac / Emulator | **Left-Click Hold & Drag** to draw line; **Release Left-Click** to start countdown; **`R` Key** for instant retry; **`H` Key** for Hint | Cursor changes to a **Pencil/Brush icon** when hovering over valid draw space, and a **Red Cross (`🚫`)** over No-Draw zones |
| **Controller / Gamepad** | Console / PC / Apple TV (Optional) | **Left Stick** moves brush cursor; **Hold `RT` / `South Button (A/Cross)`** to draw stroke; **Release** to start simulation; **`Y / Triangle`** to retry | D-Pad snaps focus across UI popups with visible button prompts |

- **Dynamic Input Switching:**
  - Automatically detects active pointer (`Touchscreen.current` vs. `Mouse.current` vs. `Gamepad.current`) and hides the virtual brush cursor on touch devices while displaying it on Mouse/Gamepad.
- **Input Rebinding / Accessibility:**
  - Includes **Line Smoothing Sensitivity** (`Low / Medium / High` Catmull-Rom spline smoothing) and **One-Handed Left/Right HUD Flip** in Settings.

---

## Appliacation Control and Maintainance
### (1) Analysis (option)

Integrated with **Firebase Analytics**, **Adjust / AppsFlyer MMP**, and **AppLovin MAX Impression-Level Ad Revenue (ILAR)** to measure cohort LTV, level funnel drop-offs, and ad ROAS.

- **Current Tracking Capabilities:**
  - **User / Device ID Retrieval:** Generates and persists a local `InstallUUID` alongside `IDFA` (via iOS ATT prompt) / `GAID` (Android) for attribution and crash diagnostics.
  - **Revenue & Event Tracking:**
    - **Level Funnel Events:** `level_start`, `level_complete` (params: `level_id`, `attempt_count`, `stars_earned`, `ink_used_pct`, `is_procedural`), and `level_fail` (params: `level_id`, `cause_of_death` [bee/lava/spike/fall], `time_remaining_sec`).
    - **Monetization Events:** `ad_impression_revenue` (real-time ILAR ping sent to Firebase/Adjust), `rewarded_ad_complete` (param: `placement` [hint/super_ink/revive/skip/roulette/skin]), and `iap_purchase_verified`.
    - **Retention Milestone Pings:** `level_5_reached`, `level_15_reached`, `level_30_completed`, `level_50_infinite_reached`, and `ad_watch_milestone_{5,10,25,50}`.

### (2) Remote control (option)
Powered by **Firebase Remote Config** (fetched on app launch with a `3-second` timeout fallback to compiled defaults) so designers can live-tune ad pacing, difficulty, and infinite level scaling without submitting a new binary.

- **App Version & Maintenance Control:**
  - **Force Update:** Compares `Application.version` against `min_required_version`; if older, shows a non-dismissible popup redirecting to the App Store / Google Play Store.
  - **Maintenance Mode:** Displays a cute "Cats are napping for maintenance!" banner with countdown timer when `maintenance_mode == true` (bypassed for QA devices listed in `whitelist_device_ids`).
- **Feature Flags & Live Balancing:**
  - Allows A/B testing interstitial cooldowns (`35s` vs. `50s` vs. `65s`), stage countdown duration (`6.0s` vs. `7.0s`), and bee knockback force in real time to maximize D1/D7 retention and ARPDAU.

| Remote Key | Data Type | Default Value | Description / Usage |
| :--- | :--- | :--- | :--- |
| **`maintenance_mode`** | Boolean | `false` | Locks live access during critical backend/store maintenance |
| **`min_required_version`** | String | `"1.0.0"` | Triggers mandatory store update prompt if client version is lower |
| **`interstitial_start_level`** | Int | `4` | First level index where Interstitial Ads are allowed to show |
| **`interstitial_cooldown_sec`** | Int | `50` | Minimum seconds required between two Interstitial Ad impressions |
| **`base_survival_countdown_sec`** | Float | `7.0` | Global survival countdown duration (in seconds) for standard stages |
| **`bee_force_multiplier`** | Float | `1.0` | Global physics multiplier on bee attack thrust for live difficulty tuning |
| **`infinite_mode_budget_scale`** | Float | `1.0` | Scales the procedural hazard budget formula for Levels 31 to $\infty$ |
