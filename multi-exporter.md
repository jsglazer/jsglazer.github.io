---
layout: default
title: Multi Exporter for Obsidian
---

# Multi Exporter for Obsidian

## Overview
Multi Exporter (`multi-exporter`) is a desktop-only Obsidian plugin developed by jsglazer that exports notes to high-quality, publication-ready PDFs using CSS Paged Media. Its core design principle is absolute layout consistency: the editor's live preview renders the exact paginated output, ensuring that the final exported PDF never drifts from what you see on the screen.

## Features
- **CSS Paged Media Support**: Uses the PagedJS polyfill to support professional print features like margins, running headers/footers, and page numbers.
- **Drift-Free Live Preview**: The in-app preview is generated directly by the paginating webview, removing formatting drift.
- **Custom Profile Stylesheets**: Apply normalizations or layout overrides via profile-specific CSS stylesheets, allowing note layouts to adapt to various submission formats (e.g., reports, research papers).
- **Pagination Diagnostics & Warnings**: Automatically logs layout reports, warning when specific DOM elements fail to fit within page boxes and must be moved to subsequent pages.

## Requirements & Installation
1. **Install Plugin**:
   - Open Obsidian.
   - Search for `Multi Exporter` in community plugins (or manually copy folder into `.obsidian/plugins/multi-exporter/`).
   - Enable the plugin in Settings.
2. **Print Stylesheets Snippet**:
   - Create a CSS snippet under `.obsidian/snippets/print-styles.css` using standard CSS Paged Media rules (e.g., `@page { size: A4; margin: 20mm; }`).
   - Enable the snippet in Obsidian settings > `Appearance` > `CSS snippets`.
3. **Configure Export Profiles**:
   - Go to Multi Exporter plugin settings.
   - Create export profiles (e.g., "Academic Manuscript", "Executive Summary") and map them to their corresponding CSS snippets.

## Migration
- **Replacing Standard PDF Export**: Replaces Obsidian's built-in print-to-PDF tool, which often suffers from page-break cuts, line slicing, and header/footer limitations.
- **Replacing External Compilers**: Offers a lightweight, inside-Obsidian alternative to running external PDF converters like Pandoc or Typst.

## Future Integrations (Placeholders)
- **LaTeX Academic Layout Export**: Enable compiling markdown directly to structured LaTeX articles with complete style support using local LaTeX engines.
- **Microsoft Word / PowerPoint Handouts**: Compile slides and outline handouts directly from Obsidian to native `.docx` and `.pptx` documents using preset styling sheets.
- **Apple Keynote Slide Deck Generator**: Convert pagination boundary files into native Keynote slides via macOS automation scripts.
