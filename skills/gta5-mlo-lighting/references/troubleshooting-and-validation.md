# Validate the static lighting

Use the [asset walkthrough](asset-lighting-walkthrough.md) to author, export and inspect the four sets. The comparisons below have not been run on the office.

## Make four assets from one baseline

Keep mesh, UVs, image, textures, receivers, test card, placement, room data, timecycle and unrelated lights fixed. For lens **off**, assign a non-emissive GTA shader to the same lens faces with the same diffuse image. For lens **on**, assign the tested emissive shader. For light **absent**, remove only the test light record. For light **present**, add the same record. Don't use the time mask to fake the absence of a record.

| State | Lens | Test light | What it proves when it works | What it doesn't prove |
|---|---|---|---|---|
| A | Off | Absent | Baseline lens and room appearance. | Which pre-existing source contributes to the baseline. |
| B | On | Absent | B vs A verifies the lens change. It may produce bloom. | That slats or ceiling receive direct light. |
| C | Off | Present | C vs A verifies localized light on the matte receiver away from the lens halo. | That the lens material works or the wash is correctly aimed everywhere. |
| D | On | Present | D vs C verifies a bright diffuser. D vs B verifies receiver light with it on. | That spill, LODs, other doorway states or other generations pass. |

1. Export four sets to staging. Deploy one at a time under identical stems in the correct stream tree. Keep other variants outside the streamed resource and competing resources off the test server. In the server console, use `stop <resource>`, replace the affected binaries, then `start <resource>`. Reconnect or restart the client if an old copy persists. Hash the selected deployment files and confirm the intended record before attributing a result to them. [Cfx server commands](https://docs.fivem.net/docs/server-manual/server-commands/)
2. Fix camera position, view angle, FOV, resolution, graphics and post-processing. Hold weather and time as closely as practical or wait for matching conditions. Write down the actual conditions. Let camera exposure settle. For each state test close, at normal gameplay distance, at noon and midnight. Also take equivalent views from just inside and just outside the doorway with the same door state. Repeat closed if relevant. A room designed to hide with the door shut should still do so.
3. Compare the same lens, matte card, slat and ceiling patches in each image. Include a dark reference patch outside the test light. If the reference also brightened, repeat at matching exposure. A halo overlapping a surface in B is not proof of direct light. Look away from the halo. Prove C vs A before substituting the wash for the Point. Run the same matrix for one wall or cove fixture at a time, then confirm both together after removing the card.

## Next check by symptom

| First observation | Next check |
|---|---|
| Lens absent even in A | Check whether the face exists at the active export LOD and faces the viewer. If present, check culling and overlap. |
| Lens present but B looks like A | Follow the lens geometry's shader index in the deployed binary, then resolve DiffuseSampler to its texture and supported value. |
| Lens switches off as you step back | Inspect the lower LOD faces and slots first, then mip/texture resolution. |
| C looks like A and the native record is absent | Check the selected export root, actual light ancestry and native Sollumz type. |
| C looks like A and the light is in the binary | Prove the file loaded, then verify local origin, in-range matte card, masks, falloff/exponent and Light Effect overrides. |
| Sprite but no matte patch | Check Corona Only and isolate the Point with corona and volume suppressed. |
| Works only at night or only by day | For C inspect the light time mask and Flashiness. For B inspect the selected shader and timed archetype. If unchanged, check exposure contrast. |
| Light and fixture vanish crossing the doorway | Compare owner room/portal attachment, portal From/To and corner direction, door flag, floor Room ID and entity-set visibility. |
| Fixture stays visible but light disappears at doorway | Compare interior/exterior flags and fade before changing portal data or expanding range. |
| Works close, direct patch drops out farther away | Check Light Fade Distance and light LOD flags. If geometry also disappears, inspect its bounds/LOD. |
| Card works, real slats do not | Move/rotate the card to match the slats. If it lights there, check receiver normals, materials and vertex colors separately. If both fail, check the beam or shadowing. |
| Capsule looks like a dot or points across the strip | Read Type, Extent.X and Direction from the binary. Try one short segment, then one directed Spot if it still fails. |
| Hot corner or scalloped wall | Turn off one adjoining light in the test build. Adjust stand-off, taper or spacing based on which pattern disappears. |
| Light on the wrong side of a surface | Check unshadowed light volume first. Reduce range and use aim before paying for shadows or adding a tested culling plane. |
| Whole room is flat or dark in A | Inspect timecycle, receiver material and vertex colors separately. Don't use ambient edits to stand in for a failed C test. |
| Works in Legacy only | Check the selected Enhanced tree, Gen9 binary, texture dependency and mounted paths. A Gen8 pass is not a Gen9 pass. |

## Pass and report

**Asset pass** requires the final deployment files to contain the correct diffuser assignment, sampler and texture for the intended LODs, and the intended native light types and values. There should be no unexplained changes to map placement, rooms, collision or unrelated records.

**FiveM pass** requires a lens change in B/A or D/C and a localized patch in C/A and D/B. At gameplay distance the perimeter reads continuously, the ceiling has a gradient, the slats still have dark gaps, and corners aren't visibly double-lit. No unintended spill or disappearance across the doorway. Check performance with any shadow flags enabled and repeat the visual test without the card, on each generation you intend to ship.

Log file hashes, versions, generation, variant, time, weather, door state, position, graphics and screenshot names. Mark each statement **confirmed from asset**, **confirmed in FiveM**, **suspected**, or **untested**. An export read-back is not a game pass.