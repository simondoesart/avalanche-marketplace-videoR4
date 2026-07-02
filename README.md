# avalanche-marketplace-videoR4

A Claude **plugin marketplace** for Avalanche brand video generation.

## Repo structure (this folder = repo root)
```
avalanche-marketplace-videoR4/
├── .claude-plugin/marketplace.json   ← marketplace catalog (HIDDEN folder)
├── plugins/avalanche-video/          ← the plugin
└── README.md
```
Reveal the hidden `.claude-plugin` folder in Finder with **Cmd + Shift + . (period)**.

## Install (Claude Code / terminal)
```
/plugin marketplace add simondoesart/avalanche-marketplace-videoR4
/plugin install avalanche-video@avalanche-marketplace-videoR4
/reload-plugins
```
Connect the **Higgsfield** MCP when prompted, then run `/avalanche-video:make-video`.

## Note
Add the official logo at `plugins/avalanche-video/assets/avalanche-logo.png` before use.
