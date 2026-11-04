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
           │
           ▼
[Lane Battle: Manage Funds & Spawn Units] ──► [Deploy Super Weapon / Cannon]
           │
           ▼
    [Victory / Defeat]
           │
     ┌─────┴────────────────────────┐
     ▼                              ▼
[Earn Coins & Fish Treats]   [Defeat: Watch Ad / Retry]
     │
     ▼
[Upgrade Niiiko Roster & Base Cannon Stats]
     │
     ▼
[Unlock Next Global Region / Relic Buff]
```

### 3.1 Battle Mechanics

- **Lane Setup:** Single horizontal 2D battlefield. The player's Niiiko Research Lab is on the left; the Human Outpost/City Base is on the right.
    
      
    
- **Energy / Money Generation:** An automatic resource meter (_Catnip Cash / Money_) ticks upward in real time.
    
      
    
- **Unit Summoning:** Tapping an available unit icon on the deployment deck spends the required cash and spawns that unit, which marches rightward toward the human base.
    
      
    
- **Collision & Engagement:** Units advance until encountering opposing units or bases within their attack range. Combat triggers automatically according to unit attack cooldowns and reach.
    
      
    
- **Knockback Mechanism:** Dealing a threshold amount of burst damage forces units backward, providing defensive breathing room.
    
      
    
- **Base Super Weapon (Niiiko Particle Blaster):** A rechargable manual skill with a long cooldown that sweeps the entire screen or an area-of-effect (AoE) zone to clear swarms or knock back advancing bosses.
    
      
    
- **Win/Loss Conditions:**
    
      
    - **Victory:** Destroy the human base on the far right (reduce HP to 0).
        
          
        
    - **Defeat:** The player's laboratory on the far left is destroyed.
        
          
        

## 4. Unit Design & Rosters

### 4.1 Niiiko Units (Player Army)

|**Unit Name**|**Role**|**Cost**|**Speed**|**Attack Type**|**Special Trait / Mechanic**|
|---|---|---|---|---|---|
|**Lab-Coat Niiiko**|Meatshield / Swarm|50|Fast|Single Target (Melee Wrench)|Low cooldown, cheap cost; stalls high-damage human attackers.|
|**Toolbox Niiiko**|Tank|120|Moderate|Single Target (Heavy Hammer)|High HP; resists initial knockbacks from human charges.|
|**Beaker Niiiko**|Ranged DPS|220|Slow|AoE (Splash Acid Vial)|Throws bubbling beakers from safe distance; counters dense swarms.|
|**Long-Leg Niiiko**|Single-Target Sniper|450|Moderate|Long Range (Laser Pointer)|Massive burst damage against high-HP human tank units.|
|**Mech-Suit Niiiko**|Uber Boss / Finisher|950|Slow|Heavy AoE (Piston Slam)|Massive health, high damage, ground-slam knocks enemies backward.|

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
|**Thailand**|Stages 6–10|Night markets, neon tuk-tuks, street vendor shielders.|_Golden Spices:_ +10% Money Generation speed.|
|**Singapore**|Stages 11–15|Futuristic high-rise CBD, security drones, high-tech boss barricades.|_Transit Card:_ -8% Deploy Cost on all units.|

## 6. Economy, Progression & Monetization

### 6.1 Currencies

- **Catnip Cash (Soft Currency 1 - In-Battle):** Generated during matches to deploy units and upgrade the in-match money production rate.
    
      
    
- **Fish Treats / Coins (Soft Currency 2 - Meta):** Awarded from stage completions; used to level up unit base stats (HP, Attack) and laboratory features (Max Base HP, Cannon Recharge Rate).
    
      
    
- **Niiiko Gems (Hard Currency):** Earned via achievements or bought via IAP; used for special gacha pulls and premium boosters.
    
      
    

### 6.2 Ad Placements (Hybrid Monetization)

```
┌─────────────────────────────────────────────────────────────┐
│                      AD INTEGRATION                         │
├──────────────────────────────┬──────────────────────────────┤
│ Rewarded Video               │ Interstitial Ads             │
├──────────────────────────────┼──────────────────────────────┤
│ • Double Post-Battle Coins   │ • Shown once every 3-4       │
│ • Instant Energy Refill      │   completed/failed matches.  │
│ • Free Daily Unit Gacha Pull │ • Skippable after 5 seconds. │
│ • Emergency Mid-Battle Cannon│ • Disabled permanently via   │
│   Recharge (1x per match)    │   any IAP purchase.          │
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
        
          
        

### 7.2 UI/HUD Layout (Original & IP-Safe)

- To guarantee zero policy conflicts with existing titles:
    
      
    - Deploy deck uses a bottom-right rounded grid panel rather than a flat bottom horizontal ribbon.
        
          
        
    - Money counter and production level upgrade are grouped top-left in a modern circular laboratory gauge.
        
          
        
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