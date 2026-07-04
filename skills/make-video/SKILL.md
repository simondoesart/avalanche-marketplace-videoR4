---
name: make-video
description: >
  All-in-one Avalanche video pipeline: take a brief at any stage (a one-line idea, an
  existing creative strategy/PR hook, a script, or a shotlist), workshop the strategy and
  script heavily BEFORE any shots, build a continuity bible with @element naming, produce
  a human-reviewable shotlist and canonical prompts, then generate via the Higgsfield MCP.
  Use when the user says "/make-video", "make a branded video", "new Avalanche video",
  "write a video script", or asks to plan or generate an Avalanche brand video.
---

# make-video v2 — strategy → script → continuity → shots → generate

An editor gives a minimal brief; this pipeline returns a full video plan, a workshopped script, a continuity-safe shotlist, human-readable prompts, and (on approval) Higgsfield generations. **Writing comes first. No shotlist, no elements, no prompts until the script is locked.**

## Ground rules (every run)

1. **Read the plugin files first**: `brand/brand-visual-style.md`, `library/video-types.md`, `library/prompt-format.md`, `library/global-negatives.md`, `library/prompt-building-blocks.md`, `library/scene-shot-templates.md`, `library/reference-assets.md`, `briefs/_TEMPLATE.md`, `briefs/_CONTINUITY_TEMPLATE.md`. If the normal file tool can't reach them (read-only plugin cache), read via the shell VM path — never skip them.
2. **Robust intake:** use AskUserQuestion for choices and plain chat for long text. Never rely on rich/custom form widgets; if one fails to render, fall back immediately. Never leave the user staring at a blank form.
3. **Two artifacts per project**, created from the templates and kept current: `briefs/<slug>.md` (the brief sheet — single source of truth) and `briefs/<slug>-continuity.md` (the bible). Every decision lands in them; any field is editable at any time.
4. **Prompts are derived.** Edits go to the script/shotlist/bible; prompts regenerate from source (see `library/prompt-format.md`).
5. **Money:** preflight every cost, confirm every submit, one generation per confirmation, never blind-retry. Auto-retry once on transient 401/5xx for `get_cost`/status polls only — never for submits.

## First-run setup (once per Higgsfield account)

Element IDs are per-account. On a fresh install: check `list_workspaces`; upload `assets/avalanche-logo.png` (`media_upload` → PUT → `media_confirm`), register via `show_reference_elements` create, record the id in `library/reference-assets.md`.

---

## Phase 1 — Intake: meet the brief where it is

Ask what already exists and classify the entry point:

- **A. One-line idea / statement** → run Phases 2→9 in full.
- **B. Existing creative strategy / PR hook** → capture verbatim, mark strategy LOCKED, start at Phase 3.
- **C. Existing script** → capture verbatim, offer one workshop pass against the hook, then Phase 4.
- **D. Existing shotlist or reference shots/styles** → capture, back-fill script + bible from it (Phases 3–4 compressed), then continue.

Also collect now (one AskUserQuestion batch): aspect ratio (16:9 / 9:16 / 1:1 / 21:9), target length, platform + muted-autoplay?, text plan (none / text-overlay / VO), and whether a style register is already decided — documentary · commercial advertisement · motion-graphic · abstract · snow-nature · avalanche-mg (see `library/video-types.md`) — or whether to suggest one. Create the brief sheet.

## Phase 2 — Strategy & hook (skip if provided)

Workshop, don't dictate: audience → core message → **the hook** (the one line that makes someone stop) → tone. Offer 2–3 candidate concepts with hooks when the editor has none. Iterate until the editor says **locked**. Write the locked strategy into the brief sheet. Everything downstream must trace back to this hook.

## Phase 3 — Script workshop (the heart — budget the most rounds here)

1. **Style register:** confirm or recommend one (with a one-line rationale) — it sets the look string and model routing.
2. **Draft the script** as numbered beats. Per beat: the action (one short paragraph) + the overlay/VO line if the text plan has one. Every beat must serve the hook — annotate how ("beat 4 = the payoff of the hook").
3. **Workshop in rounds.** Present the full script, invite line-level notes, apply, re-present with a one-line change log. In every round, proactively flag any beat that doesn't serve the hook and propose the fix — don't wait for the editor to catch it. Expect and welcome multiple rounds — this is the cheap place to iterate; generations are the expensive place. Save each version in the brief sheet (v1, v2, …).
4. **Gate:** proceed only when the editor explicitly locks the script. New characters/props/locations discovered while writing → note them for Phase 4, don't register anything yet.

## Phase 4 — Continuity bible + @element manager (before ANY shotlist)

1. **Extract** every character, prop, and location from the locked script; propose @names (lowercase-hyphen, unique — the @name must equal the Higgsfield element name, since the backend rewrites `<<<id>>>` to `@element_name`).
2. **Sync with the account:** run `show_reference_elements` (and `show_characters` if Soul identities exist). Print a table: @name candidate → any existing element with the same/similar name, id, created date. **Naming:** if a proposed @name collides with an old element, pick a fresh unique name (e.g. `@vendor-bkk`) — never let a new project inherit an old element by name accident.
3. **Default: create NEW elements for every project.** Existing library elements are reused **only when the editor explicitly specifies one** (e.g. `@avalanche-logo`, or a recurring campaign character named by the editor). Confirm the working set as: which @names get new imagery (all, by default) and which, if any, the editor has explicitly pointed at an existing element.
4. **New imagery:** chat-attached files are unreadable by the remote MCP — always route uploads through `media_upload_widget`. Or generate references (`generate_image` → `nano_banana_2` / `seedream_v4_5`), confirm the still with the editor, then register. Record every new @name → id in the bible AND `library/reference-assets.md`.
5. **Write the bible** from `_CONTINUITY_TEMPLATE.md`: locked wardrobe phrasing per character, prop-state timeline (luggage logic!), locations/geography, the **element-usage map** (each element → exact shots allowed, e.g. "@kiosk-scanner: kiosk shots only"), distinct background-character descriptions for any crowd, and project extra negatives. Editor confirms the bible before Phase 5.

## Phase 5 — Shotlist

1. Convert locked beats into numbered shots (S1…): beat ref, @elements used, one-line action, camera, est. seconds.
2. **Duration heuristic:** ~2.5–3s per shot. Warn on over-packing (5 shots in 10s reads rushed — recommend 12s or fewer shots).
3. **Pack shots into generations** per model capability (e.g. `seedance_2_0`: 3–4 shots per 10–12s multi-shot generation, identity held by character elements). Show the packing plan (G1 = S1–S4, …).
4. **Model + aspect confirmation (explicit):** verify current models with `models_explore`, recommend per the style register's routing (`library/video-types.md`), present 2–3 options with credit implications, and have the editor confirm **both model and aspect ratio** — never assume. Log in the brief sheet.
5. Editor approves the shotlist → Phase 6.

## Phase 6 — Compose prompts (canonical format, then lint)

1. Build one prompt block per generation **exactly** per `library/prompt-format.md`: ELEMENTS (locked phrasing verbatim) / numbered SHOTs with paragraph breaks / LOOK (style descriptor verbatim) / AUDIO / AVOID (assembled per `library/global-negatives.md`) / FORMAT.
2. **Continuity lint** (bible §8 checklist) on every prompt: elements confirmed + in usage map, wardrobe verbatim, prop states match timeline, crowds distinct, extras present, 4+ refs in one shot flagged as drift risk. Fix failures before showing anything.
   - **Hero-prop reinforcement:** for a critical prop that must render exactly (e.g. a payment terminal), pass it twice — embedded `<<<id>>>` in the prompt AND as an explicit `medias` entry with an image-reference role (supported by `seedance_2_0`).
3. Present review view (@names). Apply edits at source, regenerate, show a short diff. On approval, produce the submit view (`<<<element_id>>>`).

## Phase 7 — Preflight & generate (one at a time)

1. **Prompt diff:** if this prompt changed since last shown, display the diff before costing.
2. `generate_video` with `get_cost: true` → show credits (retry once on transient 401/5xx). Check balance via `show_plans_and_credits` for multi-generation plans.
3. **Warn before submit:** an in-flight job can't be edited — a late tweak means a deliberate re-run at full cost. Last call for changes.
4. On explicit go: submit **once**. If Higgsfield interrupts with a stock-preset suggestion on narrative/brand work, decline it without asking: resubmit the same literal generation immediately with `declined_preset_id` = the suggested preset's id (this counts as the same confirmed submit, not a new one). Record job ID + prompt version in the generation log. On an ambiguous error, check `show_generations` before any resubmit.
5. Google Flow instead of Higgsfield: output the finalized prompt + settings for manual pasting; result goes to `renders/`.

## Phase 8 — Review & iterate

Poll `job_display`. Review against (a) the continuity bible — identity, wardrobe, prop state, element placement, crowd distinctness; (b) the brand file's Do/Don't; (c) the hook — does the shot still serve it? On a miss: change only the failing block/shot at source, re-lint, re-diff, re-preflight. Log findings in the brief sheet.

## Phase 9 — Wrap

Save winners: append exact prompt + model + job ID as a new template in `library/scene-shot-templates.md`; add project learnings to the bible's extra negatives if they generalize (then promote to `global-negatives.md`); mark the brief sheet done. Renders live in the Higgsfield account — link them.

---

## Editing anything, any time

Brief sheet + bible = source of truth. "Change X" → edit the source artifact, re-derive downstream only (a wardrobe change re-lints prompts; a strategy change reopens the script), show what changed, re-confirm before any new spend.

## Guardrails

- Script locked before shotlist; bible confirmed before prompts; lint before review; diff + cost + explicit OK before submit.
- Style descriptor and AVOID list ship verbatim — paraphrasing is drift.
- Decline off-brand stock presets automatically on narrative work (resubmit with `declined_preset_id`).
- Always report: job ID, prompt version, credits spent, which template/blocks were used.
