# NightShift Thief Assets

## Unity package
Download `NightShiftThief_Unity.unitypackage`, import it into your Unity project, then run **Tools > Night Shift > Install Current Asset Package**.

The package contains **82 FBX animation clips and 33 model variants**, an atlas texture, material definitions, and Unity scripts. The setup tool creates materials, Animator Controllers, 33 prefabs, narrow flashlight beams, standalone item colliders/rigidbodies and death-only ragdoll setup in the receiving project.

**Read [UNITY_START_HERE_TR.md](UNITY_START_HERE_TR.md) before importing.** Built-in and URP setup is supplied. Unity Editor was unavailable here; compilation, prefab generation and play-mode checks remain to be performed in your project. Generated prefabs are not prebuilt inside this archive. Gameplay, inventory, networking, movement and camera-layer integration remain project-specific.

## Blender source
`NightShift_Thief.blend` is the latest editable source snapshot: character, existing actions, first-person hands, flashlight, jewelry, sack and two-hand loot. Keep this file outside Unity Assets; use the exported FBXs.

Scenes: `TWOHAND_Showcase`, `TWOHAND_FirstPerson`, `TWOHAND_ThirdPerson`. Two-hand preview frames: 1–90 gold, 91–180 wine crate, 181–270 dinosaur bone. The latest framing keeps arms and objects lower in the view.

`TWOHAND_USAGE.md` and `twohand_manifest.json` record Blender authoring notes. The current Unity package catalog is `Assets/NightShiftThief/Data/catalog.json` inside the package. `unity_package_manifest.json` records the archive hash and file inventory.

Old backups, outdated exports and review-only animation clips are excluded from the Unity package. The Blender source retains display scenes for editing and review.
