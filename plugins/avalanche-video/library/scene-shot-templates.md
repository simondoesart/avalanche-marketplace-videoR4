# Element Library — Scene / Shot Templates

Full, ready-to-fire prompt templates for recurring content types. Copy a template, swap the `{{PLACEHOLDERS}}`, and send to `generate_video` / `generate_image`. All are pre-tuned to `brand/brand-visual-style.md`.

Placeholders: `{{SUBJECT}}`, `{{PRODUCT}}`, `{{TAGLINE}}`, `{{ELEMENT_ID}}` (reference element).

---

### T1 — Logo / mark reveal (hero)
**Model:** `cinematic_studio_3_0` · **Aspect:** 16:9 · **Duration:** 6s
**✅ Validated** — first run used `avalanche-logo` element as start_image. Job `e4d1fe21-3d4e-4102-a710-cf1b9d39ebd5`, 720p, 30 credits.
> Geometric fragments and light shards fly in from all directions and snap together into the {{SUBJECT}} mark, slow deliberate dolly push-in settling on the final form, near-black #0A0A0B deep space, subtle Avalanche-red rim light on one edge, single decisive key with crisp speculars, polished CGI mesh-to-beauty finish, engineered and precise, motion settles into stillness on the final beat.

### T2 — Product / feature glamour
**Model:** `seedance_2_0` (start_image = product still) · **Aspect:** 16:9 · **Duration:** 5s
> Controlled 180° orbit around {{PRODUCT}}, locked height even speed, clean off-white #F5F6F7 studio light with soft fill and deep controlled shadows, one Avalanche-red focal accent, generous negative space, photorealistic high-end product-film aesthetic, camera settles at the end.

### T3 — "Speed" motion statement
**Model:** `kling3_0` · **Aspect:** 16:9 · **Duration:** 5s
> Clean lines of light travel along precise paths and converge to a single illuminated node, lateral dolly with strong parallax revealing depth, deep near-black space, disciplined volumetric beams, high contrast no haze, one red pulse at the convergence point, engineered warm-tech finish.

### T4 — Network / ecosystem visual
**Model:** `cinematic_studio_3_0` · **Aspect:** 16:9 · **Duration:** 8s
> Points connect into an ordered network as nodes illuminate in sequence, smooth orbital wide shot descending into an intimate close-up on the central node, near-black background, Avalanche-red highlight on the hero node only, clean geometry and aligned grid logic, cinematic and precise, resolves to stillness.

### T5 — Social vertical hook (Reels/TikTok/Shorts)
**Model:** `veo3_1_lite` or `marketing_studio_video` · **Aspect:** 9:16 · **Duration:** 4–6s
> {{SUBJECT}} resolves into frame with a fast engineered push-in and a single red-kick accent, deep dark space, crisp product light, bold minimal composition with room for a top-third {{TAGLINE}}, confident warm-tech energy, settle on the final frame.

### T6 — Earth / scale opener
**Model:** `cinematic_studio_3_0` · **Aspect:** 16:9 · **Duration:** 8s
> Orbital wide shot of Earth from space descending smoothly toward a single glowing red point on the surface, motorized-rig smoothness, deep space blacks, restrained volumetric light, cinematic scale into human-level detail, engineered and calm.

### T7 — Abstract brand texture (loop / background)
**Model:** `wan2_6` or `seedance_2_0` · **Aspect:** 16:9 · **Duration:** 5s
> Slow drifting field of clean geometric planes in graphite and near-black, one migrating Avalanche-red plane, soft key light, generous negative space, seamless loopable motion, minimal and premium.

---

## On-brand Higgsfield presets (image→video via `higgsfield_preset`)

Most stock presets are off-brand (K-pop, paparazzi, retro-game — skip). These few align with our "assemble into clarity / scale" language:

| Preset | ID | Use for |
|--------|-----|---------|
| CGI BREAKDOWN | `6372c588-7ace-48e9-ad4c-6565c2d2f817` | Mesh→beauty product/logo reveal |
| 3D RENDER | `5a77643c-b6cc-4efd-bdc6-ab8ff48dfa82` | Clean turntable orbit reveal |
| ANDROID ASSEMBLE | `5a461de5...` *(verify id via presets_show)* | "Assemble-in" fragments→form |
| Earth zoom in | `f7561a2d-7556-4aed-b21d-2ff07a28326a` | Scale opener (T6) |
| Earth zoom out | `37ff659c-3345-491f-ace1-36b8215187da` | Scale closer |
| Orbital Presence | `7335f08f-5f16-4f8c-85a3-4de5ff05e3c3` | Satellite/space brand shots |

> Presets are character-oriented, so always feed a clean on-brand start image and lean on the templates above for full control.

---

## Saving new winners
When a generation nails it, append a new `T#` here with: the exact prompt used, model, aspect, duration, and the Higgsfield job ID. That grows the library over time.
