# Element Library — Prompt Building Blocks

Modular, reusable phrases for composing shots. Full prompts always use the canonical layout in `library/prompt-format.md` — these blocks fill its SHOT / Camera lines. Filmed types (1, 2, 5) lean on the filmed-register blocks; graphic types (3, 4, 6) may use the engineered blocks below.

---

## Filmed register — camera & motion (default)

| ID | Phrase |
|----|--------|
| `handheld-drift` | "subtle handheld drift, eye-level, breathing with the subject" |
| `follow-move` | "handheld tracking alongside the subject, motivated by their movement" |
| `candid-hold` | "static eye-level medium shot, candid, letting the moment play" |
| `arrive-reveal` | "camera arrives with the subject, space revealing naturally around them" |
| `detail-insert` | "close insert on hands/object, shallow focus, quick and purposeful" |
| `settle` | "motion decelerates and settles into stillness on the final beat" |

## Engineered register — graphic types only

## Camera moves

| ID | Phrase to drop in prompt |
|----|--------------------------|
| `slow-push` | "slow, deliberate dolly push-in, motorized-rig smoothness, settling on the subject" |
| `precise-orbit` | "controlled 180° orbit around the subject, locked height, even speed" |
| `parallax-reveal` | "lateral dolly with strong foreground/background parallax, revealing depth" |
| `locked-reveal` | "locked-off camera, subject resolves into frame, no camera shake" |
| `earth-to-detail` | "orbital wide shot descending smoothly into an intimate close-up" |
| `rise-up` | "smooth vertical crane rise, revealing scale" |

## Motion / action

| ID | Phrase |
|----|--------|
| `assemble-in` | "fragments and geometric pieces fly in from all directions and snap together into a clean final form" |
| `settle` | "motion decelerates and settles into stillness on the final beat" |
| `data-flow` | "clean lines of light travel along precise paths, converging to a single node" |
| `unfold` | "structure unfolds and expands outward with engineered precision" |
| `network-form` | "points connect into an ordered network, nodes illuminating in sequence" |

## Lighting

| ID | Phrase |
|----|--------|
| `product-key` | "single decisive key light, soft fill, deep controlled shadows, crisp speculars" |
| `red-kick` | "subtle Avalanche-red rim/kick light on one edge of the subject" |
| `deep-space` | "near-black #0A0A0B background, subject floating in deep negative space" |
| `clean-white` | "bright even off-white #F5F6F7 studio light, clean product look" |
| `volumetric-disciplined` | "restrained volumetric light beams, high contrast, no haze overload" |

## Style / finish

| ID | Phrase |
|----|--------|
| `engineered` | "precise, engineered, high-end product-film aesthetic" |
| `geometric` | "clean geometry, aligned grid logic, generous negative space" |
| `cgi-reveal` | "polished CGI reveal, mesh-to-beauty finish, turntable clarity" |
| `photoreal-tech` | "photorealistic, cinematic, warm-tech, confident not cold" |

## Duration heuristic (apply at shotlist time)

**~2.5–3s per shot.** 4 shots → 10–12s; 5 shots need 13–15s. Warn on over-packing — 5 shots in 10s reads rushed. Verify against the model's allowed range before confirming.

## Aspect + duration presets

- Hero / site: `16:9`, 6–12s
- Social vertical: `9:16`, 4–6s
- Feed tile: `1:1`, 4s
- Multi-shot narrative generation: `16:9`, 10–15s (3–4 shots packed)

---

## Model routing (verify with `models_explore` each project — catalog moves)

Pass `model` to `generate_video`. Verified against the live catalog 2026-07:

| Need | Model id | Why / limits |
|------|----------|--------------|
| Multi-shot narrative w/ element identity (the proven narrative default) | `seedance_2_0` | image/video/audio refs, consistent identity, 4–15s, native audio, up to 4K (`mode: std`) |
| Cheap narrative drafts w/ refs | `seedance_2_0_mini` | same ref support, 480/720p only |
| Best cinematic hero shot | `cinematic_studio_3_0` | SOTA, 4–15s, up to 4K, genre control |
| Ultra-real premium single shots | `veo3_1` (quality `high`/`ultra`) | top realism, native audio, 4/6/8s only |
| Fast batch drafts | `veo3_1_lite` or `kling3_0_turbo` | cheap, quick iteration |
| Multi-shot w/ audio sync | `kling3_0` | 3–15s, motion transfer |
| One-click product ad (TikTok/Reels) | `marketing_studio_video` | UGC/ads format, 12–15s |
| Preset-routed image→video | `higgsfield_preset` + `preset_id` | graphic register only; decline for narrative |

**Image models** (for start frames via `generate_image`): `nano_banana_2` (Nano Banana Pro), `seedream_v4_5`, `gpt_image_2`, `cinematic_studio_2_5`, `soul_2` (trained characters).

**Rule of thumb:** draft on a fast/cheap model, finalize the winner on `cinematic_studio_3_0` or `veo3_1`. Budget is credits (workspace has a running balance — check with `show_plans_and_credits`).
