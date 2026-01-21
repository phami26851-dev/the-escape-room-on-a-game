# The Escape Room — Starter Scaffold

This repository contains a minimal scaffold to run the small Unity escape-room prototype scripts (pickup, inventory, door lock, simple puzzle manager, and a basic save system).

Quick overview
- Unity version: any recent Unity 2020+ or 2021+ should work for these scripts.
- Drop the `Assets/` folder into a Unity project or copy the files into `Assets/Scripts/`.
- Create a Scene (e.g., `Main.unity`) and wire the objects as described below.

Files included
- Assets/Scripts/ItemPickup.cs — pick up items via raycast and keypress
- Assets/Scripts/Inventory.cs — singleton inventory storing item ids
- Assets/Scripts/DoorLock.cs — simple door that opens when inventory has a required item
- Assets/Scripts/PuzzleManager.cs — flag-based puzzle manager
- Assets/Scripts/SimpleSaveSystem.cs — minimal JSON save/load skeleton
- .gitignore — Unity-friendly ignore file

Setup & wiring (Unity)
1. Create a new Unity project (3D) or open an existing one.
2. Copy the `Assets/Scripts/` files into your project.
3. Create a GameObject named `Inventory` and attach `Inventory.cs` to it.
   - Since Inventory uses DontDestroyOnLoad, create it once in your startup scene.
4. Create a GameObject named `PuzzleManager` and attach `PuzzleManager.cs`.
5. Items:
   - For each item prefab, attach a collider (set to non-trigger or trigger depending on your design) and the `ItemPickup` script.
   - Set the `itemId` string on each item (e.g., `red_key`).
6. Door:
   - Create a door GameObject that pivots along the hinge Y-axis.
   - Attach `DoorLock.cs` and set `requiredItemId` (e.g., `red_key`) or leave empty if unlocked.
   - For testing, press `F` during play while aiming at the door to call `TryOpen()` (prototype).
7. Interaction:
   - The sample `ItemPickup` uses a center-screen raycast and `E` to pick up objects.
   - Add a simple UI text for prompts if desired.
8. Save/Load:
   - `SimpleSaveSystem` is a skeleton; extend it to read/write real Inventory and PuzzleManager state.
9. Playtest and iterate:
   - Start small (one room, 1–2 puzzles). Expand once core loop feels good.

Git workflow (example)
- Initialize repository:
  - git init
  - git add .
  - git commit -m "Add Unity escape-room starter scaffold"
  - Create remote and push as needed.

What I can do next
- Generate a Unity scene (.unity) and prefabs (requires me to export .unity YAML content — tell me if you want that).
- Make the UI for inventory and interaction prompts.
- Expand the save system to actually persist inventory & puzzle flags.
- Create an example puzzle (key + locked door + hint chain) fully wired.

If you want, tell me whether you prefer a single ready-to-import Unity package (scene + prefabs + assets) or just the scripts and README (what I provided). I can then produce the additional files and wiring steps.