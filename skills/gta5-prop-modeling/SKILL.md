---
name: gta5-prop-modeling
description: Design, size, and model GTA V and FiveM hard-surface props in Blender from real measurements and vanilla visual references.
---

# GTA V prop modeling

1. Define gameplay function, interaction side, floor/wall/ceiling mounting, expected placement, and closest camera distance. Choose one vanilla GTA V prop for scale and one for material/silhouette. Record their names and measurements if available. Never invent a vanilla model name or claim an in-game comparison you did not perform. If unavailable, mark the comparison pending and use a labeled metric proxy.
2. Work in meters. Write target X width × Y depth × Z height before modeling. Record origin and front direction; default to floor-center at Z=0 and a consistent front direction for new freestanding props. Use the mounting plane for wall/ceiling fixtures. Check dimensions from evaluated geometry after modifiers. Require within 2% per axis unless the brief specifies another tolerance. Apply rotation and scale where the export workflow requires it; preserve functional pivots for moving parts.
3. Block out against a 1.8 m human proxy and neighboring fixtures. Approve silhouette and ergonomics before detail: switch reach, drawer clearance, pipe port height, and player walk path. Capture front, side, and three-quarter views with a scale cue.
4. Build industrial props as editable Blender geometry or parametric Blender Python. AI concepts are references, not dimension authority. Treat image-to-3D output as source geometry until scale, topology, UVs, and materials are repaired; prefer authored geometry for precise tanks, cabinets, racks, pumps and pipes.
5. Use major shapes first, then believable assembly: panel seams, folded steel, flanges, braces, latches, and a restrained number of silhouette bevels. Bake or texture tiny screws and grain that do not change the silhouette. Avoid random greebles. Make upgrades visibly change silhouette or equipment layout, not just tint.
6. Deliver editable source, dimensions, pivot/front direction, material slots, triangle count per LOD, and proposed collision. Share hardware and materials across the pack; keep variants aligned to their intended mounting points. If Blender cannot run, deliver source scripts and label all renders/measurements pending.
