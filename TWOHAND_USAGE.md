# Two-hand loot — review draft

Open Thief_TwoHand_Loot_REVIEW.blend.

Scenes:
- TWOHAND_Showcase: three independent loot models.
- TWOHAND_FirstPerson: raise and walk-sway previews; Space plays. Gold frames 1–90, wine crate 91–180, bone 181–270.
- TWOHAND_ThirdPerson: two-hand support poses.

Items: LOOT_Gold_Bar, LOOT_Wine_Crate, LOOT_Dinosaur_Bone.
Category: two_hand. Item-local Support_R and Support_L are contact anchors.

FP_TwoHand_Raise_* keeps the item visible during raising.
FP_TwoHand_Hold_* are static holds.
FP_TwoHand_Walk_* add restrained two-hand walking sway (30 FPS, frames 1–41; duplicated loop endpoint).
TP_TwoHand_Hold_* are third-person support poses, not full locomotion.
PREVIEW actions and display scenes are review helpers, not export assets.

Items remain separate static meshes. Preview instances attach to hand.R; left hand supports the opposite side. Unity inventory, animation blending, physics, and spawning are not implemented here. No FBX or final package was exported.
