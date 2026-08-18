---
layout: default
title: HAL System
---

# HAL System

## Overview
The HAL (Heuristics and Logics) system is an integrated knowledge compilation and research synthesis vault located in `VaultSchar`. Built on a "compiler analogy," HAL decouples raw source documentation from compiled conceptual knowledge. It utilizes a structured LLM agent (e.g., Claude or Gemini) to parse daily notes and raw files, compiling them into a tightly cross-referenced, queryable academic wiki complete with health testing (linting).

## Features
HAL operates across four conceptual layers representing a software compiler architecture:

- **Layer 1: Daily Logs (`Daily/`)**: Append-only logs capturing research sessions and discussions. These serve as the input logs documenting intellectual progress.
- **Layer 2: Raw Sources (`Raw/`)**: Curated and immutable source documents. Includes clipped web articles (`Articles/`), student notes (`Notes/`), and academic literature (`Papers/`).
- **Layer 3: The Wiki (`Wiki/`)**: The "executable" knowledge base compiled by the LLM. It includes:
  - `Wiki/Concepts/`: Single explanatory articles for key concepts.
  - `Wiki/Connections/`: Summaries of cross-cutting relationships connecting concepts.
  - `Wiki/DocSum/`: Standardized, 3-to-5 sentence summaries of raw sources.
  - `Wiki/QA/`: Saved answers to complex queries for cumulative knowledge building.
  - `Wiki/index.md`: An auto-updated catalog of all pages.
- **Layer 4: Configuration (`CLAUDE.md` / `GEMINI.md`)**: The compiler specification directing the LLM how to compile, update, lint, and query the vault.
- **Automated Linting**: Periodic health checks verifying link integrity (broken links), identifying orphan concepts, listing uncompiled daily logs, flagging stale pages, and detecting logical contradictions in compiled content.

## Requirements
- A Python environment configured in `/Users/josh/VaultSchar/HAL` (managed with the `uv` package manager).
- Structured folder hierarchy in `VaultSchar` (`Daily/`, `Raw/`, `Wiki/`).
- Markdown files with YAML frontmatter to support indexing.

## Migration
- **Structured Knowledge Graph**: Moving to the HAL system replaces unstructured, flat folders of notes with a formal compilation process where source materials and concepts are programmatically linked and cross-referenced.
- **AI-Managed Wiki**: The human researcher focuses on reading, annotating, and writing daily logs, while the compiler agent manages the indexing, cross-referencing, and layout of the compiled `Wiki` directory.
