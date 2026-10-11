# NightShift Thief Assets

Latest editable Blender snapshot of the low-poly thief character project for future Unity use.

## Start here
Open `NightShift_Thief.blend` in Blender. This source snapshot includes the existing character, animation actions, first-person arms, flashlight, jewelry and the new two-hand loot previews.

## Two-hand loot
- Gold bar
- Wine crate with six bottles
- Dinosaur bone

Scenes: `TWOHAND_Showcase`, `TWOHAND_FirstPerson`, `TWOHAND_ThirdPerson`.
First-person preview: frames 1-90 gold, 91-180 crate, 181-270 bone. Press Space to play.

The latest first-person framing lowers the shoulders and items to preserve visibility. Hold, raise and walk-sway actions are separate. Items remain independent meshes.

See `TWOHAND_USAGE.md` and `twohand_manifest.json` for action names and integration notes.

## Status
Blender source/review snapshot. This repository does not contain a configured Unity project. Inventory, player animation blending and runtime item physics still require Unity integration. Third-person two-hand clips are support poses, not full locomotion. No outdated FBX exports, backup versions, temporary previews or previous final ZIPs are included.

Preserve original actions when making changes. Do not treat PREVIEW actions or display objects as production export assets.
