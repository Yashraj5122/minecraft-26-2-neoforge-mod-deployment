# Minecraft 26.2 NeoForge Mod Deployment

Reference docs for a private 5-player NeoForge 26.2 co-op/RPG server.

## Contents

- [`minecraft_26_2_neoforge_mod_deployment.md`](minecraft_26_2_neoforge_mod_deployment.md) — full deployment doc: server config, mod lists by category, dependency audit, compatibility notes, and performance guidance.
- [`minecraft_26_2_neoforge_mod_deployment.xlsx`](minecraft_26_2_neoforge_mod_deployment.xlsx) — spreadsheet version of the same.
- [`MOD_LIST.md`](MOD_LIST.md) — plain mod list segregated by client-only, server-only, and client+server.
- [`Mods/MOD_MANIFEST.csv`](Mods/MOD_MANIFEST.csv) — per-mod inventory (version, filename, sha1, size, Modrinth slug, source) for re-downloading and verifying every jar.

## Baseline

```text
Minecraft: 26.2
NeoForge: 26.2.0.84
Java: 25
RAM: 4 GB
Players: 5
```

## Note

The actual `.jar` files under `Mods/` are not tracked in this repo (see `.gitignore`) — use the manifest to re-download and verify them.
