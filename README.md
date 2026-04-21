# Commuter Theme

> Vaseline for your eyes — without the smudge.

A color theme crafted for reading code on the train. After years of testing, it works equally well in dark *and* light environments (no commute required).

---

## Supported Editors

| Editor       | Theme File                                                 |
| ------------ | ---------------------------------------------------------- |
| TextMate     | `Commuter.tmTheme`                                         |
| Sublime Text | `Commuter.tmTheme`                                         |
| Xcode        | `Commuter.dvtcolortheme`                                   |
| Zed          | `Commuter.json`                                            |
| Obsidian     | `Commuter.obsidian.css` + `Commuter.obsidian-manifest.json` |
| Ghostty      | `Commuter.ghostty`                                         |
| Terminal.app | `Commuter.terminal`                                        |

All theme files live in the [`Themes/`](Themes) directory.

## Installation

### TextMate
Double-click `Themes/Commuter.tmTheme` to install.

### Sublime Text
Copy `Themes/Commuter.tmTheme` into your `Packages/User/` directory, then select it from **Preferences → Color Scheme**.

### Xcode
Copy `Themes/Commuter.dvtcolortheme` into:

```
~/Library/Developer/Xcode/UserData/FontAndColorThemes/
```

Restart Xcode and pick **Commuter** under **Preferences → Themes**.

### Zed
Copy `Themes/Commuter.json` into:

```
~/.config/zed/themes/
```

Then select **Commuter** from the theme picker (`cmd-k cmd-t`).

### Obsidian
Obsidian expects a folder per theme. In your vault:

```
<Vault>/.obsidian/themes/Commuter/
├── manifest.json   ← from Commuter.obsidian-manifest.json
└── theme.css       ← from Commuter.obsidian.css
```

Create the folder, copy the two files in (renaming them as shown), then enable **Commuter** under **Settings → Appearance → Themes**. Dark mode only — in light mode Obsidian's defaults apply.

### Ghostty
Copy `Themes/Commuter.ghostty` into `~/.config/ghostty/themes/` as `Commuter` (no extension), then add to `~/.config/ghostty/config`:

```
theme = Commuter
```

### Terminal.app (macOS)
Double-click `Themes/Commuter.terminal` (or drag it into **Terminal → Settings → Profiles**) to import. Select the profile and click **Default** to make new windows use it. Colors only — your font, size, and cursor prefs are untouched.

## License

Free to use, tweak, and share.
