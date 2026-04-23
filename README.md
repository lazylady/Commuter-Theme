# Commuter Theme

> Vaseline for your eyes — without the smudge.

A color theme crafted for reading code on the train. After years of testing, it works equally well in dark *and* light environments (no commute required).

---

## Supported Apps

| App          | Theme File                                                 |
| ------------ | ---------------------------------------------------------- |
| Zed          | `Commuter.json`                                            |
| VS Code      | `Commuter.vscode.json` + `Commuter.vscode-package.json` + `Commuter.vscode-README.md` |
| Obsidian     | `Commuter.obsidian.css` + `Commuter.obsidian-manifest.json` + `Commuter.obsidian-README.md` |
| Alfred       | `Commuter.alfredappearance`                                |
| Xcode        | `Commuter.xccolortheme`                                    |
| Ghostty      | `Commuter.ghostty`                                         |
| Terminal.app | `Commuter.terminal`                                        |
| Sublime Text | `Commuter.tmTheme`                                         |
| TextMate     | `Commuter.tmTheme`                                         |

All theme files live in the [`Themes/`](Themes) directory. The palette, semantic roles, and scope mappings are documented in [`PALETTE.md`](PALETTE.md) — the source of truth for anyone porting Commuter to a new editor.

## Installation

### Zed
Copy `Themes/Commuter.json` into:

```
~/.config/zed/themes/
```

Then select **Commuter** from the theme picker (`cmd-k cmd-t`).

### VS Code
VS Code expects an extension folder. In your extensions directory:

```
~/.vscode/extensions/commuter/
├── package.json                     ← from Commuter.vscode-package.json
└── themes/
    └── Commuter-color-theme.json    ← from Commuter.vscode.json
```

Restart VS Code and pick **Commuter** from **Code → Settings → Color Theme** (`cmd-k cmd-t`). The same layout works for Cursor (`~/.cursor/extensions/commuter/`) and VSCodium.

### Obsidian
Obsidian expects a folder per theme. In your vault:

```
<Vault>/.obsidian/themes/Commuter/
├── manifest.json   ← from Commuter.obsidian-manifest.json
├── theme.css       ← from Commuter.obsidian.css
└── README.md       ← from Commuter.obsidian-README.md
```

Create the folder, copy the two files in (renaming them as shown), then enable **Commuter** under **Settings → Appearance → Themes**. Dark mode only — in light mode Obsidian's defaults apply.

### Alfred
Double-click `Themes/Commuter.alfredappearance` to import into Alfred, then pick **Commuter** under **Alfred Preferences → Appearance**. Typography is Avenir Next — adjust inside Alfred if you prefer a different face.

### Xcode
Copy `Themes/Commuter.xccolortheme` into:

```
~/Library/Developer/Xcode/UserData/FontAndColorThemes/
```

Restart Xcode and pick **Commuter** under **Settings → Themes**.

### Ghostty
Copy `Themes/Commuter.ghostty` into `~/.config/ghostty/themes/` as `Commuter` (no extension), then add to `~/.config/ghostty/config`:

```
theme = Commuter
```

### Terminal.app (macOS)
Double-click `Themes/Commuter.terminal` (or drag it into **Terminal → Settings → Profiles**) to import. Select the profile and click **Default** to make new windows use it. Colors only — your font, size, and cursor prefs are untouched.

### Sublime Text
Copy `Themes/Commuter.tmTheme` into your `Packages/User/` directory, then select it from **Preferences → Color Scheme**.

### TextMate
Double-click `Themes/Commuter.tmTheme` to install.

## License

Free to use, tweak, and share.
