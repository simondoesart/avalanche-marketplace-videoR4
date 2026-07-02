# Video Types — Definitions & Reference Routing

The `/make-video` skill uses this file to know, for each video type: the look, which references to pull, which Higgsfield model to route to, and which building blocks to lean on. All types still obey `brand/brand-visual-style.md`.

> Refine freely. Drop visual references into `assets/<type>/` and register the best as reference elements (see `reference-assets.md`). The more references a type has, the more consistent its output.

---

## 1. Human-centric
**What it is:** People-forward story/emotion pieces — real moments between real people in lived-in spaces. Documentary, not advertising. Testimonials, family/relationship beats, "day in the life," narrative vignettes. The priority is authentic human warmth, captured — never slick or rendered-looking.

**Signature look (locked):** shot on 35mm film, Kodak Vision3 / Portra tones. Naturalistic overcast daylight, soft diffused light. Muted earthy palette — desaturated greens and warm browns. Gentle film grain, soft halation in highlights. Documentary realism, candid composition, photographed not rendered, no oversaturation. Subtle handheld movement, eye-level medium framing, genuine interaction and expression.

**Reusable look string** (paste into prompts, per shot):
> Shot on 35mm film, Kodak Vision3 / Portra tones, naturalistic overcast daylight, soft diffused light, desaturated greens and warm browns, gentle film grain, soft halation in highlights, documentary realism, subtle handheld movement, candid composition, photographed not rendered, no oversaturation.

**Reference image:** father + teenage son laughing in a modest kitchen, overcast window light, earthy tones. (Add stills to `assets/human/` and register the strongest as reference elements.)

**Pull references:** character(s) — reference element or Soul-trained for identity consistency; location/environment (real, modest interiors); wardrobe/props. Identity + wardrobe consistency across shots matters most here.

**Model routing:** `seedance_2_0` (multi-reference identity, multi-shot narrative, native audio — the proven default for this look) → `kling3_0` (multi-shot + audio sync) → `veo3_1` (hero realism). Soul characters → `soul_2` for start frames.

**Default blocks:** naturalistic overcast key, subtle handheld drift, candid framing, warm earthy grade, real emotion. Prefer this look string over the brand's deep-dark-space default.

**Aspect defaults:** 16:9 hero, 9:16 social.

**Brand fit:** this type intentionally departs from the deep-black/red-focal house style — warmth and realism come first. Brand enters softly: through context, a product in-scene, or a single restrained red accent (never forced dark space or CGI polish). Keep audio natural/diegetic, no score unless briefed.

**Do/Don't:** real emotion, candid beats, natural ambient sound · avoid uncanny faces, forced smiles, oversaturation, on-screen text/UI/HUD, lip-synced or discernible dialogue unless intended.

## 2. B-roll generation
**What it is:** Cinematic, conceptual supporting footage — the "provoking imagery" that carries a voiceover or sits under a headline. Not neutral filler: each shot is a composed, filmic idea. Recurring theme = **business/work meets nature/scale** (finance world + mountains, skylines, open sky), often surreal juxtapositions (a desk on a mountaintop, a desk on a skyscraper ledge). Silhouettes, dynamic angles, contemplative motion.

**Signature look (locked):** shot on 35mm film, Kodak Vision3 / Portra tones — the same authentic film base as human-centric, just composed cinematically. Real film grain, soft halation, naturalistic light, photographed not rendered, no oversaturation, never glossy or plasticky. Anamorphic widescreen feel, shallow depth of field, atmospheric haze, gentle natural flare. Golden-hour warmth or moody blue-grey overcast. Strong silhouettes against bright backgrounds. Dynamic vantage points — low angles, high/aerial views, tracking side-profiles. Provoking, a little surreal, but grounded and grainy — not a shiny commercial.

**Reusable look string** (paste into prompts, per shot):
> Shot on 35mm film, Kodak Vision3 / Portra tones, real film grain, soft halation, naturalistic light, photographed not rendered, no oversaturation, not glossy. Cinematic anamorphic widescreen, shallow depth of field, atmospheric haze, gentle natural flare, strong silhouettes, dynamic angle, contemplative slow camera move, provoking and grounded, filmic and authentic.

**Reference images:** businessman at a desk on a fog-shrouded alpine peak; silhouette on the phone against a sunset city skyline; low-angle of a woman at a glowing screen with sticky notes; suited cyclist tracking past a dusk skyline; man at a desk on a skyscraper ledge over the city. Theme: work + nature/scale, elevated and surreal. (Add stills to `assets/b-roll/`.)

**Pull references:** environment/location stills (mountains, skylines, interiors), subject silhouette refs, prop close-ups. Often text-to-video works without references — the concept and grade carry it.

**Model routing:** `cinematic_studio_3_0` (hero cinematic b-roll, genre control) → `veo3_1` (ultra-real silhouettes, scale, light) → `seedance_2_0` (reference-locked locations) → `veo3_1_lite` for cheap batches of many clips.

**Default blocks:** `slow-push` / `parallax-reveal` / `rise-up`, `volumetric-disciplined` or golden-hour natural light, shallow depth, silhouette staging, generous negative space, `settle`.

**Aspect defaults:** 16:9, 21:9 for epic; 9:16 crops via `reframe`.

**Brand fit:** more permissive on palette than the house dark-space rule (golden hour and blue-grey are welcome), but keep compositions disciplined and reserve red for a single intentional accent when the brand needs to register. Authentic film texture over polish. Loopable and cut-friendly.

**Do/Don't:** composed, cinematic, one clear idea per shot, real film grain, natural and authentic, unobtrusive under VO · avoid glossy/shiny commercial finish, plasticky CGI look, busy/chaotic action, literal stock clichés, flat lighting, oversaturation.

## 3. Abstract creations
**What it is:** Elevated, art-directed abstraction of technology — the most on-house-brand type. Macro closeups of light strands and glowing nodes, particle fields, network meshes, dot-matrix globes, data-as-texture. Plus **compositing techniques**: double exposure, and ASCII / code-art / halftone overlays laid over an existing clip. The bar is **high design — not corny stock footage.** Artful, restrained, deliberate.

**Signature look (locked):** deep near-black space with luminous accents. Blue-white light lines and nodes, sparing orange/Avalanche-red focal points. Macro/extreme closeup with shallow bokeh, OR clean particle/mesh systems. Double-exposure blends (subject + data/texture). ASCII/code-art/dot-matrix/halftone treatments over real footage. Ordered, engineered motion — flowing, converging, resolving. High-design and intentional, never busy or cliché.

**Reusable look string** (paste into prompts, per shot):
> Elevated abstract technology visual, high design, deep near-black background, luminous blue-white light strands and glowing nodes, sparing orange/red focal accent, macro shallow bokeh or clean particle/network mesh, engineered flowing motion converging to order, artful and restrained, not stock footage, cinematic.

**Techniques to reach for:**
- **Macro/closeup** of fiber-optic light lines, nodes, textures — shallow bokeh.
- **Particle & network systems** — meshes, dot-matrix globes, connecting lines with node accents.
- **Double exposure** — blend a subject or landscape with data/texture.
- **ASCII / code-art / halftone overlay** — take an existing clip and lay a code/dot-matrix treatment over it (post/compositing step; can pair a Higgsfield clip with an overlay pass).
- **Data as texture** — charts/tickers used artfully, never as literal corny stock.

**Reference images:** macro of glowing fiber-optic strands with light nodes; extreme closeup of a stylus over a data/stock-chart screen (double-exposure feel, red/teal); particle dot-matrix globe inside an orange-node network mesh. (Add stills to `assets/abstract/`.)

**Pull references:** palette swatches, geometry/shape refs, or an existing clip to composite over. Often text-to-video — references optional.

**Model routing:** `cinematic_studio_3_0` (premium clean abstraction) → `wan2_6` (stylized/experimental, good for glitch/artful treatments) → `seedance_2_0` (loopable reference-driven). Overlays/double-exposure/ASCII usually a **post/compositing** pass on top of the generated clip.

**Default blocks:** `data-flow`, `network-form`, `unfold`, `deep-space`, `red-kick`, `geometric`, `settle`.

**Aspect defaults:** 16:9 and 1:1 loops; 9:16 for verticals.

**Brand fit:** strongest alignment with the house style — deep dark space, one red/orange focal accent, engineered geometry. Lean into it here.

**Do/Don't:** high design, one focal accent, ordered/engineered motion, artful compositing · avoid corny/literal stock footage, rainbow gradients, chaotic noise, generic "big data" clichés.

## 4. Motion graphic assets
**What it is:** Isolated motion elements built to be **composited into an edit**, not finished shots. Objects, icons, shapes, kinetic accents, transition elements, UI/logo motion — rendered on a clean keyable background so they can be dropped over any footage. Art direction is per-asset and open; the defining requirement is **isolation + keyability.**

**Signature spec (locked):** subject isolated on a **pure chroma-green background** (solid, evenly lit, no spill) for keying — or pure black / pure white / transparent where the tool supports it. No environment, no set, no cast shadows on the subject unless wanted in the key. Even lighting, crisp edges, no motion blur that would fight the key. Clean and technical.

**Reusable spec string** (paste into prompts):
> Single isolated {{element}} centered on a pure flat chroma-green screen background, evenly lit, no environment, no props, no cast shadows, crisp clean edges, no motion blur, designed for green-screen keying and compositing.
> (Swap "pure flat chroma-green screen" for "pure black background" or "pure white background" when better for the element.)

**Background & keying:** if a clean green render isn't achievable, generate on solid black/white and key with Higgsfield background-removal (`remove_background`, `video_background_remover`, `sam_3_video`) to produce an alpha/matte.

**Pull references:** `avalanche-logo` element, brand palette, any object/UI/icon stills to animate. Often best with a `generate_image` start frame first (element on green), then animate.

**Model routing:** `cinematic_studio_3_0` or `seedance_2_0` with a green-screen `start_image`; `kling3_0` for clean motion. Start frames via `nano_banana_2` / `seedream_v4_5` (prompt the pure background). Then key with the background-removal tools above.

**Default blocks:** `assemble-in`, `locked-reveal`, `settle`, `engineered` — plus whatever per-asset motion the brief calls for.

**Aspect defaults:** match the target edit (16:9, 1:1, 9:16); often the element is scaled in post so exact frame is flexible.

**Do/Don't:** clean even key, crisp edges, isolated subject, consistent lighting · avoid green spill/reflections on the subject, busy backgrounds, heavy motion blur, distorted logos/marks/type.

_No fixed art direction yet — refine per asset as briefs come in._

## 5. Snow & nature environments
**What it is:** The literal Avalanche world — alpine landscapes and snow phenomena. Glaciers and ice walls, peaks in haze, wind-sculpted snow textures, cloud-shrouded ranges, snow-dusted rock, and powder spray / slough in motion (the avalanche energy itself). Ranges from vast scale to intimate macro. Editorial, fine-art, quiet and cinematic.

**Signature look (locked):** cool **blue-grey duotone** grade — desaturated, near-monochrome with a cold cyan-blue cast, high-key snow with deep shadow accents. Overcast high-altitude flat light, or low raking side-light for snow-texture detail. Atmospheric haze, cloud, and mist. Fine photographic grain, subtle editorial framing. Cold, still, and vast — never warm or saturated. This cold blue-grey is the type's signature.

**Reusable look string** (paste into prompts, per shot):
> Alpine snow landscape, cool blue-grey duotone grade, desaturated near-monochrome with a cold cyan cast, high-key snow and deep shadow accents, overcast high-altitude light or low raking side-light on snow texture, atmospheric haze and cloud, fine photographic grain, editorial fine-art, quiet and vast, cinematic, no warm tones, no oversaturation.

**Motion note:** for the powder-spray / avalanche-slough shots, prompt real snow physics — a rider or slope releasing a plume of powder, billowing spray, drifting particles. This is the brand's namesake motion; treat it as hero material.

**Reference images:** stratified glacier ice wall; blue-hazed alpine peak and ridgelines; macro of wind-sculpted snow drifts with sparkle; cloud-shrouded snowy range; snow-dusted rocky summit; rider throwing a powder-spray slough down a slope. All in the cold blue-grey grade. (Add stills to `assets/snow-nature/`.)

**Pull references:** environment/location stills, snow-texture macros, weather/cloud refs, powder-motion refs.

**Model routing:** `veo3_1` (ultra-real nature, snow physics, light) → `cinematic_studio_3_0` (cinematic scale, epic genre) → `seedance_2_0` (reference-locked locations). Grade toward cold blue-grey in the prompt.

**Default blocks:** `earth-to-detail`, `rise-up`, `parallax-reveal`, `volumetric-disciplined`, natural high-altitude key, `settle`. Powder-spray = hero motion beat.

**Aspect defaults:** 16:9 and 21:9 for epic scale; 9:16 verticals also work (many refs are portrait).

**Brand fit:** distinct cold palette rather than the house dark-space/red — this is the natural-world register. Bring in Avalanche red only as a single rare accent (a lone figure, a marker) when needed; otherwise let the blue-grey and snow motion carry the brand association.

**Do/Don't:** real snow physics, cold blue-grey grade, grand but controlled, editorial restraint · avoid cartoonish/fake snow, warm tones, oversaturation, cluttered composition.

## 6. Avalanche motion-graphic assets
**What it is:** The signature brand asset. Two modes:
- **Mode A — Avalanche snow-blast (primary):** a photorealistic, high-energy avalanche/snow blast rendered on a clean **keyable or solid background** (black · redscreen · greenscreen) with a reserved safe area for a logo/tagline lockup. The hero brand motion — snow becomes the identity.
- **Mode B — Mark/geometry kinetic identity:** the Avalanche logo/triangle assembling, revealing, or resolving (the T1 family). Fragments → mark, engineered red-accent motion.

### Mode A — Avalanche snow-blast
**Signature look (locked):** dense snow chunks, shattered clumps, fine powder spray, airborne particles, a turbulent mist plume rising. Strong contact occlusion where snow overlaps + believable self-shadowing. Snow carries a **cool bluish/cyan tint — never pure white.** Clean safe area (bottom ~20–25%) left empty for a future logo/tagline. High-energy but controlled.

**Master prompt** (proven in NanoBanana Pro → use `nano_banana_2` for stills, then animate; swap the background line for the variant you need):
> **{{BACKGROUND}}.** Add a photorealistic, high-energy avalanche blast. Include dense snow chunks, shattered clumps, fine powder spray, airborne particles, and a turbulent mist plume rising upward; add strong contact occlusion where snow overlaps and believable self-shadowing within the snow. Clean safe area at the very bottom of the image (leave the bottom ~20–25% completely empty with no snow, mist, or particles) for a future logo/tagline. Snow color must have a cool bluish/cyan tint (not pure white).

**Background variants** (`{{BACKGROUND}}`):
- **Black:** "Black background/gradient" — safe area stays pure black. Default for logo-over-blast lockups.
- **Redscreen:** "Pure saturated red screen background (flat, even, for keying)" — keep snow neutral so red keys cleanly; safe area = flat red. (For a *designed* red look instead of a key, use Avalanche Red `#E84142`.)
- **Greenscreen:** "Pure flat chroma-green screen background (even, no spill)" — for keying the blast over any footage; safe area = flat green.

**Workflow:** `generate_image` (`nano_banana_2`) for the still → animate with `generate_video` (`cinematic_studio_3_0` / `kling3_0` / `seedance_2_0`) using it as `start_image` → key with `remove_background` / `video_background_remover` if on red/green. Register strong stills in `reference-assets.md`.

### Mode B — Mark / geometry kinetic identity
**Pull references:** `avalanche-logo` element (`fa96368e-...`, required), triangle/geometry refs, palette.
**Model routing:** `cinematic_studio_3_0` + logo `start_image` (template T1); `higgsfield_preset` assemble presets for fragment→mark.
**Default blocks:** `assemble-in`, `slow-push`, `red-kick`, `deep-space`, `geometric`, `cgi-reveal`, `settle`.

**Aspect defaults (both modes):** 16:9 hero, 1:1 / 9:16 for social stings.
**Brand fit:** the truest expression of the house style — deep black space, cyan snow, one decisive Avalanche-red moment, engineered motion. Bottom safe area keeps every asset lockup-ready.
**Do/Don't:** cyan-tinted snow, clean keyable/black background, protected bottom safe area, crisp mark integrity · avoid pure-white snow, spill onto the subject, particles in the safe area, logo distortion, cluttered chaos.

---

## Reference folders (create as you add assets)
`assets/human/` · `assets/b-roll/` · `assets/abstract/` · `assets/motion-graphics/` · `assets/snow-nature/` · `assets/avalanche-mg/`

Register the strongest stills as reference elements and log them in `reference-assets.md` so the skill can auto-pull them by type.
