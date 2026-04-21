# Commuter for VS Code

> Vaseline for your eyes — without the smudge.

A dark, low-glare theme for VS Code (and compatible forks: Cursor, Windsurf, VSCodium). The same Commuter palette you get in TextMate, Xcode, Zed, Obsidian, Ghostty, and Terminal.app.

## Character

Graphite backgrounds reduce glare. Muted foregrounds make long sessions easier on tired eyes. Cyan marks focus, links, active panes, and other navigational moments. Warm tones carry semantic meaning (orange for warnings and modifications, red for errors, green for additions and success, rose for strings).

## Installation

VS Code expects an extension folder. In your extensions directory:

- macOS/Linux: `~/.vscode/extensions/commuter/`
- Windows: `%USERPROFILE%\.vscode\extensions\commuter\`

Create the folder and copy these files in (renaming as shown):

```
commuter/
├── package.json                           ← from Commuter.vscode-package.json
└── themes/
    └── Commuter-color-theme.json          ← from Commuter.vscode.json
```

Restart VS Code, then pick **Commuter** from **Code → Settings → Color Theme** (`⌘K ⌘T` on macOS).

The same layout works in Cursor (`~/.cursor/extensions/commuter/`) and VSCodium.

## Coverage

- editor, gutter, minimap, overview ruler
- syntax highlighting (TextMate scopes + semantic tokens)
- sidebar, activity bar, tabs, status bar, title bar, breadcrumbs
- panels (terminal, output, debug console) with 16-color ANSI palette
- lists, trees, inputs, dropdowns, buttons, badges
- diff editor, peek view, suggest widget, hover widget
- notifications, menus, git decorations
- error, warning, info, and debug severities

Dark theme only.
