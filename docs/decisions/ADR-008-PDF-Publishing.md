# ADR-008: PDF Publishing

## Status

Accepted

## Context

JBMC is intended to become publication-ready material. PDF output is required, but generated files must not replace the Markdown source.

## Decision

Markdown is the source of truth for JBMC publication material.

PDF files must be generated from Markdown sources.

## Principles

- Write Markdown so it can support GitBook and PDF publication.
- Keep diagrams and images organized in repository folders.
- Treat generated PDF files as outputs, not primary sources.
- Preserve readable Markdown before optimizing for PDF layout.

## Consequences

- Publication workflows must start from Markdown.
- PDF-related outputs belong under `pdf/`.
- Source documents must remain reviewable in Git.
