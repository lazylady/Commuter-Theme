# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A single color theme ("Commuter") ported to several editors and terminals. There is no build system, no tests, no package manager — each file in [Themes/](Themes) is the distribution artifact for one target app, consumed directly by that app's theme loader. Changes are made by editing the files in place.

## The shared palette

Every theme file is a manual re-encoding of the same palette in a different format. The canonical source is [PALETTE.md](PALETTE.md) — palette tokens, semantic roles, TextMate + Zed scope mappings, UI roles, ANSI palette, and porting checklist. Consult it before changing any color or adding a new port.

Rules derived from it:

- When changing a color, change it everywhere it appears across all theme files. The palette is the source of truth; drift between files is a bug.
- Hex uppercase everywhere except [Themes/Commuter.ghostty](Themes/Commuter.ghostty) (lowercase — matches Ghostty's stock themes). Follow the existing convention within each file.
- Cyan (`#109AC4` / ANSI `#66CCCC`) is a navigational accent — focus rings, active panes, links, prompts. Never content.
- Warm tones (orange/red/green/rose) carry semantic meaning (warnings, errors, success, strings). Preserve these roles when editing.

## Per-target format notes

- **TextMate / Sublime** — [Themes/Commuter.tmTheme](Themes/Commuter.tmTheme): Apple plist XML, scope-selector based.
- **Xcode** — [Themes/Commuter.xccolortheme](Themes/Commuter.xccolortheme): plist with `DVT*` keys; colors are space-separated `r g b a` floats (0–1), not hex. Convert carefully.
- **Zed** — [Themes/Commuter.json](Themes/Commuter.json): JSON against `https://zed.dev/schema/themes/v0.2.0.json`. Supports 8-digit hex with alpha (e.g. `#4D97FF66`).
- **VS Code** — [Themes/Commuter.vscode.json](Themes/Commuter.vscode.json) + [Themes/Commuter.vscode-package.json](Themes/Commuter.vscode-package.json) + [Themes/Commuter.vscode-README.md](Themes/Commuter.vscode-README.md). JSONC; supports 8-digit hex with alpha. Workbench colors are flat keys (`editor.background`, `sideBar.foreground`, …) — see [VS Code's theme color reference](https://code.visualstudio.com/api/references/theme-color) for the full set. TextMate-scope tokenColors under `tokenColors`; workbench tokens under `colors`. Structurally parallels [Commuter.json](Themes/Commuter.json) (Zed) — if you add a color to one, add it to both.
- **Obsidian** — [Themes/Commuter.obsidian.css](Themes/Commuter.obsidian.css) + [Themes/Commuter.obsidian-manifest.json](Themes/Commuter.obsidian-manifest.json) + [Themes/Commuter.obsidian-README.md](Themes/Commuter.obsidian-README.md). Dark-mode only; light mode falls back to Obsidian defaults. The three files get installed together into a per-theme folder (see root [README.md](README.md)).
- **Alfred** — [Themes/Commuter.alfredappearance](Themes/Commuter.alfredappearance): JSON under an `alfredtheme` root key. All hex values are 8-digit `#RRGGBBAA`. The theme also carries typography (font/size) and layout (padding, blur, roundness) — those are Alfred requirements, not palette concerns, so don't edit them for color work. Double-click to import.
- **Ghostty** — [Themes/Commuter.ghostty](Themes/Commuter.ghostty): 16-color ANSI palette with a defined normal/bright split. Order matters.
- **Terminal.app** — [Themes/Commuter.terminal](Themes/Commuter.terminal): plist with base64-encoded `NSColor` archives. Not hand-editable — regenerate via Terminal.app export if colors change.
- **[info.plist](info.plist)** — top-level TextMate/Sublime bundle metadata (name, uuid, rot13-obfuscated email). Rarely needs edits.

## Testing changes

There is no automated verification. Install the changed file into its target app ([README.md](README.md) has the install path for each) and eyeball it. Terminal.app's binary format in particular cannot be verified by reading the file.
