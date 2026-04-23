# Palette

The single source of truth for the Commuter color scheme. When porting to a new editor, read this document — not other theme files. Each file in [`Themes/`](Themes) is downstream from this doc; if they disagree, this doc wins.

## Design principles

- **Graphite base, not pure black.** Softer on the eyes in bright environments; avoids muddy contrast in dim ones.
- **Cyan accent is navigational.** Reserve `accent` (`#109AC4`) for focus rings, active panes, links, and badges. Never use it for content.
- **Warm tones carry meaning.** Orange warns, red errors, green succeeds, rose strings, magenta escapes. Never decorative.
- **Muted by default.** Most code is `text` or `text-muted`. Color marks exceptions.
- **Dark theme only.** No light variant — editors that ship defaults can use theirs.

## Colors

| Token | Hex | Role |
| --- | --- | --- |
| `bg` | `#262626` | Editor background |
| `surface` | `#252931` | Chrome (sidebars, tabs, status bar, panels, title bar) |
| `surface-active` | `#2D323C` | Active surface (current tab, active line, focused item) |
| `border` | `#1E2229` | Chrome borders |
| `rule` | `#363636` | Faint lines (inactive indent guide, ansi black) |
| `rule-bright` | `#565656` | Brighter lines (active indent guide, scrollbar, bright ansi black) |
| `text` | `#DADADA` | Default foreground |
| `text-muted` | `#BABABA` | Secondary text (inactive tabs, line numbers, muted icons) |
| `text-disabled` | `#888888` | Disabled text, ignored files |
| `text-fainter` | `#70727E` | Function argument/result types |
| `whitespace` | `#BFBFBF` | Invisibles |
| `accent` | `#109AC4` | Focus, active pane, links, badges, prompt |
| `accent-hover` | `#29A0BB` | Accent hover (buttons) |
| `selection` | `#4D97FF66` | Selection (40% alpha) |
| `selection-soft` | `#4D97FF1A` | Soft match / word highlight (10%) |
| `selection-bracket` | `#4D97FF33` | Bracket match / strong word highlight (20%) |
| `selection-find` | `#4D97FFAA` | Current find match (67%) |
| `comment` | `#CCCC99` | Comments, quotes (italic) |
| `keyword` | `#99CCFF` | Keywords, constants, variables, tags, imports, preprocessor, headings, lists |
| `variable-special` | `#88BFFE` | Library variable (`support.variable` / `variable.special`) |
| `cyan` | `#66CCCC` | Library functions, link URIs |
| `type` | `#99CC66` | Types, classes, attributes, enums |
| `success` | `#79B24F` | Additions, success, added ansi green |
| `warning` | `#FF9933` | Numbers, warnings, modifications, debug, ansi yellow |
| `error` | `#FF5252` | Errors, deletions, ansi bright red |
| `string` | `#FF8686` | Strings |
| `escape` | `#FF0099` | Character escapes, string interpolation |

**Off-palette one-offs** (intentional, used in exactly one place each):

| Hex | Used for |
| --- | --- |
| `#68685B` | `meta.tag.preprocessor.xml` (dims `<?xml ?>` to the point of disappearing) |
| `#990000` | `invalid` background |
| `#77CC88` | `invalid.deprecated.trailing-whitespace` background |

Don't introduce new one-offs. If a scope needs a color and none of the palette tokens fit, add a new palette entry here first, then apply it across ports.

## TextMate syntax scopes

Canonical mapping for any editor that uses TextMate-style scope selectors (TextMate, Sublime, Xcode, VS Code). Zed uses different scope names — see the next section.

| Scope | Token | Style |
| --- | --- | --- |
| `comment` | `comment` | italic |
| `keyword`, `storage.type.primitive`, `storage.type.namespace`, `storage.modifier` | `keyword` | — |
| `constant`, `constant.language`, `variable.language`, `variable.other` | `keyword` | — |
| `constant.numeric` | `warning` | — |
| `string` | `string` | — |
| `constant.character.escape`, `string source` | `escape` | — |
| `meta.preprocessor` | `keyword` | — |
| `keyword.control.import`, `storage.type.import` | `keyword` | — |
| `entity.name.function`, `support.function.any-method` | `text` | — |
| `entity.name.type` | `type` | — |
| `entity.other.inherited-class` | `type` | italic |
| `variable.parameter` | `text` | — |
| `storage.type.method` | `text-fainter` | — |
| `storage.type` | `type` | — |
| `punctuation.terminator`, `keyword.operator.js` | `text` | — |
| `meta.section entity.name.section` | `text` | italic |
| `support.function` | `cyan` | — |
| `support.class`, `support.type` | `type` | — |
| `support.constant` | `keyword` | — |
| `support.variable` | `variable-special` | — |
| `invalid` | `#FFFFFF` on `#990000` | — |
| `invalid.deprecated.trailing-whitespace` | `text` on `#77CC88` | — |
| `text source`, `string.unquoted` | `text` | — |
| `meta.tag.preprocessor.xml` | `#68685B` | — |
| `meta.tag.sgml.doctype` (and descendants) | `keyword` | — |
| `string.quoted.docinfo.doctype.DTD` | `text` | italic |
| `meta.tag`, `declaration.tag`, `entity.name.tag` | `keyword` | — |
| `entity.other.attribute-name` | `type` | — |
| `markup.heading` | `keyword` | — |
| `markup.quote` | `comment` | italic |
| `markup.list` | `keyword` | — |
| `markup.underline.link`, `string.other.link` | `cyan` | underline |
| `markup.bold` | `text` | bold |
| `markup.italic` | `text` | italic |
| `markup.inserted` | `success` | — |
| `markup.deleted` | `error` | — |
| `markup.changed` | `warning` | — |

## Zed syntax overrides

Zed uses its own token namespace. Map to palette tokens as follows:

| Zed token | Palette token |
| --- | --- |
| `comment` | `comment` (italic) |
| `keyword`, `constant`, `variable`, `property`, `tag`, `preproc`, `punctuation.list_marker` | `keyword` |
| `variable.special` | `variable-special` |
| `boolean`, `number` | `warning` |
| `string`, `string.regex`, `string.special`, `string.special.symbol` | `string` |
| `string.escape`, `punctuation.special` | `escape` |
| `function`, `operator`, `punctuation`, `primary`, `namespace` | `text` |
| `punctuation.bracket`, `punctuation.delimiter` | `text-muted` |
| `type`, `constructor`, `enum`, `variant` | `type` |
| `attribute` | `#29A0BB` italic (accent-hover) |
| `emphasis`, `emphasis.strong`, `label`, `link_text` | `accent` |
| `link_uri` | `cyan` |
| `title` | `keyword` (weight 600) |
| `predictive`, `hint` | `text-muted` (italic for predictive) |

## UI color roles

Editor / workbench concepts that every port should cover when the target format supports them.

### Editor surface

| Role | Value |
| --- | --- |
| Editor background | `bg` |
| Editor foreground | `text` |
| Cursor | `text` |
| Line highlight | `#00000012` (2% black overlay) |
| Selection | `selection` |
| Inactive selection | `selection-bracket` or `selection` at ~20% |
| Find match (current) | `selection-find` |
| Find match (other) | `selection` |
| Word highlight | `selection-soft` (read) / `selection-bracket` (write) |
| Bracket match | border `accent`, background `selection-bracket` |
| Whitespace / invisibles | `whitespace` |
| Indent guide | `rule` (inactive) / `rule-bright` (active) |
| Line number | `text-muted` (inactive) / `text` (active) |
| Link text | `accent` |
| Link hover | `cyan` |

### Diagnostics & VCS

| Role | Value |
| --- | --- |
| Error diagnostic | `error` |
| Warning diagnostic | `warning` |
| Info / hint diagnostic | `accent` / `text-muted` |
| Gutter modified | `warning` |
| Gutter added | `success` |
| Gutter deleted | `error` |
| Git: modified | `warning` |
| Git: added / untracked | `success` |
| Git: deleted | `error` |
| Git: renamed | `accent` |
| Git: conflicting | `warning` |
| Git: ignored | `text-disabled` |
| Diff inserted | `success` at 10% alpha |
| Diff removed | `error` at 10% alpha |

### Chrome

| Role | Value |
| --- | --- |
| Sidebar / panel / tabs / status bar / title bar background | `surface` |
| Chrome borders | `border` |
| Active tab background | `surface-active` |
| Active tab border (indicator) | `accent` |
| Active tab foreground | `text` |
| Inactive tab foreground | `text-muted` |
| Sidebar item hover / selected (inactive) | transparent bg (`#00000022`), `accent` foreground |
| Sidebar item focused | `surface-active` bg, `text` foreground |
| Focused pane border | `accent` |
| Badge | `accent` bg, `text` fg |
| Button | `accent` bg, `text` fg, `accent-hover` on hover |
| Input background | `surface-active` |
| Dropdown / menu background | `surface` |
| Scrollbar slider | `#56565688` → `#666666AA` hover → `#666666CC` active |
| Status bar (debugging) | `warning` bg, `bg` fg |

## Terminal ANSI palette

16 slots, shared by every terminal target (Ghostty, Zed, VS Code, Terminal.app). Bright red is softer (rose), bright yellow is the comment tone — this matches `less` / `ls --color` conventions where "bold" is a hue shift, not a lightness boost.

| Slot | Name | Hex |
| --- | --- | --- |
| 0 | black | `#363636` |
| 1 | red | `#FF5252` |
| 2 | green | `#79B24F` |
| 3 | yellow | `#FF9933` |
| 4 | blue | `#99CCFF` |
| 5 | magenta | `#FF0099` |
| 6 | cyan | `#66CCCC` |
| 7 | white | `#DADADA` |
| 8 | bright black | `#565656` |
| 9 | bright red | `#FF8686` |
| 10 | bright green | `#99CC66` |
| 11 | bright yellow | `#CCCC99` |
| 12 | bright blue | `#3399FF` |
| 13 | bright magenta | `#FF3399` |
| 14 | bright cyan | `#99DDDD` |
| 15 | bright white | `#EEEEEE` |

## Conventions

- **Hex uppercase**, with 8-digit alpha where needed (`#4D97FF66`). Ghostty is the one exception — lowercase there, to match Ghostty's stock themes.
- **No font-family or size decisions** in the theme. A color theme sets colors; leave the user's font alone. (The Xcode and Alfred themes name font families because their formats require it — keep those defaults.)
- **Palette drift is a bug.** See the "off-palette one-offs" note above before adding a new hex value anywhere.

## Adding a new port

1. Read the target editor's theme format docs.
2. Work from this document, not from an existing theme file. Starting from an existing file is how drift propagates.
3. Encode each role using the palette tokens from the tables above.
4. Add a row to the editor table in [README.md](README.md) and a format-notes bullet in [CLAUDE.md](CLAUDE.md).
5. Install locally and eyeball: a code sample (comments, keywords, strings, numbers, types, tags), a markdown file, a git diff view, a terminal session, focused vs. unfocused panes, error squiggles.
