---
layout: default
title: Zotero Converter
---

# Zotero Converter

## Overview
Zotero Converter (`zotero-convert`) is a Zotero plugin developed by jsglazer that automates the conversion of various digital source formats (such as EPUBs, Word documents, text files, and web pages) into standard PDF documents. Standardizing all files to PDFs solves the fragmentation problem in digital note-taking, enabling a unified annotation workflow inside Zotero's native PDF reader.

## Features
- **Auto-Conversion on Ingestion**: Detects non-PDF digital items when added to Zotero (e.g., EPUB, DOCX, TXT, Web clipping) and converts them to PDFs.
- **Child Attachment Management**: Attaches the newly generated PDF as a child item to the parent bibliographic item, keeping library files neat and organized.
- **Format Normalization**: Standardizes typography and layout during conversion, ensuring readability on both desktop and tablet readers.
- **Original Source Retention**: Retains original format attachments for reference while prioritizing the converted PDF for active reading, highlighting, and annotation.

## Requirements & Installation
1. **Download & Install**:
   - Download the `.xpi` file of `zotero-convert` from [GitHub releases](https://github.com/jsglazer/zotero-convert/releases).
   - In Zotero, select `Tools` > `Add-ons`, click the gear icon, choose `Install Add-on From File...`, select the `.xpi`, and restart Zotero.
2. **Dependencies**:
   - Ensure system-level conversion tools (such as Pandoc or LibreOffice headless binaries) are installed and added to your system `PATH` if converting Microsoft Word or EPUB formats.
3. **Preferences Setup**:
   - Go to `Tools` > `Zotero Converter Settings`.
   - Specify output PDF quality, compression levels, and auto-conversion triggers for newly imported files.

## Migration
- **Eliminating Manual Steps**: Replaces tedious manual PDF conversion workflows (such as "Print to PDF", web-to-PDF converters, or custom Automator shell scripts like `Md-Tex-PDF` and `Md-PDF`).

## Future Integrations (Placeholders)
- **Advanced LaTeX/Word Conversion**: Convert draft manuscript PDFs back to raw editable LaTeX or Word documents with citations preserved.
- **Keynote PDF slide splitter**: Automate the conversion and splitting of PowerPoint/Keynote PDFs into single-slide notes inside Zotero.
