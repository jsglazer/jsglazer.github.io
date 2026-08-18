---
layout: default
title: Integrated Research & Publishing Environment
---

# Integrated Research & Publishing Environment

This repository documents the setup, design, and integration of a modernized literature research, knowledge synthesis, and document publishing environment tailored for PhD-level research. By coupling Zotero's reference management capabilities with Obsidian's knowledge base features and the structured compilation of the HAL system, this setup forms a secure and efficient workspace for managing academic projects.

---

## Workflow Overview

The integrated environment standardizes document collection, annotation, concept mapping, and publishing into a systematic pipeline. It replaces fragmented workflows with a unified, compiler-driven knowledge graph. The workflow consists of the following core tasks:

- **Reading and Annotating PDFs in Zotero**: Digital sources of all types are converted to PDF format and annotated (using highlights and comments linked to specific highlight colors) directly in Zotero's native reader. Notes are then automatically exported and kept in sync with Obsidian.
- **Creating and Annotating Markdown in Obsidian**: Researchers can create original markdown notes and annotate both synced literature notes and original files using [MD Annotation](md-annotation.html), a delimiter-free, out-of-band annotation sidebar that preserves the clean plain-text structure of note bodies.
- **Synthesizing Knowledge via the HAL System**: Notes and articles are collected in a structured vault system inside `VaultSchar` (modeled after a compiler architecture) where an LLM compiler agent automatically indexes materials, writes document summaries (`DocSum/`), and identifies logical connections (`Connections/`) to build a cross-referenced research wiki.
- **Adding Citations Directly from Zotero**: Citations and bibliography details are pulled dynamically into Obsidian notes using [Zotero Manager](zotero-manager.html), supporting both local database queries and cloud Web API fallbacks.
- **Publishing and Document Export**: Finished articles, reports, or research summaries are compiled directly from Obsidian into publication-ready PDFs using [Multi Exporter](multi-exporter.html) with CSS Paged Media. Future output pipelines will support LaTeX, Microsoft Word/Powerpoint, and Apple Keynote.

---

## Workflow Diagrams

### Basic Workflow Pipeline
The diagram below maps the step-by-step researcher workflow from document acquisition through reference curation, note-taking, knowledge base compilation, and document publishing.

```mermaid
flowchart TD
    classDef input fill:#efe,stroke:#333,stroke-width:1px;
    classDef zotero fill:#eef,stroke:#333,stroke-width:1px;
    classDef obsidian fill:#fee,stroke:#333,stroke-width:1px;
    classDef hal fill:#fef,stroke:#333,stroke-width:1px;
    classDef publish fill:#ffe,stroke:#333,stroke-width:1px;

    subgraph Inputs ["1. Document Acquisition"]
        Web["Web Articles / Clippings"]:::input
        EPUB["EPUBs & Files (TXT, DOCX)"]:::input
        PDF["Digital PDFs"]:::input
        Paper["Physical Documents"]:::input
    end

    subgraph ZoteroEnv ["2. Reference Management (Zotero)"]
        ZC["Zotero Converter\n(Normalize formats to PDF)"]:::zotero
        ZReader["Zotero PDF Reader\n(Annotate with custom color labels)"]:::zotero
        BN["Better Notes\n(Sync notes to markdown)"]:::zotero
    end

    subgraph ObsidianEnv ["3. Note-Taking & Integration (Obsidian)"]
        ZM["Zotero Manager\n(Pull citations, sync labels)"]:::obsidian
        Notes["Obsidian Vault Notes\n(Literature & manual notes)"]:::obsidian
        MDA["MD Annotation\n(Delimiter-free annotations)"]:::obsidian
    end

    subgraph HALEnv ["4. Knowledge Synthesis (HAL System)"]
        RawKB["Raw Sources\n(Articles, Notes, Papers)"]:::hal
        HALCompile["HAL Compiler Agent\n(Claude / Gemini)"]:::hal
        WikiKB["Wiki Concept & Connections\n(Wiki/Concepts, Wiki/Connections, DocSum)"]:::hal
    end

    subgraph OutputEnv ["5. Production & Export"]
        ME["Multi Exporter\n(CSS Paged Media Preview & PDF)"]:::publish
        LaTeX["LaTeX / Word / Keynote\n(Future output pipelines)"]:::publish
    end

    Web --> ZC
    EPUB --> ZC
    PDF --> ZReader
    ZC --> ZReader
    Paper -->|Type or Dictate| Notes
    
    ZReader --> BN
    BN -->|Auto-Sync Markdown| ZM
    ZM --> Notes
    
    Notes --> MDA
    Notes -->|Ingest| RawKB
    
    RawKB --> HALCompile
    HALCompile --> WikiKB
    WikiKB -->|Reference & Query| Notes
    
    Notes --> ME
    WikiKB --> ME
    ME -->|Export PDF| Output["Final Research Document"]:::publish
```

### Data Flow Diagram
The diagram below illustrates how data flows between the primary databases and files across software systems, illustrating sync boundaries and compiler ingestion.

```mermaid
flowchart LR
    classDef zotero fill:#eef,stroke:#333,stroke-width:1px;
    classDef obsidian fill:#fee,stroke:#333,stroke-width:1px;
    classDef hal fill:#fef,stroke:#333,stroke-width:1px;
    classDef export fill:#ffe,stroke:#333,stroke-width:1px;

    subgraph ZoteroData ["Zotero Data Store"]
        ZDB[(Zotero Database)]:::zotero
        ZPDF[PDF Annotations]:::zotero
        BNNotes[Better Notes Export]:::zotero
    end

    subgraph ObsidianData ["Obsidian Note Vault"]
        OMD[Obsidian Notes .md]:::obsidian
        MDA_Meta[MD Annotation Sidebar Metadata]:::obsidian
    end

    subgraph HALData ["HAL Synthesis Store"]
        RawDocs[Raw Sources]:::hal
        DailyLogs[Daily Session Logs]:::hal
        Wiki[Wiki Concepts & Connections]:::hal
    end

    subgraph Publishing ["Output Format"]
        PagedPDF[CSS Paged Media PDF]:::export
    end

    ZPDF -->|Extracted by better-notes| BNNotes
    BNNotes -->|Synced as Markdown| OMD
    ZDB -->|Zotero Web API / local query by zotero-manager| OMD
    OMD -->|Coordinate-based metadata| MDA_Meta
    OMD -->|Ingested into Raw/| RawDocs
    DailyLogs -->|Compiled by HAL Compiler| Wiki
    Wiki -->|Direct markdown links| OMD
    OMD -->|Rendered via PagedJS| PagedPDF
    Wiki -->|Rendered via PagedJS| PagedPDF
```

---

## Software & Plugin Overview

Detailed specifications, feature matrices, setup requirements, and migration information for each component are provided on their dedicated subpages:

- **[Better Notes for Zotero](better-notes.html)**: A safe, sandbox-oriented fork of `zotero-better-notes` that synchronizes PDF reader annotations with Obsidian notes using Liquid templates and TypeScript security.
- **[Zotero Highlighter Descriptions](highlighter-descriptions.html)**: A Zotero plugin that maps default highlight colors to custom semantic and cognitive coding labels.
- **[Zotero Converter](zotero-convert.html)**: A Zotero utility plugin that converts non-PDF digital documents (EPUBs, web clippings, text files) into standardized PDF formats for unified annotation.
- **[Zotero Manager for Obsidian](zotero-manager.html)**: A modernized integration plugin that pulls citations, references, and annotations into Obsidian, supporting Web API fallback and Nunjucks persist blocks.
- **[MD Annotation for Obsidian](md-annotation.html)**: A delimiter-free markdown annotation and comment plugin that stores highlights out-of-band to preserve note body clean text.
- **[Multi Exporter for Obsidian](multi-exporter.html)**: A desktop-only Obsidian exporter that pagination-renders previews and PDFs using CSS Paged Media.
- **[HAL System](hal.html)**: A compiler-modeled research compiling vault inside `VaultSchar` that structures raw notes and daily session logs into a consistent academic wiki.
