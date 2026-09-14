# Minecraft 26.2 NeoForge Mod Deployment

![Minecraft](https://img.shields.io/badge/Minecraft-26.2-3b8526?style=flat-square)
![NeoForge](https://img.shields.io/badge/NeoForge-26.2.0.84-e5883e?style=flat-square)
![Java](https://img.shields.io/badge/Java-25-orange?style=flat-square)
![License](https://img.shields.io/badge/docs%20license-MIT-blue?style=flat-square)

Reference documentation and mod pack for a private NeoForge 26.2 co-op/RPG server: full deployment notes, a dependency audit re-checked against live Modrinth metadata, and a ready-to-install client mod pack.

## Quick start (players)

1. Download the latest client mod pack from [Releases](https://github.com/Yashraj5122/minecraft-26-2-neoforge-mod-deployment/releases/latest).
2. Install **NeoForge `26.2.0.84`** for Minecraft **26.2** (Java 25 required).
3. Extract the zip contents into your `.minecraft/mods` folder.
4. Launch and connect.

See [MOD_LIST.md](MOD_LIST.md) for what's in the pack, or the full [deployment doc](minecraft_26_2_neoforge_mod_deployment.md) for per-mod details and compatibility notes.

## Contents

| File | Purpose |
|---|---|
| [`minecraft_26_2_neoforge_mod_deployment.md`](minecraft_26_2_neoforge_mod_deployment.md) | Full deployment doc: server config, mod lists by category, dependency audit, compatibility notes, performance guidance |
| [`minecraft_26_2_neoforge_mod_deployment.xlsx`](minecraft_26_2_neoforge_mod_deployment.xlsx) | Spreadsheet version of the same |
| [`MOD_LIST.md`](MOD_LIST.md) | Plain mod list segregated by client-only, server-only, and client+server |
| [`Mods/MOD_MANIFEST.csv`](Mods/MOD_MANIFEST.csv) | Per-mod inventory (version, filename, sha1, size, Modrinth slug, source) for re-downloading and verifying every jar |

## Server baseline

| Setting | Value |
|---|---|
| Minecraft | 26.2 |
| NeoForge | 26.2.0.84 |
| Java | 25 |
| Server RAM | 4 GB |

## Notes

- `.jar` files under `Mods/` and packaged zips under `Mods/mod-zips/` are not tracked in this repo (see `.gitignore`) — use the manifest to re-download and verify them, or grab a prebuilt pack from [Releases](https://github.com/Yashraj5122/minecraft-26-2-neoforge-mod-deployment/releases).
- This repo distributes packaging/reference material only. Each bundled mod remains the property of its original author and is subject to its own license as published on Modrinth/CurseForge — see [LICENSE](LICENSE) for scope.
