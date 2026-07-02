# Avalanche Video — Claude plugin

Everything a video editor needs to generate on-brand Avalanche videos with Claude + Higgsfield, in one installable bundle.

## What's inside
```
avalanche-video/
├── .claude-plugin/plugin.json   # plugin manifest
├── .mcp.json                    # declares the Higgsfield MCP server
├── skills/make-video/SKILL.md   # the /make-video pipeline
├── commands/make-video.md       # command playbook (same flow)
├── brand/brand-visual-style.md  # the look & motion rules
├── library/
│   ├── video-types.md           # the 6 video types + reference/model routing
│   ├── prompt-building-blocks.md
│   ├── scene-shot-templates.md  # T1–T7 ready-to-fire templates
│   └── reference-assets.md      # element registry (re-registered per account)
├── briefs/_TEMPLATE.md          # editable per-video brief sheet
└── assets/                      # bundled brand assets (add avalanche-logo.png)
```

## Install (direct handoff)
1. Unzip this folder.
2. Add it as a plugin in Claude (Cowork/Claude Code): **Settings › Capabilities › add plugin**, and point to this folder (or a marketplace that lists it).
3. Connect the **Higgsfield** MCP when prompted — each editor authenticates with **their own** Higgsfield account (their credits, their generations). The server is already declared in `.mcp.json`.

## First run
- The skill runs a one-time **setup**: it uploads `assets/avalanche-logo.png` into the editor's Higgsfield workspace, registers it as a reference element, and records the new ID in `library/reference-assets.md`. (Element IDs are per-account, so this can't be pre-baked.)
- ⚠️ **Add the logo file first:** drop the official transparent horizontal KO logo into `assets/avalanche-logo.png` before zipping/handing off. (It couldn't be auto-bundled from the source account.)

## Use
Ask Claude: **"make a branded video"** (or run `/make-video` once installed as a real command). It runs a guided intake — story angle, brief/script, aspect ratio, video type, tool, model, duration, elements, reference uploads — every field editable, then generates, reviews against brand, and saves winners.

## Updating
Edit any file in this folder and re-hand-off, or edit the installed skill in Settings › Capabilities. Nothing is locked.

## Notes
- **Google Flow** has no MCP connector — it's a manual handoff (the skill outputs a Flow-ready prompt to paste in Flow; drop the result into `renders/`).
- Renders live in the Higgsfield account; save them from the Higgsfield result widget.
