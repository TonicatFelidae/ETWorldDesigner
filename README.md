# 🪐 ETWorldDesigner

> **A World-First Game Ecosystem & Design Architecture**
>
> *Build the world first — its planets, lands, races, magic, and history — and spawn an entire constellation of games across multiple genres within that living universe.*

---

## 🌌 Vision: The World-First Philosophy

In traditional game development, games are often designed in isolation: a single game loop is invented, a disposable world is wrapped around it, and when the project finishes, all worldbuilding assets and lore are discarded.

**ETWorldDesigner flips this paradigm:**

```
                  ┌─────────────────────────────────────┐
                  │          THE LIVING WORLD           │
                  │   Planets • Continents • Factions   │
                  │   Races • Magic Systems • History   │
                  └──────────────────┬──────────────────┘
                                     │
           ┌─────────────────────────┼─────────────────────────┐
           ▼                         ▼                         ▼
   ┌───────────────┐         ┌───────────────┐         ┌───────────────┐
   │ Town Defense  │         │      RTS      │         │ RPG / Survival│
   │ "Hold the     │         │ "Empire Wars  │         │ "Explore the  │
   │  Frontier"    │         │  & Conquest"  │         │  Wilderness"  │
   └───────────────┘         └───────────────┘         └───────────────┘
```

1. **The Universe is the Core Asset**: We design deep, cohesive foundations: cosmology, planetary geography, distinct races, geopolitical factions, magic/technology laws, and historical timelines.
2. **Games are Lenses into the World**: Each game is a specific window into this universe, experiencing the same world at different scales, perspectives, and eras:
   - Defend a frontier outpost against indigenous behemoths (**Town Defense / Colony Survival**).
   - Command continental armies in grand faction warfare (**Real-Time Strategy**).
   - Infiltrate ancient ruins as an operative or adventurer (**Tactical RPG / Action**).
   - Explore regional trade routes and naval conflicts (**Management / 4X**).
3. **Cumulative Value**: Every unit design, faction trait, cultural belief, and geographical location developed in the world bible immediately feeds into *every* past, present, and future game.

---

## 🏛️ Project Architecture

This repository acts as the master knowledge vault (Obsidian-ready) and design hub, separated into two complementary engines:

```
ETWorldDesigner/
├── 🌍 WorldDesigner/            # The Universe Engine (Lore, Systems, Cosmology)
│   ├── 🪐 Cosmology/           # Planets, star systems, celestial rules
│   ├── 🗺️ Geography/           # Continents, biomes, regions, maps, cities
│   ├── 🧬 Races & Factions/     # Species, cultures, traits, political powers
│   ├── 🔮 Systems/             # Magic laws, technology trees, natural laws
│   ├── 📜 Lore & Chronology/   # Timelines, historic wars, myths, legends
│   └── 🎨 World Style Guide/   # Visual identities, architecture, heraldry
│
├── 🎮 GameDesigner/             # The Game Engine (Mechanics, Design Docs, Prototypes)
│   ├── 🛡️ TownDefense/          # Frontier siege, tower & colony survival
│   ├── ⚔️ RTS/                  # Real-Time Strategy: factions, economy, units
│   ├── 🏹 RPG_Tactics/          # Squad tactics, character progression, dungeon crawls
│   └── 🧩 SharedAssets/         # Naming bibles, shared rule sets, design tokens
│
└── 🤖 .obsidian/               # Obsidian vault settings & graph database
```

---

## 🌍 Layer 1: WorldDesigner (The Master Bible)

The world is structured hierarchically from planetary macro-scale down to individual cultural artifacts:

### 1. Planets & Environments (`/Geography`)
- **Celestial Bodies**: Planetary orbit, climate zones, moons, day/night cycles, seasonal hazards.
- **Biomes & Territories**: Bioluminescent fungal forests, crystal barrens, magma deltas, floating archipelagos.
- **Strategic Resources**: Rare ores, arcane leylines, sacred flora, and energy sources that drive geopolitical friction.

### 2. Races & Civilizations (`/Races & Factions`)
- **Biology & Psychology**: Physical strengths, sensory perception, lifespans, instinctual drives.
- **Societies & Philosophies**: Governance (theocracies, technocracies, clans), religious pantheons, moral taboos.
- **Faction Dynamics**: Historical alliances, rivalries, trade treaties, and existential tensions.

### 3. Magic & Technology Systems (`/Systems`)
- **Universal Rules**: Where does energy originate? What are the strict limitations and costs?
- **Socio-technical Integration**: How do everyday citizens use magic/tech? How does it shape warfare, transport, and architecture?

---

## 🎮 Layer 2: GameDesigner (Genre Manifestations)

Every game project maps directly back to entities defined in `WorldDesigner`:

| Game Concept | World Context | Gameplay Experience |
| :--- | :--- | :--- |
| **Outpost Town Defense** | A fledgling mining expedition on a hostile continent | Build walls, manage workforce, deploy faction-specific guard towers, and survive nightly swarms of native creatures. |
| **Continental RTS** | The Great Succession War between major empires | Macro-economy, base building, tech trees reflecting faction lore, heroic commanders, and combined-arms warfare. |
| **Tactical Dungeon RPG** | Ancient precursor vaults beneath a collapsed capital | Small squad tactics, deep elemental magic interactions, lore exploration, artifact retrieval. |
| **Survival Roguelike** | Stranded scout behind enemy lines during a cataclysm | Resource foraging, stealth, understanding local fauna/flora rules to stay alive. |

---

## 🤖 AI-Powered Design Pipeline

ETWorldDesigner integrates with AI workflows to accelerate the bridge between imagination and production:

- **Lore Consistency Verification**: Validating that new faction units, spell mechanics, and events align with the established world bible.
- **Generative Concept Prototyping**: Generating architectural style guides, faction emblems, unit rosters, and dialogue samples based on world constraints.
- **Mechanics Translation**: Translating world lore (e.g., *"Race X has brittle bones but commands resonance magic"*) into concrete game mechanics (e.g., *low HP pool, pulsing AoE sound attacks*).

---

## 🚀 Getting Started

1. **Open in Obsidian**: Open the `ETWorldDesigner` directory as a vault to browse lore links, tags, and relational graph views.
2. **Start with World Seed**: Begin in `WorldDesigner/` by establishing the core planetary rules and initial 2–3 factions.
3. **Draft the First Game**: Choose a focused game format (such as a Town Defense prototype) in `GameDesigner/` that showcases one specific conflict within the world.
