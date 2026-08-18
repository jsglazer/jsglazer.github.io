---
layout: default
title: Zotero Manager for Obsidian
---

# Zotero Manager for Obsidian

## Overview
Zotero Manager for Obsidian is a modernized replacement for the original `obsidian-zotero-integration` plugin (originally developed by mgmeyers). It provides a high-performance, secure way to import bibliographic metadata, citations, and PDF annotations directly from Zotero into your Obsidian vault. It is built to leverage modern Obsidian features, target strict TypeScript compiler standards, and run without external binaries.

## Features
- **Zotero Web API Fallback Mode**: Allows the plugin to operate entirely without a local Zotero application running or Better BibTeX being installed by querying Zotero's cloud servers directly.
- **Overwrite Protection**: Automatically prompts with a confirmation modal before overwriting any pre-existing files in your vault during import operations.
- **Persist Blocks**: Supports Nunjucks persist blocks (`{% raw %}{% persist "key" %}...{% endpersist %}{% endraw %}`) that preserve manual edits you make inside Obsidian notes during subsequent imports or sync runs.
- **Connection Status Badges**: Shows a live **Linked** / **Not Linked** badge in the plugin settings to facilitate easy debugging of connection issues.
- **Color Label Integration**: Supports formatting and styling annotations using the custom color labels configured in the companion Zotero `better-notes` plugin.
- **No External Binaries**: Extracts PDF annotations using Zotero's native APIs, removing the need to download and execute platform-specific binaries.
- **Strict TypeScript & Modern target**: Rebuilt using strict TypeScript on Obsidian API 1.4+ (upgraded from the loose TypeScript rules and 1.1.x targets of the predecessor).

## Requirements & Installation
1. **Install Plugin**:
   - Open Obsidian.
   - Go to `Settings` > `Community Plugins` and enable them.
   - Search for `Zotero Manager` (or copy the plugin folder containing `manifest.json`, `main.js`, and `styles.css` directly to your vault's `.obsidian/plugins/zotero-manager/` folder).
   - Toggle the plugin `On` to enable it.
2. **Configure Connection**:
   - Go to plugin settings.
   - For **Local Connection**: Ensure Zotero is running locally and the `Better BibTeX` plugin is installed in Zotero to supply citekeys. Verify the Live connection status badge shows **Linked**.
   - For **Web API Fallback**: Toggle Web API Mode on, enter your Zotero User ID and Web API Key, and fetch references directly from the cloud.
3. **Setup Templates**:
   - Design your import templates in Obsidian using Nunjucks formatting. Save templates in your vault's designated templates folder and select them in the plugin settings.

## Migration
- **High Template Compatibility**: The template engine remains **Nunjucks**, making your existing templates from `obsidian-zotero-integration` highly compatible with minimal or no modifications.
- **Web API Limitation**: The Zotero native item picker (CAYW) is unavailable in Zotero Web API fallback mode. The plugin automatically falls back to an in-Obsidian fuzzy-search modal.
- **Feature Comparison Matrix**:

| Feature | `obsidian-zotero-integration` (Old) | `zotero-manager` (New) |
| --- | --- | --- |
| **PDF Annotation Extraction** | Runs external GitHub binaries | Uses Zotero native API |
| **Web API Fallback (No Local Zotero)** | ❌ No | ✔️ Yes |
| **TypeScript Compilation** | Loose | Strict |
| **Obsidian API Target** | 1.1.x (Outdated) | 1.4+ (Modern) |
| **Overwrite Protection** | ❌ None | ✔️ Confirm modal |
| **Persist Blocks** | ❌ No | ✔️ Yes |
| **Template Engine** | Nunjucks | Nunjucks (compatible) |

## Future Integrations (Placeholders)
- **LaTeX/BibTeX Exporter**: Integration with LaTeX citekeys to support automatic `.bib` export from notes directly.
- **Pandoc Integration**: Direct connection with Pandoc to convert Zotero-imported markdown notes into Word documents or PowerPoint slides with citations.
