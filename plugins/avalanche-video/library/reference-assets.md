# Element Library — Visual Reference Assets

Registry of reusable brand assets that feed image-to-video. Two kinds of reusable identity in Higgsfield:

- **Reference Elements** (`show_reference_elements`) — instant, image-based characters / environments / props. Multiple per shot. Referenced in prompts as `<<<element_id>>>`.
- **Soul Characters** (`show_characters`) — trained identities (5–20 photos, ~10 min). One per shot. Soul V2 / Cinema models only.

---

## How to register an asset (Reference Element)

1. `media_upload` → PUT the file bytes → `media_confirm` (get a `media_id`).
2. `show_reference_elements` action=`create` with `medias:[{id, url}]`, `category` auto, optional `name`.
3. Record it in the table below.
4. Use it in any prompt by embedding `<<<element_id>>>` — the backend injects the image automatically.

Files to register live in `/assets/` in this folder (drop logos, palettes, product renders, reference stills there).

---

## Registered elements

| Name | Type | element_id | Notes |
|------|------|-----------|-------|
| avalanche-logo | prop | `fa96368e-32ec-49c7-8f59-e09a51b7e22b` | Horizontal 4C KO logo. Use as start_image or `<<<fa96368e-32ec-49c7-8f59-e09a51b7e22b>>>` in prompts. First used in T1 test (job e4d1fe21). |
| | environment | | Deep-space brand background plate |
| | prop | | Hero product render |

## Soul characters (trained)

| Name | soul_id | Status | Notes |
|------|---------|--------|-------|
| _(none yet)_ | | | Only needed if we feature a recurring on-camera person |

---

## Palette swatches (for start-frame generation)

Feed these hexes into `generate_image` prompts to keep frames on-palette:
- Avalanche Red `#E84142` · Near-black `#0A0A0B` · Off-white `#F5F6F7` · Graphite `#2A2E33`

## Suggested first uploads
1. **Avalanche logo mark** (transparent PNG) → the hero of T1.
2. **Brand background plate** (deep-space dark) → reusable environment.
3. **Primary product render** (if applicable) → T2 glamour orbit.
4. **2–3 on-brand reference stills** (looks we want to match) → style anchors.

Once these exist, most videos become: pick a template → drop in the element → generate.
