---
name: fivem-prop-export-qa
description: Prepare and verify Blender/Sollumz props for GTA V and FiveM with drawables, textures, archetypes, collision, LODs, and optional MLO entity sets.
---

# FiveM prop export and QA

1. Identify the installed Blender/Sollumz export path, target FiveM build and a known-good test resource. Export via the supported native route where available, or via CodeWalker XML and conversion. XML is not a stream-ready binary; never rename it as one.
2. Verify the Sollumz Drawable hierarchy, LOD slots, shader assignments and texture resolution. Export the drawable `.ydr` and use a matching archetype in `.ytyp` for custom models. Use embedded textures or a correctly linked `.ytd`, as appropriate. Set bounds and physics references using the supported workflow; verify export by inspecting or reopening the result. Register custom archetypes in the test resource where required.
3. Use simple functional collision: separate hulls or primitives for the solid parts of an open rack; no collider sealing a real walk-through gap. Do not make decorative bolts collidable. Use embedded collision or properly configured separate bounds based on placement. Check simplified LODs where needed at actual viewing distances; preserve silhouette and check transitions rather than blindly applying decimate.
4. Test one standalone asset first by spawning the registered model in a controlled FiveM resource, without a new YMAP placement for that smoke test. Compare against a vanilla prop and player ped. Verify ground contact, scale, shading, texture binding, normal direction, collision, and LOD behavior. Measure the actual draw/texture cost if repeated in quantity.
5. For an existing MLO, keep baseline furnishings separate from named upgrade entity sets. Configure the prop references and placements in the MLO data; use the appropriate entity-set natives and refresh after changes. Entity sets toggle authored contents; they do not create rooms or portals. Author shells, room/portal relationships and access gating separately. When swapping variants, verify both directions, re-entry, and no duplicate props or overlapping collision.
6. Report each gate as PASS, FAIL, or NOT RUN, with evidence: dimensions, export inspection, fresh-resource model load, in-game screenshots, collision walkthrough, and entity-set test if applicable. Do not label an asset FiveM-tested without runtime evidence.

Reference: https://docs.sollumz.org/tutorials/creating-props
