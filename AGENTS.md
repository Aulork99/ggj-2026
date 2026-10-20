# Agent Guide — Unmasked

## Project facts

- Unreal Engine **5.8** on the active `feature-dev` gameplay branch. `upgrade/ue58` is a separate upgrade branch; `feature-dev` is no longer the UE 5.5 checkpoint.
- Blueprint-only project; there is no game C++ source directory.
- Project file: `unmasked/unmasked.uproject`.
- Default map: `/Game/FirstPerson/Maps/MainLevel`.
- Game logic and content assets live under `unmasked/Content/`.

## Main content areas

| Directory | Contents |
|-----------|----------|
| `Content/FirstPerson/` | Character, weapon, game mode, Enhanced Input assets, and main map |
| `Content/Blueprints/` | SoundGenerator, Repeater, Projectile, Time, End, and MainMenu mechanics |
| `Content/LevelPrototyping/` | Doors, buttons, moving platforms, audio, and prototype assets |

## Input system

- Uses **Enhanced Input** (`/Script/EnhancedInput.EnhancedPlayerInput`).
- Input Actions and Mapping Contexts are under `Content/FirstPerson/Input/`.
- Current contexts are `IMC_Movement` and `IMC_Shooting`; shooting actions include `IA_Shoot` and `IA_Reload`.
- Avoid restoring the removed `IMC_Default` / `IMC_Weapons` assets unless intentionally changing the input design.

## Opening and validating

- Open `unmasked/unmasked.uproject` with UE 5.8. Keep an independent rollback baseline before bulk asset resaves; do not save UE 5.8 assets into an older-engine branch.
- `ModelingToolsEditorMode`, `ModelContextProtocol`, and `AllToolsets` are enabled in the project.
- There is no CI or automated game-test suite. Compile affected Blueprints and test behavior with Play In Editor, especially movement, weapon attachment/fire, projectile behavior, sound generation/repeaters, doors, and end/menu flow.

## Unreal MCP

- The optional, experimental Unreal MCP server is local to the editor and serves `http://127.0.0.1:8000/mcp`.
- Auto-start is an editor-user preference, not a project asset. If disabled, start it from the editor console with `ModelContextProtocol.StartServer 8000`.
- MCP toolsets can modify assets. Use read-only inspection for analysis; only call mutating tools when the user explicitly requests edits.
- Do not expose the local MCP server beyond loopback; it has no authentication layer.

## Version control and assets

- `.uasset` and `.umap` files are tracked with **Git LFS** via the repository-root `.gitattributes`.
- The repository-root `.gitignore` scopes Unreal-generated files to `unmasked/`, including `Saved/`, `Intermediate/`, `DerivedDataCache/`, `Build/`, and `Binaries/`.
- Avoid bulk resaves or engine-version conversions without a clean branch and a recoverable LFS baseline.
