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

## Requirements
- Zotero 6 or Zotero 7.
- External document processors (e.g., Pandoc or system-level PDF conversion utilities) if required by the plugin config.

## Migration
- **Eliminating Manual Steps**: Replaces tedious manual PDF conversion workflows (such as "Print to PDF", web-to-PDF converters, or custom Automator shell scripts like `Md-Tex-PDF` and `Md-PDF`).
