# Production Architectural Render Prompt

Use this scaffold when generating or editing architectural images for production review.

```text
Use case: sketch-to-render / architecture-production-render
Asset type: production architectural visualization for an architecture firm
Prompt mode: full-scene render / materialization-refinement / close-up detail photo / targeted correction
Primary request: <create or improve the architectural image>
Input images:
- Image 1: <design reference / edit target / quality benchmark / material reference>

Design invariants:
- Preserve the exact architectural layout, proportions, crop, camera angle, panel rhythm, shelf positions, cabinet massing, ceiling/floor relationship, and intended materials from the design reference.
- Treat the reference as a built object, not as a loose mood board.
- For edit targets and close-up crops, preserve the selected geometry and camera even more strictly than the material brief.

Scene:
<completed real interior/exterior installation, room type, architectural context>

Subject:
<main architectural element and its components>

Style:
Professional architectural photography of a real completed site. Natural, physically plausible, construction-aware, high-end but not over-staged. Avoid obvious CGI, SketchUp, game-render, showroom-render, or generic AI image aesthetics.

Camera:
Verticals remain straight and architectural. Use a plausible professional lens feel, realistic exposure, slight natural edge softness, believable perspective, and no synthetic over-sharpening.

Lighting physics:
Use physically plausible daylight/interior lighting. Include correct light direction, soft shadow edges, contact shadows, ambient occlusion in corners and shelf recesses, realistic reflection strength, and natural falloff. Shadows must agree with object positions.

Material physics:
Describe each visible material with scale, finish, and behavior:
- wood: correct grain scale, varied grain, pores, seams, satin or matte sheen, no plastic gloss
- stone: honed/polished behavior, subtle reflections, believable edge highlights
- paint/plaster: fine surface texture, no perfectly flat synthetic color
- glass/metal/ceramic: correct reflection, transparency, weight, and scale
- floor: aggregate/tile/wood scale with natural variation and perspective alignment

Detail requirements:
Model construction details cleanly: panel seams, edge thickness, reveals, shelf supports, junctions, cabinet bases, countertop thickness, trim alignment, and believable object contact with surfaces.

Anti-slop constraints:
No warped shelves, bowed panels, impossible joinery, broken perspective, floating objects, melted accessories, duplicated handles, fake labels, fake text, logos, watermarks, distorted verticals, noisy material mush, plastic wood, repeating procedural grain, excessive clutter, random luxury decor, people, or changes to the intended architecture.

Quality bar:
The image must pass production review for attention to detail, realism, and physics. It should read as a carefully photographed built installation or a top-tier visualization that is indistinguishable from one.
```

## Close-Up Architectural Detail Option

Use this translated and enhanced prompt when the user asks for a close-up architectural detail of a selected bar-counter edge or a similar material junction. Adapt the nouns only when the selected detail is not a bar counter.

```text
Use case: close-up architectural detail from an existing interior image
Asset type: professional interior detail photograph for architecture production review
Prompt mode: close-up detail photo
Primary request: Create a believable architectural detail photograph of the selected crop from the provided interior image.

Input image authority:
- Treat the source image as the exact existing room geometry, camera direction, crop, and design intent.
- Materialize and refine only the selected area. Do not design a new bar, create a new scene, straighten the existing perspective, or change the room geometry.

Selected detail:
- Foreground edge of the bar counter, with visible countertop thickness and the transition to the tiled counter front below.
- The countertop edge should dominate the foreground and lead perspectivally into the softly blurred interior.
- The focal plane is the crisp front edge, the fine shadow reveal under the slab, and the precise junction with the tile face below.

Camera:
- Camera very close to the counter edge, slightly below the countertop surface.
- Use a shallow, oblique view along the edge, with natural shallow depth of field.
- Keep the foreground highly detailed and sharp. Let the background fall into believable optical blur, not fake tilt-shift or synthetic haze.

Materials:
- Countertop: high-quality natural stone, cast stone, terrazzo-like engineered stone, concrete composite, or matte solid surface. Show fine aggregate or grain, subtle pores, restrained reflections, slight edge irregularity, and believable slab thickness.
- Tiled front: calm, high-quality architectural tiles with fine grout lines. Keep the tile pattern restrained, precise, and not decorative.
- Joint: make the connection between countertop and tile face constructionally plausible, with a fine dark shadow line below the slab.

Lighting:
- Inherit the soft natural light from the existing interior.
- Add subtle highlights on the countertop surface, soft shadows under the overhanging edge, and realistic darkening inside the connection joint.

Style:
- High-end interior detail photography of a completed installation.
- It should feel photographed and physically present, not like a flawless rendering or sterile CGI.

Strict exclusions:
- No new scene, no new bar design, no invented furniture, no glassware, no decoration, no people, no plants, no signage, no logos.
- No unrelated materials added from nothing, no exaggerated reflections, no high-gloss finish, no plastic surfaces, no perfect central perspective, no line straightening, and no changes to the existing room geometry.
```

## Iteration Prompts

Use one targeted correction per iteration:

```text
Keep the previous composition and architecture. Correct only this issue: <exact issue>.
Physical rule: <why it is wrong, e.g. shelves must remain level and supported; shadows must match the sunlight direction>.
Do not alter: <layout, materials, camera, design invariants>.
```

## Quick Failure Labels

Use these labels while inspecting outputs:

- Geometry drift: changed proportions, lost symmetry, bent verticals.
- Construction failure: unsupported shelf, impossible joinery, floating counter.
- Material failure: plastic wood, repeated grain, wrong stone/glass reflectance.
- Lighting failure: shadows disagree, no contact shadows, fake glow.
- Scale failure: decor too large/small, shelf thickness unrealistic, floor pattern scale wrong.
- Close-up failure: focal plane misses the selected edge, depth of field looks fake, material pores are too large, joint lacks a shadow reveal, or the model invents new objects.
- AI artifact: melted object, fake text, duplicated part, noisy details.
