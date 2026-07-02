---
name: make-video
description: >
  Produce an on-brand Avalanche video end to end via the Higgsfield MCP. Runs a guided
  intake (story angle, brief/script, aspect ratio, video type, generation tool, model,
  duration, elements, reference uploads) with every field editable, then generates,
  reviews against brand, and saves winners. Use when the user says "/make-video",
  "make a branded video", "new Avalanche video", or asks to generate an Avalanche brand video.
---

# make-video — Avalanche branded video pipeline

Turn an idea into an on-brand Avalanche video. **Always run the intake before generating — never jump straight to `generate_video`.**

## Plugin files (read first, every run)
This plugin bundles the brand system. Read these from the plugin root before anything else:
`brand/brand-visual-style.md`, `library/video-types.md`, `library/prompt-building-blocks.md`, `library/scene-shot-templates.md`, `library/reference-assets.md`. They hold the look rules, the six video-type definitions, reusable prompt pieces, and the reference-element registry.

## First-run setup (do once per Higgsfield account)
Reference-element IDs are per-account, so the bundled `avalanche-logo.png` must be registered in **this** installer's Higgsfield workspace before it can be used in prompts:
1. Confirm the Higgsfield MCP is connected (`list_workspaces`). If not, tell the user to connect it (this plugin declares the server; they authenticate with their own Higgsfield account).
2. Upload `assets/avalanche-logo.png` (`media_upload` → PUT bytes → `media_confirm`).
3. Register it (`show_reference_elements` action=create) and write the returned `element_id` into `library/reference-assets.md`.
4. Repeat for any other bundled assets. After this, prompts can use the logo via `<<<element_id>>>` or as a `start_image`.

## Step 0 — Open a brief sheet
Create/overwrite a `briefs/<slug>.md` from `briefs/_TEMPLATE.md` — the single editable record of every field. Update it as answers arrive; re-show it whenever the user changes something. This persistence is what makes every field revisable.

## Step 1 — Intake (ask, don't assume)
Collect these in small batches (AskUserQuestion for choices; free text directly). Write answers into the brief sheet.
1. **Story angle** — have one, or generate from the brief?
2. **Brief or script** — the long input, verbatim; context to edit or build a script from.
3. **Aspect ratio** — 16:9 hero · 9:16 social · 1:1 feed · 21:9 epic.
4. **Video type** — one of the six in `library/video-types.md`. Drives references + model routing.
5. **Generation tool** — Higgsfield (connected/automated) · Google Flow (no MCP → manual handoff: produce a Flow-ready prompt, user runs it in Flow, imports result into `renders/`).
6. **Model** — list only models available for the tool. For Higgsfield call `models_explore`, recommend per the video-type routing, show 2–3 with a default.
7. **Duration** — seconds; note the model's allowed range.
8. **Elements to include** — logo, product, character, prop, environment, on-frame text; map each to a reference element.
9. **Reference uploads** — offer `media_upload_widget` for Location/Character/Prop imagery. Register uploads as reference elements, log in `library/reference-assets.md`, embed as `<<<element_id>>>`. No images? Offer to generate them (`generate_image` → `nano_banana_2` / `seedream_v4_5`).

## Step 2 — Script / story angle (default: auto-draft, then confirm)
If the angle/script needs creating, draft from the brief in brand voice for the chosen type, then show for edits/approval before generating. New characters/props → loop back to Step 1.

## Step 3 — Confirm the full brief (editable)
Show the complete brief sheet; invite changes to any field. Proceed only on approval.

## Step 4 — Compose the prompt
`SUBJECT + CAMERA + MOTION + LIGHTING + STYLE + aspect/duration`, pulling the chosen type's look string + default blocks and embedding `<<<element_id>>>` references. Reuse a matching `T#` template when one fits.

## Step 5 — Preflight + confirm cost (MANDATORY)
`generate_video` with `get_cost: true`, show the credit cost, WAIT for explicit go-ahead.

## Step 6 — Generate (once)
Submit exactly one `generate_video`. Record the job ID in the brief sheet.
- Never blind-retry. On an ambiguous error, call `show_generations` to check whether the job already landed before resubmitting. One submit per confirmation.
- Google Flow: output the finalized Flow-ready prompt + settings instead; result goes into `renders/`.

## Step 7 — Review against brand
Poll `job_display`. Check vs the Do/Don't cheat-sheet and the video-type notes. If off, adjust the specific block and regenerate — don't rewrite everything.

## Step 8 — Finalize + save
`upscale_video` / `reframe` for other aspects. Append the exact prompt + model + job ID as a new `T#` in `library/scene-shot-templates.md`; mark the brief sheet done. Renders live in the Higgsfield account — link the result; the user saves from the widget.

## Editing any field, any time
Brief sheet = source of truth. On "change X": edit that line, re-derive downstream (changing video type re-pulls references + re-routes the model), re-confirm, then regenerate.

## Guardrails
- One red focal point per shot; deep dark space by default; engineered motion.
- Skip off-brand stock presets (K-pop, paparazzi, retro-game, dance memes).
- **Confirm every submit.** Preflight cost, get OK, one generation per confirmation, verify with `show_generations` before any resubmit.
- Check credits with `show_plans_and_credits` before large batches.
- Always report the job ID and which template/blocks were used.
