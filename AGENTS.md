# AGENTS.md — Hermes Team Canvas

## What This Is

Multiplayer infinite multimedia whiteboard plugin for Hermes. Public repo, open collaboration.

## Repo Structure

```
architecture/   — What we're building (design docs, diagrams)
adr/            — Decisions (numbered, MADR format)
research/       — What we've learned (landscape, comparisons, deep dives)
diagrams/       — Shared diagrams (not architecture-specific)
```

## Rules

- **Public repo.** No secrets, no internal fleet details, no credentials.
- **Research splits by topic, not by author.** If you're working on CRDTs, edit `research/interaction-pattern-matrix.md` — don't create a new file.
- **ADRs are numbered.** Check `adr/README.md` for the next number. One decision per file.
- **Diagrams are Mermaid.** `.mmd` files in `architecture/diagrams/` or `diagrams/`. Render with `npx @mermaid-js/mermaid-cli`.
- **STATUS.md is the source of truth** for what's done, in progress, and blocked.
- **CONTRIBUTING.md** explains conventions. Read it before adding files.

## Key Files

| File | Purpose |
|------|---------|
| `STATUS.md` | Project status — read first |
| `CONTRIBUTING.md` | How to add research, ADRs, diagrams |
| `architecture/README.md` | Design vision and principles |
| `research/README.md` | Research index |
| `adr/README.md` | ADR template and index |

## Current State

Background research phase. No code yet. Architecture and research documents being structured.
