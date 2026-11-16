---
name: gta5-mlo-lighting
description: "Diagnose and author static GTA V and FiveM MLO lighting with Blender, Sollumz, CodeWalker, and native assets. Use for dim LED diffusers, missing wall or ceiling wash, Point, Capsule and Spot lights, room and portal visibility, and Legacy or Enhanced export and streaming."
---

# GTA V / FiveM static interior lighting

Use native GTA asset data only. Inspect fxmanifest.lua solely for asset loading. Keep lighting, diagnosis and verification asset-only.

- Load [the walkthrough](references/asset-lighting-walkthrough.md) for the keyboard sequence. The relevant creator takeaways are already built into the steps.
- Load [validation and troubleshooting](references/troubleshooting-and-validation.md) for the four-state test and the next check.
- Load [the evidence notes](references/tutorial-evidence.md) to distinguish creator descriptions and chapters from independently verified details, or to translate a 2.4 workflow.

1. Record the Blender, Sollumz, CodeWalker and FiveM versions and target generation. Trace the visible faces and current LOD to the drawable, its archetype and the active MLO entity and room. Keep placement, room logic and unrelated assets intact.
2. Separate lens self-emission from native light hitting a surface. Make the lens work using its GTA shader and sampler. Prove one drawable Point on a matte card before tuning the slats and cove with a Capsule or Spot. Keep timecycle and receiver vertex data fixed for that comparison.
3. Inspect the deployment copy, not just authoring XML. Check the geometry's shader and texture, the drawable's native light records, and which resource tree the client loads.
4. Use the four asset variants and label each outcome **confirmed from asset**, **confirmed in FiveM**, **suspected**, or **untested**. A screenshot can show layout, not the assigned shader, light records, or streamed file. Give the file, field, test condition and next action. Don't claim an export or playtest you didn't run.