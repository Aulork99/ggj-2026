# Unmasked — GGJ 2026

`Unmasked` is a first-person Unreal Engine game prototype. Gameplay is built in
Blueprints and includes movement, shooting/projectiles, sound generators and
repeaters, timed sequences, doors/buttons, and menu/end-game flow.

## Engine and project

- Current upgrade branch: **Unreal Engine 5.8** (`upgrade/ue58`).
- UE 5.5 checkpoint: `feature-dev`.
- Project file: `unmasked/unmasked.uproject`.
- Main map: `/Game/FirstPerson/Maps/MainLevel`.
- Game logic and assets are under `unmasked/Content/`.

Open the project with UE 5.8. Keep the UE 5.5 checkpoint available until the
upgrade branch has been validated; saving assets in 5.8 may make them
incompatible with 5.5.

## Enhanced Input

The project uses Unreal's Enhanced Input system. Mapping contexts and actions
are in `Content/FirstPerson/Input/`:

- `IMC_Movement` — movement, look, and jump mappings.
- `IMC_Shooting` — `IA_Shoot` and `IA_Reload` mappings.

## Content layout

- `Content/FirstPerson/` — player character, weapon, game mode, input, and map.
- `Content/Blueprints/` — sound, repeater, projectile, time, menu, and end logic.
- `Content/LevelPrototyping/` — doors, buttons, moving platforms, and prototype audio/assets.

## Unreal MCP (optional)

UE 5.8's experimental Unreal MCP can expose editor tools to compatible AI
clients. The local endpoint is `http://127.0.0.1:8000/mcp`. To start it
automatically with the editor, enable **Edit → Editor Preferences → General →
Model Context Protocol → Auto Start Server**. The endpoint is loopback-only and
has no authentication; do not expose it to other machines.

## Assets and testing

- Unreal `.uasset` / `.umap` files use Git LFS (see the repository-root
  `.gitattributes`).
- Unreal-generated `Saved/`, `Intermediate/`, `DerivedDataCache/`, `Build/`, and
  `Binaries/` files under `unmasked/` are ignored by the repository-root
  `.gitignore`.
- There is no automated build/test suite. Validate in the UE 5.8 editor by
  compiling affected Blueprints and testing with Play In Editor.
