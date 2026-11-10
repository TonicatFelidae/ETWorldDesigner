# Game Design Document: Niiiko vs Human: Cat Girl Defense

## 1. Executive Summary & Overview

- **Game Title:** Niiiko vs Human: Cat Girl Defense
    
      
    
- **Platform:** Mobile (Android primary via Google Play, iOS secondary)
    
      
    
- **Genre:** 2D Side-Scrolling Tower Defense / Lane Battler
    
      
    
- **Target Audience:** Casual mobile gamers, anime/cat-girl enthusiasts, fans of _The Battle Cats_ and meme-humor defense titles.
    
      
    
- **Monetization Model:** Free-to-Play (F2P) supported by Hybrid Monetization (Rewarded Ads, Interstitials, Optional IAP Starter/Gem packs).
    
      
    
- **Core Philosophy / Elevator Pitch:** Command an army of quirky, lab-coat cat-girls to establish independent Niiiko rule across the globe, repelling waves of ridiculous, degenerate human enemies using cartoon slapstick combat and experimental super-science.
    
      
    

## 2. Core Narrative & Visual Style

### 2.1 Narrative Premise

Frustrated by human inefficiency, greed, and general weirdness, the Niiiko race decides humanity’s reign is over. From their clandestine research laboratories, the Niiikos mobilize to declare sovereign rule across Earth's major cities. Humans, refusing to concede power, deploy their strangest characters—from frantic street swarms to greasy corporate suits—to reclaim their cities.

  

### 2.2 Art & Visual Direction

- **Style:** 2D clean cell-shaded/vector cartoon anime aesthetic with expressive, hand-drawn sprite animations.
    
      
    
- **Tone:** Parody, slapstick, and comedic hyperbole.
    
      
    
- **Safety & Compliance (IARC Everyone 10+ / Teen):**
    
      
    - Attacks consist purely of cartoon bonks, wrench slaps, comical laser zaps, and puff-of-smoke or flying-into-the-sky knockouts.
        
          
        
    - Human enemy attack patterns are exaggerated and humorous (awkward disco flailing, dazzling smiles, frantic stomping) with zero sexualized contact or gore.
        
          
        

## 3. Core Gameplay Loop

```
[World Map / Stage Selection]
           │ (Spends 10 Energy [Main Menu])
           ▼
[Lane Battle: Push Frontline ──► Reveal Ghost Build Slots (+)]
           │                              │ (Pay Coins to Claim Slabs)
           │                              ▼
           │                     [Construct Buildings: Cannery / Mound / Lab]
           │                              │ (Acts as Forward Rally Point)
           ▼                              ▼
[Summon Niiiko Units with Food] ◄─────────┘
           │
           ├──► [Defend Supply Chain Against Advancing Humans]
           │
           ├──► [Deploy Particle Blaster (Cat Coins)]
           │
           ▼
    [Victory / Defeat]
           │
     ┌─────┴────────────────────────┐
     ▼                              ▼
[Earn EXP & Relics]          [Defeat: Watch Ad / Retry]
     │
     ▼
[Main Menu: Spend EXP to Unlock New Cats]
     │
     ▼
[Unlock Next Global Region / Relic Buff]
```

### 3.1 Battle Mechanics

- **Lane Setup:** Single horizontal 2D battlefield. The player's Niiiko Research Lab is on the left; the Human Outpost/City Base is on the right.
    
      
    
- **In-Battle Resources (Food & Cat Coins):**
    - **0: Food (Fish Can):** An automatic resource meter ticks upward in real time. Food is used exclusively in-battle to buy and summon units.
    - **1: Coin (Cat Coin):** Dropped during combat by damaging and defeating human enemies. Cat Coins are used exclusively in-battle to upgrade the Worker Production Gauge (increasing Food generation speed and capacity) and to activate/power in-battle weapons.
    
      
    
- **Unit Summoning:** Tapping an available unit icon on the deployment deck spends the required **Food (Fish Cans)** and spawns that unit, which marches rightward toward the human base.
    
      
    
- **Collision & Engagement:** Units advance until encountering opposing units or bases within their attack range. Combat triggers automatically according to unit attack cooldowns and reach.
    
      
    
- **Knockback Mechanism:** Dealing a threshold amount of burst damage forces units backward, providing defensive breathing room.
    
      
    
- **Base Super Weapon (Niiiko Particle Blaster):** A rechargeable in-battle weapon powered by **Coins (Cat Coins)** that sweeps the entire screen or an area-of-effect (AoE) zone to clear swarms or knock back advancing bosses.
    
      
    
- **Win/Loss Conditions:**
    
      
    - **Victory:** Destroy the human base on the far right (reduce HP to 0).
        
          
        
    - **Defeat:** The player's laboratory on the far left is destroyed.
        
          
        

### 3.2 Progressive Territory Expansion (Slot System)

*(Visual Reference: [Demo Map.png](Demo%20Map.png))*

![Demo Map: Territory Expansion & Battlefield HUD](Demo%20Map.png)

Unlike *The Battle Cats*, the battlefield is an active, conquerable supply territory:

1. **The Core Mechanic:** Players start with only their Main Base (left) and 0 forward build slots. As Niiiko combatants push enemies backward across the lane, a ghost outline with a glowing yellow `+` indicator is revealed.
2. **Claiming Slabs:** Pay a scaling Coin cost to establish a paved grey foundation slab. Slots must be unlocked in sequence from left to right.
3. **Building Construction:** Tapping an open slab allows the real-time choice of constructing:
   - **Fish Cannery:** Boosts passive Food income (`+X Food/sec`). Focus here to spam huge swarms.
   - **Fortified Barricade (Mound):** High-health roadblock that passively attacks back or serves as a physical chokepoint to protect previous investments.
   - **Research Lab:** Boosts Coin production (`+Y Coins/wave`) or unlocks battlefield-wide damage modifiers.
4. **Hazard Level: Protecting Your Supply Chain:**
   - **High Risk / High Reward:** Unlike *The Battle Cats*, the backline is no longer invulnerable. If human attackers overwhelm your defense line, they will stop and attack your economic buildings.
   - **Destruction & Reclamation:** If a building's HP is reduced to 0, it is destroyed, removing your resource boost. The slot becomes an "Empty Ruin" that you must pay to reclaim and rebuild once the line is re-secured.
   - **Aggressive Advantage:** Expanding forward reduces the deploy-to-fight distance, acting as a forward rally point. You must aggressively protect this frontline to prevent economic collapse.

## 4. Unit Design & Rosters

### 4.1 Niiiko Units (Player Army)

|**Unit Name**|**Role**|**Food Cost**|**Speed**|**Attack Type**|**Special Trait / Mechanic**|
|---|---|---|---|---|---|
|**Lab-Coat Niiiko**|Meatshield / Swarm|50 Food|Fast|Single Target (Melee Wrench)|Low cooldown, cheap cost; stalls high-damage human attackers.|
|**Toolbox Niiiko**|Tank|120 Food|Moderate|Single Target (Heavy Hammer)|High HP; resists initial knockbacks from human charges.|
|**Beaker Niiiko**|Ranged AoE / Splash Damage|220 Food|Slow|AoE (Splash Acid Vial)|Throws bubbling beakers from safe distance; counters dense swarms.|
|**Long-Leg Niiiko**|Single-Target Sniper|450 Food|Moderate|Long Range (Laser Pointer)|Massive burst damage against high-HP human tank units.|
|**Mech-Suit Niiiko**|Uber Boss / Finisher|950 Food|Slow|Heavy AoE (Piston Slam)|Massive health, high damage, ground-slam knocks enemies backward.|

### 4.2 Human Enemies (Opponents)

|**Unit Name**|**Role**|**Behavior & Mechanics**|**Counter Strategy**|
|---|---|---|---|
|**Trench-Coat Dasher**|Fast Rusher|Scurries quickly down the lane in an oversized coat; low HP.|Spam cheap Lab-Coat Niiikos early to prevent line collapse.|
|**Greasy Uncle (Tank)**|Heavy Tank|Trudges forward performing an awkward, flailing disco shuffle that deals contact damage; very high health.|Deploy Beaker Niiiko behind frontline tanks to melt his HP.|
|**Charming Tricker**|Debuffer / Crowd Control|Flashes a dazzling sparkling smile; causes frontline Niiikos to pause/freeze for 2 seconds.|Long-Leg Niiiko snipes him before he enters charm range.|
|**Capture Specialist**|Disabler|Fires net launchers that temporarily trap frontline units in place.|Swarm with cheap units so valuable high-tier units stay safe.|
|**City Commissioner (Boss)**|Stage Boss|Slow moving, massive health pool; stomps ground to wipe small swarms.|Time the Base Cannon discharge to interrupt his windup.|

## 5. World Map & Stage Progression (MVP Chapter 1: Southeast Asia)

To validate the game quickly, Chapter 1 launches with 15 focused stages across 3 primary cultural hubs:

  

|**Region**|**Stages**|**Environment & Thematic Gimmick**|**Completion Relic Reward**|
|---|---|---|---|
|**Vietnam**|Stages 1–5|Old town alleyways, motorcycle rushers, street-cart barricades.|_Drip Coffee:_ +10% Unit Movement Speed across all units.|
|**Thailand**|Stages 6–10|Night markets, neon tuk-tuks, street vendor shielders.|_Golden Spices:_ +10% Food Generation speed.|
|**Singapore**|Stages 11–15|Futuristic high-rise CBD, security drones, high-tech boss barricades.|_Transit Card:_ -8% Food Deploy Cost on all units.|

## 6. Economy, Progression & Monetization

### 6.1 Currencies

The game features four strictly partitioned currencies across two operational contexts:

- **0: Food (Fish Can) [In-Battle Only]:** Used solely in battle to buy and deploy Niiiko units onto the lane. Automatically accumulates in real time based on the active Worker Production Level.
    
      
    
- **1: Coin (Cat Coin) [In-Battle Only]:** Used solely in battle to upgrade the Worker Production Gauge (increasing Food tick rate and max storage cap) and to power/fire in-battle weapons (Niiiko Particle Blaster). Earned during combat from defeating human enemies.
    
      
    
- **2: EXP [Main Menu Only]:** Used exclusively in the Main Menu to unlock new cats / cat-girls in the Niiiko Lab Roster. Earned by clearing stages, completing daily missions, and fulfilling milestones.
    
      
    
- **3: Energy [Main Menu Only]:** Used exclusively in the Main Menu to enter battles (`10 Energy` per battle attempt). Automatically regenerates over time (`1 Energy` every `2.5 minutes`, cap `100`).

### 6.2 Ad Placements (Hybrid Monetization)

```
┌─────────────────────────────────────────────────────────────┐
│                      AD INTEGRATION                         │
├──────────────────────────────┬──────────────────────────────┤
│ Rewarded Video               │ Interstitial Ads             │
├──────────────────────────────┼──────────────────────────────┤
│ • Double Post-Battle EXP     │ • Shown once every 3-4       │
│ • Instant Energy Refill      │   completed/failed matches.  │
│ • Free Daily Unit Gacha Pull │ • Skippable after 5 seconds. │
│ • Emergency Mid-Battle Cannon│ • Disabled permanently via   │
│   Boost (1x per match)       │   any IAP purchase.          │
└──────────────────────────────┴──────────────────────────────┘
```

## 7. Technical Architecture & Production Strategy

### 7.1 Engine & Systems

- **Engine:** Unity / Godot (2D pipeline).
    
      
    
- **Target Build Size:** Under 70MB for rapid mobile downloading over cellular networks.
    
      
    
- **Code Reusability (85% Target):**
    
      
    - _Unit Logic:_ Standardized state machines (`Idle`, `Move`, `Attack`, `Knockback`, `Die`).
        
          
        
    - _UI Framework:_ Tabbed decks, shop interface, and modal dialogs adapted directly from previous studio frameworks.
        
          
        
    - _Ad Architecture:_ Reusable wrapper for Google Mobile Ads (AdMob) handling rewarded video callbacks, banner mediation, and interstitial frequency capping.
        
          
        

### 7.2 UI/HUD Layout (Original & IP-Safe — Matching `Demo Map.png`)

- To guarantee zero policy conflicts with existing titles:
    
      
    - Deploy deck uses a bottom-right rounded, cat-eared `Summoning Deck` panel with card slots rather than a flat bottom horizontal ribbon (as shown in `Demo Map.png`).
        
          
        
    - Food and Coin counters are housed in a top-left cat-eared wooden plaque displaying available Food (Fish Cans) and Cat Coins.
        
          
        
    - Top-right cat-eared banner displays the active territory slab counter (e.g., `3/5` build slots), elapsed time, and a pocket-watch stage timer (`Tim 10m`).
        
          
        
    - Intermediate battlefield displays sequential grey foundation slabs with constructed buildings (Fish Cannery, Fortified Mound), forward rally spawn points, and glowing yellow `+` ghost indicators for unclaimed slabs.
        
          
        
    - Cannon skill is placed inside an interactive mechanical syringe/dial icon on the lower left.
        
          
        

## 8. Milestone Production Roadmap (30-Day MVP Plan)

- **Phase 1 (Days 1–7) — Core Mechanics & Lane Framework:**
    
      
    - Import existing 2D framework; configure horizontal lane physics and collision layers.
        
          
        
    - Integrate unit state machines, basic attack logic, and base HP damage systems.
        
          
        
- **Phase 2 (Days 8–16) — Art Integration & Polish:**
    
      
    - Implement final sprite sheets for 5 Niiiko units, 5 human enemy types, and 3 regional backgrounds.
        
          
        
    - Build cartoon knockback effects, defeat dust puffs, and hit-stop visual feedback.
        
          
        
- **Phase 3 (Days 17–23) — Meta Loop & Monetization:**
    
      
    - Implement World Map UI and stage progression tracking.
        
          
        
    - Connect AdMob rewarded ads (double rewards, energy refills) and interstitial frequency logic.
        
          
        
- **Phase 4 (Days 24–30) — Testing, Polish & Rollout:**
    
      
    - Perform difficulty curve balance on Stages 1 through 15.
        
          
        
    - Prepare store listing assets (app icon, screenshots, 15-second 9:16 and 16:9 gameplay ad cuts).
        
          
        
    - Push to Google Play internal/closed testing tracks for live UA baseline validation.