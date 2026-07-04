# Avalanche — Brand Visual Style (Video) · v2

> Single source of truth for how Avalanche videos look, move, and sound.
> Every generation reads from this file. Edit here → every future video changes.

---

## 1. Essence

**Photographed, not rendered.** Real light, real texture, real people. Warmth on the human; restraint everywhere else. The brand shows up through story and a single decisive accent — never through gloss, HUDs, or CGI polish.

Three words to hold on every shot: **Warm. Grounded. Deliberate.**

---

## 2. The house look (default for every video)

This is the locked style descriptor. It ships verbatim in the **LOOK** section of every prompt unless the chosen video type overrides it:

> Shot on 35mm film, Kodak Vision3 / Portra tones, naturalistic warm light and soft diffused light, gentle film grain, soft halation, documentary realism, photographed not rendered, no oversaturation.

**Pacing:** fast-paced but grounded — quick, purposeful cuts, each shot one clear idea, motion always motivated by the story.

**Framing:** eye-level, candid, lived-in spaces. Subtle handheld drift is welcome; whip-chaos is not.

## 3. Audio (locked)

> Audio: diegetic only, no music, no score.

Natural ambient sound belongs to the scene — room tone, streets, machines, breath. Score/music only when a brief explicitly asks for it. No lip-synced or discernible dialogue unless intended. Assume muted-autoplay: the story must land silent.

## 4. The avoid list (locked — the "de-creep" rulebook)

Ships verbatim in the **AVOID** section of every prompt (see `library/global-negatives.md` for the full tiered list):

> Avoid: any facial mesh or wireframe on the face, cyan or green tech-HUD overlays, extreme eye close-ups, dot-grid scan animations, red reticles or target-locks on the face, cold clinical lab settings, surveillance or "system watching you" POV, on-screen text or UI, oversaturation, glossy plasticky CGI.

Principle behind it: **technology in Avalanche stories is warm, human, and invisible** — never surveillance-coded, never clinical, never a system watching a person.

---

## 5. Color

Film-native palette first: desaturated greens, warm browns, honest skin tones, natural highlights with soft halation. No forced grade.

Brand accents, used sparingly:

| Role | Color | Hex | Use |
|------|-------|-----|-----|
| Primary accent | Avalanche Red | `#E84142` | One intentional accent per video when the brand needs to register — a garment, a marker, a light. Never wallpaper. |
| Deep base | Near-black | `#0A0A0B` | Backgrounds for the graphic register only (see §8). |
| Light base | Off-white | `#F5F6F7` | Clean surfaces, motion-graphic plates. |
| Cool support | Graphite | `#2A2E33` | Graphic-register mid-tones. |

**Rules:** no rainbow gradients, no neon-purple "crypto" cliché, no gold coins, no oversaturation — ever.

## 6. Motion language

- **Motivated movement:** the camera moves because the story moves — following, revealing, arriving. Subtle handheld for human moments; smooth deliberate moves for emphasis.
- **Fast-paced but grounded:** cut rhythm carries energy; individual shots stay calm and legible. ~2.5–3s per shot.
- **A beat of settle:** end moves with a moment of stillness when the shot is a closer.
- Avoid: dance/meme energy, whip-chaos, random drift, slow-motion glamour unless briefed.

## 7. On-frame text

Default: **none** (it's in the avoid list — AI-generated type garbles). Text overlays are added in the edit, not in generation. When a text-led script is the concept, plan overlay timing in the script and leave clean compositional room; prefer clean geometric sans (Inter / Archivo / Montserrat), white or Avalanche Red, in post.

---

## 8. Legacy graphic register (opt-in only)

The former house style — deep near-black space, engineered motion, one red focal point, assembling geometry, CGI reveals — is retained **only** for the graphic video types (`abstract`, `motion-graphic`, `avalanche-mg` in `library/video-types.md`). It is no longer the default. Never apply it to human-centric or narrative work, and never mix its HUD/mesh/CGI vocabulary into filmed material.

---

## 9. Do / Don't cheat-sheet

**Do:** 35mm film texture · warm naturalistic light · real emotion, candid beats · diegetic sound only · one red accent max · fast, purposeful cut rhythm · distinct, described background characters · photographed not rendered.

**Don't:** facial mesh/wireframe · tech-HUD overlays · eye macro close-ups · scan/reticle animations · clinical labs · surveillance POV · on-screen text or UI · oversaturation · glossy plasticky CGI · garbled signage · third-party logos · music/score (unless briefed) · crowd sameness.

---

## 10. Growing this file

When a generation nails the look, save its job ID + exact prompt as a template in `library/scene-shot-templates.md` and note here what made it work.
