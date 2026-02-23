# OpenClaw Technical Dossier

This repository contains a technical source-code analysis package for OpenClaw, designed for four primary audiences:

- Agent Architect
- AI Agent Engineer
- LLM Engineer
- LLM/Agent Data Scientist

## Documentation Structure

- `docs/baseline-v1/`: original first-pass documentation, preserved as-is in a subfolder
- `docs/deep-dive-v2/`: second-generation super deep-dive set
- `docs/deep-dive-v3/`: **ultra deep-dive (PhD-level)** set with formal models, Mermaid diagrams, and file/function call-flow analysis

## Current Deep-Dive Snapshot

- Source repo: `https://github.com/openclaw/openclaw`
- Commit: `445c7a65e6d1348f5a64f3ca8ad45369d0ab2027`
- Commit time: `2026-02-23 18:19:23 +0000`

## Quick Start

1. Read `docs/deep-dive-v3/00_navigator.md`
2. Choose a role-based reading track
3. Use `docs/baseline-v1/` and `docs/deep-dive-v2/` as evolution references

## Snapshot Size (Approximate)

- Total files: ~6,245
- LOC in `src/`: ~654,679
- TypeScript files (repo-wide): ~4,427
- Tests in `src` (test/e2e/live patterns): ~1,355
- Plugin manifests: 36

## Note

This dossier focuses on implementation behavior and runtime architecture. It does not replace official OpenClaw operational documentation.
