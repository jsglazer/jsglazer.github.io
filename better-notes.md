---
layout: default
title: Better Notes for Zotero
---

# Better Notes for Zotero

## Overview
Better Notes for Zotero is a safe, sandbox-oriented fork of windingwind's original `zotero-better-notes` plugin. It is designed to act as a secure, reliable bridge between Zotero's PDF reader annotations and Obsidian's markdown environment. It ensures that notes created inside Zotero can be exported and kept in sync with Obsidian vaults without executing arbitrary, unsafe JavaScript code. By utilizing strict TypeScript compilation, it guarantees runtime stability and eliminates common crashes.

## Features
- **Native Annotation Color Labels**: Assign semantic meanings or label names to standard highlight colors (e.g., Yellow = "Key Finding", Red = "Contradiction"). These labels can be printed alongside annotations or used to group annotations into structured sections using `{% raw %}{% annotations grouped %}{% endraw %}`.
- **Multiple Synced Notes per Item**: Each Zotero bibliographic item can sync multiple independent notes to disk. The plugin automatically prompts for a short unique ID if there is a filename clash.
- **Automatic 3-Way Merge**: Handles sync conflicts by performing an automatic 3-way merge on non-conflicting edits. True conflicts present a visual diff viewer to resolve changes.
- **Dedicated Keyboard Shortcuts**:
  - `⌃⌥S` — Run sync immediately (syncs all notes)
  - `⌃⌥M` — Open Sync Manager
  - `⌃⌥T` — Open Template Editor
  - `⌃⌥P` — Open Zotero Plugins/Add-ons window
- **Safe Template Sandboxing**: Replaced the original arbitrary-JavaScript template engine with a safe, sandboxed Liquid template language (using variables like `{% raw %}{{ item.title }}{% endraw %}` and filters like `| year`).
- **Strict TypeScript Architecture**: Re-written and compiled under strict TypeScript rules to eliminate runtime crashes.

## Requirements & Installation
1. **Download Plugin**: Download the latest release `.xpi` file of `better-notes` from the [GitHub releases page](https://github.com/jsglazer/better-notes/releases).
2. **Install in Zotero**:
   - Open Zotero.
   - Go to `Tools` > `Add-ons`.
   - Click the gear icon (top-right) and select `Install Add-on From File...`.
   - Choose the downloaded `.xpi` file and click `Install`.
   - Restart Zotero when prompted.
3. **Configure Sync settings**:
   - Go to `Tools` > `Better Notes` > `Sync Manager` or use shortcut `⌃⌥M`.
   - Configure the export destination path to point directly to your Obsidian vault's literature notes directory.
4. **Create Export Template**:
   - Go to the Template Editor (`⌃⌥T`).
   - Define custom templates (such as `ItemNoteMD-Liquid` and `Annotations-Liquid`) to render notes into markdown using Liquid tags.

## Migration
- **Replacing windingwind's `zotero-better-notes`**: To transition to jsglazer's modernized version, uninstall the old plugin and install `better-notes` from the release package.
- > [!WARNING]
  > **JavaScript Templates are Lost**
  > Arbitrary JavaScript execution within templates has been removed for sandboxing and security reasons.
  > 
  > **Migration Action:** You must rewrite any custom JavaScript-based templates into **Liquid syntax**. For example:
  > - *Old (JS):* `item.getField('title')`
  > - *New (Liquid):* `{% raw %}{{ item.title }}{% endraw %}`

## Future Integrations (Placeholders)
- **LaTeX Bibliographic Sync**: Export references directly using BibLaTeX syntax alongside notes for publication in LaTeX formats.
- **Word/Keynote Notes Support**: Export structured summaries formatted for quick integration with Microsoft Word outline imports and Keynote slides.
