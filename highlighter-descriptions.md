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

## Requirements
- Zotero 6 or Zotero 7.
- A matched color configuration mapping inside Obsidian's `zotero-manager` settings to translate color labels into appropriate CSS styles (e.g., matching Yellow to Key).

## Migration
- **Establishing a Standard**: This plugin replaces arbitrary, unmapped highlighting habits with a structured, labeled annotation taxonomy.
- **Zotero to Obsidian Mapping**: Note that while Zotero Better Notes exports highlight color names, the Obsidian Zotero Manager plugin settings map these color names to functions (e.g., `Yellow => Key`) using a custom CSS/mapping table.
