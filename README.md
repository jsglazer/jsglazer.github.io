---
layout: default
title: Zotero-Obsidian Research Workflow
---

I'm an incoming PhD student in public policy. Before I start school, I decided to prepare a modern workflow for taking both digital and paper notes. I leveraged the amazing work of developers who build plug-ins for Zotero and Obsidian, namely [windingwind's zotero-better-notes](https://github.com/windingwind/zotero-better-notes) and [obsidian-zotero-integration](https://github.com/mgmeyers/obsidian-zotero-integration). I am releasing a modernized set of these plug-ins, plus other tools, which are more efficient and secure than their predecessors.

The core workflow remains annotating digital items in Zotero and keeping notes in Obsidian. Zotero remains the platform for managing citations (digital and paper) and creating annotations. Obsidian remains the platform for taking notes, developing wikis, utilizing spaced repetition, and other knowledge management activities.

My new plugins replace the following:

- [Better Notes for Zotero](https://github.com/jsglazer/better-notes)
- [Highlighter Descriptions for Zotero](https://github.com/jsglazer/zotero-highlighter-descriptions)
- [Zotero Converter](https://github.com/jsglazer/zotero-convert) (new plug-in for converting all sources to PDF)
- [Zotero manager for Obsidian](https://github.com/jsglazer/zotero-manager)

---

# Zotero & Obsidian Plugins: Migration & Feature Overview

This document outlines the major feature, architectural, and language improvements when moving to the modernized versions of the Zotero and Obsidian integration plugins maintained by [@jsglazer](https://github.com/jsglazer).

---

## 1. Zotero Plugin: windingwind's `zotero-better-notes` ➔ jsglazer's `better-notes`

The new [better-notes](https://github.com/jsglazer/better-notes) is a direct fork of [windingwind's zotero-better-notes](https://github.com/windingwind/zotero-better-notes), focused on safety, reliability, and tighter Obsidian integration.

### 🚀 Key Improvements & New Features

- **Native Annotation Color Labels:** Assign meanings/labels to highlight colors (e.g., *Yellow = "Key Finding"*, *Red = "Contradiction"*). These can be printed alongside annotations or used to group annotations into structured sections using `{% raw %}{% annotations grouped %}{% endraw %}`.
- **Multiple Synced Notes per Item:** Each Zotero item can now sync multiple independent notes to disk. The plugin prompts for a short unique ID if there is a filename clash.
- **Automatic 3-Way Merge:** Handles sync conflicts by performing an automatic 3-way merge on non-conflicting edits. True conflicts present a diff viewer.
- **Dedicated Keyboard Shortcuts:**
  - `⌃⌥S` — Run sync immediately (syncs all notes)
  - `⌃⌥M` — Open Sync Manager
  - `⌃⌥T` — Open Template Editor
  - `⌃⌥P` — Open Zotero Plugins/Add-ons window
- **Better Sync Management & Exports:** Cleaner markdown outputs, improved error handling, and additional context menu items.

### 🏗️ Architectural & Language Improvements

- **Sandboxed Liquid Templates:** Replaced the original arbitrary-JavaScript template engine with a safe, sandboxed Liquid template language (using variables like `{% raw %}{{ item.title }}{% endraw %}` and filters like `| year`).
- **Strict TypeScript:** Re-written and compiled under strict TypeScript rules to eliminate runtime crashes.

### ⚠️ Migration Details & Features Lost

> [!WARNING]
> **JavaScript Templates are Lost**
> Arbitrary JavaScript execution within templates has been removed for sandboxing and security reasons.
> 
> **Migration Action:** You must rewrite any custom JavaScript-based templates into **Liquid syntax**. For example:
> - *Old (JS):* `item.getField('title')`
> - *New (Liquid):* `{% raw %}{{ item.title }}{% endraw %}`

---

## 2. Obsidian Plugin: mgmeyers' `obsidian-zotero-integration` ➔ jsglazer's `zotero-manager`

The new [zotero-manager](https://github.com/jsglazer/zotero-manager) is a modernized replacement for the original [obsidian-zotero-integration](https://github.com/mgmeyers/obsidian-zotero-integration), built for modern Obsidian versions.

### 🚀 Key Improvements & New Features

- **Zotero Web API Fallback Mode:** Allows the plugin to work entirely without local Zotero running or Better BibTeX being installed by pulling data directly from Zotero's cloud servers.
- **Overwrite Protection:** Displays a confirmation modal before overwriting existing files in your vault.
- **Persist Blocks:** Supports Nunjucks persist blocks (`{% raw %}{% persist "key" %}...{% endpersist %}{% endraw %}`) that preserve manual edits you make inside Obsidian notes during subsequent imports or syncs.
- **Connection Status Badges:** Live **Linked** / **Not Linked** badge in the plugin settings to debug connection issues.
- **Color Label Integration:** Supports formatting annotations using the custom color labels configured in the companion Zotero `better-notes` plugin.

### 🏗️ Architectural & Language Improvements

- **No External Binaries:** Extracts PDF annotations using Zotero 6's native API, removing the need to download and run platform-specific binaries.
- **Strict TypeScript & Modern Obsidian API:** Rebuilt using strict TypeScript on Obsidian API 1.4+ (upgraded from mgmeyers' loose TypeScript on 1.1.x).

### ⚠️ Migration Details & Features Lost

> [!NOTE]
> **High Template Compatibility**
> The template engine remains **Nunjucks**, making your existing templates from `obsidian-zotero-integration` highly compatible.
> 
> **Web API Limitation:** The Zotero native item picker (CAYW) is unavailable in Zotero Web API fallback mode. The plugin falls back to an in-Obsidian search modal.

### Feature Comparison Matrix

| Feature | `obsidian-zotero-integration` (Old) | `zotero-manager` (New) |
| --- | --- | --- |
| **PDF Annotation Extraction** | Runs external GitHub binaries | Uses Zotero 6 native API |
| **Web API Fallback (No Local Zotero)** | ❌ No | ✔️ Yes |
| **TypeScript Compilation** | Loose | Strict |
| **Obsidian API Target** | 1.1.x (Outdated) | 1.4+ (Modern) |
| **Overwrite Protection** | ❌ None | ✔️ Confirm modal |
| **Persist Blocks** | ❌ No | ✔️ Yes |
| **Template Engine** | Nunjucks | Nunjucks (compatible) |
