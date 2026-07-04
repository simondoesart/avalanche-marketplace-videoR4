# Avalanche Video — Claude plugin (v2)

All-in-one Avalanche video tool: define the strategy, workshop the script, plan continuity with @elements, build the shotlist, and generate via the Higgsfield MCP — from a minimal brief.

## What's inside
```
avalanche-video/
├── .claude-plugin/plugin.json      # plugin manifest
├── .mcp.json                       # declares the Higgsfield MCP server
├── skills/make-video/SKILL.md      # the v2 phased pipeline
├── brand/brand-visual-style.md     # house look: 35mm film / diegetic audio / de-creep
├── library/
│   ├── video-types.md              # 6 style registers + model routing
│   ├── prompt-format.md            # canonical human-reviewable prompt layout
│   ├── global-negatives.md         # baked-in tiered AVOID lists
│   ├── prompt-building-blocks.md   # shot phrases + duration heuristic + routing
│   ├── scene-shot-templates.md     # saved winning templates
│   └── reference-assets.md         # element registry (re-registered per account)
├── briefs/
│   ├── _TEMPLATE.md                # per-video brief sheet (phased)
│   └── _CONTINUITY_TEMPLATE.md     # continuity bible: @elements, wardrobe locks, usage map
└── assets/                         # bundled brand assets (avalanche-logo.png)
```

## The pipeline (what "/make-video" does)

1. **Intake** — brief enters at any stage: one-line idea, existing strategy/PR hook, existing script, or existing shotlist/style refs.
2. **Strategy & hook** — workshopped until locked (skipped if provided).
3. **Script workshop** — the heavy phase: versioned drafts, line-level rounds, locked before anything visual.
4. **Continuity bible + @elements** — every character/prop/location gets an @name matching a Higgsfield reference element (dedupe check, upload widget, usage map, locked wardrobe phrasing).
5. **Shotlist** — beats → numbered shots, ~2.5–3s/shot, packed into generations; model + aspect explicitly confirmed.
6. **Prompts** — one canonical, human-readable block per generation; continuity-linted before review.
7. **Generate** — prompt diff → cost preflight → explicit OK → one submit (stock presets declined by default).
8. **Review & wrap** — checked against bible + brand; winners saved as templates.

## Install (per editor)
1. Add this folder (or its marketplace) as a plugin: **Settings › Capabilities › add plugin**.
2. Connect the **Higgsfield** MCP when prompted — each editor authenticates with **their own** Higgsfield account (their credits, their generations).
3. First run registers `assets/avalanche-logo.png` as a reference element in that account (IDs are per-account).

## Use
Say **"/make-video"** or "make a branded video" — or just paste a brief/script and say what you're making.

## Notes
- **Google Flow** has no MCP — the skill outputs a paste-ready prompt instead; drop results into `renders/`.
- Renders live in the editor's Higgsfield account; save from the result widget.
- Editing: change any file here and re-hand-off, or edit the installed skill in Settings › Capabilities.
