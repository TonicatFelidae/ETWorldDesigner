# Neko Seek (CNekoSeek)

A Cozy Hand-Drawn Hidden-Cat & Collection Adventure
Product Vision & Game Design Document
ETStudio / 2026

---

## Game Concept

| Concept | Value |
| :--- | :--- |
| **Title** | Neko Seek (`CNekoSeek` / ポイ活にゃんこをさがせ！ / Pにゃんこをさがせ！：ねこの探し物ゲーム) |
| **Subtitle** | Find the Hidden Cats & Complete the Cat Card Collection! |
| **Description** | Players explore sprawling, hand-drawn illustrated worlds—from bustling Cat City and ancient Desert Pyramids to Tropical Islands, Eastern Villages, and Outer Space—panning and zooming to spot mischievous hidden cats and secret treasure chests. Finding cats builds up a Fever combo multiplier, unlocks 3-piece fractional Cat Cards with multi-tier lore bios, and rewards players with Clues, Gacha Tickets, and Energy. |
| **Genre** | Hidden Object / Casual Puzzle / Collection |
| **Theme** | Cute, cozy, whimsical, relaxing |
| **Setting** | Illustrated diorama worlds inhabited by themed cats across 5 distinct campaigns (Cat City, Desert Pyramid, Tropical Island, Eastern Village, Outer Space) |
| **Player Role** | Cat Seeker & Collector |
| **Core Gameplay** | Pan, zoom, and tap to find hidden cats and 3 hidden treasure chests per stage while maintaining a Fever combo multiplier |
| **Objective** | Clear all campaign stages across 3 difficulties (Easy, Normal, Hard), collect all 3 stars per stage to unlock all 20+ Cat Cards and their secret bios, and claim collection milestone rewards |
| **Progression** | Campaign-based vertical node path (10 rounds per campaign, 3 difficulties per round), User Leveling (`GameplayLevelConfig`), Cosmetic Score Level (`LevelingConfig`), and Cat Card Shelf Collection |
| **Unique Selling Point** | Combines relaxing hand-drawn hidden-object gameplay with a rhythmic 5-tier Fever combo system, 3-difficulty replayability (15 / 30 / 50 cats) that progressively unlocks deeper character lore (Common / Rare / Premium bios), and fractional 3-piece Cat Card reveals tied to hidden treasure chests. |
| **Art Style** | 2D hand-drawn line art backgrounds with color-fill pop animations on discovered cats and vibrant chibi cat character cards |
| **Audio (BGM/SFX)** | Upbeat, cozy background music per screen (`BG0` Home, `BG1–4` Gameplay, `BG4` Gacha, `BG5` Collection) paired with dynamic pitch-shifting cat meow SFX (`1.0x` to `1.4x` pitch during Fever) and light haptic vibration feedback |
| **Target Audience** | Casual mobile puzzle players & cat lovers (All ages, core demographic Women 10–40) |
| **Platform** | Android, iOS |

---

## References

- **Unity Project Path:** `/Users/taniafelidae/UnityProjects/CNekoSeek`
- **Google Sheet Data Sync (`ScriptableSheet`):** Sheet ID `1a1XANLjNPD5wr91zZeEicF6An1_LpCX8BNEuud6xHj8` (`CampaignData`, `RoundData`)
- **Visual / Market References:** *Hidden Folks*, *Find Out*, *Cats Hidden in Paris*

---

## Game cycle

A full gameplay cycle in **Neko Seek** flows from the Home Screen node path into an interactive hidden-object stage and concludes at the Result & Card Reveal screen:

- **Step 1 (Preparation / Input):** On the `HomeScreen`, the player selects a Campaign (via `CampaignMapScreen`), focuses an unlocked Round node on the vertical `ProgressPath`, optionally toggles the difficulty (`EASY` / `NORMAL` / `HARD` once Easy is cleared), and taps **Play** to spend **Energy** (`2` / `4` / `8` Energy based on difficulty).
- **Step 2 (Active / Seek Phase):** Inside `PlayScreen`, the player pans and pinch-zooms (`ETImageZoom`) across the stage illustration to tap hidden cats (`CatTouchPoint`) and up to 3 hidden treasure chests (`ChestTouchPoint`). Finding cats rapidly builds the **Fever Gauge** for up to `3.0x` score, while tapping empty background penalizes `-1` User Point. Players can use **Regular Hints** or time-limited **Special Hints** (3x combo hints) via **Clues** or Rewarded Ads.
- **Step 3 (Completion / Climax):** Once all target cats (`15` on Easy, `30` on Normal, `50` on Hard) are found, the `Win` animation triggers, clear time is recorded, and the next round prefab is preloaded in the background via Addressables.
- **Result:** `ResultScreen` displays the final stage score, stars earned (`0–3` from chests), fractional Cat Card reveal (`CardAvatar` unlocking 1/3 of the card art per star), User Level-Up processing, and awards `+1 Clue`, `+1 Ticket`, `+50 User Points`, and adds the round score to `TotalScore`.

**Key Aspects of Every Cycle:**
- **Stage Progress Tracking:** Tracked by found cat counter (`curCount / _currentMaxCat`: `0/15`, `0/30`, or `0/50`) and a 3-Star Bar (`0/3` treasure chests opened).
- **Auto-Save & Mid-Stage Resume:** Stage state (`StageSaveData`: cat seed, chest seed, found cats, opened chests, score, hints used, elapsed time) auto-saves every `5 seconds` (`AUTOSAVE_INTERVAL = 5f`) and on app pause/exit, allowing seamless mid-round resumption.
- **Dynamic Seed & Mirroring:** Each round prefab contains 50 cat placements and 10 chest placements; on start, `Round.RandomSeedGeneration()` randomly selects the required number of cats (`15` / `30` / `50`) and `3` chests. On odd campaign cycles (`cycle % 2 == 1`), the stage anchor is horizontally flipped (`SetAnchorXFlipped`) for fresh replayability.
- **Energy Gate & Regeneration:** Energy caps at `30` and passively regenerates `+1 Energy` every `10 minutes` (`600 seconds`).

---

## Game reward

After completing each round cycle, the player receives:

- **Base Cycle Reward:**
  - **+1 Clue** (Discovery auto-find hint token)
  - **+1 Ticket** (Gacha currency)
  - **+50 User Points** (`matchCompletePoints = 50` toward User Level-Up)
- **Variable / In-Stage Rewards:**
  - **Stage Score:** Base `1,000` points per cat found × active **Fever Multiplier** (`1.0x` to `3.0x`), accumulated into persistent `TotalScore` (fallback `starCount * 1000` if score is 0).
  - **In-Stage User Points:** `+3` User Points per cat found (`catFoundPoints`), `+10` User Points per treasure chest opened (`chestFoundPoints`), `-1` User Point per empty background click (`emptyClickPenalty`). Every `100` User Points grants `+1 User Level`.
  - **Stars & Cat Card Pieces:** Up to `3 Stars` per difficulty by tapping hidden treasure chests in the stage. Each star reveals `1/3` of the round's Cat Card illustration; collecting all `3 Stars` unlocks the full Cat Card, its difficulty-specific bio (`Common` / `Rare` / `Premium`), and the ability to set that cat as the player's profile avatar.
- **Final Reward Formula:**
  - `Round Score = Sum of (1000 × FeverLevelMultiplier) for each Cat Found`
  - `Total High Score = EasyHighScore + NormalHighScore + HardHighScore`
- **Reward Modified by Ad:**
  - Watching a Rewarded Ad activates **Regular Hints** (auto-zooms and highlights 1 cat), **Special Hints** (guarantees 3 consecutive cat hints), **Gacha Re-open**, or completes the **Watch Ads Daily Mission**.
- **Reward Modified by Mechanics:**
  - Chaining cat discoveries within `1 second` of the countdown delay advances the **Fever Level** up to Level 4 (`3.0x` score multiplier per cat).

---

## Core gameplay

Core gameplay revolves around visual discovery, combo pacing, multi-difficulty mastery, and collection progression:

### (1) Hidden Cat & Treasure Chest Discovery (`Round` & `PlayScreen`)
Players pan and pinch-to-zoom (`ETImageZoom`, default phone zoom `3.375x`) across detailed 2D scenes:
- **Cat Touch (`CatTouchPoint` & `InvindualCat`):** Tapping a hidden cat triggers light haptic vibration (`52ms`), plays a pitch-scaled cat meow SFX, transitions the cat sprite from uncolored/hidden to colored (`ShowWithColorChangeEffect`), spawns a `TouchEffect` particle burst (with celebratory pop-up text every 5th concurrent touch), increments the cat counter, and adds Fever score and `+3` User Points.
- **Treasure Chest Touch (`ChestTouchPoint` & `InvindualChest`):** 3 chests are randomly spawned from 10 candidate spots per round. Tapping a chest opens the crate, plays a homing star particle effect (`ETClaimEffectMain`) to the top `StarBar`, grants `+1 Star` (up to 3 per round/difficulty), and adds `+10` User Points.
- **Empty Click Penalty (`BackgroundTouchPoint`):** Tapping the background without hitting a cat or chest deducts `-1` User Point (clamped at `0`).

### (2) Fever Combo System (`FeverController` & `FeverData`)
Finding cats in quick succession builds the Fever gauge, increasing both the score earned per cat and the audio pitch of cat meow SFX:
- **Base Score per Cat:** `1,000`
- **Fever Time Added per Cat Touch:** `+1.0 second` (capped at `maxFeverTime = 5.0 seconds`)
- **Countdown Delay:** `1.0 second` grace period after each cat touch before the Fever gauge begins decaying at `1.0s / sec`.

| Fever Level | Fever Time Range | Score Multiplier | Score per Cat | Sound Pitch |
| :--- | :--- | :--- | :--- | :--- |
| **Level 0 (Normal)** | `0.0s – 1.0s` | `1.0x` | `1,000` | `1.0x` |
| **Level 1** | `1.0s – 2.0s` | `1.1x` | `1,100` | `1.1x` |
| **Level 2** | `2.0s – 3.0s` | `1.5x` | `1,500` | `1.2x` |
| **Level 3** | `3.0s – 4.0s` | `2.0x` | `2,000` | `1.3x` |
| **Level 4 (Max Fever)** | `4.0s – 5.0s` | `3.0x` | `3,000` | `1.4x` |

### (3) Regular Hint & Special Hint System (`HintConfirmUI` & `SpecialHintButton`)
When players get stuck looking for remaining cats, two hint systems assist them:
- **Regular Hint (`HintType = 0`):** Available anytime via the Hint button. Opens `HintConfirmUI` where the player can spend **1 Clue** (`TouchClue`) or watch a **Rewarded Ad** (`placement: "hint"`). Smoothly pans and zooms the camera (`SmoothFocusOnTarget`) to center on an uncollected cat, reveals its highlight at `50%` alpha, and punches its scale (`DOPunchScale`).
- **Special Hint (`HintType = 1` / `SpecialHintButton`):** Appears automatically after a timed threshold if the round is not yet cleared. When triggered via **1 Clue** or a **Rewarded Ad** (`placement: "special_hint"`), the countdown timer stops permanently and guarantees **3 consecutive cat hints** (`specialMaxHint = 3`)—automatically focusing the next cat each time the highlighted cat is tapped.

| Occurrence | Trigger Timing | On-Screen Countdown | Role | Effect |
| :--- | :--- | :--- | :--- | :--- |
| **1st Appearance** | `min(avgPlayerClearTime, 120s)` for Rounds 1–10; `min(avgPlayerClearTime, 180s)` for Rounds 11+ | `15 seconds` before hiding | Prevent early frustration when stuck | Grants `x3` guaranteed auto-focus cat hints |
| **2nd Appearance** | `+120s` (Rounds 1–10) or `+180s` (Rounds 11+) after 1st timeout/consumption | `15 seconds` before hiding | Mid-session assistance & ad revenue | Grants `x3` guaranteed auto-focus cat hints |
| **3rd+ Appearance** | `+2^N × 60s` (`240s`, `480s`, `960s`...) after Nth timeout/consumption | `15 seconds` before hiding | Exponential backoff to prevent spam | Grants `x3` guaranteed auto-focus cat hints |

### (4) Campaign Map & Multi-Difficulty Progression (`CampaignMapScreen` & `ProgressPath`)
- **Vertical Progress Path (`ProgressPath` & `NodeInfo`):** Displays the active campaign's 10 rounds as connected nodes with scroll-focus and touch-focus priority handover. Focusing a node displays its `NodeInfo` card (Round title, 3-star rating, high score, energy cost, and `CardAvatar` preview).
- **3 Difficulty Tiers (`EASY`, `NORMAL`, `HARD`):** Clearing a round on `EASY` unlocks the difficulty toggle button on `HomeScreen` for that round. Each difficulty tracks its own independent 3-star count and high score (`RoundRecord`), increases the number of hidden cats to find, increases the Energy cost, and unlocks a deeper tier of the Cat Card's lore bio:

| Difficulty ID | Label / Card Rarity | Target Cats to Find | Energy Cost Multiplier | Base Energy Cost | Cat Bio Unlocked (at 3 Stars) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **0** | **EASY (`Common`)** | `15 Cats` | `1x` (`easyEnergyMultiplier`) | `2 Energy` | Standard Description (`description`) |
| **1** | **NORMAL (`Rare`)** | `30 Cats` | `2x` (`normalEnergyMultiplier`) | `4 Energy` | Favorite Food / Normal Bio (`descriptionNormal`) |
| **2** | **HARD (`Premium`)** | `50 Cats` | `4x` (`hardEnergyMultiplier`) | `8 Energy` | Secret Habit / Hard Bio (`descriptionHard`) |

### (5) Collection of creatures / items (`CardCollectionScreenUI` & `CollectionInfoPopup`)
- **Wooden Shelf Catalogue:** Displays all 20 Cat Cards arranged 3 per wooden shelf (`CatCollectionShelfItem`). Players can toggle the view across **Easy**, **Normal**, and **Hard** difficulties.
- **Fractional Card Reveal (`CardAvatar` & `CardPieceBoxAnimator`):** Each star earned in a round unlocks `1/3` of that round's Cat Card image. Collecting all `3 Stars` on a difficulty unlocks the full card illustration, reveals the cat's name and difficulty-specific bio (`Common`, `Rare`, `Premium`) in `CollectionInfoPopup`, and enables the **"Set as Avatar"** button (`_btnSetAsAvatar`) to equip the cat on the player's `UserBannerUI`.
- **Collection Milestones (`collectionMilestones`):** Each difficulty tracks up to `60 Stars` (`20 rounds × 3 stars`) along a top progress bar with 3 claimable milestone chests (tracked per difficulty via `CatCollection_Milestone_{difficulty}_{index}`):
  - **Milestone 1:** `15 Stars` (configured in `GameData.asset`, fallback `20` in code) $\to$ **+10 Tickets**
  - **Milestone 2:** `35 Stars` (configured in `GameData.asset`, fallback `40` in code) $\to$ **+15 Tickets**
  - **Milestone 3 (code default):** `60 Stars` $\to$ **+20 Tickets**

### (6) Gacha (`GachaScreenUI` & `GachaData`)
- **Cost & Daily Limit:** Costs **1 Ticket** per pull (`ticketCost = 1`), up to **10 pulls per day** (`maxPlayPerDay = 10`, resets daily at `00:00 UTC` via `Gacha_LastDate`). Players can also re-open via a **Rewarded Ad** (`TouchReOpen`, placement `"gacha_reopen"`).
- **Gacha Yield Table (`GachaRankItem[]`):** Rewards **Energy** based on weighted probability rolls:

| Rank | Tier Label | Reward (`Energy`) | Weight / Chance (%) |
| :--- | :--- | :--- | :--- |
| **1** | `1st` | **+1,000 Energy** | `1%` |
| **2** | `2nd` | **+300 Energy** | `3%` |
| **3** | `3rd` | **+100 Energy** | `10%` |
| **4** | `4th` | **+5 Energy** | `25%` |
| **5** | `5th` | **+1 Energy** | `40%` |
| **6** | `No Luck` | **0 (Better luck next time!)** | `21%` |

### (7) Daily Rewards (`DailyRewardUI` & `DailyRewardSaveData`)
A 7-day consecutive login calendar that operates offline and automatically pops up on `HomeScreen` after the initial tutorial if an unclaimed reward is available:

| Day | Reward Type | Amount |
| :--- | :--- | :--- |
| **Day 1** | **Energy** (`rewardIndex: 0`) | `50` |
| **Day 2** | **Ticket** (`rewardIndex: 2`) | `1` |
| **Day 3** | **Energy** (`rewardIndex: 0`) | `100` |
| **Day 4** | **Ticket** (`rewardIndex: 2`) | `1` |
| **Day 5** | **Clue** (`rewardIndex: 1`) | `10` |
| **Day 6** | **Ticket** (`rewardIndex: 2`) | `1` |
| **Day 7** | **Energy** (`rewardIndex: 0`) | `200` |

- **Buttons:** Tapping a claimable day slot opens `ConfirmPopupReward` and plays homing particle effects (`ETClaimEffectMain`) into the top currency bar.
- **Mechanisms (`CheckAndAdvanceDay`):**
  - Advances `currentDay` by 1 on consecutive daily logins (`daysDiff == 1`) after the previous day was claimed.
  - Missing a day (`daysDiff > 1`) or completing all 7 days resets the streak back to **Day 1** (`ResetProgress()`).

### (8) Daily Missions (`DailyQuestPopup`)
14 offline daily quests that reset every day (`CheckDailyReset` by date string `yyyy-MM-dd`). They drive daily retention, core loop engagement, and rewarded ad impressions:

| ID | Mission Name | Reward | Required Action |
| :--- | :--- | :--- | :--- |
| **1** | **Open the App** | `10 Energy` | Open app each day (auto-completes on launch, `conditionNumber: 1`) |
| **2** | **Find 10 Cats** | `5 Energy` | Find 10 cats (`conditionNumber: 10`) |
| **3** | **Find 50 Cats** | `5 Energy` | Find 50 cats (`conditionNumber: 50`) |
| **4** | **Find 100 Cats** | `10 Energy` | Find 100 cats (`conditionNumber: 100`) |
| **5** | **Find 200 Cats** | `1 Ticket` | Find 200 cats (`conditionNumber: 200`) |
| **6** | **Find 500 Cats** | `50 Energy` | Find 500 cats (`conditionNumber: 500`) |
| **7** | **Find 1000 Cats** | `1 Ticket` | Find 1,000 cats (`conditionNumber: 1000`) |
| **8** | **Win 1 Round** | `5 Energy` | Win 1 round (`conditionNumber: 1`) |
| **9** | **Win 5 Rounds** | `50 Energy` | Win 5 rounds (`conditionNumber: 5`) |
| **10** | **Win 10 Rounds** | `1 Ticket` | Win 10 rounds (`conditionNumber: 10`) |
| **11** | **Watch Ads** | `1 Ticket` | Watch 1 Rewarded Ad directly via the "Watch" mission button (`conditionNumber: 1`) |
| **12** | **Use 1 Hint** | `5 Energy` | Use hint 1 time (`conditionNumber: 1`) |
| **13** | **Use 5 Hints** | `10 Energy` | Use hint 5 times (`conditionNumber: 5`) |
| **14** | **Use 10 Hints** | `1 Ticket` | Use hint 10 times (`conditionNumber: 10`) |

### (9) IAP Shop (option)
- **Status in `CNekoSeek`:** Not currently active in the offline casual build. Legacy hooks for Rakuten Point Exchange (`_lockRakuten`, `TrackRakutenShopOpened`) are preserved in `HomeScreen` and `AnalyticsManager` for point-activity (ポイ活) regional builds where accumulated points (`10,000 pt`) exchange for `100 Rakuten Points`.

### (10) Rating UI (option)
- **Trigger Timing & Conditions (`ResultScreen.cs`):** Checked on `ResultScreen.OnEnable()` using `_showRatingUI = PlayerPrefs.GetInt(G.IsShowRating, 0) == 0 && (_gameDat.level - 1) % 5 == 0;` (triggers every 5th cleared stage if the player has not rated yet).
- **Flow:** Intercepts `TouchHome()` or `TouchNextLevel()` on the Result Screen to invoke `ShowRatingUI()` before showing any post-stage interstitial ad.

### (11) FAQ (`FAQPopup`)
- **Access Point:** Accessible via the FAQ button on `HomeScreen` (`TouchFAQ()`).
- **Display Method:** Offline expandable accordion list (`EUExpandableList`) parsed from platform-specific local CSV assets in `Assets/Resources/`:
  - Default / Editor: `NekoSeekFAQ.csv`
  - Android: `NekoSeekFAQ_And.csv`
  - iOS: `NekoSeekFAQ_iOS.csv`
- **Question Categories & Content:** 17 localized Japanese Q&A entries covering how to play, troubleshooting puzzles/video ads, magnifying glass hints (虫メガネ), treasure chests & stars (宝箱), Gacha rules & midnight reset, Daily Missions, and Rakuten Point gift code rules.
- **Contact / Support Link (`TouchSendHelp`):** "Send Inquiry" button at the bottom of the FAQ list that opens a pre-filled `mailto:` email to `info_poikatsunyankowosagase@fancsglobal.com` containing the app name (`ポイ活にゃんこをさがせ！` on Android / `Pにゃんこをさがせ！：ねこの探し物ゲーム` on iOS), Device Model, OS Version, App Version, and `AppUUID`.

### (12) Tutorial (`TutorialPopup`)
- **Trigger Condition:** Automatically opens on first launch when entering `HomeScreen` (`PlayerPrefs` key `G.IsFirstTimePlayGame == 0`), and can be re-opened anytime via the Tutorial button on `HomeScreen` (`TouchTutorial()`).
- **Tutorial Type:** Paginated modal carousel (`PageNavigator`) with 6 illustrated slides (`TutorialItem 1–6`, on iOS `count - 1` if gift code slide is present):
  - **Step 1 (`TutorialItem 1`):** *"Press the Start button to begin the game!"*
  - **Step 2 (`TutorialItem 2`):** *"Find the cats to earn score and finish the round."*
  - **Step 3 (`TutorialItem 3`):** *"Finding treasure chests will earn you Stars! You can unlock a cat with 3 stars."*
  - **Step 4 (`TutorialItem 4`):** *"Here is your cat card collection, click each cat to show their bio."*
  - **Step 5 (`TutorialItem 5`):** *"Each round have 3 difficults, complete them to show more of the cat's secret informations."*
  - **Step 6 (`TutorialItem 6`):** *"Complete the previous campaign to unlock the next area."*
- **Completion Flow:** Closing the tutorial (`TouchQuit()`) immediately chains into `CheckDailyRewardOnEnable()` on `HomeScreen`.

### (13) Inbox (`NotificationPopup` & `NotificationManager`)
- **Access Point:** Accessible from `HomeScreen` via `TouchNoffication()` (`NotificationPopup`) and checked automatically on session start via `NotificationManager.CheckAndPushNotificationOnStart()`.
- **Mechanism:** Supports session-based announcements (`everyTimeNotifications`) and one-time persistent notices (`notificationDats` tracked by `PlayerPrefs` ID state `0 = unread`, `1 = read`).

### (14) Settings (`SettingPopup`)
- **Access Point:** Accessible from both `HomeScreen` (`State = 0`) and `PlayScreen` (`State = 1`, which pauses active gameplay and shows the **Home / Give Up** button).
- **Audio Controls:**
  - **SFX / UI Volume Slider (`_EFSlider`):** Adjusts `SoundGeneral.Instance.UI` and `SoundGeneral.Instance.EF` volume with audio preview.
  - **BGM Volume Slider (`_BGSlider`):** Adjusts `SoundGeneral.Instance.BG` volume.
- **System / Preferences (`ETSystemGeneral`):** Supports Haptic Vibration toggle (`onVibrationSettingChange`) and Night Mode background tint toggle (`onNightModeSetting`).
- **Account & Legal Links:** Buttons for **Privacy Policy** (`TouchPrivacy`), **Terms of Service** (`TouchTermOfService`), and **Return to Home** (`TouchHome` during gameplay).

---

## Content

### (1) Rarity and tier (Campaigns, Cat Cards & Difficulties)
Instead of RPG stat multipliers, **Neko Seek** structures content across **5 Campaigns** (10 rounds each) and **3 Difficulty/Rarity Tiers** per Cat Card:

**Card Difficulty / Bio Rarity Tiers (`CollectionInfoPopup`):**

| Difficulty Index | Difficulty Name | Card Value Title | Target Cats | Unlock Condition |
| :--- | :--- | :--- | :--- | :--- |
| **0** | **Easy** | `Common` | `15` | Collect 3 Stars on Easy to unlock card & base bio |
| **1** | **Normal** | `Rare` | `30` | Collect 3 Stars on Normal to unlock favorite food bio |
| **2** | **Hard** | `Premium` | `50` | Collect 3 Stars on Hard to unlock secret habit bio |

**Campaign Progression (`Campaign 1–5`):**

| Campaign ID | Campaign Name | Rounds | Map Sprite | Status / Unlock Requirement |
| :--- | :--- | :--- | :--- | :--- |
| **Campaign 1** | **Cat city** | Rounds `1–10` | `City_Map1` | Unlocked by default (`unlockRequiredRound: 1`) |
| **Campaign 2** | **Desert Pyramid** | Rounds `11–20` | `City_Map2` | Unlocks after clearing Round 10 (`unlockRequiredRound: 11`) |
| **Campaign 3** | **Tropical Island** | Rounds `21–30` | `City_Map3` | Coming Soon (`unlockRequiredRound: 21`) |
| **Campaign 4** | **Eastern Village** | Rounds `31–40` | `City_Map4` | Coming Soon (`unlockRequiredRound: 31`) |
| **Campaign 5** | **Outer Space** | Rounds `41–50` | `City_Map5` | Coming Soon (`unlockRequiredRound: 41`) |

**Implemented Cat Roster (`Round 1–20`):**
- **Campaign 1 (Cat City):** `#1 Taxi cat` (`Cat_1_01_Taxi`), `#2 Police cat` (`Cat_1_02_Police`), `#3 Barista cat` (`Cat_1_03_Barista`), `#4 Contractor cat` (`Cat_1_04_Contractor`), `#5 Mailman cat` (`Cat_1_05_MailMan`), `#6 Reporter cat` (`Cat_1_06_Reporter`), `#7 Chef cat` (`Cat_1_07_Chef`), `#8 Firefighter cat` (`Cat_1_08_FireFighter`), `#9 Business cat` (`Cat_1_09_Business`), `#10 Street Musician cat` (`Cat_1_10_StreetMusician`).
- **Campaign 2 (Desert Pyramid):** `#11 Pharaoh cat` (`Cat_2_01_Pharaoh`), `#12 Scribe cat` (`Cat_2_02_Srcibe`), `#13 Warrior cat` (`Cat_2_03_Warrior`), `#14 Merchant cat` (`Cat_2_04_Merchant`), `#15 Temple cat` (`Cat_2_05_Temple`), `#16 Mummy cat` (`Cat_2_06_Mummy`), `#17 Boatman cat` (`Cat_2_07_BoatMan`), `#18 Oracle cat` (`Cat_2_08_Oracle`), `#19 Farmer cat` (`Cat_2_09_Farmer`), `#20 Bastet cat` (`Cat_2_10_Bastet`).

### (2) Statistic & Reward Formula
- **Cosmetic Score Level (`LevelingConfig.cs`):**
  - Displayed on `UserBannerUI`, dynamically calculated from `TotalScore` (max level `999`).
  - **Linear Formula (`scoreIncreasePerLevel = 0`):** `CosmeticLevel = 1 + floor(TotalScore / 1000)` (`baseScorePerLevel = 1000`).
- **Gameplay User Level (`GameplayLevelConfig.cs`):**
  - Persistent level saved in `LocalSaveData.userLevel` (`pointsPerLevel = 100`, clamped `[0, 300]`).
  - **Point Faucets/Sinks:** Cat Found `+3`, Chest Found `+10`, Match Complete `+50`, Empty Click `-1`.
  - **Level-Up Processing:** At `ResultScreen`, while `UserPoints >= 100`, `UserLevel` increments by `+1` and `UserPoints` deducts `100`.
- **Energy Cost Formula (`GameData.GetEnergyCost`):**
  - `EnergyCost = BaseEnergy (2) × DifficultyMultiplier` (`Easy = 1x → 2`, `Normal = 2x → 4`, `Hard = 4x → 8`).

### (3) Currency
Four currencies are managed reactively via `UserDat` (`R3.SerializableReactiveProperty<long>`) and animated via `ETClaimEffectMain`:

- **Energy (`CurrencyType.Energy = 0`):**
  - **Initial / Max Cap:** Starts at `30`, passive cap `30` (`DEFAULT_MAX_ENERGY = 30`).
  - **Used in:** Starting rounds (`2` Energy on Easy, `4` on Normal, `8` on Hard).
  - **Acquired from:** Passive regeneration (`+1` per `10 minutes` / `600s` when below 30), Daily Rewards (Days 1, 3, 7), Daily Missions, Gacha prizes (`1` to `1,000` Energy), and Rewarded Ads (`ClaimAdEnergyReward = +10`).
- **Clue / Discovery (`CurrencyType.Clue = 1`):**
  - **Used in:** Activating Regular Hints or Special Hints in `HintConfirmUI` without watching ads (`-1 Clue`).
  - **Acquired from:** Clearing any round (`+1 Clue` per round completion) and Day 5 Login Reward (`+10 Clues`).
- **Ticket (`CurrencyType.Ticket = 2`):**
  - **Used in:** Playing Gacha (`1 Ticket` per roll, up to 10/day).
  - **Acquired from:** Clearing any round (`+1 Ticket` per round completion), Daily Login Rewards (Days 2, 4, 6), Daily Missions (Find 200/1000 cats, Win 10 rounds, Watch Ads, Use 10 hints), and Cat Collection Milestones (`+10`, `+15`, `+20` Tickets).
- **Star (`CurrencyType.Star = 3`):**
  - **Used in:** Unlocking fractional Cat Card pieces (`3 Stars` per round/difficulty = full card unlock & bio reveal) and progressing Cat Collection Milestones (`60 Stars` total per difficulty).
  - **Acquired from:** Finding and tapping the 3 hidden treasure chests inside each stage.

---

## Design
## UI Design

### (1) Characters design
- **Style Direction:** Cozy, expressive 2D chibi mascot cats dressed in occupation or cultural costumes matching their campaign theme (e.g., *Taxi Cat, Barista Cat, Pharaoh Cat, Bastet Cat*).
- **Features:**
  - Clean silhouette and distinct props (e.g., coffee cup, hard hat, royal crook, acoustic guitar) so each cat stands out both as a tiny hidden stage sprite and as a full-res collectible card portrait.
  - Warm pastel color fills that animate in (`ShowWithColorChangeEffect`) when tapped inside black-and-white/line-art stage backgrounds.
  - 3-layer personality writing per cat: a public summary (`Easy`), a favorite gourmet dish (`Normal`), and a humorous secret habit (`Hard`).

### (2) Important Design Notes
- **Visual Comfort & Night Mode:** Includes a Night Mode setting (`nightModeBackgroundColors`) that shifts stage backgrounds from stark white (`#FFFFFF`) to a warm cream/sepia tone (`rgb(1.0, 0.86, 0.71)`) to reduce eye strain during long seek sessions.
- **Short Screen Layout Adaptation (`ScreenLayout.cs`):** Physically short screens (`Screen.height / Screen.dpi < 4.2 inches`, such as 4.0" 16:9 devices) automatically compress `ResultScreen` vertical spacing (`_shortScreenSpacing = 10f`) so MREC and bottom banner ads never overlap action buttons.
- **Information Hierarchy in Collection:** Uncollected or partially collected Cat Cards (< 3 Stars) mask their name as `"Unknown"`, mask their bio as `"Unlocked by collecting more stars"`, and lock the `"Set as Avatar"` button until all 3 stars are earned on that difficulty.

---

## Monetization

### (1) Ad monetization (option)
Implemented via `ETEngine.IMonetizationService` with `GoogleAdsProvider` (`GoogleMobileAdsManager` / AdMob) and AppLovin MAX hooks:
- **Banner Ads:** Bottom adaptive banner (`GoogleBannerPosition.Bottom`, `AdaptiveBanner = true`).
- **MREC Ads:** `300x250` medium rectangle slots reserved on `ResultScreen` and `DailyRewardUI` (with `ScreenLayout.IsShortScreen()` safety checks).
- **Interstitial Ads:**
  - `placement: "home_play"`: Shown when starting a round from `HomeScreen` on `level > 1` if interstitial cooldown has passed (`HasInterstitialCooldownPassed()`).
  - `placement: "result_home"` & `"result_next_level"`: Shown when leaving `ResultScreen` (unless `RatingUI` is triggered).
  - In-stage `ADSBREAK_COUNTDOWN = 120s` timer prepared for stages `level >= 6`.
- **Rewarded Ads:**
  - `placement: "hint"`: Unlocks a Regular Hint in `HintConfirmUI` when out of Clues or saving Clues.
  - `placement: "special_hint"`: Activates the 3x Special Hint combo in `HintConfirmUI`.
  - `placement: "gacha_reopen"`: Grants a bonus Gacha pull in `GachaScreenUI` (`GachaKind.RewardAd`).
  - `placement: "daily_mission"`: Completes Mission #11 ("Watch Ads") in `DailyQuestPopup` for `+1 Ticket`.

### (2) IAP monetization (option)
- **Status in `CNekoSeek`:** Not used. All progression currencies (`Energy`, `Clues`, `Tickets`, `Stars`) are earned through gameplay, collection milestones, daily missions, and rewarded ads.

---

## Appliacation System

### (1) Push notifications (`PushNotificationData.asset` & `PushNotificationHelper`)
Scheduled locally on `HomeScreen.OnEnable()` and `OnApplicationPause(true)`. Supports dynamic JST streak-loss warnings (`GetDynamicDailyRewardNotificationMessage`) as well as scheduled inactivity reminders:

| Interval | Push Title | Push Body |
| :--- | :--- | :--- |
| **24 Hours** | Neko Seek | `Find the cats today and claim your bonus!` (or dynamic: `Log in today or you'll lose X points/tickets!`) |
| **72 Hours (3 Days)** | Neko Seek | `The cats miss you! Come back and claim your bonus!` |
| **168 Hours (D7)** | Neko Seek | `Come play with the cats and claim your bonus!` / `🎁 Come back now to get your bonus!` |
| **336 Hours (D14)** | Neko Seek | `🎁 Come back now to get your bonus!` (`D14InactivityHours: 336`) |
| **720 Hours (D30)** | Neko Seek | `🎁 Come back now to get your bonus!` (`D30InactivityHours: 720`) |

### (2) Asset Dilivery by Addressable (`GameDat`, `CatAssetManager`, `CampaignAssetManager`)
- **Addressable Groups Strategy (`Default Local Group`):**
  - **Round Prefabs:** 20+ stage prefabs stored in `Assets/Rounds/` with Addressable keys `#1 Round` through `#20 Round` (validated up to `#40 Round` via `RoundAddressablesValidator.cs`).
  - **Cat Sprites & Collection Data:** Cat portraits in `Assets/Game/___Art___/Cat/` (`Cat_1_01_Taxi` to `Cat_2_10_Bastet`) and `CollectionItemData` assets loaded and cached via `CatAssetManager`.
  - **Campaign Map Sprites:** Island map sprites (`City_Map1` to `City_Map5`) loaded and cached via `CampaignAssetManager`.
- **Download & Preload Flow (`GameDat.PreloadARound`):**
  - Checks `Addressables.GetDownloadSizeAsync(desiredAddress)` first; if remote dependencies exist, downloads them via `Addressables.DownloadDependenciesAsync`.
  - If loading or downloading takes longer than `250ms` (`showLoadingIfSlow`), automatically displays `ShowLoadingPage()` until completion.
  - **Next-Round Preloading:** As soon as `PlayScreen.Win()` triggers, `PreloadARound(isNextRound: true)` preloads the next stage in the background during the win animation.
- **Fallback & Error Handling:** Both `GameDat`, `CatAssetManager`, and `CampaignAssetManager` include automatic `#if UNITY_EDITOR` `AssetDatabase` fallbacks so levels and sprites load seamlessly in Editor Play Mode even if Addressable bundles haven't been built.

### (3) Multiple Input Intergrate (`TouchPoint`, `ETImageZoom`, `ProgressPath`, `CampaignMapScreen`)
- **Cross-Platform Pointer & Touch Architecture (`UnityEngine.EventSystems`):**

| Input Device | Supported Platform | Primary Actions Mapping | UI Navigation Behavior |
| :--- | :--- | :--- | :--- |
| **Touchscreen** | Mobile (iOS / Android) | Single-tap (`IPointerDownHandler`/`IPointerUpHandler` with movement distance check) to find cats/chests; 1-finger drag (`ScrollRect`) to pan; 2-finger pinch (`ETImageZoom`) to zoom; ignores `Input.touchCount > 2` | Vertical drag-snap with touch-focus handover on `ProgressPath`; horizontal swipe carousel (`_swipeThreshold = 80f`) on `CampaignMapScreen` |
| **Mouse & Keyboard** | PC / Mac Editor | Left-click to tap cats/chests and drag maps; scroll wheel zoom; debug shortcut `KeyCode.Q` in `PlayScreen.Update()` to instant-win stage | Click-to-focus round nodes or drag-scroll vertical/horizontal lists |

---

## Appliacation Control and Maintainance

### (1) Analysis (option) (`AnalyticsManager.cs` & `Unity.Services.Analytics`)
Integrated with **Unity Services Analytics** (`CustomEvent`) with test observer hooks (`EventObserver`, `DisableAnalyticsSendingForTests`):
- **Tracked Funnel & Gameplay Events:**
  - `splash_loading_started` / `splash_loading_ended`: Splash screen load lifecycle.
  - `new_user`: First-time user initialization.
  - `stage_started` / `stage_cleared`: Stage progression funnel with `{ "stage": stage }` parameter.
  - `gacha_opened`: Gacha screen engagement.
  - `rakuten_shop_opened`: Point exchange shop engagement.
  - `d7_notification_opened`: Day-7 re-engagement attribution.
  - `AB_test_loaded`: Remote config / A/B test cohort assignment.
- **Ad Impression Milestone Tracking (`ad_watch_milestone`):**
  - Persists total watched video impressions in `PlayerPrefs` (`ua_rewarded_impressions_total` and `ua_interstitial_impressions_total`).
  - Fires `ad_watch_milestone` every `100` impressions (`MilestoneStep = 100`) up to `2,000` (`MilestoneMax = 2000`) with `{ "ad_media_type", "impressions_count" }`.

### (2) Remote control (option) (`Unity.Services.RemoteConfig`)
- **Remote Config & A/B Testing Integration:**
  - Uses `Unity.Services.RemoteConfig` alongside `AnalyticsManager.TrackABTestLoaded` for live A/B testing and remote feature tuning.
  - Documented remote keys include `AB_cat_sound` (controls cat touch audio behavior in `Round.cs`).
