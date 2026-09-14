# Minecraft 26.2 NeoForge Mod Deployment

## 1. Main Mods / VPS Configuration

| Configuration | Details |
|---|---|
| Game | Minecraft Java Edition |
| Minecraft Version | **26.2** |
| Mod Loader | **NeoForge 26.2.0.84** |
| Java | **Java 25** |
| Server RAM | **6 GB** |
| Server Type | Private Multiplayer / Co-op RPG |

> **Deployment rule:** Use NeoForge 26.2 builds of all mods. Do not mix Fabric, Forge, or older Minecraft-version jars.

This document reflects a **fresh dependency audit performed against the exact Minecraft 26.2 NeoForge release metadata** for every installed mod (via each mod's live Modrinth version record, not inferred from older Minecraft/Fabric/Forge builds). See sections 6–9 for corrected dependency and compatibility findings.

> **Re-audited 2026-09-14** — every mod in `Mods/MOD_MANIFEST.csv` individually re-checked against live Modrinth NeoForge 26.2 metadata: all required dependencies present, no broken builds among installed mods, no active mod-to-mod conflicts. AzureLib Armor and Accessories confirmed to still have no NeoForge 26.2 build. Patch updates applied: JEI → `30.32.0.215`, Puzzles Lib → `26.2.4`.

## 2. Client-Only Mods

| Mod | Purpose | Server Impact |
|---|---|---|
| Xaero's Minimap | Minimap and waypoints | None |
| Xaero's World Map | Full-screen world map | None |
| Sodium | Client rendering/FPS optimization | None |
| Iris Shaders | Shader pack support | None |
| Punchy! - First Person Animations | First-person combat animations | None |
| Dynamic Lights | Dynamic handheld/world lighting | None |
| AmbientSounds 6 | Environmental ambience | None |
| Eating Animation Fork | Eating/drinking animations | None |
| RPG-HUD | RPG-oriented HUD | None |
| Particular Reforged | Particle effects overhaul | None |

> **Note:** Xaero's Minimap/World Map and similar client experience mods may declare Client & Server in loader metadata, but for this private server they can be kept in the client pack unless a specific server-side integration is intentionally enabled.

> **Particular Reforged:** Current NeoForge 26.2 build should be treated as **client-side** and should not be installed on the dedicated server unless the exact build documentation requires it.

> **Eating Animation Fork:** Not distributed on Modrinth — the verified NeoForge 26.2 build (`NeoForge-26.2+4.0.0`) must be downloaded manually from CurseForge (`eating-animation-fork`).

> **Iris Shaders — recommended shader pack:** [Complementary Reimagined](https://modrinth.com/shader/complementary-reimagined) `r5.8.1` (Minecraft 26.2, Iris-compatible). Shader packs are not mods — download the `.zip` from Modrinth and place it in `.minecraft/shaderpacks`, then select it from the Iris in-game shader menu. Not bundled in the mod manifest/pack since it installs separately.

## 3. Server-Only Mods

| Mod | Purpose | Server Impact |
|---|---|---|
| Let Me Despawn | Mob despawning / entity management | Low / beneficial |

## 4. Client + Server Mods

| Mod | Purpose | Server Impact |
|---|---|---|
| Just Enough Items (JEI) | Item and recipe lookup | Very Low |
| Better Combat | Enhanced combat mechanics | Low |
| Visual Workbench | Visible crafting-table inventory | Very Low |
| AppleSkin | Food/saturation information | Very Low |
| Sound Physics Remastered | Sound propagation/reverb | Low |
| Mutant Monsters | Mutant mobs | Medium |
| Advanced Hook Launchers | Grappling/traversal mechanics | Low |
| Clumps | XP orb merging | Beneficial / Very Low |
| Jade | Block/entity information | Very Low |
| Corpse | Death-item recovery | Low |
| Guard Villagers | Village guards | Low-Medium |
| Dungeons & Taverns | Structures/dungeons | Medium during chunk generation |
| Waystones | Fast travel | Low |
| Explorations | Additional exploration structures | Medium during chunk generation |
| Structory | Atmospheric/world structures | Medium during chunk generation |
| Sophisticated Backpacks | Upgradeable backpack storage | Low |
| Saddlebag | Wolf saddlebag storage / companion utility | Low |

## 5. RPG Series (ZsoltMolnarrr)

| Mod | Purpose | Server Impact |
|---|---|---|
| Arsenal (RPG Series) | RPG weapons | Low |
| Archers (RPG Series) | Archer class | Low |
| Paladins & Priests (RPG Series) | Paladin/Priest classes | Low-Medium |
| Rogues & Warriors (RPG Series) | Rogue/Warrior classes | Low-Medium |
| Wizards (RPG Series) | Wizard class/spells | Medium |
| Armory (RPG Series) | RPG armor | Low |
| Jewelry (RPG Series) | RPG accessories | Medium |
| Skill Tree (RPG Series) | Skill progression | Medium |
| Relics (RPG Series) | RPG relics/trinkets | Low-Medium |

> All nine RPG Series mods share the same author (ZsoltMolnarrr) and interlock through the shared libraries listed in Section 6 (Spell Engine, Armor Model API, Ranged Weapon API, Structure Pool API, Runes, Bundle API, Spell Power Attributes, Curios API, Critical Strike, Pufferfish's Skills).

## 6. Required Dependencies

**Audit method:** for every installed mod, the exact NeoForge 26.2 file's own Modrinth version record was queried directly (`GET /project/{slug}/version`, matched by exact filename) and its declared `dependencies` array read. No dependency below is inferred from a Fabric build, a Forge build, or a pre-26.2 Minecraft version.

| Mod | Dependency | Required/Optional | Platform | Minecraft Version | NeoForge Compatible | Notes | Source |
|---|---|---|---|---|---|---|---|
| Particular Reforged | BaguetteLib | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — particular-reforged v1.5.7 |
| Iris Shaders | Sodium | Required | NeoForge | 26.2 | Yes | Installed (v0.9.2+mc26.2-neoforge, exact version pinned by Iris's own dependency record) | Modrinth — iris v1.11.4+26.2-neoforge |
| Let Me Despawn | Almanac (Almanac Lib) | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — lmd v1.26.9.1 |
| Better Combat | Player Animation Library | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — better-combat v3.2.2+26.2 |
| Better Combat | Cloth Config API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — better-combat v3.2.2+26.2 |
| Visual Workbench | Puzzles Lib | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — visual-workbench v26.2.1 |
| Mutant Monsters | Puzzles Lib | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — mutant-monsters v26.2.2 |
| Advanced Hook Launchers | ForgeEndertech | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — advanced-hook-launchers v26.2.0.0 |
| AmbientSounds 6 | CreativeCore | Required | NeoForge | 26.2 | Yes | **Was missing from initial download — now added** (v2.14.16) | Modrinth — ambientsounds v6.3.6 |
| Waystones | Balm | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — waystones v26.2.0.12 |
| Waystones | Shogi | Required | NeoForge | 26.2 | Yes | **Was missing from initial download — now added** (v26.2.0.5) | Modrinth — waystones v26.2.0.12 |
| Arsenal (RPG Series) | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — arsenal-rpg-series v1.5.1+26.2 |
| Arsenal (RPG Series) | Ranged Weapon API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — arsenal-rpg-series v1.5.1+26.2 |
| Archers (RPG Series) | Armor Model API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — archers v3.1.2+26.2 |
| Archers (RPG Series) | Structure Pool API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — archers v3.1.2+26.2 |
| Archers (RPG Series) | Bundle API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — archers v3.1.2+26.2 |
| Archers (RPG Series) | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — archers v3.1.2+26.2 |
| Archers (RPG Series) | Ranged Weapon API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — archers v3.1.2+26.2 |
| Sophisticated Backpacks | Sophisticated Core | Required | NeoForge | 26.2 | Yes | Installed (v26.2-1.5.0.2337) | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |
| Paladins & Priests (RPG Series) | Structure Pool API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — paladins-and-priests v3.1.2+26.2 |
| Paladins & Priests (RPG Series) | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — paladins-and-priests v3.1.2+26.2 |
| Paladins & Priests (RPG Series) | Armor Model API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — paladins-and-priests v3.1.2+26.2 |
| Paladins & Priests (RPG Series) | Runes | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — paladins-and-priests v3.1.2+26.2 |
| Rogues & Warriors (RPG Series) | Structure Pool API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — rogues-and-warriors v3.1.2+26.2 |
| Rogues & Warriors (RPG Series) | Armor Model API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — rogues-and-warriors v3.1.2+26.2 |
| Rogues & Warriors (RPG Series) | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — rogues-and-warriors v3.1.2+26.2 |
| Wizards (RPG Series) | Armor Model API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — wizards v3.1.2+26.2 |
| Wizards (RPG Series) | Runes | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — wizards v3.1.2+26.2 |
| Wizards (RPG Series) | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — wizards v3.1.2+26.2 |
| Wizards (RPG Series) | Structure Pool API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — wizards v3.1.2+26.2 |
| **Armory (RPG Series)** | Ranged Weapon API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — armory-rpg-series v1.5.2+26.2 |
| **Armory (RPG Series)** | Armor Model API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — armory-rpg-series v1.5.2+26.2 |
| **Armory (RPG Series)** | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — armory-rpg-series v1.5.2+26.2 |
| **Jewelry (RPG Series)** | Ranged Weapon API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — jewelry v2.4.1+26.2 |
| **Jewelry (RPG Series)** | Spell Power Attributes | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — jewelry v2.4.1+26.2 |
| **Jewelry (RPG Series)** | **Curios API** | Required | NeoForge | 26.2 | Yes | Installed. Confirmed via exact 26.2 NeoForge metadata — Jewelry uses Curios API, **not** Accessories | Modrinth — jewelry v2.4.1+26.2 |
| **Jewelry (RPG Series)** | Structure Pool API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — jewelry v2.4.1+26.2 |
| Skill Tree (RPG Series) | Pufferfish's Skills | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — skill-tree v1.6.1+26.2 |
| Skill Tree (RPG Series) | Ranged Weapon API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — skill-tree v1.6.1+26.2 |
| Skill Tree (RPG Series) | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — skill-tree v1.6.1+26.2 |
| Skill Tree (RPG Series) | Critical Strike | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — skill-tree v1.6.1+26.2 |
| Relics (RPG Series) | Spell Engine | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — relics-rpg v1.4.1+26.2 |
| Relics (RPG Series) | Ranged Weapon API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — relics-rpg v1.4.1+26.2 |
| Spell Engine | Spell Power Attributes | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — spell-engine v1.10.5+26.2 |
| Spell Engine | Curios API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — spell-engine v1.10.5+26.2 |
| Spell Engine | Player Animation Library | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — spell-engine v1.10.5+26.2 |
| Spell Engine | Cloth Config API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — spell-engine v1.10.5+26.2 |
| Runes | Bundle API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — runes v1.3.2+26.2 |
| Bundle API | Curios API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — bundle-api v4.0.0+26.2 |
| Bundle API | Player Animation Library | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — bundle-api v4.0.0+26.2 |
| Bundle API | Cloth Config API | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — bundle-api v4.0.0+26.2 |
| Bundle API | Spell Power Attributes | Required | NeoForge | 26.2 | Yes | Installed | Modrinth — bundle-api v4.0.0+26.2 |
| Dynamic Lights | Fabric API | Required (per metadata) | Fabric only | 26.2 | N/A | **Metadata artifact** — this Modrinth version is a single multi-loader (Fabric/NeoForge/Quilt) entry; Fabric API has no NeoForge equivalent and is not needed for the NeoForge build | Modrinth — lambdynamiclights v4.12.4+26.2 |

### Removed from this list (corrected)

| Removed dependency | Previously attributed to | Reason for removal |
|---|---|---|
| **AzureLib Armor** | Armory (RPG Series) | Exact Armory 26.2 NeoForge version metadata (`armory-rpg-series v1.5.2+26.2`) lists only Ranged Weapon API, Armor Model API, and Spell Engine as required. AzureLib Armor was a dependency of older 1.21.x Armory releases and is **not** declared by the current 26.2 NeoForge build. AzureLib Armor also has no NeoForge 26.2 release at all (latest build targets MC 1.21.1). |
| **Accessories** | Jewelry (RPG Series) | Exact Jewelry 26.2 NeoForge version metadata (`jewelry v2.4.1+26.2`) lists Curios API, not Accessories, as the accessory-slot dependency. Accessories also has no NeoForge 26.2 release at all (latest build targets MC 1.21.10). |

Neither AzureLib Armor nor Accessories is required by any other currently installed 26.2 NeoForge mod in this pack, so both are fully removed rather than merely reclassified as optional.

## 7. Optional Dependencies

| Mod | Dependency | Required/Optional | Platform | Minecraft Version | NeoForge Compatible | Notes | Source |
|---|---|---|---|---|---|---|---|
| Xaero's Minimap | Open Parties and Claims | Optional | NeoForge | 26.2 | Yes | Not installed; only needed for party/claim integration | Modrinth — xaeros-minimap v26.5.0 |
| Xaero's World Map | Open Parties and Claims | Optional | NeoForge | 26.2 | Yes | Not installed | Modrinth — xaeros-world-map v1.46.0 |
| Sound Physics Remastered | Simple Voice Chat | Optional | NeoForge | 26.2 | Yes | Not installed; only needed if voice chat integration desired | Modrinth — sound-physics-remastered v1.5.1+26.2 |
| Sound Physics Remastered | Cloth Config API | Optional | NeoForge | 26.2 | Yes | Already installed (required elsewhere) | Modrinth — sound-physics-remastered v1.5.1+26.2 |
| Jade | Just Enough Items (JEI) | Optional | NeoForge | 26.2 | Yes | Already installed | Modrinth — jade v26.2.10 |
| Corpse | Jade | Optional | NeoForge | 26.2 | Yes | Already installed | Modrinth — corpse v1.1.19+26.2 |
| Ranged Weapon API | EMI | Optional | — | — | **No NeoForge 26.2 build found** | Not installed; not needed since JEI already covers recipe lookup | Modrinth — ranged-weapon-api v4.0.0+26.2 |
| BaguetteLib | YetAnotherConfigLib (YACL) | Optional | Fabric | — | N/A | Fabric-only config UI; not applicable to the NeoForge build | Modrinth — baguettelib v2.0.5 |
| ForgeEndertech | Advanced Chimneys | Optional | NeoForge | 26.2 | Yes | Not installed; cosmetic add-on only | Modrinth — forgeendertech v26.2.0.2 |
| Sophisticated Backpacks | Just Enough Items (JEI) | Optional | NeoForge | 26.2 | Yes | Already installed (recipe/upgrade lookup) | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |
| Sophisticated Backpacks | Curios API | Optional | NeoForge | 26.2 | Yes | Already installed (required elsewhere) | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |
| Sophisticated Backpacks | TrashSlot | Optional | NeoForge | 26.2 | Yes | Not installed; adds a trash slot integration | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |
| Sophisticated Backpacks | Item Borders | Optional | NeoForge | 26.2 | Yes | Not installed; cosmetic rarity borders | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |
| Sophisticated Backpacks | Chipped | Optional | NeoForge | 26.2 | Yes | Not installed; cosmetic backpack skins | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |
| Sophisticated Backpacks | Sawmill | Optional | NeoForge | 26.2 | Yes | Not installed | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |
| Sophisticated Backpacks | Crafting Tweaks | Optional | NeoForge | 26.2 | Yes | Not installed | Modrinth — sophisticated-backpacks v26.2-3.26.2.2154 |

## 8. TBD / On Hold Mods

| Mod | Status |
|---|---|
| **Biomes O' Plenty** | TBD — keep disabled until the current world-generation stack has been tested |

> **Eating Animation Fork** is planned/approved (see Section 2) but requires a **manual** CurseForge download since it is not distributed on Modrinth.

## 9. Compatibility Issues

- **Armory (RPG Series) — corrected:** The current Armory 26.2 NeoForge release (`armory-rpg-series v1.5.2+26.2`) **does not require AzureLib Armor**. This was true for older 1.21.x releases only. No action needed; AzureLib Armor is not part of this pack.
- **Jewelry (RPG Series) — corrected:** The current Jewelry 26.2 NeoForge release (`jewelry v2.4.1+26.2`) **uses Curios API**, not Accessories, for its accessory slots. Trinkets (Fabric-only) is not applicable to this NeoForge pack and was never required.
- Previous statements describing AzureLib Armor or Accessories as blockers to Armory/Jewelry functionality are **withdrawn** — they were based on an incorrect dependency assumption, not on the actual 26.2 NeoForge metadata.
- **Dynamic Lights** declares a "Fabric API required" dependency in its Modrinth metadata; this is a cross-loader artifact of a single multi-loader version listing and does not apply to the NeoForge build actually installed.
- **Dynamic Lights** also declares Sodium Dynamic Lights and RyoamicLights as **incompatible** in its live version metadata. Neither is installed in this pack — do not add either alongside Dynamic Lights.
- **DarkMobs** filename still reads `darkmobs-neoforge-26.1-1.2.7.jar`, but its version metadata explicitly lists `26.2` among supported game versions — the file is correct for this pack despite the outdated filename.
- **Eating Animation Fork** is CurseForge-exclusive (not on Modrinth) — verified build `NeoForge-26.2+4.0.0` must be sourced and installed manually.
- Keep using the exact **NeoForge** artifact for each mod. Do not substitute Fabric or Forge jars with the same Minecraft version.

### Good combinations

- Better Combat + RPG Series
- Better Combat + Punchy!
- Xaero's Minimap + Xaero's World Map
- Sound Physics Remastered + AmbientSounds 6
- DarkMobs + Mutant Monsters

### Areas to test

1. **DarkMobs + Mutant Monsters + RPG Series** — potentially high combat difficulty; start with conservative DarkMobs settings.
2. **Dungeons & Taverns + Explorations + Structory + RPG structures** — no known inherent hard conflict; monitor structure density and chunk-generation performance.
3. **Better Combat + Punchy! + RPG weapons/spells** — test weapon animations, attacks, shields, bows, and spell interactions.

## 10. Server Performance / Overhead

### Lowest impact

- JEI, AppleSkin, Jade, Clumps, Let Me Despawn, Waystones, Corpse
- Client-only visual/audio/UI mods (Section 2)

### Moderate impact

- Better Combat, Mutant Monsters, DarkMobs, Guard Villagers, Advanced Hook Launchers
- RPG Series (Section 5)

### Highest potential server impact

- **Dungeons & Taverns**
- **Explorations**
- **Structory**

These primarily add overhead during **new chunk generation and structure placement**, rather than continuously while the server is idle. (Classification unchanged — no dependency-metadata finding in this audit affects chunk-generation cost.)

### 6 GB Server Guidance

The current list is reasonable for a **private co-op server**, but the pack is no longer lightweight. The two newly confirmed required libraries (CreativeCore, Shogi) are lightweight utility/config libraries and do not change this assessment.

Monitor: TPS, MSPT, CPU usage, Heap usage, Garbage-collection pauses, Entity count, Chunk-generation time.

Recommended operational practices:

- Pre-generate the initial playable region before opening the server.
- Avoid multiple players rapidly generating terrain in distant directions.
- Keep **Biomes O' Plenty** disabled until the current world-generation stack has been tested.
- Do not add additional heavy world-generation or technology mods without re-evaluating the 6 GB allocation.

## Pinning / Launcher Guidance

| Setting | Value |
|---|---|
| Minecraft | **26.2** |
| NeoForge | **26.2.0.84** |
| Java | **25** |
| Server RAM | **6 GB** |

> **NeoForge 26.2.0.84 is pinned because it is the recommended/starred 26.2 NeoForge option available in TLauncher for your players.** Mod pages are validated against the 26.2 game line; they do not generally specify a minimum/maximum NeoForge patch within 26.2.

## Final Deployment Baseline

```text
Minecraft: 26.2
NeoForge: 26.2.0.84
Java: 25
RAM: 6 GB
```

**Pinned-version rule:** Standardize the VPS and all player clients on NeoForge `26.2.0.84`. Use only NeoForge 26.2 mod builds; do not mix loader variants.
