---
layout: default
title: Zotero Highlighter Descriptions
---

# Zotero Highlighter Descriptions

## Overview
Highlighter Descriptions (`zotero-highlighter-descriptions`) is a Zotero plugin that allows researchers to map standard highlight colors in Zotero's PDF reader to specific cognitive or semantic categories. By assigning descriptive label names to highlight colors (e.g., Red = "Disagree/Skeptical", Yellow = "Key Finding"), it establishes a rigorous and consistent coding regime that survives exports and translates cleanly to note-taking templates.

## Features
- **Custom Color Label Naming**: Provides an interface within Zotero settings to define descriptive names for Zotero's default annotation colors.
- **Cognitive Mapping Regime**: Facilitates standard academic coding schemes. For example:
  - **Red**: Disagree/skeptical of author's point, or debunked by other studies.
  - **Yellow**: Key point; to be included in note summaries (most frequently used).
  - **Green**: Agree with claims; quotes to include directly in my work.
  - **Purple**: Sections and structural headings.
  - **Blue**: Connection to another source or research question (often paired with a comment).
  - **Pink**: Confusing or needs clarification.
  - **Orange**: Key definitions.
- **Integration with Better Notes & Zotero Manager**: Color names are output during Better Notes note generation, allowing downstream markdown notes in Obsidian to style or query highlights by their semantic category rather than just color.

## Requirements & Installation
1. **Download Plugin**: Download the latest `.xpi` file of `zotero-highlighter-descriptions` from [GitHub releases](https://github.com/jsglazer/zotero-highlighter-descriptions/releases).
2. **Install in Zotero**:
   - Open Zotero, go to `Tools` > `Add-ons`, click the gear icon, select `Install Add-on From File...`, and install the `.xpi` file.
   - Restart Zotero.
3. **Map Color Values**:
   - Go to Zotero Preferences > Highlighter Descriptions.
   - Map each default highlight color (Yellow, Red, Green, etc.) to your preferred semantic label (e.g., `Yellow` = `Key Finding`, `Red` = `Disagree`).
4. **Matched Obsidian Configuration**:
   - Ensure the color labels match your Obsidian `zotero-manager` stylesheet mappings.

## Migration
- **Establishing a Standard**: This plugin replaces arbitrary, unmapped highlighting habits with a structured, labeled annotation taxonomy.
- **Zotero to Obsidian Mapping**: Note that while Zotero Better Notes exports highlight color names, the Obsidian Zotero Manager plugin settings map these color names to functions (e.g., `Yellow => Key`) using a custom CSS/mapping table.

## Future Integrations (Placeholders)
- **Word/Keynote Style Mapping**: Automatically maps highlighting color descriptions to MS Word styles or Apple Keynote slide layouts when copying text.
- **LaTeX Color Syntax**: Export color categories directly to LaTeX `xcolor` definitions inside bibliography pages.
