---
name: production-architecture-render
description: "Use when Codex needs production-grade architectural image generation or refinement from interior/exterior reference images, CAD/SketchUp views, sketches, mood images, briefs, or selected close-up crops, especially when material fidelity, construction logic, lighting physics, correct scale, and avoidance of AI artifacts are critical."
---

# Production Architecture Render

## Goal

Create architectural visuals that read as real site photography or top-tier production visualization, not generic AI art or obvious CGI. Use with the built-in `imagegen` skill/tool for raster generation or editing.

## Source Authority

When sources conflict, preserve the `edit target` first, then the `design reference`, then material and quality references. Use briefs to clarify intent, not to overwrite visible geometry, camera, or crop.

For non-English briefs, translate production intent into precise English before prompting. Preserve camera, material, construction, and negative constraints; do not soften exclusions while translating.

## Workflow

1. Classify every input image before prompting:
   - `edit target`: image to preserve while changing only specified details.
   - `design reference`: geometry, proportions, camera angle, layout, material placement.
   - `quality benchmark`: target realism, lighting, finish, and naturalness.
   - `material reference`: wood, stone, metal, fabric, glass, paint, tile, concrete.
2. Choose the prompt mode:
   - `full-scene render`: complete interior/exterior visualization.
   - `materialization/refinement`: keep geometry and camera; improve materials, lighting, and realism.
   - `close-up detail photo`: crop-preserving detail of an edge, joint, surface, reveal, or material transition.
   - `targeted correction`: fix one named output failure.
3. Extract invariants from the highest-authority source:
   - camera position and crop
   - major walls, openings, panels, cabinetry, shelves, counters, ceiling, floor
   - panel seams, module rhythm, joinery lines, object scale, and edge thickness
   - material assignments and visible design intent
4. Build the prompt using `references/production-prompt.md`. For close-up work, use its close-up architectural detail option and adapt only the subject nouns needed for the selected crop.
5. State physics and construction constraints explicitly:
   - gravity, support, shelf thickness, cabinet alignment, correct perspective
   - natural contact shadows, occlusion, reflections, and light falloff
   - plausible material scale and non-repeating texture grain
6. Add a strict anti-slop gate:
   - no warped geometry, melted decor, impossible shelves, duplicated handles, floating objects, fake text, distorted verticals, or plastic materials
   - no generic luxury clutter unless requested
   - no over-smoothed AI finish or perfect symmetry that fights real construction
7. Generate one strong candidate. Inspect it against the quality gate.
8. If iterating, make one targeted correction at a time. Do not use vague "make it better" follow-ups; name the failed element and the physical rule it violated.

## Close-Up Detail Mode

Use this mode for close-ups, detail crops, selected excerpts, `Ausschnitt`, material junctions, edge conditions, shadow reveals, tile-to-counter transitions, hardware details, or surface refinement.

Prioritize these details:

- Preserve selected geometry, perspective, and crop. Do not redesign the room or invent a new object.
- Put the focal plane on the architectural detail: edge thickness, reveal, joint, seam, grout, support, contact shadow, or material transition.
- Use a plausible close camera: near the surface, shallow oblique angle, natural depth of field, crisp foreground detail, and softly blurred context.
- Describe materials at detail scale: pores, aggregate, grain, honed or matte sheen, edge irregularity, grout width, shadow lines, believable thickness.
- Exclude new furniture, decor, glasses, plants, people, signage, logos, and geometry changes unless explicitly requested.

## Prompting Rules

Prefer architectural photography language over render-engine language unless the user explicitly wants CGI. Use "real site photograph", "professional architectural photography", "physically plausible", and "completed installation" for realism.

Keep layout authority with the design reference. Add realism through materials, light, scale, and camera behavior, not by changing the architecture.

Name common architecture failures in negative constraints: impossible joinery, bent straight lines, over-glossed wood/stone, repeated procedural textures, melted small objects, fake text, and generic luxury clutter.

## Validation

Before accepting an output, check:

- Geometry: straight verticals, level shelves, aligned panels, plausible cabinet depth.
- Construction: supported shelves/counters, believable joinery, no floating or fused objects.
- Materials: wood grain scale, stone reflectance, metal/glass behavior, paint roughness.
- Lighting: directional source, soft shadow edges, contact shadows, ambient occlusion.
- Camera: plausible lens, no distorted crop, no over-sharpened synthetic edges.
- Close-up detail: correct focal plane, natural depth of field, sharp selected edge/joint, believable material thickness, and no invented scene elements.
- Artifacts: no malformed objects, fake text/logos, repeated noise, melted handles, extra limbs/people.

If any item fails, iterate with a correction that names the exact issue.
