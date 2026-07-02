# Element Library — Prompt Building Blocks

Modular, reusable phrases. Assemble a prompt by picking one from each relevant group and stitching with the brand style. Every block is written to match `brand/brand-visual-style.md`.

**Prompt formula:**
`[SUBJECT] + [CAMERA MOVE] + [MOTION/ACTION] + [LIGHTING] + [STYLE/FINISH] + [aspect + duration]`

---

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

## Aspect + duration presets

- Hero / site: `16:9`, 6–8s
- Social vertical: `9:16`, 4–6s
- Feed tile: `1:1`, 4s

---

## Model routing (which Higgsfield model for the job)

Pass `model` to `generate_video`. Grounded in our workspace catalog:

| Need | Model id | Why |
|------|----------|-----|
| Best cinematic hero shot | `cinematic_studio_3_0` | SOTA, 4–15s, up to 4K, genre control |
| Ultra-real premium | `veo3_1` (quality `high`/`ultra`) | Top-tier realism, native audio |
| Fast batch drafts | `veo3_1_lite` or `kling3_0_turbo` | Cheap, quick iteration |
| Reference/identity-consistent (product, multi-SKU) | `seedance_2_0` | Image/video/audio references, consistent identity |
| Multi-shot sequence with audio | `kling3_0` | Multi-shot, audio sync, motion transfer |
| One-click product ad (TikTok/Reels) | `marketing_studio_video` | UGC/ads format, 12–15s |
| Preset-routed image→video | `higgsfield_preset` + `preset_id` | See `scene-shot-templates.md` for on-brand presets |

**Image models** (for start frames via `generate_image`): `nano_banana_2` (Nano Banana Pro), `seedream_v4_5`, `gpt_image_2`, `cinematic_studio_2_5`, `soul_2` (trained characters).

**Rule of thumb:** draft on a fast/cheap model, finalize the winner on `cinematic_studio_3_0` or `veo3_1`. Budget is credits (workspace has a running balance — check with `show_plans_and_credits`).
