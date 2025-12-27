# Lizard TUI

Terminal User Interface for visualizing [Lizard](https://github.com/terryyin/lizard) code complexity analysis.

## Requirements

- Python 3.10+
- `textual` >= 0.40.0
- `lizard` >= 1.17.0
- `fzf` (optional, for path browsing)
- `fd` (optional, faster file finding)

## Usage

```bash
python3 lizard_tui.py [path]
```

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Ctrl+Q` | Quit (works everywhere, including input boxes) |
| `Ctrl+O` | Browse folders with fzf |
| `Ctrl+F` | Browse files and folders with fzf |
| `r` | Refresh analysis |
| `c` | Copy critical functions (CCN > 15) to clipboard (excludes test files) |
| `1` | Sort by CCN (descending) |
| `2` | Sort by NLOC (descending) |
| `3` | Sort by name |
| `?` | Show legend dialog |
| `ESC` | Clear filter / Close dialog |

## Layout

- **Left panel**: Summary stats and complexity distribution bars
- **Center**: Tabbed content (Files default, Functions)
- **Right panel**: Code preview (visible only in Functions tab)

## Features

- Parses Lizard text output
- Color-coded complexity levels:
  - Green: Low (CCN 1-5)
  - Yellow: Medium (CCN 6-10)
  - Orange: High (CCN 11-15)
  - Red: Critical (CCN > 15)
- Loading dialog with spinner during analysis
- Legend dialog explaining acronyms (CCN, NLOC, Tokens, Params, Length)
- Code preview panel shows selected function source
- Copy critical functions to clipboard (excludes *test* files)

## File Structure

```
lizard_tui.py    # Main TUI application
pyproject.toml   # Package configuration
CLAUDE.md        # This file
```

## Acronyms

- **CCN**: Cyclomatic Complexity Number - linearly independent paths through code
- **NLOC**: Non-commenting Lines of Code
- **Tokens**: Number of tokens (keywords, operators, identifiers)
- **Params**: Parameter count
- **Length**: Total lines including comments and blanks
