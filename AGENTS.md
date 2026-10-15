# GGJ 2026 — Unmasked

## Project structure

- **UE 5.5**, Blueprint-only (no C++ source directory exists).
- Project root: `unmasked/unmasked.uproject`.
- All game logic is in Blueprints under `Content/`.

## Key Blueprint areas

| Directory | Contents |
|-----------|----------|
| `Content/FirstPerson/` | Character, weapon, game mode, input mappings, main level map |
| `Content/Blueprints/` | Core mechanics: SoundGenerator, Repeater, Projectile, Time, End, MainMenu |
| `Content/LevelPrototyping/` | Doors, buttons, moving platforms, audio, prototyping meshes/materials |

## Starting the project

Open in UE 5.5 Editor via `unmasked/unmasked.uproject`. Editor default map is `/Game/FirstPerson/Maps/MainLevel`. Add the `ModelingToolsEditorMode` plugin if prompted.

## Input system

Uses **Enhanced Input** (`/Script/EnhancedInput.EnhancedPlayerInput`). Input Action and Mapping Context assets live in `Content/FirstPerson/Input/`.

## Asset tracking

- `.uasset` / `.umap` files are tracked with **Git LFS** (see `.gitattributes`).
- `Saved/`, `Intermediate/`, `DerivedDataCache/`, `Build/`, `Binaries/` are gitignored.

## No build/test system

No package.json, no CI config, no tests. Iterate in-editor (Play In Editor).
