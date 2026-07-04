# WORKED EXAMPLE — "No Card Machine" (read-only reference)

_A condensed end-to-end example of the v2 pipeline, from a one-line brief to a lint-passed canonical prompt. Use it to see what "good" looks like at each phase. Not a real project._

## Phase 1 — Entry point A (one-line idea)

> "A street food vendor in Bangkok gets paid instantly by a tourist — no card machine, no wait."

Deliverable: 16:9 · ~30s · X/web, muted-autoplay · text-overlay script (no VO) · style: suggest.

## Phase 2 — Hook (locked after 2 rounds)

**Hook:** "The fastest payment rail in the world is already at a plastic stool in Bangkok." Audience: crypto-curious mainstream. Tone: warm, observational, zero tech-speak on the human layer.

## Phase 3 — Script v3 (LOCKED) — register: documentary

1. Dawn prep at the stall — steam, charcoal, hands. _Overlay: "Bangkok. 6:04 AM."_ (establishes the human — sets up the hook's "plastic stool")
2. Lunch rush builds; @vendor works the wok, never looks up. _Overlay: none._ (pace)
3. @tourist points, orders; gets a nod. _Overlay: "No shared language."_ (tension)
4. @tourist holds phone over @terminal on the counter; a small nod from @vendor; food handed over in the same motion. _Overlay: "No card machine. No wait."_ (the payoff — the hook lands here)
5. @vendor back to the wok before the tourist has turned around. _Overlay: "Avalanche."_ (button)

## Phase 4 — Continuity bible (excerpt)

| @name | Type | element_id | Status |
|-------|------|-----------|--------|
| @vendor | character | `(registered in Phase 4)` | confirmed |
| @tourist | character | `…` | confirmed |
| @stall | environment | `…` | confirmed |
| @terminal | prop | `…` | confirmed |

- **@vendor locked phrasing:** "a Thai woman in her 50s, short grey-streaked hair, worn navy apron over a faded floral shirt, gold stud earrings"
- **@tourist locked phrasing:** "a tall man in his 30s, sunburnt, olive linen shirt with rolled sleeves, canvas tote on his left shoulder"
- **Prop timeline:** @terminal sits on the counter from beat 1 (visible but unremarked) → used beat 4 → unremarked beat 5. Tote stays on @tourist's shoulder throughout.
- **Element-usage map:** @terminal — counter shots only (S4); never at the wok, never held.
- **Crowd (S2):** "a motorbike courier in an orange vest waiting with a helmet under his arm; two schoolgirls sharing one skewer; an older man reading his phone under the awning."
- **Extra negatives:** "no cash visible anywhere, no QR codes on screen."

## Phase 5 — Shotlist (approved) — model: `seedance_2_0` std 1080p · 16:9 (confirmed)

S1 dawn-prep (b1, 3s) · S2 rush (b2, 3s) · S3 order (b3, 3s) · S4 payment (b4, 3s) → **G1, 12s**. S5 back-to-wok (b5, 3s) + brand button → **G2, 6s**. ~3s/shot ✓ no over-packing.

## Phase 6 — Canonical prompt, G1 (lint: PASS 8/8)

```
GENERATION 1 of 2 — "No Card Machine" · covers script beats 1–4

ELEMENTS
@vendor — a Thai woman in her 50s, short grey-streaked hair, worn navy apron
          over a faded floral shirt, gold stud earrings
@tourist — a tall man in his 30s, sunburnt, olive linen shirt with rolled
           sleeves, canvas tote on his left shoulder
@stall — a small Bangkok street-food stall under a green awning, plastic
         stools, charcoal grill and wok station
@terminal — a small matte payment terminal resting on the stall counter

SHOT 1 — dawn-prep (3s)
Early morning at @stall. @vendor lights the charcoal and lays out skewers;
steam rises through low warm light. The @terminal sits on the counter,
unremarked. Clean compositional room in the lower third for a text overlay.

Camera: static eye-level medium shot, candid, letting the moment play.

SHOT 2 — rush (3s)
Midday. @vendor works the wok without looking up. Around the stall: a
motorbike courier in an orange vest waiting with a helmet under his arm;
two schoolgirls sharing one skewer; an older man reading his phone under
the awning.

Camera: subtle handheld drift, eye-level, breathing with the subject.

SHOT 3 — order (3s)
@tourist, canvas tote on his left shoulder, points at the menu board and
holds up two fingers. @vendor answers with a single nod, already reaching
for the wok.

Camera: handheld tracking alongside the subject, motivated by their movement.

SHOT 4 — payment (3s)
At the counter, @tourist holds his phone briefly over the @terminal. A small
nod from @vendor as she hands over the food in the same motion — the payment
is over before the exchange feels like it began.

Camera: close insert on hands/object, shallow focus, quick and purposeful;
motion settles into stillness on the final beat.

LOOK
Shot on 35mm film, Kodak Vision3 / Portra tones, naturalistic warm light and
soft diffused light, gentle film grain, soft halation, documentary realism,
photographed not rendered, no oversaturation.

AUDIO
Diegetic only, no music, no score. Street ambience, charcoal crackle, wok
sizzle, crowd murmur. No discernible dialogue.

AVOID
no garbled or legible signage text, no readable posters or screens, no
third-party logos or brand marks, no on-screen text or UI or captions, no
watermark, no oversaturation, no glossy plasticky CGI, no CGI glow on real
devices, no facial mesh or wireframe on the face, no cyan or green tech-HUD
overlays, no extreme eye close-ups, no dot-grid scan animations, no red
reticles or target-locks on the face, no cold clinical lab settings, no
surveillance or "system watching you" POV, no music, no score, no slow-motion
glamour, no forced smiles, no uncanny faces, each background character
described distinctly, no cash visible anywhere, no QR codes on screen.

FORMAT
16:9 · 12s · seedance_2_0 (std, 1080p) · 4 shots · audio on
```

Submit view: identical, with each @name replaced by its `<<<element_id>>>`; @terminal also passed as an explicit image-reference media (hero-prop reinforcement).

## Phase 7 — (example stops here)

Next: prompt diff (n/a, v1) → `get_cost: true` → show credits → explicit OK → single submit.
