# Repository guide for AI coding agents

## Purpose and editing boundary

This repository contains SnowRunner mods, mod-pack sources, and reference
copies. The only mod folder intended for personal use and publication is
`MainTrucksParametersPhysicsMod/` (the exact folder name currently present in
this repository). Make requested game-mod changes only inside that folder.
Do not edit, synchronize, or repackage other mod folders unless explicitly
asked.

`Original/` is a vanilla-game reference copy and must never be edited. Other
folders are separate mods, source material, or comparisons; treat them as
read-only unless explicitly asked to work there. Keep changes targeted and
preserve the game's relative paths under `[media]/`.

This file is the current repository-wide guidance. If older guidance in
`SNOWRUNNER-MOD-CONTEXT.md` conflicts with it, follow this file.

## Folder map

| Folder | Contents and role |
|---|---|
| `AddonsLeaning/` | Addon XML tweaks, including crane and other addon definitions. |
| `CameraMod/` | Truck XML camera and cockpit-view changes. |
| `De-RC-Fication/` | Truck XML changes intended to make vehicles less remote-control-like. |
| `DestructubleTrees/` | Environment and truck XML related to destructible trees. |
| `Engines/` | Engine definitions and engine-related truck XML. |
| `Gearboxes/` | Gearbox definitions. |
| `MainTrucksParametersPhysicsMod/` | **The only editable/publishable mod folder.** The personal combined pack; its README documents included truck handling, camera, crane, and log-bunk tweaks. |
| `MrBussesWheelPack/` | MrBusses wheel-pack content, including wheel assets and pack data. |
| `NanakoWheelPack/` | Nanako wheel-pack content, including classes, prebuild, and UI data. |
| `NewFriction/` | Terrain and surface XML for friction changes. |
| `NightShiftLights/` | NightShift lighting mod files, presets, and installation/editing instructions. |
| `Original/` | Vanilla-game `[media]` reference files; read-only. |
| `RealMetalPlankWeight/` | XML changes for metal-plank cargo weight. |
| `RLM/` | Real Life Mod distribution/source files and optional components; read-only here. |
| `RLM-v2/` | Another Real Life Mod copy/version and optional components; read-only here. |
| `Suspension/` | Truck suspension XML changes. |

## Working in the publishable pack

- Read `MainTrucksParametersPhysicsMod/README.txt` before changing pack
  behavior.
- Preserve `[media]` paths and XML formatting; change only the requested
  parameters and files.
- Use `Original/[media]/` for comparisons when needed, but never write there.
- Do not alter unrelated settings or sibling mod folders.
