# Global Negatives — the baked-in AVOID list

Every prompt's **AVOID** section is assembled from these tiers, in order. Tiers 1–2 are always on. Never make the editor re-type any of this.

## Tier 1 — Universal (every prompt, every type)

> no garbled or legible signage text, no readable posters or screens, no third-party logos or brand marks, no on-screen text or UI or captions, no watermark, no oversaturation, no glossy plasticky CGI, no CGI glow on real devices

## Tier 2 — De-creep (every prompt containing a person or a device)

> no facial mesh or wireframe on the face, no cyan or green tech-HUD overlays, no extreme eye close-ups, no dot-grid scan animations, no red reticles or target-locks on the face, no cold clinical lab settings, no surveillance or "system watching you" POV

## Tier 3 — Style-conditional (add when the type applies)

| Condition | Add |
|-----------|-----|
| Filmed/narrative types (documentary, commercial, snow) | no music, no score, no slow-motion glamour, no forced smiles, no uncanny faces |
| Crowd or group in shot | each background character described distinctly — vague group descriptions collapse into sameness |
| Snow & nature | no cartoonish or fake snow, no warm tones |
| Motion-graphic / keyable assets | no green spill on subject, no cast shadows into the key, no heavy motion blur, no logo distortion |
| Graphic register (abstract / avalanche-mg) | no rainbow gradients, no neon-purple crypto cliché, no gold coins, no chaotic noise |

## Tier 4 — Project extras (per-project slot)

Lives in the project's continuity bible under **Extra negatives**. Anything the project teaches you goes here immediately — e.g. from the NEC film: "no wedding dresses in street scenes", "only the bride wears a sash". Once added, it ships in every subsequent prompt for that project automatically.

## Assembly rule

AVOID = Tier 1 + Tier 2 (if person/device) + matching Tier 3 rows + Tier 4, deduplicated, as one comma-separated paragraph. Paste verbatim — never paraphrase or trim.
