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

## Requirements
- Obsidian 1.7.2+ (Desktop only, as webview engines are required for pagination preview rendering).

## Migration
- **Replacing Standard PDF Export**: Replaces Obsidian's built-in print-to-PDF tool, which often suffers from page-break cuts, line slicing, and header/footer limitations.
- **Replacing External Compilers**: Offers a lightweight, inside-Obsidian alternative to running external PDF converters like Pandoc or Typst.
