# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

An Obsidian CSS theme ("Notion Darker") translated from the Typora [notion-style-darker](https://github.com/ciathyza/notion-style-darker) theme. Minimal, muted dark aesthetic with Notion-inspired design.

There is no build system, no package manager, and no test suite — this is a pure CSS project.

## File Layout

- `theme/theme.css` — the single deliverable: the Obsidian theme stylesheet
- `theme/manifest.json` — Obsidian theme metadata (name, version, minAppVersion, author)
- `reference/notion-style-darker.css` — the original Typora source theme (read-only reference)
- `reference/obsidian_app.css` — a snapshot of Obsidian's built-in CSS (read-only reference for class names and variables)
- `reference/obsidian_manifest.json` — reference manifest from another theme (Flexoki), kept for structural reference

## How to Test the Theme

Copy `theme/theme.css` into an Obsidian vault's theme folder:

```
<vault>/.obsidian/themes/Notion Darker/theme.css
```

Then in Obsidian: Settings → Appearance → Themes → select "Notion Darker".

Changes to `theme.css` are picked up immediately by Obsidian when the file is saved (no reload needed if the vault is open).

## Architecture

`theme.css` is organized into sections in this order:

1. **Color Palette** (`.theme-dark`) — CSS custom properties mapped from the Typora source variables. The mapping is documented inline.
2. **Typography** (`body`) — font stacks and base size.
3. **Headings, Layout, Components** (`:root`) — heading scale, layout widths, blockquote, checkbox, and code block variables.
4. **Inline Code** — distinct styling (red text, dark bg) separated from block code.
5. **Search Highlights** — gold highlight colours from the Typora source.
6. **Images / HR / Tables / Font Smoothing** — targeted overrides matching Typora's visual defaults.

When adding new sections, follow the existing comment banner style (`/* ===\n   Section Name\n   === */`) and document any non-obvious mapping from a Typora variable.

## Variable Mapping Convention

Typora CSS variables (e.g. `--bg-color`, `--accent-color`) are translated to Obsidian CSS variables (e.g. `--color-base-00`, `--accent-h/s/l`). The `reference/notion-style-darker.css` file is the source of truth for original values. Comments in `theme.css` record the original variable name when the mapping is not 1:1.
