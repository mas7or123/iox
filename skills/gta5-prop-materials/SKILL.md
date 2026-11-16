---
name: gta5-prop-materials
description: Author GTA V-style industrial prop textures, UVs, decals, and Sollumz shader assignments; use for bland, repetitive, or overly glossy props.
---

# GTA V prop materials

- Start with 2–4 readable materials per prop (e.g. painted steel, galvanized steel, rubber, molded plastic). Use a muted body color and a small functional accent. Make the major surfaces legible from the gameplay camera. Use a vanilla reference for contrast and specular response, not a cinematic render.
- For a warehouse pack, share a trim or atlas for common edges/hardware and use small localized decals for variation: inspection tags, faded inventory codes, maintenance marks, or stencil numbers. Put wear where it has a cause: handle rub, base grime, chips at impacts, streaks below seams. No all-over rust, cloned scratches, uniform noise, random sticker spam, or baked directional lighting in diffuse. Use original or properly licensed sources; vanilla textures are comparison references unless redistribution is explicitly authorized.
- Keep UV scale consistent within the asset family. Check checker distortion, seam placement, intended overlaps, mip-safe gutters, and text readability. Start at 512 px for small clutter, 1024 px for ordinary equipment, 2048 px only where close-up needs justify it; these are starting budgets, not GTA limits. Inspect the actual packed textures and mip behavior.
- Choose the Sollumz shader before final export. For compatible opaque props, evaluate `normal_spec` and explicitly assign `DiffuseSampler`, `BumpSampler`, and `SpecSampler`. Use an appropriate supported shader for emissive, alpha, tint, or other special behavior. Verify shader-specific channel and alpha semantics with the selected toolchain and a reference. Do not connect a generic metallic/roughness pack as if it were GTA specular. Preview normals as non-color data in Blender and check for inverted relief in game.
- Compare at close and room distance in FiveM, under the actual warehouse lights. Reject wet-looking plastic, blown metal highlights, unreadable lettering, repeating obvious wear, and missing textures. Keep fixture glow distinct from actual room illumination; test both.

Reference: https://docs.sollumz.org/tutorials/creating-props/setting-up-sollumz-shaders
